Changelog
=========

For details and minor changes, please see the `version control log messages
<http://trac.chrisarndt.de/code/log/projects/python-rtmidi/trunk>`_.


2013-11-05 version 0.4.1b
-------------------------

Building:
  * Include missing ``_rtmidi.cpp`` file in source distribution.

Documentation:
  * Fill in release data placeholders in ``INSTALL.rst``.


2013-11-05 version 0.4b
-----------------------

Fixes:
  * Fix string conversion in constructors and ``open_*`` methods.

  * Change default value ``queue_size_limit`` argument to ``MidiIn``
    constructor to 1024.

  * Update version number in ``RtMidi.cpp/h`` to reflect actual code state.

Enhancements / Changes:
  * Elevated development status to beta.

  * Allow ``MidiIn/Out.open_port`` methods to be used with the ``with``
    statement and the port will be closed at the end of the block.

  * ``MidiIn``/``MidiOut`` and ``open*()`` methods: allow to specify ``None``
    as client or port name to get the default names.

  * Move ``midiconstants`` module from examples into ``rtmidi`` package
    and added ``midiutil`` module.

  * ``midiutils.open_midiport``:

    * Allow to pass (substring of) port name as alternative to port number.
    * Re-raise ``EOFError`` and ``KeyboardInterrupt`` instead of using
      ``sys.exit()``.
    * Add ``client_name`` and ``port_name`` arguments.
    * Add ``use_virtual`` argument (default ``False``) to request opening
      of a virtual MIDI port.
    * Add ``interactive`` keyword argument (default ``True``) to disable
      interactive prompt for port.

  * Raise ``NotImplemented`` error when trying to open a virtual port with
    Windows MultiMedia API.

  * Change default name of virtual ports.

Documentation:
  * Re-organize package description and installation instructions into several
    files and add separate text files with changelog and license information.

  * Add detailed instructions for compiling from source on Windows

  * Add docstrings to all methods and functions in ``_rtmidi`` module.

  * Add docstring for ``midiutils.open_midiport`` function.


Examples:
  * Add new example package ``osc2midi``, a simple, uni-directional OSC to MIDI
    mapper.

  * New example script ``sendsysex.py`` to demonstrate sending of MIDI system
    exclusive messages.

  * New example script ``wavetablemodstep.py`` to demonstrate sending of
    MIDI control change messages.

  * New ``sysexsaver`` example.

  * Convert ``midifilter`` example script into a package.

  * Upgrade  from ``optparse`` to ``argparse`` in example scripts.

  * Enable logging in test scripts.


Building:
  * Switch from ``distribute`` back to ``setuptools``.

  * Include ``ez_setup.py`` in source distribution.

  * Include examples in source distribution.

  * Install ``osc2midi`` example as package and command line script.

  * Enable C++ exceptions on Windows build.


2013-01-23 version 0.3.1a
-------------------------

Enhancements:
    * Increase sysex input buffer size for WinMM API again to 8192 (8k) bytes.
      Requested by Martin Tarenskeen.


2013-01-14 version 0.3a
-----------------------

Bug fixes:
    * Add ``encoding`` parameter to ``get_port_name`` methods of ``MidiIn``
      and ``MidiOut`` to be able to handle non-UTF-8 port names, e.g. on
      Windows (reported by Pierre Castellotti).
    * Add ``encoding`` parameter to ``get_ports`` method as well and pass it
      through to ``get_port_name``. Use it in the test scripts.

Enhancements:
    * Increase sysex input buffer size for WinMM API to 4096 bytes.

Examples:
    * Add new ``midifilter.py`` example script.

Building:
    * Add ``setuptools``/``distribute`` support.


2012-07-22 version 0.2a
-----------------------

Bug fixes:
    * Fix uninitialized pointer bug in ``RtMidi.cpp`` in 'MidiOutJack' class,
      which caused a warning in the jack process callback when creating a
      ``MidiOut`` instance with the JACK API.
    * ``testmidiin_*.py``: fix superfluous decoding of port name (caused error
      with Python 3).

Enhancements:
    * Simplify some code, some things gleaned from rtmidi_python.
    * Documentation typo fixes and more information on Windows compilation.
    * Enhancements in test scripts:

      * ``test_probe_ports.py``: Catch exceptions when creating port.
      * ``test_midiin_*.py``:

        * Better error message for missing/invalid port number.
        * Show how to convert event delta time into absolute time when
          receiving input.

Building:
    * Building on OS X 10.6.9 with CoreMIDI and JACK for OS X successfully
      tested and test run without errors.
    * WinMM support now compiles with Visual Studio 2008 Express and tests
      work under Windows XP SP3 32-bit.
    * Add command line option to exclude WinMM or WinKS API from compilation.
    * Add missing ``extra_compile_args`` to Extension kwargs in setup file.
    * Add ``library_dirs`` to Extension kwargs in setup file.
    * Use ``-frtti`` compiler option on OS X (neccessary on 10.7?).
    * Fix file name conflict on case-insensitive file systems by prefixing
      ``rtmidi.{pyx,cpp}`` with an underscore
    * Provide correct compiler flags for compiling with Windows MultiMedia API.
    * Adapt windows library and include path for Visual Studio 2008 Express.
    * add support for compiling with Windows Kernel Streaming API (does not
      not compile due to syntax errors in RtMidi.cpp yet).


2012-07-13 version 0.1a
-----------------------

First public release.