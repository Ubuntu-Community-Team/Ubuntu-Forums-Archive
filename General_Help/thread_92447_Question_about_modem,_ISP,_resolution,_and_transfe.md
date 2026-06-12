---
title: "Question about modem, ISP, resolution, and transferring files"
date: 2005-11-19
forum: General Help
---

### Post by Loman on 2005-11-19
Hello, everyone, I am an Ubuntu (and linux in general) newbie, and I have some questions that I was hoping someone could answer.
First, let me tell you about my system:
**CPU**: Pentium 4 1800 MHz
**Motherboard**: Intel D845PT
**Memory**: 768 MB RAM
**Sound**: SB Live! Wave Device
**Video**: RADEON 9600 SERIES
**Modem**: BCM V.90 56K Modem
If you need any more info, just tell me :)

My questions are as follows:
Ubuntu doesn't seem to be able to detect my modem, can anyone give me any advice on this issue?
I use [PeoplePC](http://www.peoplepc.com) as my ISP, is it possible to use it with Ubuntu?
Can I change my resolution to 1280x1024 or 1280x960? The highest I see is 1024x768.
I have Ubuntu installed on a partition, with Windows XP on another, is it possible to transfer files directly between them?

Chances are good that I will have more questions in the future, I'll try to keep them in this topic to avoid cluttering up the forums. Any help will be greatly appreciated. Thank you for reading this :D

---

### Post by Bachstelze on 2005-11-19
For the modem detection stuff, I advise you to visit [http://www.linmodems.org](http://www.linmodems.org)
To change the resolution, you've got to edit the /etc/X11/xorg.conf but I'm lso quite new to Linux, so better wait for someone more knowledgeable.
About having both XP and Ubuntu, yes, it is very possible, though it's recommended to install XP first.

---

### Post by Loman on 2005-11-19
Thank you for the link :)

I've had XP for a few years now, and just got my Ubuntu disks in the mail today. I just can't connect to the internet in Ubuntu, so I'll probably have to download  whatever I need in Windows, then transfer it to Ubuntu.

---

### Post by Loman on 2005-11-26
sorry for the double post, but it's been a few days and I still haven't resolved ANY of my issues.

I tried pppconfig, but nothing happens when I "pon". This is so frustrating. If ubuntu could just detect my modem, I think it would work.

I tried creating a FAT32 partition to share files between Ubuntu/Windows, but Ubuntu won't let me read/write from it. I tried formatting it from within Ubuntu, but that did nothing.

Please, someone help this poor newbie out, these issues are really hindering my progress with ubuntu. If only one of them was fixed, I'd be happy.

---

### Post by Bachstelze on 2005-11-26
> I tried pppconfig, but nothing happens when I "pon". This is so frustrating. If ubuntu could just detect my modem, I think it would work.

Here is a HOWTO on getting your modem work : [http://linmodems.technion.ac.il/first.html](http://linmodems.technion.ac.il/first.html)
> 
I tried creating a FAT32 partition to share files between Ubuntu/Windows, but Ubuntu won't let me read/write from it. I tried formatting it from within Ubuntu, but that did nothing.

here's how to mount your FAT32 partition in read/write mode : 

Open a terminal, get root access by typing "sudo -i"

First, you have to know the name of your fat32 partition. Type "fdisk -l" (this is a lower-case L, not an upper i). You'll get something like this : 

```
Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1265    10161081   83  Linux
/dev/hda2            1266        4864    28908967+   5  Extended
/dev/hda5            1266        1387      979933+  82  Linux swap / Solaris
/dev/hda6            1388        4864    27928971   83  Linux

```

but you'll have your FAT32 partition somewhere in. All you need to remember is the name of your partition, it will be something like /dev/hdax (replace x with the correct number). Now you neet to reate a **mounting point** for your partition (the directory where all your partition's files will be located). For example,

```
mkdir /mnt/windows
```

Now you have all the info you need, the only thing you hae to do is edit the /etc/fstab file :

```
gedit /etc/fstab
```

it will look like this :

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       /home           ext3    defaults        0       2
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Add a line at the end of it looking like this :

```
/dev/hdax	/mnt/windows	vfat	rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850	0	0
```

Don't forget to change /dev/hdax to the name of your partition you found before and /mnt/windows to the mounting point you created. Save the file, exit gedit and run "mount -a". Voil&#224; :)

EDIT : You can also mount your NTFS partitions (if any), but it's highly recommended to mount them read only by adding the following line to your /etc/fstab

```
/dev/hdax	/media/windows	ntfs	ro,user,auto,gid=100,nls=utf8,umask=002	0	0
```

To get the partition infos, it works the same as above :)

