---
title: "modem problem on laptop"
date: 2005-11-27
forum: General Help
---

### Post by royal_flare on 2005-11-27
I have an Asus degatto laptop which i have recently installed with 5.10
the modem does not work. I am still a newbie and I am not sure if I am doing the instructions in the internet right. whenver i type 

modprobe ltserial

I get this

Fatal: Error inserting ltserial (/lib/modules/2.6.12-9-386/other/ltserial.ko) : No such device.

I don't know how to edit the grub too.

can anyone give me a detailed step by step instruction. What to type what result to expect and such. I hope someone can spare the time to help
Thank you in advance.

---

### Post by towsonu2003 on 2005-11-27
it seems you have a "winmodem". they are hard to configure, and sometimes they just don't work unfortunately i must say; but reading, patience, and being stubborn usually solves the problem. 

best thing to do, i think, is to go to linmodems.org, read that page, download scanModem tool, read the readme in it, and follow the instructions very very carefully. basically, you will run scanModem to find out what modem you have and how to configure it... but please read all documentation very carefully...

once you run scanmodem, after reading the file 1stread.txt and infogeneral.txt, proceed to reading modemdata.txt and follow its instructions as close as possible...  if you can't figure out what it says, you can mail the output to their mailing list to get some help... but before sending, be sure you read what it says at the very beginning about mailing :)

good luck

let us know how you're doing, any problems, and how you succeeded if you do (hopefully).

PS. no need to edit grub (unless linmodems.org advises to do so)...

---

### Post by royal_flare on 2005-11-27
I have read the ModemData.txt but I cannot understand it. meaning there seems to be no clear thing to do. It think it says that I have a smartlink but according to windows xp I have a Lucent .

Here is a copy of that text file. I really hope someone can help me



 DO use the following line as the email Subject Line, to alert cogent experts:
      scanModem, Ubuntu 5.10 "Breezy Badger"  kernel 2.6.12-9-386
 Occassionally reponses are blocked by an Internet Provider mail filters.
 So do in a day also check the Archived responses at [email]DISCUSS@linmodems.org[/email]
Code updated on:  2005_Oct_23
------------ --------------  System information ------------------------
 Ubuntu 5.10 "Breezy Badger" 
 on System with processor: i686
 currently under kernel:   2.6.12-9-386
 The kernel was assembled with compiler:  3.4.5
 with current System compiler GCC=4.0.2
    /usr/bin/gcc -> gcc-4.0
      
 The Major.Minor versions differ in the designated compiler 4.0.2 and the 3.4.5 used in kernel assembly!!"
But there must be a match on the target for driver installation, 
of gcc Major.Minor versions or kernel and drivers!!
Otherwise the drivers will fail to load with warning:
  Invalid module format!!"
See [http://linmodems.technion.ac.il/archive-fifth/msg04252.html](http://linmodems.technion.ac.il/archive-fifth/msg04252.html) 
 

A package kernel-kbuild-2.6-3 or later version must be installed to support compiling

Checking for kernel-headers needed for compiling.
The kernel-headers have base folder: 
/lib/modules/2.6.12-9-386/build -> /usr/src/linux-headers-2.6.12-9-386
/usr/src/linux-headers-2.6.12-9-386
 A /dev/modem symbolic link is not set.

drwxr-xr-x  2 root root 0 2005-11-28 03:40 /dev/.udevdb
There is an active UDEV file system, creating device nodes in volatile RAM.
However information from Proprietary drivers is soon to be excluded from 
the supporting /sys/ file structure.  Thus device nodes for Proprietary modem drivers
will then have to be created by bootup scripts.

 Checking for modem symbolic link support lines within /etc/udev/ files

 USB modem not detected.


Modem candidates are at PCI_buses:  0000:00:02.6
    
Providing detail for device at  0000:00:02.6
  with vendor-ID:device-ID
	    ----:----
Class 0703: 1039:7013   Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0) (prog-if 00 [Generic])
  SubSystem 1043:1616  Asustek Computer, Inc.: Unknown device 1616
	Flags: medium devsel, IRQ 18
 Checking for IRQ 18 sharing with modem.
O-APIC-level  SiS SI7012

  
                  -----PCI_IDs-------                    --CompilerVer- 
    Feature List:  Primary  Subsystem Distr  KernelVer   kernel default  CPU
 ./scanModem test 1039:7013 1043:1616 debian 2.6.12-9-386  3.4.5 4.0.2    i686
   for this pair, -----PCI_IDs-------, a modem codec is not in the records.

 Acessing archival information on all codecs used by SubVendor 1043 , for all Modem controllers
