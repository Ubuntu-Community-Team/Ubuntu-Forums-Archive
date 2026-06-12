---
title: "Dialup Modem Help."
date: 2008-11-18
forum: General Help
---

### Post by Mickeyj4j on 2008-11-18
I am very New to Linux. I am using ubuntu 8.04.1 LTS Desktop edition, Instaled inside windows using 10gig.

I want to install my Dial-up Modem. I have scanned it and got a generic driver for it slmodem-2.9.11-20070422.tar. I have red the read-me file. I can see what it wants me to do but don't know how to do it. It says: 

Installation
============

1. Unpack tar.gz package file:

	$ gzip -dc slmodem-2.9.X.tar.gz | tar xf -

2. 'cd' to package directory:

	$ cd slmodem-2.9.X

3. Review and edit 'Makefile' (if need):

   In many cases you will need to correct path to your local kernel
   source tree:

        KERNEL_DIR=/path/to/linux

   Default KERNEL_DIR is '/lib/modules/<kerne-version>/build'. Many Linux
   Distributions use directory '/usr/src/linux-<version>' also.

   Note: If you are using Linux kernel 2.4, only header files should be
         available for build in $(KERNEL_DIR)/include

   Another way to pass right value KERNEL_DIR is to use command line
   parameter while running 'make':

        $ make KERNEL_DIR=/path/to/linux ...

4. Run 'make' command to compile package:

	$ make

5. Install. As 'root' user run:

	# make install

   It will install:

   - application 'slmodemd' under '/usr/sbin' directory

   - hardware specific drivers (kernel modules) 'slamr' and 'slusb'
     under conventional kernel modules directory

   - character device nodes '/dev/slamr0-3' with major number 212
     (for pci modems) and '/dev/slusb0-3' with major number 213
     (for usb modems).

   - config modules for autoloading (by editing file '/etc/modules.conf')
     (only with 2.4 kernels)

6. Config modem country.

   Use AT+GCI=<T.35 country code> command to setup country.

   Also you can setup default modem country by passing command line
   parameter '--country=MY_COUNTRY' to program 'slmodemd'.

   See output of 'slmodemd --countrylist' for a list of supported
   country names and T.35 country codes (see also 'slmodemd --help').

   Note: Command ATI7 shows currently installed country setting.

8. Uninstallation.

   In package directory just type:

	# make uninstall
-----------------------------------------------------------------
:guitar: :-({|= :-\" \\:D/

[LIST=1]
[*]I cannot work it out?
[*]Is there a short cut to it?
[*]A direct installer package would be good, one that can run directly without having to use the terminal and know the program language?
[*]Where can i go to learn Linux?
[/LIST]

---

### Post by Mickeyj4j on 2009-03-12
I upgraded to Broadband now no problems with anything. I use Linux Mint its easier faster better than anything i seen.

---

### Post by Bartender on 2009-03-16
Well, upgrading to broadband is certainly *one* way to solve confusing dial-up instructions...;)

---