---

### Post by Loman on 2005-11-26
when I try to type "sudo -i" It says this: "unable to lookup via gethostname()"

I tried the other stuff, too, but got the same reply. 

Also, when I try to edit the fstab file it tells me I'm not the owner so I can't edit them

I can't try to fix my modem yet, because I don't have any floppies or blank CDs, so I guess I need to get this to work first

Thanks for helping :)

---

### Post by Bachstelze on 2005-11-26
are you SURE you type it in a terminal window ? It seems pretty weird

---

### Post by Loman on 2005-11-26
Yep, it's the terminal... I think I'm going to try re-installing Ubuntu and see if that helps

---

### Post by Loman on 2005-11-26
Well, reinstalling helped a bit, now I can do everything you posted until I try to edit fstab.

When I type "gedit /etc/fstab" I get this error:
"(gedit:9044): Gtk:WARNING **: Cannot open display"

and when I try to edit it by double clicking it, it just won't let me. I tried to change it so it wouldn't be read-only, but it say "You are not the owner so you cannot change permissions" or something like that. So then I copied and pasted it to the desktop and edited it there, but it gives me the "owner" message when I try to drag and drop it back to the original folder

---

### Post by stocksy on 2005-11-26
[QUOTE=Loman]Well, reinstalling helped a bit, now I can do everything you posted until I try to edit fstab.

When I type "gedit /etc/fstab" I get this error:
"(gedit:9044): Gtk:WARNING **: Cannot open display"
[/QUOTE]

Try "sudo nano -w /etc/fstab" instead.

---

### Post by Loman on 2005-11-26
I finally got it to show/read/write to the FAT32 partition, using Administration>Drives, now I'm going to concentrate on getting my modem to work. 

Oh yeah, can anyone explain how to edit /etc/X11/xorg.conf so I can use 1280x1024 resolution?

Thank you guys again for the help :D

---

### Post by Dr. Nick on 2005-11-26
Just put "1280x1024" under the mode line for each colordepth and restart X. If that doesnt work post your current xorg.conf here as your monitor may be detected wrong, hindering your choices
you can run "cat /etc/X11/xorg.conf" in a terminal to get a easy copy/paste version of xorg

---

### Post by Fittersman on 2005-11-26
hey loman if your still having problems with hte gethostbyname thing send me a private message and ill help you out with that

---

### Post by Rumpty on 2005-11-26
Loman, the "pon" command has to include your ISP name. In my case the command is "pon paradise". 

You will have filled in your ISP name when configuring pppconfig.

---

### Post by Loman on 2005-11-26
I thought that if you left it as "provider" you could just type "pon" and it would work. I guess I'll have to try that. I think the biggest problem is that my modem can't be detected. When I installed, I got and error saying:
"Network autoconfiguration failed. Your network is probably not using DHCP protocol. Alternatively the DHCP server may be slow or *some network hardware is not working properly*". I tried updating my modem drivers in windows, only to find out that it is extremely hard to find drivers for my modem. The way it is looking now, I am going to have to buy a new modem.

Dr Nick, I got my resolution to work after I used the "sudo nano -w" command that Stocksy posted, so Thank You both.

Fittersman, that problem was fixed when I reinstalled, but thank you anyway :)

EDIT: I just installed the ATI drivers and... nothing changed. The 3D Screensavers run at ~10FPS. They should run better than that, seeing as I have a 9600XT. I tried running "ATI Control" from the Applications menu, but nothing happens when I click on it. Anyone have any advice?

---

