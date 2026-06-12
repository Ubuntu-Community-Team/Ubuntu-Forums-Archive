---
title: "My Winmodem Worked Once."
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by PlantPerson on 2006-04-04
So I installed Ubuntu on my laptop.  I downloaded the scanModem utility from linmodems.org and used it to scan my system.  It output this file:
```
DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386  
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at DISCUSS@linmodems.org
Code updated on:  2006_March_29
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386

 https://wiki.ubuntu.com/DialupModemHowto has good general guidance.
A /dev/modem symbolic link is not present
 USB modem not detected.

 Checking for audio card 
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 01)
	Reading /proc/asound/pcm 
00-00: Intel ICH : Intel 82801CA-ICH3 : playback 1 : capture 1
00-01: Intel ICH - MIC ADC : Intel 82801CA-ICH3 - MIC ADC : capture 1
01-00: Intel ICH - Modem : Intel 82801CA-ICH3 Modem - Modem : playback 1 : capture 1

The modem is supported by an ALSA modem driver plus slmodemd, OR alternatively
an hsfmodem package from http://www.linuxant.com/drivers. Further diagnostics
below may resolve between the two.
ALSA modem drivers are included in 2.6.n kernel packages and currently include:
	snd-hda-intel, a joint audio + modem driver
	snd-ali5451  ,        "             "
	intel8x0m        , depending on intel8x0    audio driver
	snd_via82xx_modem,          "   snd_via82xx   "
	snd-atiixp-modem ,          "   snd-atiixp    "
Driver loading itself does NOT resolve between ALSA and hsfmodem alternatives. 

 The potentially supporting drivers now loaded on this System are:
0 snd_intel8x0
1 snd_intel8x0m


 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2
-------------
 Found make utility.
-------------
Checking for kernel-headers needed for compiling.
 Kernel-header resources needed for compiling are not manifestly ready!

Modem candidates are at PCI_buses:  0000:00:1f.6
    
Providing detail for device at  0000:00:1f.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 8086:2486   Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 01) (prog-if 00 [Generic])
  SubSystem 1179:0001  Toshiba America Info Systems Toshiba Satellite 1110 Z15 internal Modem
	Flags: bus master, medium devsel, latency 0, IRQ 11
 Checking for IRQ 11 sharing with modem.
      XT-PIC  uhci_hcd:usb1, uhci_hcd:usb2, uhci_hcd:usb3, Intel 82801CA-ICH3, ohci1394, yenta, yenta, Intel 82801CA-ICH3 Modem

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 8086:2486 1179:0001 debian_version 2.6.12-9-386  3.4.5 4.0.2    i686
              From records, 1179:0001 has soft modem codec type SIL27
The following two Root commands should set up the modem.
	sudo modprobe snd-intel8x0m
	sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
Get the SLMODEMD.gcc3.tar.gz from http://linmodems.technion.ac.il/packages/smartlink/
       
 The controller: 8086:2486 82801CA/CAM ICH3 

 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Pctel
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers
snd_intel8x0m          16836  0 
snd_ac97_codec         72188  2 snd_intel8x0m,snd_intel8x0
snd_pcm                78344  4 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd                    48644  9 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
snd_page_alloc         10120  3 snd_intel8x0m,snd_intel8x0,snd_pcm

  Driver snd-intel8x0m  may enable codec acquisition 
  === Begin mc97 codec query  ===
 the MC97 file is:	/proc/asound/card1/codec97#0/mc97#1-1
 --------
1-1/0: Silicon Laboratory Si3036,8 rev 7

Extended modem ID: codec=1 LIN1
Modem status     : GPIO MREF ADC1 DAC1 PRE(ADC2) PRF(DAC2) PRG(HADC) PRH(HDAC)
Line1 rate       : 8000Hz
 --------
 from /proc/asound/card1/codec97#0/mc97#1-1+regs
    0:7c = 5349
    0:7e = 4c27
    Translating into:  SIL27
an AgereSystems codec
  === End mc97 codec query  ===

 Beginning check for older ac97_codec modems.
 An older ac97_modem codec was not detected.

 Agreement between diagostic and Archive data.
 The Subsystem has an Agere Systems codec SIL27

 The modem can be set up by Root commands:
   sudo modprobe snd-intel8x0m
   sudo slmodemd --alsa -c YOUR_COUNTRY modem:1
 
 The ALSA modem driver snd-intel8x0m provides low level hardware access.
 The slmodemd provides high level functions and is  not kernel-version specific.
 From http://linmodems.technion.ac.il/packages/smartlink/   follow the link 
 SLMODEMD.gcc3.tar.gz 
 Also download the ungrad-winmodem.tar.gz and the http://linmodems.technion.ac.il/packages/unloading.gz
 Within the SLMODEMD package the 1st_Read.txt gives instructions 
 For guidance on bootup automation see:
   http://linmodems.technion.ac.il/archive-fifth/msg04652.html
 
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.
 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at http://www.smlink.com/ owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  http://www.smlink.com/main/index1.php?ln=en&main_id=40
 But a more recent code and a much broader license for other chipset support,
 can be downloaded from http://linmodems.technion.ac.il/packages/smartlink/  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   SLMODEMD.gcc3 - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
 Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and
 http://linmodems.technion.ac.il/slmodem-serial.html

 == Checking PCI IDs through modem chip suppliers ==

 Vendor=8086 is Intel, Inc. producing HaM and 536ep host controller free (HCF) modems, 537 soft modem
http://developer.intel.com/design/modems/ .  Also produced are
AC97 and MC97 controllers managing a varierty of non-Intel soft modem Subsystems.
 These subSystems often have PCI_IDs assigned by the modem assembler, rather than the chip provider.
 Download Intel-537ep drivers through:  http://developer.intel.com/design/modems/support/drivers.htm  
 Also check at: http://linmodems.technion.ac.il/packages/Intel/537/  
 for beta releases and perhaps Already compiled drivers for some Linux distributions
 A very detailed installation report cogent to 537 type modems is at:
                  http://linmodems.technion.ac.il/archive-fifth/msg00541.html

 Setup call id with:
 	Type 1 : When the phone line is not in use                    at+vcid=1
	Type 2 : When the phone line is already in use on a call      at+pcw=0
 ---------------------

  ======= PCI_ID checking completed ====== 
 Update=2006_March_29

Analyzing information for PCMCIA device at PCI Bus 02:0b.0
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication

Analyzing information for PCMCIA device at PCI Bus 02:0b.1
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
	Subsystem: Toshiba America Info Systems: Unknown device 0001
	Flags: bus master, slow devsel, latency 168, IRQ 11
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31b1.tar.gz at  http://ltmodem.heby.de/
drwxr-xr-x  2 root root 0 2006-04-02 14:20 /dev/.udevdb

There is an active UDEV file system, creating device nodes in volatile RAM.
For SmartLink modems using the slamr.ko or slusb.ko drivers an /etc/init.d/ script
will be necessary to create /dev/slamr0 or /dev/slusb0 ports, or manually by:
#  mknod -m 600 /dev/slamr0 c 242 0
#  mknod -m 600 /dev/slusb0 c 243 0
upon each bootup.

For information on modem port creation under the UDEV device file system see:
   http://linmodems.technion.ac.il/archive-fourth/msg03299.html  for Conexnant modems
   http://linmodems.technion.ac.il/archive-fifth/msg01177.html  for Lucent/Agere DSP modems
   
 Checking for modem symbolic link support lines within /etc/udev/ files


Checking the /etc/apt/sources.list
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted








A package kernel-kbuild-2.6-3 or later version must be installed to support compiling


    /usr/bin/gcc -> gcc-4.0
      
 The Major.Minor versions differ in the designated compiler 4.0.2 and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See http://linmodems.technion.ac.il/archive-fifth/msg04252.html 
 
Kernel-header resources needed for compiling are not manifestly ready!
Checking /usr/src/ for compressed compressed headers or kernel-source

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

The following information blocks just query some ppp support items.

====================================================
   grep -rs ppp /etc/modprobe.*
-------------------------------------
/etc/modprobe.d/aliases:alias net-pf-24 pppoe
/etc/modprobe.d/aliases:alias ppp-compress-18 ppp_mppe_mppc
-------------------------------------
 Resident PPP support modules are properly uncompressed .
 COMM services are not active
Be sure to read the section about ppp related modules and aliases in Modem/YourSystem.txt
 ---- dmesg queries -------
[4294670.677000] audit: initializing netlink socket (disabled)
[4294671.063000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[4294698.392000] pnp: Device 00:0a disabled.
[4294706.811000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294706.811000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294707.157000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294707.157000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294717.424000] ibm_acpi: ec object not found
[4294717.569000] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19a-dev
[4294717.569000] toshiba_acpi:     HCI method: \_SB_.VALD.GHCI
[4294717.593000] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[4294717.593000] toshiba_acpi: ktoshkeyd will check 2 times per second
[4294717.593000] toshiba_acpi: Dropped 0 keys from the queue on startup
[4294730.813000] apm: BIOS version 1.2 Flags 0x02 (Driver version 1.16ac)
[4294730.813000] apm: overridden by ACPI.

  pppd version 2.4.2 may not be fully compatible with 2.6.8 kernel releases.
  If an initial CONNECT is achieved without PPP being subsequently established,
  drop back to a 2.4.1 version.  This has worked for PCTEL AMR modem users,
  supported by the http://www.smlink.com  slmodem software.
  Check pppd version with:
    pppd --version
  See  http://linmodems.technion.ac.il/archive-fourth/msg03167.html
    
  debian_version is not yet providing pre-compiled drivers for WinModems

```

