---
title: "need floppy help ASAP"
date: 2005-12-06
forum: General Help
---

### Post by Fittersman on 2005-12-06
i can mount it and all that but when i try and write to my floppy it tells me that i dont have the neccesairy permissions and it is makin me mad. I need to write stuff to my floppy or some way of transportation by friday!! (no modem yet, windows partition is dumb also so that is the only thing i can think of)

---

### Post by noob_Lance on 2005-12-06
why not a thumb drive?

---

### Post by canadianwriterman on 2005-12-06
I had some problems with using my floppy that I solved by downloading and installing an update to pmount. Go to:

[http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/](http://archive.ubuntu.com/ubuntu/pool/main/p/pmount/)

Download and install pmount_0.9.6-1~breezy1_i386.deb

---

### Post by tomwell on 2005-12-06
You need to enable the can mount floppy drive in your user permissions.... Its that simple...i think lmao!!

Administration->Users and groups-> edit your user ... 

Hope that helps...

Peace

Tom

---

### Post by Fittersman on 2005-12-06
its already set up so i have all those checked off.

the problem is that the driver is "owned" by user root and i cannot do anything to it but read it and execute files, no writing. So i go to the recovery console and try to change that and it tells me that it is a read only file and cannot be changed, is there another way?

---

### Post by Bachstelze on 2005-12-06
A simple workaround is running nautilus as root (sudo nautilus) and copying your files on the disk but there might be another way. Is there a line about your floppy drive in your /etc/fstab file ?

---

### Post by Fittersman on 2005-12-06
ill check tomorrow.

do you follow me hymntolife?
lol

---

### Post by tomwell on 2005-12-07
if you can locate the file in terminal you can change the file permissions by using:

[http://www.ss64.com/bash/chmod.html](http://www.ss64.com/bash/chmod.html)

I hope am not completely wrong... LMAO!!
Good site too...

Peace

Tom

---

### Post by hajk on 2005-12-07
Same problem on my box: no write permission on a mounted floppy, even though  Properties says that I'm the owner. Changing the permissions by checking an empty box fails immediately by emptying the box again. At the bottom it says: ...you are not the owner.

Strangely enough, I can copy a file from HD to floppy just by dragging it onto the floppy icon; the other way also works. So that would be a work-around.:rolleyes:

---

### Post by Fittersman on 2005-12-07
same thing as me pretty much but i can only read and execute i cannot drag and drop or any way of writing to the floppy.

---

### Post by Bachstelze on 2005-12-07
Fittersman > have you checked your /etc/fstab file as I told you ?

---

### Post by Fittersman on 2005-12-07
no

---

### Post by Bachstelze on 2005-12-07
Theny ou should do it "ASAP", a little bit of editing on it might do the trick.

---

### Post by Fittersman on 2005-12-07
can you post yours so i can do the editing on mine, im alright with that kinda stuff i know what to change and what not to

---

### Post by Bachstelze on 2005-12-07
Well, no I can't. I have no floppy drive so it wouldn't be much useful :p Basically what you need to do is find the line where your drive mounting infos are and replace the "defaults" mounting parameters with this :

```
rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850
```

for FAT32 partitions and floppy disk (read/write access) and this : 

```
ro,user,auto,gid=100,nls=utf8,umask=002
```

for NTFS partitions (read-only). Then save your file and run

```
sudo mount -a
```

Then it should work.

---

### Post by Fittersman on 2005-12-07
k ill try it when i get home

---

### Post by Fittersman on 2005-12-07
floppy driver works now good but i need to get a larger file than a floppy can hold to windows by friday now...

---

### Post by Fittersman on 2005-12-07
floppy driver works now good but i need to get a larger file than a floppy can hold to windows by friday now... i have an mp3 player

---

### Post by Bachstelze on 2005-12-07
Then you have three solutions : 

1) Use an USB Keydrive. (EDIT : The MP3 player should work here.)

2) Find a fat32 partition you could use to access on both Ubuntu and Windows

3) Create a multifile archive. I don't know if there is a prog to do it for linux but WinRar works perfet with WINE.

---

### Post by Fittersman on 2005-12-07
how do i use a USB keydrive?