### Post by Loman on 2005-11-27
Well, I've been reading around the forums for advice on getting my video card to work, and I guess I got the advice I needed just a little to late. Someone said that using fglrxconfig to build the xorg.conf is a bad idea, but I had already done that... and naturally I forgot to make a backup. Is there any way I can revert the xorg.conf back to default and start over, or am I boned?

---

### Post by Fittersman on 2005-11-27
im havin problems with my video card too, ubuntu like to use the intel one integrated on my motherboard but i have a Radeon 7500 series, the thing is that ubuntu knows its there because its listed in device manager but it dont like to use it.

---

### Post by Dr. Nick on 2005-11-27
So you have 2 video cards and its using the wrong one?
If yes then you need to edit your Xorg.conf, the driver section to whatever the ati driver is and the BusID fields to the type of interface, agp,pci etc. I dont kow the ID for each of those but if you look around you can find them, or post your xorg.conf and I may be able to help figure it out by comparing it to mine

---

### Post by Bachstelze on 2005-11-27
Or symply deactivate the Intel one in your BIOS settings, Ubuntu won't regognise it anymore and you will be able to reconfigure your xorg.conf automatically with the ATI.

---

### Post by Dr. Nick on 2005-11-27
[QUOTE=Loman]Well, I've been reading around the forums for advice on getting my video card to work, and I guess I got the advice I needed just a little to late. Someone said that using fglrxconfig to build the xorg.conf is a bad idea, but I had already done that... and naturally I forgot to make a backup. Is there any way I can revert the xorg.conf back to default and start over, or am I boned?[/QUOTE]

I think it makes a backup for you. I looked in my /etc/X11/ directory and I had a xorg.conf from back in sept that I idnt backup. It was auto labeled xorg.conf.200509161458 

If you dont have a backup try to run ```
sudo dpkg-reconfigure xserver-xorg
``` and It should lead you through the xorg setup and make you a xorg.conf

---

### Post by Fittersman on 2005-11-27
i cant find my intel card in bios i dont know where it would be i looked everywhere

---

### Post by Dr. Nick on 2005-11-27
Most likely integrated componets, may just be called "onboard vga/video" or it may not be their at all, in that case you would need to use my previous xorg solution

---

### Post by Loman on 2005-11-27
[QUOTE=Dr. Nick]I think it makes a backup for you. I looked in my /etc/X11/ directory and I had a xorg.conf from back in sept that I idnt backup. It was auto labeled xorg.conf.200509161458[/QUOTE]

Awesome, I don't know why I didn't see it before, it was xorg.conf.save for me. Thanks a bunch! :)

Now, if I can just get my graphics card to work, I'll be in pretty good shape.

---