CXT
SIL27
CXT
SIL21
CXT

       
 The controller: 1039:7013  SIS 630 
 is capable of supporting soft modem chips from AT LEAST manufacturers:
	Pctel
	AgereSystems
	Conexant
	Intel
	Smartlink
 The Subsystem PCI id does not itself identify the modem Codec.
Checking for autoloaded ALSA modem drivers

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

 DisAgreement between diagostic and Archive data.  Using diagnostic: CODEC=SIL27
 The Subsystem has an Agere Systems codec SIL27

 The modem can be set up by:
 # su - root
 # modprobe snd-intel8x0m
 # slmodemd --alsa -c YOUR_COUNTRY hw:1
 
 The ALSA modem driver snd-intel8x0m provides low level hardware access.
 The slmodemd provides high level functions and is  not kernel-version specific.
 From [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)   follow the link  
 SLMODEMD.gcc3.tar.gz or SLMODEMD.gcc4.tar.gz depending on your Systems' gcc major version.
 Also download the ungrad-winmodem.tar.gz and the [http://linmodems.technion.ac.il/packages/unloading.gz](http://linmodems.technion.ac.il/packages/unloading.gz)
 Within the SLMODEMD package the 1st_Read.txt instructions 
 For guidance on bootup automation see:
   [http://linmodems.technion.ac.il/archive-fifth/msg04652.html](http://linmodems.technion.ac.il/archive-fifth/msg04652.html)
 
	Read Modem/Slmodem.txt instruction for doing the slamr diagnostic.

 The debian Linux includes sl-modem packages with Smartlink drivers
   Install the kernel-headers-2.6.12-9-386.deb
   If necessary, set a symbolic link needed for slmodem compiling:
     # ln -s /usr/src/kernel-headers-2.6.12-9-386 /lib/modules/2.6.12-9-386/build
     as described in Modem/DriverCompiling.txt
   Then install the two sl-modem/slmodem packages and follow their directions.
   Thereafter the above slamr diagnositic can be run.

 == Checking PCI IDs through modem chip suppliers ==

 SmartLink at [http://www.smlink.com/](http://www.smlink.com/) owns vendor IDs 163c, 2000, 2003, and 2004
 The official download site is:  [http://www.smlink.com/main/index1.php?ln=en&main_id=40](http://www.smlink.com/main/index1.php?ln=en&main_id=40) ,
 with slmodem-2.9.10 and later releases only licensed for Smartlink chipsets.
 
 A series maintaining a much broader license for other chipset support,
 can be downloaded from [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)  
 Though not always needed, download the files: 
   slmodem-CurrentVersion.tar.gz - provides the most general code package.
   slmodemd-CurrentVersion.tar.gz - provides a compiled slmodemd 
   ungrab-winmodem.tar.gz  -  may be needed for usage with slamr. 
Details on their usage are in Slmodem.txt, Slmodem-ALSA.txt and    [http://linmodems.technion.ac.il/slmodem-serial.html](http://linmodems.technion.ac.il/slmodem-serial.html)  
   
 == Checking PCI IDs through modem chip suppliers ==
 Vendor 1039 is SiS, Silicon Integrated System, producing  soft modem controllers and subsystems.

  ======= PCI_ID checking completed ====== 
 Update=2005_Oct_23

Analyzing information for PCMCIA device at PCI Bus 00:10.0
0000:00:10.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 01)
	Subsystem: ENE Technology Inc CB710 Cardbus Controller
	Flags: bus master, medium devsel, latency 168, IRQ 16
GREPping for an inserted PCMCIA modem with filter:        ommunication
 If a PCMCIA modem is currently inserted and the sockets activated by
    /etc/init.d/pcmcia start
 then the PCMCIA bridge is NOT transparent.

 If the modem is known to have a Lucent digital signal processing chipset,
 then PCMCIA.tar.gz variant assembled by Joern Wustenfeld is necessary,
 rather than the standard ltmodem-8.31a10.tar.gz at  [http://ltmodem.heby.de/](http://ltmodem.heby.de/)
GCCversion=4.0.2
   
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
[4294668.693000] audit: initializing netlink socket (disabled)
[4294669.066000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[4294701.410000] shpchp: acpi_shpchprm:\_SB_.PCI0 evaluate _BBN fail=0x5
[4294701.410000] shpchp: acpi_shpchprm:get_device PCI ROOT HID fail=0x5
[4294709.152000] ibm_acpi: ec object not found
[4294720.695000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294720.695000] apm: overridden by ACPI.
  debian is not yet providing pre-compiled drivers for WinModems

---

### Post by Bachstelze on 2005-11-27
OK, so here's how to do : 

go here : [http://linmodems.technion.ac.il/packages/smartlink/](http://linmodems.technion.ac.il/packages/smartlink/)

download the  SLMODEMD.gcc3.tar.gz file and unpack it somewhere

copy the slmodemd file into your /usr/sbin directory

run those commands

sudo chmod +x /usr/sbin/slmodemd
sudo modprobe snd-intel8x0m
sudo slmodemd --alsa -c YOUR_COUNTRY hw:1
then DO NOT press Ctrl-C

Open a new terminal, run

sudo wvdialconf /etc/wvdial.conf

hopefully it will detect your modem. Run

sudo gedit /etc/wvdial.conf

enter your ISP's phone number and your login/password, close gedit, run

sudo wvdial

and hope it works :p

---

### Post by royal_flare on 2005-11-27
thank you for reply HymnToLife
everything went fine until i got to

 sudo wvdial

i got this 

tux@tux:~$ sudo wvdial
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
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.


but I am sure Ii wrote the right phone number, login name and password
am I supposed to hear any ring? because I heard nothing.

---

### Post by Bachstelze on 2005-11-27
If I remember well, wvdialconf adds something to those three lines that you have to remove, single quotes I think. Your lines have to be :

Phone = PhoneNumber
Username = login
Password = password

with NOTHING else. BTW, if once you are connected, you get a "carrier lost" error (often the case), add this line

Carrier check = no

---

### Post by royal_flare on 2005-11-27
it adds <> but I have taken those already, but still the error. any mor ideas?

---

### Post by Bachstelze on 2005-11-27
here's how mine looks after running wvdialconf

```
[Dialer Defaults]
Modem = /dev/ttySL0
Baud = 460800
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
; Phone = <Target Phone Number>
; Username = <Your Login Name>
; Password = <Your Password>

```

You also have to remove the semicolons at the beginning of the lines.

---

### Post by royal_flare on 2005-11-27
oh... i did not remove the semicolons
one more question must I always go all those steps to use my modem?

---

### Post by Bachstelze on 2005-11-27
[QUOTE=royal_flare]oh... i did not remove the semicolons
one more question must I always go all those steps to use my modem?[/QUOTE]

No, you "only" have to run the slmodemd line and the wvdial. There might be a way to do it automatically but I didn't look into it.

---

### Post by royal_flare on 2005-11-28
after correctly entering the number, username and password, minus the <> and semicolons, it finally dialled! However my happiness was short lived, It continuously asked me for my password. It is really frustrating. First time it asked me I typed the password I used when I edited wvdialconf. Weird thing is it did not use asterisk to mask what was being typed. And it seems that I used the wrong password, when I am pretty sure it is the right one. here is what is being shown to me. The password is the bold one below. Then I even tried a blank password but still to know avail. Does any have an idea why this happens. I really want to use ubuntu, but this modem issue is really frustrating for a newbie like me. Hope someone patient out there can still help me. Thanks

tux@tux:~$ sudo wvdial
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
--> Sending: ATDT4161221
--> Waiting for carrier.
ATDT4161221
 CONNECT 50667
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT4161221
--> Waiting for carrier.
Welcome to 3Com Total Control HiPer ARC (TM)
Networks That Go The Distance (TM)
Login:/Username:
ATDT4161221
Password: **pn3gytry**

--> Timed out while dialing.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
ATDT4161221
CONNECT 50667
--> Carrier detected.  Waiting for prompt.
--> Connected, but carrier signal lost!  Retrying...
--> Sending: ATDT4161221
--> Waiting for carrier.
Welcome to 3Com Total Control HiPer ARC (TM)
Networks That Go The Distance (TM)
Login:/Username:
Login:/Username:
ATDT4161221
Password:
^A
--> Timed out while dialing.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
Login:/Username:
Login:/Username:
ATDT4161221
Password:
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
Login/Password Error! Please Try Again!Request Denied
--> Voice line detected.  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
NO CARRIER
--> No Carrier!  Trying again.
--> Sending: ATDT4161221
--> Waiting for carrier.
ATDT4161221

[1]+  Stopped                 sudo wvdial

---

### Post by Bachstelze on 2005-11-28
> --> Connected, but carrier signal lost! Retrying...

Add a line in your wvdialconf.txt saying : 

```
Carrier check = no
```

I think I already told you that... Well, never mind, it should work now :)

---