---

### Post by Bachstelze on 2005-12-07
You just plug it in a USB slot, it should be immediately recognized.

---

### Post by Fittersman on 2005-12-07
no such luck...

---

### Post by Bachstelze on 2005-12-07
You're really not lucky... For me it works just fine. Try logging out (not reboot, just log out) and re-login with the key plugged.

---

### Post by Fittersman on 2005-12-08
alright and here is my modem thinger :D (modemdata.txt) i brought the whole modem folder so if you need others i got it


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_Oct_25
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 USB modem not detected.


 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling

Modem candidates are at PCI_buses:  0000:01:0b.0
    
Providing detail for device at  0000:01:0b.0
  with vendor-ID:device-ID
	    ----:----
Class 0780: 11c1:044c   Communication controller: Lucent Microelectronics LT WinModem (rev 02)
  SubSystem 11c1:044c  Lucent Microelectronics LT WinModem
	Flags: bus master, medium devsel, latency 64, IRQ 255
 Checking for IRQ 255 sharing with modem.

There is a Bad IRQ=255 . Carefully read the related guidance in Modem/ModemData.txt

 The modem will NOT function because of interrupt assignment: IRQ 255
 Possible corrections are:
   1) to access the  the boot up BIOS change to a non-PNP mode.
   Instructions for accessing BIOS are at:
      [http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within:  Additional Resourcces.
   2) Within some BIOS setups, IRQ assignments can be changed.
   3) On non-laptop systems moving the modem card to another slot has helped.
   4) Sometimes upgrading the kernel changes IRQ assignment.

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 11c1:044c 11c1:044c debian 2.6.12-9-386  3.4.5     i686
 == Checking PCI IDs through modem chip suppliers ==
	  
 The modem has a supported Lucent/Agere DSP (digital signal processing) chipset
  with primary PCI_ID:  11c1:044c
 DSP=1
 Native suppport for AMD x86_64 systems had NOT been implemented.
 However, there is a too brief report that with under a i686 kernel 
 compiled with x86_64 optimization and serving an AMD x86_64 motherboard,
 the ltmodem drivers are effective.

 Agere Systems, Inc provides periodic software releases for their DSP modems,
 which are made more Newbie friendly by volunteers or Linux distros.
 Browse [http://linmodems.technion.ac.il/Ltmodem.html](http://linmodems.technion.ac.il/Ltmodem.html) for older information.

 
 There are some installer packages and also resources for compiling drivers.
 ----------------------
 SuSE/Novell Linux and some other Distros provide compiled drivers +installers.
    Search package lists for ltmodem  
 For other Distros and 2.6.n kernels, see: 
   [http://linmodems.technion.ac.il/archive-fifth/msg04605.html](http://linmodems.technion.ac.il/archive-fifth/msg04605.html)
 and browse 
   [http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/](http://linmodems.technion.ac.il/packages/ltmodem/kernel-2.6/) 
     ltmodem-2.6-alk-7b.tar.gz  has the most general instructions for installations,
     		and the core code is used in: 
     ltmodem-8.31b1.tar.gz  , which automates the processes; 
     ltmodem-2.6-7alk.src.rpm can be used for rpm using Distros.
	   # rpmbuild --rebuild ltmodem-2.6-7alk.src.rpm  
	   will deposit an installer at:
	        /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.12-9-386.rpm 	   Check with  
            # ls -l   /usr/src/rpm/RPMS/i686/ltmodem*
	    Then install with:
	    # rpm -i /usr/src/rpm/RPMS/i686/ltmodem-kv_2.6.12-9-386.rpm
	    or similar.
 
 [http://ltmodem.heby.de](http://ltmodem.heby.de) has support for ISA card modems, Lucent/Agere chip PCMCIA card modems
 and kernels 2.2.n through current 2.6.n (at least up to 2.6.11)  
            Packages for compiling drivers are:
            ResourceName                Use for kernel ranges
        --------------------------------------------------------------------------------------------------	    
        ltmodem-8.26a.tar.gz         kernels 2.4.21 and earlier
        ltmodem-8.30a3.tar.gz       kernels 2.4.21 and subsequent 2.4.2n kernels
	    which were assembled with a gcc-2.9n comiler
        ltmodem-8.31a10.tar.gz     beginning with 2.4.21 through and into 2.6.n  kernels 
There are also numerous pre-compiled driver packages, though those for older kernels are at::
     [http://linmodems.technion.ac.il/packages/ltmodem/](http://linmodems.technion.ac.il/packages/ltmodem/)
See [http://linmodems.technion.ac.il/resources.html#lucent](http://linmodems.technion.ac.il/resources.html#lucent)  for some special cases:
    Knoppix, Demudi, etc
Some additional 2.4.n installers are available from:
[http://dag.wieers.com/packages/kernel-module-ltmodem/](http://dag.wieers.com/packages/kernel-module-ltmodem/) for some other 2.4.n installers     


 Vendor 11c1 corresponds to Lucent Technologies or subsidiary Agere Systems, Inc.
 Information is at:  [http://www.agere.com/client/modem_dsp.html](http://www.agere.com/client/modem_dsp.html). Produced are both:
   1) modems identifiable from their primary PCI IDs and 
   2) soft modem Subystem chips requiring identification through codec readouts.
   
 Lucent/Agere Mars/WinModem drivers from version 8.30 onwards have
 the necessary fix for SMP machines which includes machines with
 hyperthreading turned on (virtually acting as two CPUs).
 
 Call waiting specified by, +pcw=1, is not implmented in the ltmodem drivers.
Configuration with forcing is described in: [http://linmodems.technion.ac.il/archive-fifth/msg00055.html](http://linmodems.technion.ac.il/archive-fifth/msg00055.html)
 0x044c -- Mars 3 Perseus data/fax only:North America and Global board
 0x044c -- Mars 3.2 Mercury data fax only when no eeprom is present, North America DAA


 Add either of the following lines to the Debian  /etc/apt/sources.list
 to enable automatic updates on installer availability:
   deb [http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/](http://www.physcip.uni-stuttgart.de/heby/ltmodem/dists/debian/) ./
   deb [http://www.sfu.ca/~cth/ltmodem/dists/debian/](http://www.sfu.ca/~cth/ltmodem/dists/debian/) ./


  The desired installer name is like:
========================================
ltmodem-2.6.12-9-386_8.nn_i386.deb
----------------------------------------
 ltmodem-kv-Kernel_FL-LTver--.CPU.rpm   explains the versioning.
 For your System
            Kernel_FL is 2.6.12-9-386 , the full kernel version displayed by: uname -r
                      LTver is 8.31a10, the release of the compiler kit
                               8.nn is the Agere core code designation.
       The proccesor type or CPU is:  i686      dispayed by:  uname -m
 used in compiling and assembling driver packages.

      
 A suitable installer is not available as of this 2005_Oct_25 update.
 Check in the section debian at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
   for a subsequent Installer submission.
 Older releases have been archived at:
   [http://linmodems.technion.ac.il/packages/ltmodem/archive/](http://linmodems.technion.ac.il/packages/ltmodem/archive/)
 Also there is a RPM search engine at:   [http://rpm.pbone.net](http://rpm.pbone.net)
 The closest match to your   i686=CPU   is recommended.
   The closest match to your   i686=CPU   is recommended.
   For example replacements in order of preference for an
     i686 would be i586, i486 and i386
 If not present use the  ltmodem-8.31a10.tar.gz compiler kit.

 The list of available Installers for debian as of this 2005_Oct_25
 is inserted into to Modem/YourModem.txt
  ======= PCI_ID checking completed ====== 
 Update=2005_Oct_25
A PCMCIA CardBus is not detected on this System.

/etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe

 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
 deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse

## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free

## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-9-386    	[http://www.debian.org/distrib/packages](http://www.debian.org/distrib/packages) or install CD
 Ubuntu 		linux-headers-2.6.12-9-386		[http://http://packages.ubuntu.com/](http://http://packages.ubuntu.com/) or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	[http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/](http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/) 
	[http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html](http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html), or other mirrors.
  SuSE		kernel-source-2.6.12-9-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-9-386 or kernel-smp-devel-2.6.12-9-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

drwxr-xr-x  2 root root 0 2005-12-07 22:26 /dev/.udevdb
There is an active UDEV file system, creating device nodes in volatile RAM.
However information from Proprietary drivers is soon to be excluded from 
the supporting /sys/ file structure.  Thus device nodes for Proprietary modem drivers
will then have to be created by bootup scripts.

 Checking for modem symbolic link support lines within /etc/udev/ files

   
For information on modem port creation under the UDEV device file system see:
   [http://linmodems.technion.ac.il/archive-fourth/msg03299.html](http://linmodems.technion.ac.il/archive-fourth/msg03299.html)  for Conexnant modems
   [http://linmodems.technion.ac.il/archive-fifth/msg01177.html](http://linmodems.technion.ac.il/archive-fifth/msg01177.html)  for Lucent/Agere DSP modems
   
The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourModem.txt
A /dev/modem symbolic link is not present

 No devfsd.conf file found, indicated absense of the devfsd daemon package
 for device file system (devfs) symbolic link support.

DEVFSD=
 ---- dmesg queries -------
[4294671.330000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.330000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.331000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.430000] audit: initializing netlink socket (disabled)
[4294703.348000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294703.348000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294712.338000] ibm_acpi: ec object not found
[4294721.981000] apm: BIOS version 1.2 Flags 0x0b (Driver version 1.16ac)
[4294721.981000] apm: overridden by ACPI.

  Beginning with Fedora 2  kernel-2.6.6-1.427, kernel-headers needed 
  for compiling drivers are provide at: /lib/modules/kernel-version/build/
  Thus upgrading above kernel 2.6.5-1.358 to 2.6.6-* is Stongly Recommended
  
  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the [http://www.smlink.com](http://www.smlink.com)  slmodem software.
  Check pppd version with:
    pppd --version
  See  [http://linmodems.technion.ac.il/archive-fourth/msg03167.html](http://linmodems.technion.ac.il/archive-fourth/msg03167.html)
    
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by mafiaman1134 on 2005-12-09
my drive wont even mount

---

### Post by Fittersman on 2005-12-09
do you know howto manually mount it?

cd /etc/media

then type sudo mount floppy

(if you didnt know how)

---

### Post by Bachstelze on 2005-12-09
This part doesn't seem good :

> The modem will NOT function because of interrupt assignment: IRQ 255
Possible corrections are:
1) to access the the boot up BIOS change to a non-PNP mode.
Instructions for accessing BIOS are at:
[http://linmodems.technion.ac.il/resources.html](http://linmodems.technion.ac.il/resources.html) within: Additional Resourcces.
2) Within some BIOS setups, IRQ assignments can be changed.
3) On non-laptop systems moving the modem card to another slot has helped.
4) Sometimes upgrading the kernel changes IRQ assignment.

solution 3) seems the simplest, hope it works.

---

### Post by Fittersman on 2005-12-09
what?? thats crazy why the hell does ubuntu have to be dumb (im no good with hardware...)

---

### Post by ninotob on 2005-12-09
[QUOTE=Fittersman][re usb key not mounting] no such luck...[/QUOTE]

I have a stubborn thumb drive ... mostly I use it on my powerbook but it won't automount in ubuntu .... I really ought to work on resolving that, but it's just so much easier to mount it manually than track down the problem.

```

sudo mkdir /mnt/usbkey
sudo mount /dev/sda1 /mnt/usbkey

```

You can open a file browser window to the /mnt/usbkey directory and copy over what you want.
When done copying, **type this before unplugging**:

```

sudo umount /mnt/usbkey

```

EDIT:  if "sda1" won't mount, try "sda2" 3 4, if that doesn't work, sdb1, sdb2 etc till you hit it.  Also, you might have to explicitely state the filesystem, likely FAT32, in which case the mount command would be "sudo mount -t vfat /dev/sda1 /mnt/usbkey" (omit the quotes of course).

---

### Post by Fittersman on 2005-12-10
hey is there way to mount a pci slot manually? because i know what slot its in but its not manually being detected. its like PCI 3 [1:11:0] or something id have to recheck that though

---