### Post by Loman on 2005-11-28
Now I'm trying to install binutils and it's not working. I'm following the instructions in the readme, but to no avail. Here is what the console says:
```
root@ubuntu:~# cd /binutils-2.16.1
root@ubuntu:/binutils-2.16.1# ./configure
creating cache ./config.cache
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking build system type... i686-pc-linux-gnuoldld
checking for a BSD compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH
root@ubuntu:/binutils-2.16.1# make
make: *** No targets specified and no makefile found.  Stop.
root@ubuntu:/binutils-2.16.1# make install
make: *** No rule to make target `install'.  Stop.
root@ubuntu:/binutils-2.16.1# 
```

What is this gcc/cc thing? Am I doing something wrong?

---

### Post by Bachstelze on 2005-11-28
gcc is the GNU C Compiler. You can install it through Synaptic.

---

### Post by Loman on 2005-11-28
Do I need internet access in Ubuntu to use Synaptic? I only have internet access in Windows.

---

### Post by Bachstelze on 2005-11-28
[QUOTE=Loman]Do I need internet access in Ubuntu to use Synaptic? I only have internet access in Windows.[/QUOTE]

Still didn't get your modem working ? Where is the problem ? I posted the HOWTO a billion times :/

---

### Post by Loman on 2005-11-28
I think the problem is either my modem is just a POS, or I am an Idiot (yes, with a capital I :D)

I just got kind of aggravated messing with my modem, so I moved on to my video card. Looks like I'll have to go back to the modem.

---

### Post by Bachstelze on 2005-11-28
Here's what to do for your modem : 

Download this : [http://linmodems.technion.ac.il/packages/scanModem.gz](http://linmodems.technion.ac.il/packages/scanModem.gz) and copy it into your home directory. Then open a terminal and run those three commands : 

```
gunzip scanModem.gz
chmod +x scanModem
./scanModem
```

After a short while, you will have a Modem diretory created, pst here the FULL contents of your modemData.txt file and I'll see if I can help you :)

---

### Post by Loman on 2005-11-28
Ok, done that, but when I type ./scanModem it say something like "file not found"

Everything else seemed to work, though. I can see the unzipped scanModem file in my / directory. There's even a "Modem" folder, but nothing is in it.

I tried just typing /scanModem (no period before) and I got this:
```
Class 0703: 14e4:4212   Modem: Broadcom Corporation BCM4212 v.90 56k modem (prog -if 00 [Generic])
  SubSystem 14e4:0002  Broadcom Corporation: Unknown device 0002
        Flags: bus master, fast devsel, latency 32, IRQ 22

                  -----PCI_IDs-------                    --CompilerVer-
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 14e4:4212 14e4:0002 debian 2.6.12-9-386  3.4.5 none    i686


   A subfolder Modem/  has been written,  containing these files with more detailed Information:
 ------------------------------------------------------------------------------------------
 1stRead.txt DriverCompiling.txt InfoGeneral.txt ModemData.txt Rational.txt Slmodem-ALSA.txt Slmodem.txt SoftModem.txt Testing.txt UNSUBSCRIBE.txt YourModem.txt 
-------------------------------------------------------------------------------------------
       Please read 1stRead.txt first for Guidance.
```

It says that the files were written in the folder, but there's nothing there.

---

### Post by Bachstelze on 2005-11-28
do not unzip the files in your / dir, put it in your home.

---

### Post by Loman on 2005-11-28
Sweet, it worked. Here's my ModemData:
```


 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2005_Oct_07
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 The kernel was assembled with compiler:  3.4.5
 a gcc-3.4.5  package must be installed to support driver compiling

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
Checking /usr/src/ for compressed compressed headers or kernel-source
/usr/src/fglrx.tar.bz2

Kernel-header resources needed for compiling are not manifestly ready!
If compressed resources are present, expand and then configure them following DriverCompiling.txt
They may have to be installed.
Within your Linux distributions' installation CD or online resource (and mirrows), search for :
  Distribution  PackageName			OnLine
  ----------------------------------------------------------------------
 Debian  		kernel-headers-2.6.12-9-386    	http://www.debian.org/distrib/packages or install CD
 Ubuntu 		linux-headers-2.6.12-9-386		http://http://packages.ubuntu.com/ or install CD
 Xandros
                        kernel-kbuild-3.6 are additionally required by  Debian, Ubuntu and Xandros
 Mandrake 	kernel-source-2.6.12-9-386	   If not present on install CDs search
 	http://mirror.switch.ch/ftp/mirror/mandrake/official/10.0/i586/Mandrake/RPMS/ 
	http://rpms.mandrakeclub.com/rpms/mandrake/official/LByName.html, or other mirrors.
  SuSE		kernel-source-2.6.12-9-386		 , kernels are named k_deflt
  FedoraCore4  kernel-devel-2.6.12-9-386 or kernel-smp-devel-2.6.12-9-386 on install CD1 or CD4
One of which must be installed if compiling drivers to match kernel 2.6.12-9-386 proves necessary.
Within the output Modem/ folder, read CompilingDrivers.txt for details.
   

 A /dev/modem symbolic link is not set.

drwxr-xr-x  2 root root 0 2005-11-28 14:17 /dev/.udevdb
There is an active UDEV file system, creating device nodes in volatile RAM.
However information from Proprietary drivers is soon to be excluded from 
the supporting /sys/ file structure.  Thus device nodes for Proprietary modem drivers
will then have to be created by bootup scripts.

 Checking for modem symbolic link support lines within /etc/udev/ files

 USB modem not detected.

