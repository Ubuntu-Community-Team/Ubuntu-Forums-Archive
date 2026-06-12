---
title: "new modem"
date: 2005-02-25
forum: Hardware &amp; Laptops
---

### Post by t3rm1n8r1x on 2005-02-25
okay, since my other modem wouldn't work, i swapped it out, only now i can't get ubuntu to recognize it in a way that i can use it to dial out, and i don't know which entry is actually the modem

lspci
0000:01:06.0 Ethernet controller: Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem
0000:01:06.1 Computer telephony device: Broadcom Corporation BCM4212 v.90 56k modem

scanpci
pci bus 0x0001 cardnum 0x06 function 0x00: vendor 0x14e4 device 0x4211
 Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem

pci bus 0x0001 cardnum 0x06 function 0x01: vendor 0x14e4 device 0x4212
 Broadcom Corporation BCM4212 v.90 56k modem

it's probably the second one, but doen anyone know where i can get drivers for this model?

---

### Post by az on 2005-02-25
[http://linmodems.technion.ac.il/](http://linmodems.technion.ac.il/)

Use this:
[http://linmodems.technion.ac.il/#scanmodem](http://linmodems.technion.ac.il/#scanmodem)

You probably have an unsupported software modem.  The people who manufactured it do not beleive you are important enough for them to 
1- make a driver for you
or
2- Release some source code or even some specifications about their product so that someone can write a driver for them.

You will have to go out and buy a supported software modem or a real hardware modem.

Good luck.
(Intel, lucent and smartlink modems have more support for linux than others.  Buy a modem with one of those chipsets.)

---

### Post by t3rm1n8r1x on 2005-02-25
is there any way to tell what kind of modem it is?

---

### Post by az on 2005-02-25
Yes.  Read the first few lines of the previous post.

Scanmodem will scan your modem.

Anyway, lspci shows it to be a broadcom modem.  It is no longer supported.

---

### Post by t3rm1n8r1x on 2005-02-25
i kinda doubt it's a soft-modem, because i didn't have to install a driver for it myself, windows did it automatically. If it's software-controlled, where'd the driver come from? the modem's never been in this computer before. now can you or somebody else help me get linux to recognize it?

---

### Post by t3rm1n8r1x on 2005-02-28
bump

---

### Post by az on 2005-02-28
What does scanmodem say?

here:

[http://65.70.147.202:8080/gromitkc/broadcom/bcm421x.html](http://65.70.147.202:8080/gromitkc/broadcom/bcm421x.html)

---

### Post by t3rm1n8r1x on 2005-02-28
this is what the main file that scanmodem generated says:

 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 4.10 kernel 2.6.8.1-3-386
 Occassionally reponses are blocked by an Internet Providers mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_Feb_ 21
------------ --------------  System information ------------------------
Ubuntu 4.10 "Warty Warthog" 
 on System with processor: i686
 currently under kernel:   2.6.8.1-3-386
 The kernel was assembled with compiler:  3.3.4
 with current System compiler GCC=3.3.4
    /usr/bin/gcc -> gcc-3.3

Checking for kernel-headers needed for compiling.
 kernel-headers have base folder /lib/modules/2.6.8.1-3-386/build
 kernel-headers have base folder /usr/src/linux-headers-2.6.8.1-3-386

 A /dev/modem symbolic link is not set.
 Checking for USB modems
 None found

Modem candidates are at PCI_buses:  0000:01:06.0
0000:01:06.1
    
Providing detail for device at PCI_bus 0000:01:06.0
  with vendor-ID:device-ID
	    ----:----
Class 0200: 14e4:4211   Ethernet controller: Broadcom Corporation BCM4211 iLine10 HomePNA 2.0 + V.90 56k modem
  SubSystem 13e0:0002   GVC Corporation: Unknown device 0002
	Flags: bus master, fast devsel, latency 32, IRQ 185
	Memory at ed002000 (32-bit, non-prefetchable)
	Capabilities: [40] Power Management version 2
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 14e4:4211 13e0:0002 debian 2.6.8.1-3-386 3.3.4 3.3.4    i686

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 14e4 is BroadCom 
   14e4:4212   is a  BCM V.90 56k modem
 There is 2.2.n kernel support at:
    [http://support.ap.dell.com/ap/en/filelib/download/index.asp?fileid=R47114](http://support.ap.dell.com/ap/en/filelib/download/index.asp?fileid=R47114)
 However the code has not been updated for some time.
 For  2.4 kernels, fix by Giacomo Comes must be used. See :
   [http://linmodems.technion.ac.il/archive-third/msg01652.html](http://linmodems.technion.ac.il/archive-third/msg01652.html)
 When serving under softmodem controllers like the Intel ICH series,
 the Broadcom Subsystem 14e4:4d64 has mc97 codec BCM64.
 For 2.6.n kernels, see success reports:
   [http://linmodems.technion.ac.il/archive-fourth/msg03690.html](http://linmodems.technion.ac.il/archive-fourth/msg03690.html)
   [http://oboc.ucdavis.edu/Marik/inspiron/](http://oboc.ucdavis.edu/Marik/inspiron/) 
   The support is achieved through a combination of:
   1) the snd-intel8x0m.ko of 2.6.n kernel releases, which provides a low level interface with the modem;
   2) an slmodemd daemon which creates ports and provides higher level functions.
   Get the slmodem-2.9.9-alsa.tar.gz from  [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
   To compile the slmodemd, it is first Necessary to install a libasound2-dev package, providing alsa headers.
   3) After compilation and installation of slmodemd, initiate service with:
   # modprobe  snd-intel8x0m
   # slmodemd --alsa --country=YOURCOUNTRY hw:0
   Read the slmodem documentation for details and Modem/Slmodem.txt


    
Providing detail for device at PCI_bus 0000:01:06.1
  with vendor-ID:device-ID
	    ----:----
Class 0402: 14e4:4212   Computer telephony device: Broadcom Corporation BCM4212 v.90 56k modem
  SubSystem 13e0:0002   GVC Corporation: Unknown device 0002
	Flags: bus master, fast devsel, latency 32, IRQ 185
	Memory at ed003000 (32-bit, non-prefetchable)
	I/O ports at c000 [size=16]
  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 14e4:4212 13e0:0002 debian 2.6.8.1-3-386 3.3.4 3.3.4    i686

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 14e4 is BroadCom 
   14e4:4212   is a  BCM V.90 56k modem
 There is 2.2.n kernel support at:
    [http://support.ap.dell.com/ap/en/filelib/download/index.asp?fileid=R47114](http://support.ap.dell.com/ap/en/filelib/download/index.asp?fileid=R47114)
 However the code has not been updated for some time.
 For  2.4 kernels, fix by Giacomo Comes must be used. See :
   [http://linmodems.technion.ac.il/archive-third/msg01652.html](http://linmodems.technion.ac.il/archive-third/msg01652.html)
 When serving under softmodem controllers like the Intel ICH series,
 the Broadcom Subsystem 14e4:4d64 has mc97 codec BCM64.
 For 2.6.n kernels, see success reports:
   [http://linmodems.technion.ac.il/archive-fourth/msg03690.html](http://linmodems.technion.ac.il/archive-fourth/msg03690.html)
   [http://oboc.ucdavis.edu/Marik/inspiron/](http://oboc.ucdavis.edu/Marik/inspiron/) 
   The support is achieved through a combination of:
   1) the snd-intel8x0m.ko of 2.6.n kernel releases, which provides a low level interface with the modem;
   2) an slmodemd daemon which creates ports and provides higher level functions.
   Get the slmodem-2.9.9-alsa.tar.gz from  [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)
   To compile the slmodemd, it is first Necessary to install a libasound2-dev package, providing alsa headers.
   3) After compilation and installation of slmodemd, initiate service with:
   # modprobe  snd-intel8x0m
   # slmodemd --alsa --country=YOURCOUNTRY hw:0
   Read the slmodem documentation for details and Modem/Slmodem.txt


  ======= PCI_ID checking completed ====== 
 Update=2005_Feb_ 21
A PCMCIA CardBus is not detected on this System.
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias char-major-108 ppp_generic
/etc/modprobe.d/aliases:alias tty-ldisc-3  ppp_async  
/etc/modprobe.d/aliases:alias tty-ldisc-14 ppp_synctty
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe
/etc/modprobe.d/aliases:alias ppp-compress-21 bsd_comp   
/etc/modprobe.d/aliases:alias ppp-compress-24 ppp_deflate
/etc/modprobe.d/aliases:alias ppp-compress-26 ppp_deflate
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/General.txt

  A port needed for the PPP protocol is absent!!!
  echo "  crw-------    1 root     root     108,   0 Dec 31  1969 /dev/ppp"

A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
ACPI: PCI Interrupt Link [LNK0] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by az on 2005-02-28
Great.  Try the sl-modem drivers.
install linux-headers, sl-modem-source and sl-modem-daemon.

Try installing the daemon first, since it will try the GPL alsa driver since you will not have compiled the non-free one.

If that does not work, compile the driver and try that.

---

### Post by t3rm1n8r1x on 2005-02-28
thanks.
if that doesn't work, i'll let you know

edit:
i can't wait til i have internet through ubuntu and can get this crap through synaptic

anyone know where to get modules-new?

dpkg: dependency problems prevent configuration of sl-modem-daemon:
 sl-modem-daemon depends on sl-modem-modules-new | sl-modem-source (>> 2.9.6-1) | kernel-image-2.6; however:
  Package sl-modem-modules-new is not installed.
  Package sl-modem-source is not installed.
  Package kernel-image-2.6 is not installed.
dpkg: error processing sl-modem-daemon (--install):
 dependency problems - leaving unconfigured

---

### Post by t3rm1n8r1x on 2005-03-01
allright, never mind about modules new, apparently those requirements were "or" and not "and", so i have the driver installed.

however, wvdialconf still can't find a modem? when ubuntu's booting, it says it makes a link to /dev/ttys0, i think, but wvdial says there isn't a device there? any(more) help would be greatly appreciated

---

### Post by az on 2005-03-01
"however, wvdialconf still can't find a modem? when ubuntu's booting, it says it makes a link to /dev/ttys0, i think, but"

ttyS0 would be a harware modem.  You have a software modem.

ttysl0 in this case.

---

### Post by t3rm1n8r1x on 2005-03-01
i noticed that during a reboot, and changed it. now it says i/o error

---

### Post by az on 2005-03-01
Are you using the alsa module or did you build the module?

To build the module, install build-essential and linux-headers-2.6.8.1-3-386

cd /usr/src
tar xvzf sl-modem-source*
cd to the directory

cd modules
cd sl-modem
sudo debian/rules binary


That should work.  Install the package it makes for you
cd ..
dpkg -i sl-modem-modules*.deb

---

### Post by t3rm1n8r1x on 2005-03-01
i'll try that now and see how it works

---

### Post by t3rm1n8r1x on 2005-03-01
i think i'm gonna need more in-depth instructions. i don't understand what i'm supposed to be doing, or where.
i've got build-essential and the headers and the sl-modem-source*.deb
when i type the tar command, it either says it can't read because it'sa directory or not in gzip format

---

### Post by az on 2005-03-02
There is only so much I can do.  Type
man ls
man tar

do 
dpkg -l sl-modem-source
and see where the source tarball is.  Then go there and untar it.  If it is already untarred, enter that directory and make the deb package by running the command I previously posted.

Basically, source code is compiled in to binary which can then be run by the computer. Source doe that is run by the computer is called a script and it rund ina script interpreter.  Bash, Python, perl are example of script languaged.  There are many programing languages.  Your kernel and their drivers are written in C.

To compile a C program, you need a C compiler (build-essential contains GCC, the GNU C Compiler)  A C program is usually a whole collection of files.  To compile all of them together, you have  a makefile.
To run a make file, you usually run make.  For many source packages, you need to do the following to install the,

tar xvzf <program>
cd <program>`
./configure
make
make install

this gets messy.  You have packages which are precompiled programs for you.  Anyway.  You will be making a package out of your sl-modem source.

You will be invoking a special makefile called debian rules.

debian/rules binary.


Off you go!

Good luck.

Links:
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://chguy.net/newbie/index.html](http://chguy.net/newbie/index.html)

---