I used the information contained here and downloaded the SLMODEMD.gcc3.tar.gz, which after several false starts installed on Ubuntu using the instructions provided.  The following is a transcript of how it was installed, complete with all my blunders and mistakes:
```
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ make
make: *** No targets specified and no makefile found.  Stop.
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ make SLMODEMD
make: *** No rule to make target `SLMODEMD'.  Stop.
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ chmod a+x slmodemd
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ cp /user/sbin
cp: missing destination file
Try `cp --help' for more information.
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo chmod a+x slmodemd
Password:
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo cp /user/sbin
cp: missing destination file
Try `cp --help' for more information.
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo cp /user/bin
cp: missing destination file
Try `cp --help' for more information.
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo cp slmodemd /usr/sbin
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ find /usr -name slmodemd
/usr/sbin/slmodemd
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ modprobe low_level_driver
FATAL: Module low_level_driver not found.
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo slmodemd --alsa -c USA modem:1 error: mixer setup: attach hw:1 error: No such file or directory
ALSA lib pcm.c:1959:(snd_pcm_open_conf) Invalid type for PCM modem:1 definition (id: modem, value: cards.pcm.modem)
error: alsa setup: cannot open playback device 'modem:1': Invalid argument
error: cannot setup device `modem:1'
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo modprobe snd-intel8x0m
plantperson@pplaptop:~/Modem_Nonsense/SLMODEMD.gcc3$ sudo slmodemd --alsa -c USA modem:1
SmartLink Soft Modem: version 2.9.11 Jan 19 2006 21:19:22
symbolic link `/dev/ttySL0' -> `/dev/pts/1' created.
modem `modem:1' created. TTY is `/dev/pts/1'
Use `/dev/ttySL0' as modem device, Ctrl+C for termination.

```
As you can see, I was kind of blundering around, not completly understanding what I was doing.  I was simply trying to follow the provided instructions.  But by the end, the modem appeared to be set up.  I input /dev/ttySL0 as the route to my modem in the Ubuntu network settings dialog and the settings to connect to my ISP.  I clicked the activate button.  My first couple of tries it didn't work, I'm not sure why.  I messed with the settings a little (the login and phone number settings.)  On the second or third try my modem made the dialing noise and suddenly I was connected.  I browsed around for a little while, then clicked on the button to deactivate the connection in the aforementioned network settings dialog.  Shortly afterward I discovered that it had not disconnected, though.  There was no dialtone on the phone.  I had to pull the plug from the modem to truly disconnect.  But then I found, trying again later, that I could not connect, even following the same method (admittedly I'm not sure how or why it worked the first time) I had before.  The modem speaker itself was silent, and if I picked up the phone I was met by a truly obnoxious beeping noise: BEEP BEEP BEEP BEEP BEEP Then I made what I think must have been my biggest mistake: I ran these commands again:
   sudo modprobe snd-intel8x0m
   sudo slmodemd --alsa -c USA modem:1
Now if I click the aforementioned button in the aforementioned dialog, I see this message:
[[img]http://img439.imageshack.us/img439/746/screenshot3et.png[/img]](http://imageshack.us)

How badly have I goofed things up, and how I can get my modem running permanently?  Thanks for your help.

---

### Post by towsonu2003 on 2006-04-14
no need to worry, nothing is messed up. I'm using a very similar modem, so I can help. Let me go step by step:

-1. Looking at the file you downloaded (tar.gz), I'm assuming you did not follow the wiki page (second link in my signature), which is perfect in this instance :)

0. Remove everything you wrote to the GUI dialer (gnome-ppp?), make sure it is deactivated and stuff (well, most probably, after a fresh reboot, modem will not be there). 

1. You compiled a package, that's great :)

2. check out the second link in my signature. you will be looking for how to configure and use wvdial. It's a dialer. 

3. check if the module is loaded ```
lsmod | grep snd-intel8x0m
```if it gives any output, it's loaded. if it's not loaded, give ```
sudo modprobe snd-intel8x0m
```

4. as usual, ```
sudo slmodemd --alsa -c USA modem:1
```leave it like that (some modems don't work properly when slmodemd is sent to the background)

5. open a NEW terminal

6. now, configure wvdial using instructions in the wiki page

7. dial with wvdial. Append the following lines at the end of your /etc/wvdial.conf file after you configured wvdial: ```

Carrier Check = no
Stupid Mode = yes
``` 

8. After dialing, 7 out of 10 times (or more), it will say "no carrier" or "no dial tone". Check if the phone is working (pick up the phne and hear dial tone). dial again. again. again. you get the point. For me, dialing takes anywhere from 2 minutes to 20 minutes. 

9. once connected, leave that terminal alone as well. I usually switch to another work space (ctrl + alt + right arrow) so I don't mess it up. 

Next time you dial, follow only these: 
3 (check module), 4 (activate modem), 5 (new terminal), 8 (dial), 9 (go to other work space)

When it's time to disconnect, simply fo to work space where wvdial terminal is, click it once (the terminal, to give focus to it), and hit ctrl + c

After a few reboots, if you see that the module is always loaded without any interference (which is what's supposed to happen), drop step 3. 

PS. Now that you already compiled the kernel, you don't need this. but when you do a clean install, you can use the precompiled thing at [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/) (it will be called slmodem alsa precompiled 2.9.9a or similar). To use, untar it to "~/home" and do "sudo ./slmodemd -a -c USA modem:1" (no quotes)

---