0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801BA/BAM AC'97 Audio (rev 05)
0000:02:0b.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

Modem candidates are at PCI_buses:  0000:02:0a.0
    
Providing detail for device at  0000:02:0a.0
  with vendor-ID:device-ID
	    ----:----
Class 0703: 14e4:4212   Modem: Broadcom Corporation BCM4212 v.90 56k modem (prog-if 00 [Generic])
  SubSystem 14e4:0002  Broadcom Corporation: Unknown device 0002
	Flags: bus master, fast devsel, latency 32, IRQ 22
 Checking for IRQ 22 sharing with modem.

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 14e4:4212 14e4:0002 debian 2.6.12-9-386  3.4.5 none    i686

      
 Information on several modem chipset providers is provided below,
 because ambiguities remain on the correct choice of supporting software.
            
 == Checking PCI IDs through modem chip suppliers ==

 Vendor 14e4 is BroadCom 
   14e4:4212   is a  BCM V.90 56k modem
 There is a driver for 2.2.n kernels called  BCOM_WAN_V20.
    Search for it at http://www.dell.com 
 However the code has not been updated for some time.
 For  2.4 kernels, fix by Giacomo Comes must be used. See :
   http://linmodems.technion.ac.il/archive-third/msg01652.html
   http://cengique.2y.net/~cengiz/BCMSM/
 There is no support under 2.6.n kernels for the
      14e4:4212  BCM V.90 56k modem
   
 When serving under softmodem controllers like the Intel ICH series,
 the Broadcom Subsystem 14e4:4d64 has mc97 codec BCM64.
 Kernels of version 2.6.6 or later are necessary.  See success reports:
   http://linmodems.technion.ac.il/archive-fifth/msg02486.html
   http://linmodems.technion.ac.il/archive-fourth/msg03690.html
   http://oboc.ucdavis.edu/Marik/inspiron/ 
   The support is achieved through a combination of:
   1) the snd-intel8x0m.ko of 2.6.n kernel releases, which provides a low level interface with the modem;
   2) an slmodemd  which creates ports and provides higher level functions.
   Get the slmodem-CurrentVersion.tar.gz from  http://linmodems.technion.ac.il/packages/smartlink/
   To compile the slmodemd, it is first Necessary to install a libasound2-dev package, providing alsa headers.  Alternately follow the link SLMODEMD.gcc3.tar.gz or SLMODEMD.gcc4.tar.gz 
   to an already compiled slmodemd with documentation. The slmodemd is not kernel specific.
   3) After compilation and installation of slmodemd, initiate service with:
   # modprobe  snd-intel8x0m
   # slmodemd --alsa --country=YOURCOUNTRY hw:1
   Read the accompanying documentation for details and Modem/Slmodem.txt


  ======= PCI_ID checking completed ====== 
 Update=2005_Oct_07
A PCMCIA CardBus is not detected on this System.
GCCversion=none
   
For information on modem port creation under the UDEV device file system see:
   http://linmodems.technion.ac.il/archive-fourth/msg03299.html  for Conexnant modems
   http://linmodems.technion.ac.il/archive-fifth/msg01177.html  for Lucent/Agere DSP modems
   
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
[4294667.296000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[4294667.296000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] disabled)
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
[4294667.296000] ACPI: LAPIC_NMI (acpi_id[0x02] dfl dfl lint[0x1])
[4294671.961000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.961000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.962000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[4294671.972000] audit: initializing netlink socket (disabled)
[4294712.571000] ibm_acpi: ec object not found
[4294721.522000] apm: BIOS not found.

  Beginning with Fedora 2  kernel-2.6.6-1.427, kernel-headers needed 
  for compiling drivers are provide at: /lib/modules/kernel-version/build/
  Thus upgrading above kernel 2.6.5-1.358 to 2.6.6-* is Stongly Recommended
  
  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  debian is not yet providing pre-compiled drivers for WinModems
```

---

### Post by Bachstelze on 2005-11-28
OK, so try this : 

download this : [http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc3.tar.gz](http://linmodems.technion.ac.il/packages/smartlink/SLMODEMD.gcc3.tar.gz)

Unpack it somewhere, copy the slmodemd file into your /usr/sbin directory, then run the following commands : 

```
sudo -s
chmod +x /usr/sbin/slmodemd
modprobe snd-intel8x0m
slmodemd --alsa -c YOUR_COUNTRY hw:1
```

Then DO NOT press Ctrl+C, open a new terminal and run

```
sudo wvdialconf /etc/wvdial.conf
```

Hopefully it will detect your modem. If so, tell me here, I'll tell you how to connect. It not, send an email with your modemdata.txt attached to [email]discuss@linmodems.org[/email] with the subject "scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386"

---

### Post by Loman on 2005-11-28
Everything goes smoothly until the "slmodemd --alsa -c YOUR_COUNTRY hw:1" part. This is what I get:
```
root@ubuntu:~# slmodemd --alsa -c USA hw:1
bash: slmodemd: command not found
```

---

### Post by Bachstelze on 2005-11-28
[QUOTE=Loman]Everything goes smoothly until the "slmodemd --alsa -c YOUR_COUNTRY hw:1" part. This is what I get:
```
root@ubuntu:~# slmodemd --alsa -c USA hw:1
bash: slmodemd: command not found
```[/QUOTE]

Do not forget to copy the slmodemd file in the archive into your /usr/sbin dir :)

---

### Post by Loman on 2005-11-28
Oh, ha ha, I thought you meant the folder that you get when you "extract all" :D

I think it detected my modem, but there were some errors, here are the results:
```
root@ubuntu:~# slmodemd --alsa -c USA hw:1
error: mixer setup: Off-hook switch not found for card hw:1
SmartLink Soft Modem: version 2.9.11 Oct 25 2005 00:13:50
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `hw:1' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.
error: rate 9600 is not supported by capture (11025).
error: rate 9600 is not supported by capture (11025).
```
```
root@ubuntu:~# wvdialconf /etc/wvdial.conf
Scanning your serial ports for a modem.

ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   S8
Port Scan<*1>: S9   S10  S11  S12  S13  S14  S15  S16
Port Scan<*1>: S17  S18  S19  S20  S21  S22  S23  S24
Port Scan<*1>: S25  S26  S27  S28  S29  S30  S31  S32
Port Scan<*1>: S33  S34  S35  S36  S37  S38  S39  S40
Port Scan<*1>: S41  S42  S43  S44  S45  S46  S47  S48
Port Scan<*1>: S49  S50  S51  S52  S53
WvModem<*1>: Cannot get information for serial port.
ttySL0<*1>: ATQ0 V1 E1 -- OK
ttySL0<*1>: ATQ0 V1 E1 Z -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK
ttySL0<*1>: Modem Identifier: ATI -- SmartLink Soft Modem
ttySL0<*1>: Speed 4800: AT -- OK
ttySL0<*1>: Speed 9600: AT -- OK
ttySL0<*1>: Speed 19200: AT -- OK
ttySL0<*1>: Speed 38400: AT -- OK
ttySL0<*1>: Speed 57600: AT -- OK
ttySL0<*1>: Speed 115200: AT -- OK
ttySL0<*1>: Speed 230400: AT -- OK
ttySL0<*1>: Speed 460800: AT -- OK
ttySL0<*1>: Max speed is 460800; that should be safe.
ttySL0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Found a modem on /dev/ttySL0.
Modem configuration written to /etc/wvdial.conf.
ttySL0<Info>: Speed 460800; init "ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0"
```
Is that good or bad?

---

### Post by Bachstelze on 2005-11-28
This was not the right thing. Press ctrl+C in your slmodemd terminal window and try typing the same line with "modem:1" instead of "hw:1"

After you tried it, run

```
sudo gedit /etc/wvdial.conf
```

ant then edit the three last lines with your ISPs parameters. Don't forget to remove the semicolons at the beginning. Save your file and try to run.

```
sudo wvdial
```

---

### Post by Loman on 2005-11-28
I got this:
```
root@ubuntu:~# slmodemd --alsa -c USA modem:1
error: mixer setup: Off-hook switch not found for card hw:1
ALSA lib pcm.c:1959:(snd_pcm_open_conf) Invalid type for PCM modem:1 definition (id: modem, value: cards.pcm.modem)
error: alsa setup: cannot open playback device 'modem:1': Invalid argument
error: cannot setup device `modem:1'
```

I just saw your edit, I'll go try it now, I just thought I'd post this since I'll have to shut down to get back to Ubuntu, then shut down to get back to windows.

---

### Post by Bachstelze on 2005-11-28
running wvdial now won't work anyway. But editing your wvdial.conf would be useful, we'll see if you can connect with the slmodemd line ran on hw:1

---

### Post by Loman on 2005-11-28
Nope, I tried both hw:1 and modem:1 again, but it doesn't work. with modem:1 it says "/dev/ttySL0 no such file or directory", and with hw:1 it says wvdial.conf doesn't have a valid usename and password. I made sure that the user and pass were in the file, but still nada.

---

### Post by Bachstelze on 2005-11-28
The "Bad username/password" thing is beause you didn't edit the /etc/wvdial.conf file properly. You have to remove everything so that the three last lines are just

Parameter = value

with no semicolon, no space at the beginning and no <>

---

### Post by Loman on 2005-11-28
Ok, I think we're getting closer :) 

Now, when I "wvdial" I get this:
```
root@ubuntu:~# wvdial
--> WvDial: Internet dialer version 1.54.0
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT6453015
--> Waiting for carrier.
ATDT6453015
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT6453015
--> Waiting for carrier.
ATDT6453015
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT6453015
--> Waiting for carrier.
ATDT6453015
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT6453015
--> Waiting for carrier.
ATDT6453015
NO CARRIER

```
> 
ATDT6453015
NO CARRIER
ERROR
--> No Carrier!  Trying again.
--> Sending: ATDT6453015
--> Waiting for carrier.

That last part keeps repeating over and over

---

### Post by Bachstelze on 2005-11-28
Okay, so it's still not the right thing... Try running the slmodemd command with hw:0 or modem:0 instead and if it doesn't work send your modemdata.txt to [email]discuss@linmodems.org[/email]

---

### Post by Loman on 2005-11-28
Still didn't work, I guess I'll send the modemdata to that address.

I really wouldn't be too worried about it, if I could get my graphics card to work. Is there any wat to download the gcc thing in windows?

---

### Post by Dr. Nick on 2005-11-28
You may not have to download it, run "sudo apt-get install build-essential" and see if it will install, It may need your CD , not sure if its on the cd

I imagine its possible to download in windows but may not be the easiest since it installs dependencies I believe

---

### Post by Loman on 2005-11-28
[QUOTE=Dr. Nick]You may not have to download it, run "sudo apt-get install build-essential" and see if it will install, It may need your CD , not sure if its on the cd

I imagine its possible to download in windows but may not be the easiest since it installs dependencies I believe[/QUOTE]

That worked, thanks :), but my video card still isn't being used :(

---

### Post by Dr. Nick on 2005-11-29
Hmm, post the output of **cat /etc/X11/xorg.conf **from a terminal. Have you tried any of the howto's on the forums like this one [http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati+howto]("http://www.ubuntuforums.org/showthread.php?t=24557&highlight=ati+howto")

Unfortunately I think it may require internet, not sure though. I dont have a ATI card so I cant help much more. Basically ati drivers are "restricted" from being installed by default due to license so they have to be installed and activated seperately, From what ive heard their linux drivers are not real good, but It should get beter fps on screensavers than the generic ones used by default.

---

### Post by Loman on 2005-11-29
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/CID"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
        Load    "GLcore"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
   SubSection  "extmod"
      Option    "omit xfree86-dga"
   EndSubSection
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"     # vendor=1002, device=4152
        Option          "UseInternalAGPGART"    "no"
        Option          "FSAAEnable"            "yes"
        Option          "FSAAScale"             "6"
EndSection

Section "Monitor"
        Identifier      "EV700"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon 9600 XT (RV350 AR)"
        Monitor         "EV700"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x 480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x 480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x 480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x 480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x 480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x 480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

I'm trying that howto right now, thanks :)

---

