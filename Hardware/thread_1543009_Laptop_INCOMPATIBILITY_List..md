---
title: "Laptop INCOMPATIBILITY List."
date: 2010-07-31
forum: Hardware
---

### Post by Elfy on 2010-07-31
[B]Welcome to the _Laptop_ Incompatibility List.
[/B]
The purpose of this thread is for you, the user, to post what laptop combination doesn't work with Ubuntu for you. If you wish, you may post how the laptop works (configuration related), and the steps you took setting it up. These informations will help other users to choose new laptops.

If you see an old warning regarding a particular laptop, bear in mind that the problem might be solved in the present release of Ubuntu.

Everyone is welcome to post here, as long as it is laptop related data. For help with laptop problems, please use the standard procedure of searching the forums, and starting your own thread for assistance if no answer is found.

Give detailed explanations when reporting incompatible laptops including the version of ubuntu you use. 

Also do not post any lspci outputs in this thread as they will be removed without question.

If the only problem is that the graphics driver is not considered fast enough please don't post here. Better to post a comment like for example *works well for standard office use but not for intense gaming* in [Laptop Compatibility List]("http://ubuntuforums.org/showthread.php?t=1543006").


Please only list
1) Version Of Ubuntu
2) Laptop Maker
3) Laptop Model
4) Known Issue


[COLOR=Red]*NOTE* This thread is exclusively for the listing of incompatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly. *NOTE*
[/COLOR]
Thank you.
Thread text shamelessy lifted and edited from Frodon's Desktop threads.

Edit - [HardwareSupport/Machines/Netbooks wiki page ]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")

---

### Post by corrytonapple on 2010-07-31
I have a Toshiba L455 with Ubuntu 10.04. The fan control with Ubuntu doesn't work, and none of the Function keys work. Now, I can not hear sound and my microphone will not work. Considering other options now.......
Oh well.

---

### Post by RebateFX on 2010-08-01
1)Version Of Ubuntu: Lucid 10.04 
2)Laptop Maker: Sony
3)Laptop Model: Vaio X Series (VPCX117LG)
4)Known Issue: Poulsbo! :(
The GMA500 graphics chipset is the only thing that lets this machine down as far as Ubuntu goes. It's a pain to get it to work with the various methods of installing poulsbo drivers out there, and when you do get it to work, the performance is very, poor.

---

### Post by Isaac_x on 2010-08-01
Ubuntu 10.04 with latest updates
Apple Macbook 2,1

Issues:

Installation:
TTY shows up at end of installation with a slew of "cannot access device" errors after ejecting the CD

Hardware:
- no sound even though the device is installed and no errors are reported
- video support breaks when using multiple monitors in horizontal (size-by-side) configuration
- external monitor flickers when at 1920x1200 when the built-in monitor is turned off
- Logitech MX440 mouse buttons not configurable

Shutdown:
- shutdown graphics shows at corner of monitor instead of filling the entire monitor like the startup graphics

Software:
- constant password prompts to install userspace applications
- ability to mount fuse filesystems in userspace, but **no ability to unmount them afterwards** without root privileges
- no GUI for NFS mounts
- no GUI for mouse button configuration

Miscellaneous:
- the user interface is frighteningly clunky. I'm saying this as someone who spends most of his time at the command line.
  - no integration between different interface elements.
  - no consistency in keyboard shortcuts
  - The default theme is square, dark, and unfriendly
  - menus are cluttered and unorganized.

---

### Post by citizencj on 2010-08-04
I have a Toshiba Satellite 1135 and neither the fan nor the built in mousepad are working.

---

### Post by TBABill on 2010-08-04
Lucid 10.04
Dell
Inspiron 1564
Issue: My model of Dell Inspiron 1564 uses the onboard GPU (Intel) built into the same chip as the CPU (Intel Core i3 CPU). The video chip is not supported in kernels 2.6.32(all) or earlier. 2.6.33 and later work fine. This is the case for any distro, not Ubuntu-specific.

---

### Post by Fludizz on 2010-08-10
1) Ubuntu 8.04LTS, 10.04LTS
2) Acer
3) Aspire AS5051

Does not work, ACPI issue (Mainboard in the notebook is Foxconn). With acpi=off the system is able to boot but then you cannot use: miniPCI, PCMCIA slot, onbaord ethernet, onboard audio, onboard modem. Basically, without acpi the system is useless and with acpi it cannot boot.

10.04 does manage to boot and install but the graphics does not work properly due to bugs in the fglrx module with the ATi Xpress 200M chipsets. Audio doesn't seem to work (Realtek HD-audio chip, don't remember exact version cannot verify, laptop is now broken).

---

### Post by spencerthayer on 2010-08-17
Acer Aspire 5738PG-6306
Ubuntu 10.4

1) Touchpad does not work without using the following commands:
sudo modprobe -r psmouse
sudo modprobe se proto=imps

If the button to turn of the touchpad is pressed then a reboot is required to get the modprobe to work again.

2) No multi-touch in the Touchpad. I read there are fixes for this and I will be trying them.

3) Dual Touchscreen monitor does not work apparently at all.

4) Bluetooth not detected.

---

### Post by mdog on 2010-08-18
Alienware M15x (configured with i5-540m and gtx 260m) running Ubuntu Lucid Lynx 10.04 LTS

Most to least critical:

1. **No fan control (fan seems to always run at lowest setting)**
2. No CPU temperature readings
3. No sensors apart from Nvidia and SMART temperatures

"sensors-detect" finds nothing, there really should be basic support for my CPU and chipset.

The kernel does find some cooling devices, but "/proc/acpi/fan" is empty (dmesg output):

```

[    0.711573] processor LNXCPU:00: registered as cooling_device0
[    0.715086] processor LNXCPU:01: registered as cooling_device1
[    0.717449] processor LNXCPU:02: registered as cooling_device2
[    0.723684] processor LNXCPU:03: registered as cooling_device3
[    1.165893] acpi device:07: registered as cooling_device4

```

---

### Post by iamnate on 2010-08-19
ASUS K50IJ - BBZ5 (Best Buy version)
Specs: [http://www.notebookshopper.net/asus-k50ij-bbz5.html](http://www.notebookshopper.net/asus-k50ij-bbz5.html)
Running Ubuntu 10.04 64 bit version

Overall: Zippy and very cheap dual core with a few tiny little issues. Wish I didn't have to dual boot to have proper speaker/headset sound management. 

Issues: 

Installation: 

CON: On LIVE CD I was not able to resolve sound issue. Plug in headset, sound in headset. Adjust volume, and all of a sudden sound on computer AND headset. With this model, I found all sorts of "fixes" that eventually left me with a low non-stop buzzing sound. So instead of install on entire disk, installed dual boot, ran updates, back to no headset AND speaker sound. Dumb sound better than no sound. I watch netflix on win7 anyway. 

PRO: On dual boot this one is very nice because no need to create extended partition, Win7 only takes up 2 partitions as opposed to some other MFR's that suck up 4 partitions.. Very little hassle, and Win7 partition was easily modified to 60 Gb and the rest of that unallocated space went to Ubuntu and swap file which was done automatically through setup process. 


Video: 

For some reason, randomly, the screen flashes garbage for a split second. No particular encumbrance and it only happens randomly. Not sure why and not enough of a bother to try to "fix" (see above). 


Touch pad:  

When selecting System > Preferences > Mouse (because no "touchpad" option, of course) there is no Touch Pad tab as there should be with this installation (as opposed to other laptops). This tab would grant one the opportunity to "shut off" the touchpad while typing and also give you the opportunity to do vertical and horizontal scrolling, which, at this time, I am unable to do. 

The touch pad is INCREDIBLY sensitive and typing with wrists or shirt cuffs leaning close to touch pad causes the mouse to jump the cursor all over the screen, particularly in places not meant. Keep eyes open and type with wrists up further than normal to prevent this, particularly if you type fast. 


Function Keys: 

The function keys are hit or miss. They all work perfectly in win7, not in ubuntu 10.04. If, for example, I choose to increase volume on speaker, that's FN+F12. Doesn't work. Neither does the screen contrast change, exactly. If you FN+F5 or FN+F6 for more than a few seconds, it randomly tries to adjust the screen for several minutes. Several long minutes until you reboot. Weird. FN+F7 (monitor shutoff) works fine unless you tried to adjust the contrast. The FN+F9 (shut off touchpad) doesn't appear to work (but it could be because I tried messing with contrast buttons. 



Other things: 

Battery, fan,  wireless networking, all worked out of the box perfectly with no issue. This system never gets hot and works with battery for hours with no hassle.  

If anyone at all has this specific model and has PERSONALLY resolved these specific issues, I would be extremely happy to know about it and post the results of such specific results in an applicable forum.

Thanks!!!

- Nate

---

### Post by Elmer Fudd on 2010-08-19
1) 10.04
2) ACER 
3) 7736Z-4809  Intel graphics
4) -No dimming (indicator works with function keys but no dimming control)
   -No mulitouch on touchpad

Everything else works great.

---

### Post by Smooth357 on 2010-08-24
1)10.04 LTS 64-bit dual boot Win 7 64-bit
2)Dell
3)Latitude D830
4)Wireless works and then doesn't work. ](*,)

= = = = =
Mörgæs 2014-12-19:
For 14.10 it all works, Intel Wireless 4965 AG / AGN wifi card.

---

### Post by rioatca on 2010-08-24
1) 10.0.4
2) DELL Latitude E6510
3) NVIDIA 310M
4) SEIKO EPSON 15' TFT LCD
 
black screen on LCD, but works on the external monitor.
See similar issue on Intel HD VGA on same Latitude model, so guess be LCD driver issue ...  still can't find the workable linux driver for it.

---

### Post by kristin70 on 2010-09-02
I have a Toshiba Satellite L300D with Ubuntu 10.04.1. The fan control with Ubuntu doesn't work, and none of the Function keys works :(

---

### Post by Tracy177 on 2010-09-02
ok 

1 ubuntu 10.04 

2 msi 

3 msi gt725 

4  udev has issue with optiarc dvd rw everytime u boot u have to restart udev to make  cpu go to 0% load (solution i upgraded kernel to 2.6.35-19 and now optiarc and udev work correctly)
intel acl1200 doesnt work out of the box u have to configure it and it take a bit of time.
OS driver for ati hd4850 use more gpu and cpu than fglrx 
i didnt try to configure or look for solution to make ati hdmi work
when you play HD clips movies from desktop or from youtube cpu load goes to 65% gpu stays at 5%

---

### Post by A Feyn Man on 2010-09-03
1. 10.04 LTS
2. Sony
3. VPCZ1290X (a.k.a. 'vaio z series')
4. original install of Win 7 on fakeraid wasn't immediately compatible, switched to 2x64GB SSDs in JBOD. Graphics are a big pain, neither integrated Intel HD or dedicated NVidia GT330M are recognized. Try to use 'nvidia-xconfig' to set up xorg.conf but to no avail. Tried to install appropriate driver from NVidia website which also didn't work. Only way to make it not boot to black screen is to edit grub boot commands replacing "quiet splash" with "single nomodeset i8042.nopnp" also to make the touchpad work. This allows me to boot in FailSafeX graphics mode which knocks down my screen to 1280x1024 but I have the 1920x1080 model and would obviously like to harness the switchable graphics.

---

### Post by corrytonapple on 2010-09-04
> **kristin70 said:**
> I have a Toshiba Satellite L300D with Ubuntu 10.04.1. The fan control with Ubuntu doesn't work, and none of the Function keys works :(
I guess it is a product wide issue.

---

### Post by A Feyn Man on 2010-09-05
Also when I boot the -24 kernel I get an error with udev

---

### Post by configur3d on 2010-09-05
1)Ubuntu: 10.04
2)Compaq
3)6510b
4)No Known Issues. The only thing I've run into was the flash player (like for youtube or hulu) but that was easily fixed by installing the "resistricted extra" package. I'm new to linux and still learning the OS...but so far everything has worked. Wireless, speakers, built in mic, graphics, The dimming functions, touch pad, usb mouse, eject button for the CD. I'm extremely pleased with this OS. I'm mostly a windows guy.

I'm still trying things out so I guess I'll edit this as I find things. But as for now everything works. I haven't tried a webcam because I don't have one. As soon as I can find one I'll give it a go. Also, haven't tried printing. 

So, yeah...it seems likes Ubuntu 10.04 and the compaq 6510b play very well together.

---

### Post by hendraorhnd on 2010-09-05
1)Version Of Ubuntu
10.04

2)Laptop Maker
HP

3)Laptop Model
HP Mini 110-3014tu

4)Known Issue
a. Webcam too slow perform for video capture 
b. Card reader does not active, output:

```

~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

HP Driver for Xp listed as Realtek USB 2.0 card reader, or intel matrix storage manager.

---

### Post by hendraorhnd on 2010-09-05
1)Version Of Ubuntu
10.04

2)Laptop Maker
HP

3)Laptop Model
HP Mini 110-3014tu

4)Known Issue
a. Webcam too slow perform for video capture 
b. Card reader does not active, output:

```

~$ lspci
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
01:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b1eb Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

HP Driver for Xp listed as Realtek USB 2.0 card reader, or intel matrix storage manager.

---

### Post by 1121eddie on 2010-09-07
OS: Ubuntu 10.04 all latest updates.
Manufacturer: Asus 
Model: X5DIJ Notebook

Known issues: Screen keeps flickering on bottom half like it's cutting out. Sound does not mute when headphones are plugged in, sounds continue to play through speakers and headphones. DVD drive tray does not eject when the button is pressed, only using right click --> eject method will work.

---

### Post by squGEIm on 2010-09-10
Version: 9.04
Maker: HP
Model: 4420s
Issue: 
I tried installing from the live dvd, but the screen won't show anything. I went to 'try without installing', the cursor blinks for a while, and then the screen goes blank. Afer a while, I can hear the starting music, but there's still no display.
I went to 'install ubuntu', but the same thing happens: the cursor blinks for a while, then the screen goes blank.
Then, I installed it inside Windows. When i went to Ubuntu in the boot loader, again the same thing happens!
I've used the same DVD to install it in another laptop (Acer Aspire), and it's working fine. So, i guess it's nothing wrong with the DVD.

---

### Post by trinityclare on 2010-09-12
Ubuntu 10.04 Lucid
Gateway
ID59C notebook

Problem #1: No brightness control, either through function keys, brightness applet, or power management settings.

Problem #2: No touchpad support -- no touchpad tab in Mouse options, no scrolling, no multitouch, no option to disable touchpad while typing (although Fn+F6 to disable the touchpad does work).

The lack of brightness control is a really bummer, otherwise I'd be spending way more time in Ubuntu and way less time in Windows.

---

### Post by poltak on 2010-09-12
Version: 10.04, 10.10 beta (both 32bit)
Maker: Acer
Model: Aspire 4736
Issue:
Brightness adjustment doesn't work. Bluetooth isn't detected.

---

### Post by ubunwhat on 2010-09-13
Ubuntu 10.4
Toshiba
Satellite P205

Cannot boot.  I get as far as the boot menu, but nothing after that.  At one time it would boot and then black screen after a few minutes of being logged in.  It is my understanding that this is related to the Intel 950 chipset.

---

### Post by lotech on 2010-09-28
1. Ubuntu 10.10 beta (32bits)
2. Lenovo
3. S10-3s
4. As least one function key no longer function, I can't turn on wifi, touchpad button also no response, worked on 10.04

5. Now the touchpad completely disabled after the update

---

### Post by c00lwaterz on 2010-09-28
Version of Ubuntu: all linux
Maker: Toshiba
Model: M900
Issues: High temperature probably in GPU and fan not working. I did not try the bluetooth and mic if it works.

---

### Post by ybaruss on 2010-09-29
Version of Ubuntu: 8.04 / 8.10 / 10.04
CPU: AMD Turion™ X2 Dual-Core Mobile Processor RM-70   							
GPU: ATI Mobility Radeon™ HD 3650 supporting HyperMemory™ technology   							
Maker: Toshiba
Model: P300D

Rather correct and increasing compatibility since 8.04.
Major issues are:

[LIST]
[*]Over temperature crash: can be overcame by forcing both CPU speed to 800MHz (rather than 2.0GHz). At this speed online video are lagging but correct when ondisk.
[*]USB Realtek RTL8187B Wireless Adapter and Chicony USB 2.0 Camera but working better since 10.04Lucid but still not able to install skype for instance.
[*]ATI fglrx divers worked strangly in 8.04Hardy but seem ok now in 10.04Lucid.
[*]Battery manager still reports absurd data particularly for charge but I didn't see power time difference with Windows.
[/LIST]

PS: Should COMPATABILITY List and INCOMPATABILITY List merged into a PERFORMANCE REPORT common post ?

---

### Post by decoherence on 2010-10-02
Ubuntu 10.04.1
Toshiba a660
No output through headphones. No input through microphone. Internal speakers work fine, tho.

Here's the thread: [http://ubuntuforums.org/showthread.php?p=9918297](http://ubuntuforums.org/showthread.php?p=9918297)

---

### Post by heroofhyrule on 2010-10-05
1.  Ubuntu Lucid 10.04 (installed via Update Manager)
2.  HP
3.  Pavilion dv6000

KNOWN ISSUES:

[LIST]
[*]Button above the TouchPad to turn said TouchPad on and off completely locks up the computer when pressed.
[*]Wireless on/off switch on the front of the laptop does not work (wireless is always on).
[*]Installation with the 10.04 LiveCD does not work; the screen becomes corrupted when attempting to boot from this CD.  I used the Ubuntu 9.04 LiveCD, installed it, and then upgraded through Update Manager; no problems booting since then.
[*]Wireless multimedia remote does not work (mine could just have a bad battery, check yours).
[*]Quickplay controls (there are 2 of them) on the left side above the keyboard do not work, however the multimedia controls (stop, pause, play, fastforward, rewind, and volume) on the right hand side do indeed work.
[*]System > About Ubuntu does not work; it loads and then quits.
[/LIST]

---

### Post by nosense10 on 2010-10-07
Hey people!

I really need help! This is my first time posting , i used Ubuntu 10.10 and i have a 

TOSHIBA L650-11F [CORE I5-430M,4GbDDR3,HD5650]

and i can't install the drivers of the wireless .

The card is Atheros AR8152 ...

---

### Post by demetrius2009 on 2010-10-13
[LIST=1]
[*]Ubuntu Maverick 10.10 64bit
[*]Asus
[*]K52JR
[*]Internal speakers works only on laptop independently if you plug in or unplug the headphones, anyway - no sound in headphones
[/LIST]

---

### Post by tpsvca on 2010-10-13
> **demetrius2009 said:**
> [LIST=1]
[*]Ubuntu Maverick 10.10 64bit
[*]Asus
[*]K52JR
[*]Internal speakers works only on laptop independently if you plug in or unplug the headphones, anyway - no sound in headphones
[/LIST]

Same problems with Asus K52F. Web cam on Skype is upside down.

---

### Post by Mel M on 2010-10-15
1)Version Of Ubuntu: 10.10 
2)Laptop Maker: ASUS
3)Laptop Model: EEEpc 1101HA
4)Known Issue: The GMA500 graphics chipset

I can run it but I'm stuck at 1024x600 (It should be 1366x768 on this 11.6" WXGA screen), with no Unity interface. Can't even use the Poulsbo drivers, installing them leaves me at tty1.

Its funny that on my ASUS EEEpc 701SD with its 7&#8221; WVGA Widescreen & 512MB of Ram, Ubunru Netbook Edition 10.10 works without any issue. I guess its because the 701SD uses GMA900. SIGH!

---

### Post by FenixAzul on 2010-10-15
**Re: Laptop INCOMPATABILITY List.**
 		1)Version Of Ubuntu: 10.10 (32bits and 64bits do the same)
2)Laptop Maker: ASUS
3)Laptop Model: G73J-B1
4)Known Issue: Very Slow during live session when installed runs a bit faster but in my aspire one runs super fast lol

---

### Post by habib_seif on 2010-10-15
Version of Ubuntu: 10.10
Laptop Maker: Dell
Laptop Model: n4030
Known Issue: Touchpad is not recognised

The touchpad is recognised as a generic mouse, and therefore, its vertical scrolling does not work.
Here is the output of "cat /var/log/Xorg.0.log |grep -i mouse" command:

```
[    23.247] (==) intel(0): Silken mouse enabled
[    24.354] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/event5)
[    24.354] (**) USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    24.354] (**) USB Optical Mouse: always reports core events
[    24.354] (**) USB Optical Mouse: Device: "/dev/input/event5"
[    24.365] (II) USB Optical Mouse: Found 3 mouse buttons
[    24.365] (II) USB Optical Mouse: Found scroll wheel(s)
[    24.365] (II) USB Optical Mouse: Found relative axes
[    24.365] (II) USB Optical Mouse: Found x and y relative axes
[    24.365] (II) USB Optical Mouse: Found absolute axes
[    24.365] (II) USB Optical Mouse: Configuring as mouse
[    24.365] (**) USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    24.365] (**) USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.365] (II) XINPUT: Adding extended input device "USB Optical Mouse" (type: MOUSE)
[    24.365] (II) USB Optical Mouse: initialized for relative axes.
[    24.365] (WW) USB Optical Mouse: ignoring absolute axes.
[    24.366] (II) config/udev: Adding input device USB Optical Mouse (/dev/input/mouse0)
[    24.381] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/event9)
[    24.381] (**) PS/2 Generic Mouse: Applying InputClass "evdev pointer catchall"
[    24.381] (**) PS/2 Generic Mouse: always reports core events
[    24.381] (**) PS/2 Generic Mouse: Device: "/dev/input/event9"
[    24.400] (II) PS/2 Generic Mouse: Found 3 mouse buttons
[    24.400] (II) PS/2 Generic Mouse: Found relative axes
[    24.400] (II) PS/2 Generic Mouse: Found x and y relative axes
[    24.400] (II) PS/2 Generic Mouse: Configuring as mouse
[    24.400] (**) PS/2 Generic Mouse: YAxisMapping: buttons 4 and 5
[    24.400] (**) PS/2 Generic Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    24.400] (II) XINPUT: Adding extended input device "PS/2 Generic Mouse" (type: MOUSE)
[    24.400] (II) PS/2 Generic Mouse: initialized for relative axes.
[    24.401] (II) config/udev: Adding input device PS/2 Generic Mouse (/dev/input/mouse1)
```

---

### Post by the wolfe on 2010-10-16
HP G61-336NR
Athlon II M300 
Lucid Linux (10.04)

1.Doesn't recognize that there is a webcam, and thus has a driver (rather lack of one)      issue.  
2. Audio out (Headphones) don't work. NO sound at all. Don't know if it is a driver issue.
3. cant wake up from suspend. The screen comes on, but looks like a busted LCD. Works fine once restarted though.

---

### Post by MDnetBoss on 2010-10-17
1)Version Of Ubuntu: 10.04
2)Laptop Maker: Toshiba
3)Laptop Model: Techra A4 1.5gb
4)Known Issue: Graphics writes very slowly, sometimes hangs.

---

### Post by doonex on 2010-10-18
[SIZE=4]i have new EPC umpc netbook 7" wince 6.0
[/SIZE][SIZE=4][FONT=Arial][COLOR=black][FONT=Arial verdana]CPU: AK7802 266M
	
	Operation System: WINDOWS CE 6.0
	
	Screen:LCD 7INCH wide-screen (800*480)
	
	Memory: 128MB
	
	Storage Device: 2GB Inbuild Flash
	
	LAN: 10/100M Ethernet Access
	
	WIFI: 802.11b/g

[/FONT][/COLOR][/FONT]can i install ubuntu?

[/SIZE]

---

### Post by Hagar55 on 2010-10-19
1) ubuntu 10.10
2) Dell Studio 1737

Intel 5100 wireless mini card

problem: wireless refuses to connect in any version of 10.10, earlier versions have no issues.

---

### Post by lottomotto on 2010-10-19
Asus F50sv
Ubuntu 10.10 (was working before up to 10.04)
starts only with acpi=off (unusable)

---

### Post by Stephen_at on 2010-10-21
1)10.10
2)Toshiba
3)Satellite SA30-203
4)Starts to boot off CD for install and then screen goes black. Suspect its a video driver problem.

Edited to add that it specifically is the intel integrated video chip which is the problem. It seems its known failing of Linux and is to do with the kernel modeset option however there seems to be no reliable work around

---

### Post by avacado on 2010-10-21
1. 10.4 or 10.10
2. Acer
3. Aspire One AOD260 netbook (alternately just D260)
4. see  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)
multi in one card reader not supported

Also, skype does not work with internal microphone unless
1. instal ALSA volume control package
2. in ALSA vol control mic tab unpadlock left from right channel and slide left microphone to zero.

---

### Post by piotao on 2010-10-21
System: Ubuntu 10.10 Maverick amd64
Laptop: Toshiba Satellite A665-3DV, NVIDIA 1GB 350M, 640HDD, 4GB, WIFI, BT, etc.
Kernel: 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux
Issues:

1. Keyboard backlight:
- not working at all, disables when kernel start (works in BIOS/windows)
- packages toshset and toshutils can be installed, but programs do not works

2. ACPI? What acpi?
- the path of /proc/acpi/fan is empty, however fan is working properly, cooling is OK

3. LM_SENSORS
- can be installed, but sensor-detect did not find ANY usable sensors, so there is no sensors for console
- gnome-sensor-applet for  gnome-panel works and shows temperatures

4. Network
- using services networking restart did not work, saying something like "restart: Unkown instance"
- network-manager from gnome-panel works, but I'm unable to enable WIFI from console
- bcm43xx WIFI driver is not present on install CD, only wire network is working (with r8169 module)

5. NVIDIA
- installing nvidia drivers from nvidia.com by running *.run files can issue incompatibility of ABI with the kernel and driver version. Reinstall of the nvidia drivers from nvidia can solve this, but package version not.

6. Keyboard
- some hotkeys are not working properly, now only volume+-, mute and screen backlight are working.
- backlight keys are working but no screen light is changed, also the OSD display control is showing some strange light levels after pressing backlight keys; they are unrelated to light levels and order of keys pressed
- economy mode can't be enabled by pressing hotkey

7. 3D Vision
- there is NOTHING about the usage of new nvidia features like 3d vision (nvidia lacks some support)
- The usb device and glasses seems to not work at all

8a. Other observations (positive):
- hibernation and suspend works from the scratch and are OK
- sound is clear and music is working thru speakers and headphones jack plug, everything OK
- did not test microphone jack yet
- CD/blueray is working properly
- Ubuntu can be installed from CD without problems
- WIFI is working OK (after installing proper packages), also wired network work flawlessly
- any kernel updates and grub changes did not harm the system stability
- touchpad and scrolling is working well
- nvidia is cooled properly, and usually is below 50° (35° after start)
- the fans are silent, but can be heard in silent room; they do not disturb

8b. Negative observations unrelated to ubuntu, but to laptop
- the case is made from soft plastic and bends in many places (this is horrible)
- the laptop is rather heavy, which is very unconfortable with soft case (again)
- the power ac/dc supply is HUGE in comparison to the others.
- the screen is like a mirror, and the dust is visible on each black polished surface. For me it's not a big problem. After work in dusty areas (traditional chalkboard in lecture room) there is much dust on laptop visible.

9. Unrelated to laptop, but to the Ubuntu.
- using gnome is great, but setup a window system to resize windows with right mouse click with left alt, is for me a pain. There is unclear dependencies between compiz and gnome-wm, and in previous 10.04 edition the support for right-mouse-resize was broken. Now, in 10.10 everything works, but I hate the way I have to configure this on every of my computers (currently 3 ubuntu installs on different hardware).

Summary:
- I used to work with fluxbox and kde. Both have window resize with alt+right mouse click.
- I was a long Gentoo user, now I'm switched to ubuntu and I'm surprised.
- MOST of things is working out of the box.
- I am positively surprized of the quality, stability and awesomeness of ubuntu project. I liked it very much from the first few days I started using it. Especially Burg, the Grub2 overlay kicks ***!
- Gentoo in comparision offers tiny speedup and responsiveness, but is way harder to maintain and takes a very long time to compile and setup every aspect of the system. I don't how enough time right now. So I'm happy.

I hope this post helps :)

---

### Post by pihbar on 2010-10-21
Ubuntu 10.10
Lenovo IdeaPad U350

This laptop does *NOT* work well with 10.10. Graphics, mounting, sound -- basically everything breaks without significant effort to fix. On 10.04, however, everything works fine -- look for my post in the compatibility list to fix common issues.

---

### Post by dh390 on 2010-10-22
1) Ubuntu 10.10 i386 / 32bit
2) Toshiba
3) Satellite 2100CDS
4) Will NOT install or load.
 
 
Will not install. Does not like the AMD K6-III+ 400Mhz processor (now running at 501Mhz). Error msg of "This kernel requires the following features not present on the CPU: cmov" "Unable to boot - please use a kernel appropriate for your CPU.".
 
I modded the laptop added the AMD K6-III+ 400Mhz processor & modded the MB for it to run at 501Mhz. Laptop runs Windows XP Pro svc pack 3 no problem. 160meg of memory.

---

### Post by sirkeith on 2010-10-24
Toshiba C650-01T

Lucid 10.04.1 would not run wireless,ethernet, USB ports, mouse, and would not do a soft reboot or shutdown.

Basically same results with Maverick 10.10 except ethernet card worked and wireless would do an ad hoc connection intermittently.

Kernel 2.6.36 installed with Maverick and all is well.

Tried compiling kernel a couple of times and gained new respect for alot of you people. Ended up with ppa.

---

### Post by Tenzy on 2010-10-25
1)Ubuntu netbook 10.04/Linux Mint 9 (tried most on Mint but problems seem the same)
2)Asus 
3)Eee PC 1015 PE

What works out of the box:
wifi
speakers
fn keys for brightness, turn off screen, sleep mode
webcam

What doesn't work but has a fix 
headphones out 
fix see here [https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

Haven't found a fix for 
microphone and mic in
other fn keys

The touchpad works fine if you are right handed. But doesn't turn off when typing. Which can get pretty annoying. It becomes a true problem if you are left handed. The one finger tap becomes a right click. Making the touchpad very hard to use. 
Because of the touchpad not turning off when typing, using a laptop mouse is not an option for lefties. When you type and accidentally tap the touchpad a contect menu keeps popping up, because you are right clicking with a tap. This happened to me about 20 times during typing this message. When you go to mouse settings there are is no touchpad settings tab.

I'll try to update this post if I find a fix.

---

### Post by twoaday on 2010-10-27
Ubuntu 10.10

Dell 

Studio 1536 


No usb support at all. Have tried every thing I could find in bug reports and online still can't find anything that works. No replies other than one other person with same issue in the forums. Staying on top of updates for now.

---

### Post by FlameReaper on 2010-10-28
Ubuntu 10.04 LTS "Lucid Lynx" on ASUS X42JR-VX141V (a.k.a ASUS K42JR)

Specs:

CPU: Intel Core i7 740QM @ 1.73GHz with TurboBoost enabled
RAM: DDR3 2GB (bought it along with an extra 2GB upgrade)
GPU: ATI Mobility Radeon HD 5470 1GB
HDD: 500GB

What works: Pretty much the basic stuff, plus some features:

1. Intel TurboBoost works, despite what I've been reading that it doesn't

What doesn't/Not so sure if they work or not:

1. ATI's driver won't work on newer kernels (tried 2.6.32-23, 2.6.32-25). and even while it worked on 2.6.32-21 there are some parts the display failed to render correctly at times, haven't tried giving it a fix. Probably will wait for AMD (I still prefer calling their graphics card department as ATI though) to fix this issue.

2. The inability to disable the touchpad, however I don't quite give a damn about it as long as Windows shows it works, maybe it's just me. Haven't found a fix.

3. Sound - try using ALSA drivers version 1.0.23 via a manual install. I don't know how I got it through but I got it fixed - previously sound won't redirect to the earphone jacks, probably have something to do with the mic/headset settings on the BIOS detection part (in which in Windows a software is supposed to detect the change in the hardware and tell the BIOS it's a headphone or a microphone) because this laptop only has a *single* jack for pretty much everything - be it earphones or microphones.

4. Wireless - From what I read the Wireless-N support is kind of... possible if using the latest ath9k driver via a manual installation of it, but since I don't have the means to verify this maybe I'll boot up Windows for a bit and do some comparison and see whatever I can conclude from doing so.
RE-EDIT: Maybe I'm too dependent on shown digits on my screen, but I get the feeling it's just the inability to display correctly in a sense that I'm *truly* using Wireless-N speeds, as how I suspected from reading various posts from other parts of the forum.
ANOTHEREDIT: Gotcha. Installation of the linux-backports-modules-wireless packages solved this problem. Hello 150Mb/s.

---

### Post by Elfy on 2010-11-02
> **xbobby_bobx said:**
> eMachines 
eMachines e625

Ubuntu 9.10/10.4/10.10.

The problem will never be fixed even if after million years of Linux because I think the developers are really lazy to work on this OS

here is the problem  HDD temp = 55c
CPU temp = 59c

IS that normal? I guess not :@

> **FlameReaper said:**
> That's normal actually. Is that idle temperature or on-load temperature? I'd be tempted to say that it's the *idle* temperature. Chill man. At least you haven't seen one which can practically boil enough water to cook eggs >_>

> **xbobby_bobx said:**
> It's hot I'm telling you it's not normal at all and if you can boil and egg on your Lapotop that means you laptop is going to die soon so beware.

Check out the first post "*NOTE* This thread is exclusively for the listing of incompatible hardware. Any idle chatter or unrelated posts will be moved/removed accordingly."

This is not for support - you have threads elsewhere - use those.

---

### Post by reic on 2010-11-02
1)Version Of Ubuntu: 10.10 
2)Laptop Maker: ASUS
3)Laptop Model: EEEpc 1101HA
4)Known Issue: Multitouch doesn't work

Touchpad is not recognized properly as multitouch touchpad; Scrolling on the touchpad's edges and clicking on the pad itself works fine though.

---

### Post by gugagoes on 2010-11-02
Ubuntu 10.10
Toshiba
Satellite L655

Issue:
 - Audio jacket doesn't work. The speakers are OK, but the audio jacket not.

 - The numbers from numeric pad doesn't work, too.:confused:

---

### Post by mustafa.alberta on 2010-11-05
Ladies and gentlemen,
I'm using acer aspire 5251-1513 and I want to install ubuntu 10.10.
I'm not sure if it works properly beside 7 or not.
I'm wondering if my friends helping me to install it on laptop?
Acer aspire 5251-1513
amd v-120
2g ram
ati 4250 graphic card
for
ubuntu 10.10
Thanks,:)

---

### Post by baldy4eva on 2010-11-05
1)Version Of Ubuntu: 10.10 
2)Laptop Maker: HP
3)Laptop Model: G60 214em
4)Known Issue: Wireless!    Complete pain to get running. Only solution I've found that keeps the wireless working, is to set up as a dual boot system and not use Windows. :(

---

### Post by GeldrinHor on 2010-11-06
1: Version: Maverick Meerkat 10.10
2: Laptop Maker: Toshiba
3: Model: Satellite A215 S5849 (rebuild)

Issues: As this laptop was originally set up with Vista Home Premium, I thought to start fresh, as it were.
The HDD in it was failing anyway, so I swapped in a new 160 GB Seagate blank drive. Installed UBUNTU 10.10, and for the most part, everything looks fine.  I then begin to install games I had, getting the necessary linux files to use (Neverwinter Nights 1 comes with a Linux client for the game).  However, issues arise as the video driver files (ATi Radeon Mobility X1200 motherboard graphics) for linux are both old and difficult to install.    

newly learning and re-learning Linux/Unix shell commands are a pain.  Jut looking for less pain. :P

---

### Post by g0kb3rk on 2010-11-07
1. Ubuntu 10.10
2. Acer
3. Aspire One D260

These are not major problems but sometimes create problems (mostly while writing) OSD of Wi-Fi and Caps and Num Locks are not shown.

PS: Card reader is not working!

---

### Post by downthesun01 on 2010-11-08
Ubuntu version: 10.10 netbook remix
Manufacturer: HP
Model: tm2t

Problems:
* No right click on touch pad. Touch pad also stays on when typing.
* No switching between the two graphics cards the computer has. Is always running on ATI card. Kills battery too quickly.
*Black screen error on next start up if I install ATI driver.
*No screen rotation when I put the computer in tablet mode.

---

### Post by Jumpmasterrt on 2010-11-13
1)Version Of Ubuntu - Anything above 9.04
2)Laptop Maker - Toshiba
3)Laptop Model - Satellite A135
4)Known Issue - It will NOT accept any version above 9.04. 
I can load and reload and install all other versions. I can only update it so far and it fails again.

---

### Post by th_agorastos on 2010-11-13
OS: Ubuntu 10.10 Netbook version
Manufacturer: Dialogue
Model: [Flybook A33i]("http://www.notebookcheck.net/Review-Dialogue-Flybook-A33i.1354.0.html")

Known issues: after logging in, just after some screen sections (the panels) load, all the windows and sections in the screen dissapear, and they reappear after a few seconds only to dissapear once again and so on...

Apparently it has something to do with the video card drivers (the device has an old ATI Mobility Radeon.

---

### Post by farmerking on 2010-11-13
1)Version Of Ubuntu: ubuntu 10.10 desktop edition
2)Laptop Maker: IBM Thinkpad
3)Laptop Model: T60 2007BT1
4)Known Issue: Installation completed, but cannot boot into the system desktop. Just got black-screen and no other response. Have tried every mode including the safety graphic mode.

---

### Post by abyssius on 2010-11-13
Purchased acer aspire 5252-v518 laptop.
Installed UBUNTU 10.04.1 with all updates
Cannot enable wireless using fn + f3 key.
Wireless enabeled automatically with Windoze7

Get the following error:
```
 atkbd.c: Unknown key pressed (translated set 2, code 0x93 on isa0060/serio0). 
```
```
 atkbd.c: Use 'setkeycodes e013 <keycode>' to make it known. 
```

*Selected acer laptop for keyboard layout in user preferences
*upgraded to the latest bios version 2.04
*installed wicd

This is result of lshw -C network

```
*-network UNCLAIMED
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:d1000000-d1003fff 
```

I'm assuming that's my wireless adapter.
Is there anything else I can try, or is wireless hopeless with this model?

---

### Post by const451 on 2010-11-14
1) Ubuntu 10.04
2) DELL Latitude E6510
3) Intel GMA HD

Black screen

---

### Post by Sneha1235 on 2010-11-15
The fan control  of  Toshiba L455 is not working . Can u tell me how can i make it compatible.

[School Community]("http://www.whichschool.com") | [School Ranking]("http://www.whichschool.com")

---

### Post by abyssius on 2010-11-15
**Computer**: Acer Aspire AS5252-V518 Laptop Computer
**Operating System**: Ubuntu 10.04.1 LTS (32-bit)
**Processor**: 	AMD V-Series Processor V-140
**Processor Speed**: 2.3GHz
**Level 2 Cache**: 	512KB Level 2 Cache
**Front Side Bus**: 	1066MHz Frontside Bus
**RAM**:           3GB DDR3 SDRAM 

**Issue**:
Wireless antenna enabled on Windows boot-up; disabled on Ubuntu boot-up. Built-in wireless antenna cannot be enabled within Ubuntu. It seems to be a key code issue. Supposedly Windows is required to trigger the Fn + F3 toggle. Requires additional wireless adapter to access the Internet wirelessly. Wired Internet access works properly.

---

### Post by BlackLabel2021 on 2010-11-15
Ubuntu 10.10 64-bit
HP Compaq
6735s
Issues:
1) After getting it "working", wireless connections could only be found and used if plugged in to an Ethernet cable. This confuses me to no end.
2) Wireless was "working" 2 hours ago. After going to class and coming back and waking my laptop up from hibernation, wireless doesn't work at all.
3) Occasional issue when waking my laptop up out of hibernation: The screen's back light will come on and everything fires up like its getting ready to roll but then its just.. black. The computer remains running and the back light stays on, but it never renders an interface.

---

### Post by ShroudedWolf51 on 2010-11-17
Machine: Toshiba Satellite L505-S5971
Ubuntu edition: 9.04

Errors: Whether installing on entire disk or dual-booting with Win7 Home Premium 64-bit, the OS installs correctly, but no matter how much space is allocated to be used as storage space for the OS to use, it declares it to be completely full and when attempting to create anything (or install updates/programs), just complains that the HDD is full.

---

### Post by manco1911 on 2010-11-17
1)Version:  Ubuntu 10.10 // 2.6.35-22    x64 bits
2) ASUS
3) G50vt-x2

Bugs:
1)Webcam is not working. It is listed on /dev/. And on lspci i cant identify it. 
2)Internal microfones not working. I only tried on Skype and with the audio recorder. No sound. 
3)Headphones not working. If i plug in all the way the headphones jack, it wont sound nothing. But if i dont plug them fully, i get sound on my headphones and on the internal speakers. 
Note: this notebook has 3 spica inputs. Headphones, microphone and audio in. The status is the same for all 3. 

So far, everything else seems to work. 
Haven't tried HDMI out yet.

---

### Post by matemargo on 2010-11-18
1) 10.10 32 bits
2) Sony Vaio
3) VPC-S120FL

Screen doesn't work. It's necessary to plug a monitor to the VGA out.
Touchpad doesn't work either.

---

### Post by DurkenV on 2010-11-19
Asus
G73JW-AX1 
Ubuntu 10.04

Sound does not work on head phones. Updated alsa driver. working great.
Intermitted flicker of the screen with OPENGL apps (Docky). Nvidia GTX 460M 1.5GB.
SD Card reader not working. Still looking for solution.

---

### Post by DurkenV on 2010-11-19
> **abyssius said:**
> **Computer**: Acer Aspire AS5252-V518 Laptop Computer
**Operating System**: Ubuntu 10.04.1 LTS (32-bit)
**Processor**: 	AMD V-Series Processor V-140
**Processor Speed**: 2.3GHz
**Level 2 Cache**: 	512KB Level 2 Cache
**Front Side Bus**: 	1066MHz Frontside Bus
**RAM**:           3GB DDR3 SDRAM 

**Issue**:
Wireless antenna enabled on Windows boot-up; disabled on Ubuntu boot-up. Built-in wireless antenna cannot be enabled within Ubuntu. It seems to be a key code issue. Supposedly Windows is required to trigger the Fn + F3 toggle. Requires additional wireless adapter to access the Internet wirelessly. Wired Internet access works properly.



Had the same issue with HP yesterday. Plugged in LAN and check system drivers and there was broadcom proprietry driver that I loaded and wirless works with shortcut buttons now.

---

### Post by ricomoss on 2010-11-19
1.) Version Kubuntu 10.10 64-bit
2.) Dell Latitude E5410
3.) Incompatibility with Intel Core i5

Black screen and "failed to get i915 symbols, graphics turbo disabled error on boot" issue.

---

### Post by abodsalas on 2010-11-20
Hi There. I also have M15x, with ubuntu 10.04.
For me the most critical incompability is that F6 (Vga out) key doesn't work.
This has lead me to 'play around' with the nvidia settings, trying to use the twinmode.
Unfortunately I have bought three other dell laptops (three different models), and they all have the same issue with the VGA out key.

---

### Post by totosmoto on 2010-11-23
Hello, My laptop is Acer 3104 and the built in microphone is not working. I use UBUNTU 10.10.
1. UBUNTU 10.10
2. ACER 3104
3. BUILT IN MICROPHONE NOT WORKING

---

### Post by enricribas on 2010-11-23
ASUS K52JC
Intel integrated/ Nvidia Optimus GeForce 310M discrete 1gb
640gb hard drive
4 gb RAM
Ubuntu 10.10 32b and 64b

I cannot either to boot to GUI only terminal. :(
Trying 10.04 now

---

### Post by gnulab on 2010-11-26
1)Version Of Ubuntu
Ubuntu 10.10

2)Laptop Maker
HP

3)Laptop Model
ProBook 4420s

4)Known Issue
Touchpad is multi-gesture type. Very little information about support for multi gesture for Ubuntu/Linux. The basic work though.

Volume will only be audible after reaching certain level, even though the volume level is already non-mute or 0. 

Function key for adjusting volume, brightness & on/off wireless works out of the box.

Hope this helps.

---

### Post by The Fiddler on 2010-11-30
> **abodsalas said:**
> Hi There. I also have M15x, with ubuntu 10.04.
For me the most critical incompability is that F6 (Vga out) key doesn't work.
This has lead me to 'play around' with the nvidia settings, trying to use the twinmode.
Unfortunately I have bought three other dell laptops (three different models), and they all have the same issue with the VGA out key.

I have never seen the VGA key work on laptops with Nvidia cards + restricted drivers enabled.

---

### Post by t1m3 on 2010-11-30
1)Version Of Ubuntu: 10.10
2)Laptop Maker: Asus
3)Laptop Model: F50SV
4)Known Issue:

- must use acpi=off or nolapic command when booting.. rather have it all with a smooth install.

---

### Post by kd4dii on 2010-11-30
Hello
     I have a Toshiba C655 running Ubuntu 10.1.
The main problem I have is the usb does not work.  I cannot use a usb mouse or access my external hard drive.  A temporary workaround involves turning off acpi.
     On the same machine I tried Ubuntu 9.1 and the usb worked but the wired ethernet connection wouldn't.  The wifi works on both.

Bob

---

### Post by elroselanesse on 2010-12-03
1)Ubuntu 10.10, 10.04, 10.04LTS, Netbook Remix 10.04
2)Sony
3)Vaio vpcs120fl
4)
a- Video does not work, You have to manually configure the xorg file to make it work.
b- Touchpad does not work, it doestn´t even appear on the xinit input list or kernel. It´s not detected at all.

---

### Post by Jechem on 2010-12-03
Laptop: MSI CR410x
Specs:
CPU: AMD V120 2.20GHz single core
RAM: 2GB DDR3
HDD: 250 GB SATA
VIDEO: AMD RS880M+SB820M/ATI Radeon HD4270 shared
Webcam: 1.3 MP (Bison)
Pre-installed OS: Windows 7 Home Premium (OEM)

Tried Ubuntu 10.04 and 10.10 and Fedora 14
webcam doesn't work. it's not recognized
AMD/ATI proprietary video driver has a bad resolution when installed.

I will have to try and figure out the webcam when I have the time.

EDIT: 
Installed 10.04 with AMD/ATI proprietary driver
guvcview for webcam worked great
card reader(ENE hardware) not working no driver available
Dual boot with Win7 and Ubuntu 10.04

---

### Post by Dr_Li on 2010-12-03
Ubuntu 10.10, 64-bit
ACER Aspire 7745G-3053

When running in live-CD mode: 
  Blue-Tooth works;
  Wireless-NIC work; 
  wired-NIC does not work.

After installation into hard-disk:
  Wired-NIC works;
  Wireless-NIC works after enabling proprietary driver;
  Blue-Tooth does not work;
  Display brightness could not change;
  Could not boot if enabling the proprietary FGLRX graphic driver.

---

### Post by owiknowi on 2010-12-04
Compal NTUC0 (AHTEC CNTU723)
Ubuntu 10.04-1 64 and 10.10 64.
Fn keys (brightness and volume) won't work.
Brightness also can't be adjusted in powermanagement.

---

### Post by 1492 on 2010-12-05
Ubuntu 10.04 LTS
Dell
Studio 17
**Wireless adapter** Adapter doesn't work, so you must get Linux compatible USB adapter. My adapter (SMC EZ connect) reduced internet speed from 11mb/s to 1mb/s only on this computer & only under Ubuntu. On Windows 7 on this computer and on other computers, internet speed is still 11mb/s, though I haven't tested it on other computer with Ubuntu

**Fan** Fan does not work & this computer gives off a lot of heat.

**Sensors** No sensors can be detected on this computer.

**Headphones** Headphones output will not work, just mutes the computer (the speakers are loud and work very well, so it may not matter).

I haven't tested the eSATA port or several others, but I have no idea what the others are called.

On Ubuntu 10.10 the built in wireless adapter does works fine, but the correct screen resolution is not on 10.10.

---

### Post by linux00 on 2010-12-09
RM NBook 4000 running (or attempting to) Ubuntu 10.10 from USB
 
My USB works fine on other PCs but my laptop gives an error message, something like
 
"unknown keyword in configuration file (random symbols)
No DEFAULT or UI configuration directive found!
boot: _"
 
I can type next to boot: where the underscore is, but nothing does anything - always says something about an invalid/corrupt kernel image. If anyone can tell me how to fix this, please private message me.
 
EDIT: This is an error in the way the laptop handles the config files, I pointed it at vmlinuz and initrd.lz and it works fine - just need to type "/casper/vmlinuz initrd=/casper/initrd.lz" and it works
 
EDIT 2: It doesn't work - it just gives another message saying something about init

---

### Post by nitin88 on 2010-12-09
1)Version Of Ubuntu: 10.04
2)Laptop Maker: Sony
3)Laptop Model: Vaio EB Series (VPCEB36FG)

Nothing is working on my laptop. i can enter logon details, once i get log into system, i cant use any thing. Touchpad sound gfx card nothing is working.

---

### Post by canucked on 2010-12-09
1) Ubuntu 10.10 Maverick 64-bit. (Also tried Ubuntu 11.04 Natty alpha1 64-bit; same results)
2) Toshiba
3) Satellite L655-S5115
4) Wireless adapter and battery not recognized; built-in microphone, microphone jack, and headphone jack not working.

I managed to get wireless and audio working completely, however I have no solution for the battery issue.  I don't know how to find the charge level of the battery, apart from booting Windows.

Here is my detailed post:
[http://ubuntuforums.org/showthread.php?t=1641931](http://ubuntuforums.org/showthread.php?t=1641931)

---

### Post by keshav kumar on 2010-12-10
version: 10.10;
laptop maker:sony;
laptop model: VPCEB36FG;
issue: sir, my laptop's touchpad is not worknig, there is no response from touchpad but USB MOUSE works fine with it.
please help me to get out of my problem.

---

### Post by Finn bjerke on 2010-12-10
[[COLOR=black]Compaq CQ56-111EO[/COLOR]]("http://www.elkjop.no/product/data/barbar-pc/PRESCQ56111EO/compaq-cq56-111eo")
 
_Build in mic_ has noisy carckling sounds, alternatively you could use bluetooth or probably USB based mic.  However for skyping etc it would be nice if the internal mic was functional.
 
Everything else seems to be working fine.

---

### Post by AKADriver on 2010-12-11
Ubuntu 10.10 live CD
Dell
Inspiron 6000
Install hangs. It proceeds as far as the screen displaying the word "ubuntu", then after about 2 minutes the dots stop scrolling.

Tried with "nomodeset", and again with "acpi=off"; in either case installer crashes with error message "Kernel panic - not syncing: Attempted to kill init!" and then a stack trace.

The same install disc installed successfully on my desktop; the laptop is currently running Windows XP SP3 with no hardware issues.

---

### Post by kamakshaiah on 2010-12-16
I am using Acer Aspire 4745. 
 
**_In Ubuntu 10.04_**
 

_Problems:_[LIST=1]
[*]Battery applet in top-right corner missing
[*]Gnome-Sound-Recorder was not working (I mean I could not either record or play sound)
[/LIST]**_In Ubuntu 10.10_**


_Problem;_[LIST=1]
[*]The sound-recorder issue was solved, but this battery applet is still missing after I upgraded to Ubuntu 10.10
[/LIST]I thing it is some thing related to hardware cofiguration problem. can somebody help me.

---

### Post by fiedler on 2010-12-16
ubuntu 10.04 & 10.10
sony vaio VPCC
turns lcd screen off when booting live cd same problem in linux mint.  Livecd boots up then goes completely blank showing no display what so ever!

---

### Post by theasprint on 2010-12-17
1)Version Of Ubuntu: 10.04 64-bit
2)Laptop Maker: SONY
3)Laptop Model: VPCCW26FG
4)Known Issue: Nvidia Graphics

While installing using Wubi with the 10.04 64bit .iso file, I was not able to see anything on the screen during the installation process (the one with the slide show). And after a long wait looking at the blank screen, Ubuntu finally finishes installation and boots up.

However the Graphics that Ubuntu 10.04 gave me was of quite low resolution. Despite Ubuntu having to provide me with its own "Nvidia Graphics Driver" (something about Nvidia X server), I am unable to have my laptop's default resolution (1600x900) displayed on my screen. 

But after viewing this thread:[http://ubuntuforums.org/showthread.php?t=1470822]("http://ubuntuforums.org/showthread.php?t=1470822") the problem is solved. 

*I heard SONY Laptops is said to be quite incompatible for Ubuntu and Hackintosh due to its BIOS.

---

### Post by Quadunit404 on 2010-12-19
I WAS going to say Samsung NP-RF510, but then I realized that the problem was Nautilus. Then I posted a [guide]("http://ubuntuforums.org/showthread.php?t=1648572") for fixing Ubuntu on the Samsung NP-RF510 because apparently vanilla Nautilus doesn't like that laptop while Nautilus Elementary has no problems with it :|

---

### Post by 65Hyper on 2010-12-21
1. Ubuntu 10.10
2. Clevo/Neo
3. M540SS
4. Driver :
    No 3D Driver, 2D only
   Issues :
    Shutting Down : System Halted 2 seconds
    Booting : No APIC required to boot. But on Ubuntu 9.04 and 9.10, it is not required.
    Booting : Shows text of what is happening.
    Very slow when driver is added.
   Installation :
    Wubi : No installation.iso found.
1. Ubuntu 10.04
2. Clevo/Neo
3. M540SS
4. Same with Ubuntu 10.10.
   Issues :
    Broken boot screen at LiveCD and Normal boot.
   Installation :
    Wubi : Does not boot "Disabling IRQ #1-10" for 6 hours. NoAPIC required.
Please fix it!!

---

### Post by Erich_ET on 2010-12-22
My notebook is a Philco model PHN 14118 and i use ubuntu 10.10
The ubuntu have no driver for 671 based sis chipset IGP
exist a driver but has no compilation for ubuntu:
[http://www.linuxconsulting.ro/xorg-drivers/](http://www.linuxconsulting.ro/xorg-drivers/)

---

### Post by dan061494 on 2010-12-22
Toshiba Satellite L505
ubuntu 10.10
When CPU reaches 100% the fan starts to run, and will not stop until the computer is put into suspend mode, or restarted/shut down. also about 1/10 of the time i try to suspend the laptop, it will just show white text on the screen and never suspend. The only thing that you can do after this is hold the power button and turn off the computer. 
Thanks

---

### Post by fireandfuel on 2010-12-23
1) Ubuntu 10.10 x64
2) Toshiba
3) Satellite C660D-10P
4) ACPI problems ... works fine with Ubuntu 10.04 x64, but refuses to work with Ubuntu 10.10 x64. 

A Fix: Disable ACPI support with "acpi=off" at kernel boot parameters, but it deactivates the "FN" keys, too.

---

### Post by Football Mania on 2010-12-24
1. Ubuntu 10.10
2. Lenovo
3. G530 3000
4. Camera doesn't work. Even if it works, it doesn't work smoothly. Especially camera in Gtalk doesn't work. This is the only hardware problem of ubuntu 10.10 with Lenovo g530 3000.

Note: The video on Gtalk at Gmail works smoothly, when I run ubuntu from a live-cd. However, it doesn't work smoothly when I install ubuntu on my hdd.

---

### Post by shadowlemon on 2011-01-05
1. Ubuntu Maverick 10.10
2. Dell
3. Studio 1735

Important note: I have: ATI mobility radeon 3650HD

**WIRELESS**

Wireless works when you install the proprietary driver vie the menu.(Connect it with a UTP cable once, and then you're good to go). 

In earlier versions this might not work out of the box (i'm talking about 9.xx). Then you will need to use this driver: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) use the instructions that are provided, and just load the driver on startup.

**VIDEO DRIVER**
If you don't need any gaming, just use the ubuntu drivers (by mesa). They work just fine with compiz, blender, etc. For more advanced gaming, just install the proprietary drivers, this works just fine. Don't be scared that your splash screen is in a low resolution, that's normal.


**OTHER**

Haven't found any other problems with this laptop on ubuntu. Though I didn't try HDMI. Dual screens works too, if you plug it in the VGA input.

---

### Post by Black Magix on 2011-01-05
Toshiba Satellite A665D

Incompatible with Kernel 2.6.35-22-generic (ubuntu 10.10, mint linux) without setting acpi=off at the end of the linux line at boot.

---

### Post by r.sadretdinov on 2011-01-08
OS - UBUNTU 10.10
Laptop - Sony VAIO VPCEF3E1R
Problem - Touchpad not working

---

### Post by Elinor on 2011-01-09
can't delete this post...

---

### Post by Elinor on 2011-01-09
1) Ubuntu from 6.04 to and including 10.10

2) Samsung

3) X05

4) Startup fails if any USB plugged in (may fail before or after login depending on version).
Won't recognise external TV through s-video (only tried on 10.04 and 10.10)

Could be worse ;)

---

### Post by rudolfl on 2011-01-09
ACER ASPIRE 4741
Ubuntu 10.10 (32-bit) (Edubuntu actually, but do not think it makes a difference)
Problem -- Nvidia driver.

Tried to install latest video driver or previous one -- could not even start X. Got latest one from Nvidia -- have errors whee client and server report different versions. So, same -- can not run X.
Using nouvea driver at the moment without 3D capablities.

Machine:
i5 processor, Nvidia GT320M video

Thanks,
Rudolf

---

### Post by Byb on 2011-01-10
1)Maverick Meercat standard (gnome)
2)Siemens Fusitsu
3)M7405
4)Can't resume from suspend to ram. Lid backlight remains on when screen goes black. Visual effects won't work.

---

### Post by anupam009 on 2011-01-10
hi gys...
i have the dell 15R machine using ubuntu my wireless driver not working properly.

one time when i connect the machine by wired Internet then it will worked but when i restarted it then it is disabled......

at hardware drivers.....it is BROADCOM STA wireless driver..

on ifconfig.....

eth0      Link encap:Ethernet  HWaddr f0:4d:a2:94:9d:60  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f24d:a2ff:fe94:9d60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:82276727 (82.2 MB)  TX bytes:6418273 (6.4 MB)
          Interrupt:33 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr c0:cb:38:0f:7b:ad  
          inet6 addr: fe80::c2cb:38ff:fe0f:7bad/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:31
          TX packets:5 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1750 (1.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1856 (1.8 KB)  TX bytes:1856 (1.8 KB)

help..........................................

---

### Post by NickyJ101 on 2011-01-10
This is a direct incompatibility but also a fix.

Ubuntu: 10.04 onwards
Laptop: Samsung X30
Issue: Failed Graphics (nVidia GeForce go 5200FX)

This is an issue with the new nVidia drivers supplied with all new versions of Ubuntu. The fix is to download and install 9.10, download the proprietary drivers the normal way then work your up through the distribution updates, when it asks to remove unused packages select no otherwise it would remove the old nVidia and start using the new nuovo driver.

This happens on all older nvidia laptops which are not compatible with the new drivers, as long as you don't do a clean install it will all be ok.

---

### Post by PopTart911 on 2011-01-10
This notebook uses the nvidia optimus technology which switches between an intel mhd4500 and an nvidia 310m graphics card based on load. Running under ubuntu, the 310m will be unavailable and the laptop will not be able to sleep. Otherwise, everything else works flawlessly.

I have a feeling that any of the optimus based laptops won't be fully supported for awhile. The way this works is that the nvidia card outputs to a special buffer in the intel card instead of the display. Currently, the nvidia driver can't open the buffer in ubuntu's intel driver to make the magic happen.

Perhaps there will be drivers in the future, but as of Jan 2011, there is no support or news of any from nvidia.

---

### Post by keylokes on 2011-01-10
compaq cq56-115dx

For the most part everything worked out of the box. including wifi.
built-in WEBCAM does NOT work .. or even recognized when i "lsusb" or "lspci"
Also when i installed the restricted graphics driver through "Additional Drivers"
it completely messed up my monitor .. so i uninstalled it and its back to normal.

i downloaded the driver from ATI's website and installed it.. and that was even worse
the log in in distorted and after pressing the "log in" all you get is the wallpaper.
so had to reinstall OS. 

other than those two issues everything else works perfect.

oh yeah .. running maverick meerkat.

---

### Post by bilallucky on 2011-01-11
1) Ubuntu 10.10 Maverick 64-bit. (Also tried Ubuntu 11.04 Natty alpha1 64-bit; same results)
2) Toshiba
3) Satellite L655-S5115
4) Wireless adapter and battery not recognized; built-in microphone, microphone jack, and headphone jack not working.

I managed to get wireless and audio working completely, however I have  no solution for the battery issue.  I don't know how to find the charge  level of the battery, apart from booting Windows.

---

### Post by cutterschoice on 2011-01-11
Hey,

I just bought a logik wireless keyboard and mouse, the keyboard worked as soon as I plugged it in but the mouse doesn't. Ubuntu works perfectly on my laptop and I've had no problems with anything so far, but i'll admit i'm a complete novice. Because the keyboard works i'm inclined to think that it might be the mouse that is faulty but really I have no idea. I tried all the things I could think off (restarting the computer, browsed the mouse preferences, ahd a look through the forums threads) but couldn't find whats wrong)

Has anyone else had similar problems with a wireless mouse? Am I missing a thread that was set up for precisely this kind of issue?

Any help would be very much appreciated

Cheers.

(apologies if this is in the wrong thread, like I said, i'm a complete moron when it comes to these things)
)

---

### Post by WASHAD on 2011-01-14
Sony Vaio VPCF132FX:
Ubuntu/Kubuntu 10.10 (64bit)

Got a sweet new Sony i7 and wiped windows right away. I perhaps should have waited, because there are a host of problems. I finally broke down and bought the support package from Canonical. I was given permission to share with others the fixes that work for me. As we work through them, I'll update this post. 

Problems:

[1] Installing with updates, or installing updates after install causes machine to freeze on login. 
[2] Installing NVidia driver's garbles screen on Ubuntu, and freezes screen on reboot in Kubuntu. {work-around}
[3] Touchpad doesn't work. {solved}
[4] Sleep and hibernate do not work. 
[5] HDMI output doesn't work. 
[6] Brother wireless printer (HL-2170W) won't print


Solutions:

[1] For now, I didn't install with updates and I haven't updated my system. More to come on this one. {Update Feb27 2010} I think I was wrong on this one. Updates seem to work - as long as I don't install NVidia. 



[2] Video card bug, cannot use NVidia drivers. Please add your name to the bug list if appropriate (so it gets fixed more quickly). 

[]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/643895")

{Work around}
Use mesa for 3d;

sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx




[3] Found the solution to the touchpad in this forum;

[http://ubuntuforums.org/showthread.php?t=1526740]("http://ubuntuforums.org/showthread.php?t=1526740")

---

### Post by Abdoh1 on 2011-01-17
[FONT=Arial][SIZE=2]
1)Ubuntu 10.10 with latest update 
2)Laptop Maker Dell
3)Dell 1525
4)many problems i blog about it on my blog [http://bnselim.wordpress.com/2010/12/24/ubuntu-10-10/](http://bnselim.wordpress.com/2010/12/24/ubuntu-10-10/)

[/SIZE][/FONT][SIZE=2][FONT=Arial]1- Bad image quality in Firefox 
2- Video quality totally bad using Totem Movie Player 2.32.0 
3- I can’t add Arabic as a second language I tried to download Arabic language package failed massage appeared and paged installed even with this i can’t read Arabic in txt files 
4- Sound icon in system try disappear suddenly!!! 
5- can’t load subtitle to any kind of film specially Arabic subtitle  using Totem Movie Player 2.32.0[/FONT][/SIZE][FONT=Arial][SIZE=2]

if any geek know how can i solve it, please reply>>>>
[/SIZE][/FONT]

---

### Post by aldee96 on 2011-01-21
Ubuntu 10.10 latest updated
Munfacturer Sony
Model VGN-CR11GH/L

Known issues is the camera works fien for taking pictures but for recording a video it's worst, it's just 1 or 2 fps.My camera type is Ricoh Co., Ltd Visual Communication Camera VGP-VCC6 [R5U870]

Any solutions?

---

### Post by chhatoipritam on 2011-01-21
Version of Ubuntu: Maverick Meerkat 64-bit
MAKE: Sony
MODEL: VPCEB34EN (E series in general)
ISSUES: TOUCHPAD (ALPS) Not recognised at all (in both 32-bit and 64-bit); fn keys( work fine in 32 bit); Sound is not loud, on trying to increase it cracks.

---

### Post by WinRiddance on 2011-01-21
.

[SIZE=2]1)Version Of Ubuntu ..... 9.10 and 10.04 and 10.10

2)Laptop Maker ..... HP/Compaq

3)Laptop Model ..... 6735s with 4 GB Ram and 320 GB disk

4)Known Issue ..... Constant CPU overheating to the point that the system crashes, i.e. becomes so completely unresponsive that only a hard reset corrects the problem. Ubuntu 10.10 worked best so far, but still the CPU is running quite hot daily (being used as a laptop with attached display, keyboard, and mouse). I'm not a gamer and I do not play hard core 3D games but the 3D effects are enabled. No compiz cube or other effects aside from standard wobbling windows though. I've fiddled with the power settings as well as the bios countless times in the past 12 months. I suspect the horrible ATI HD 3200 graphics chip is to blame, it's been a problem since Ubuntu 9.04 Jaunty.[/SIZE]

---

### Post by 3177 on 2011-01-26
> **chhatoipritam said:**
>  Sound is not loud, on trying to increase it cracks.

are you using the default alsa driver?

---

### Post by sam198923 on 2011-01-27
try going to your panal and select add to panal and add the indicator applet got battery bar working for mee.......

---

### Post by demilord on 2011-01-27
Compaq mini 133
Wireless works.... 50/50..  sometimes it works sometimes doesnt.. it has a realtek wireless chipset..

further touchpad responses bad with tapping.. further everything works O.O.B...

---

### Post by felita on 2011-01-27
hi
tosh c650-01t , working well with 10.10 (but i need to update the kernel to 2.6.36 (maverick)
USB and wireless are working perfectly 
also epson nx510 printer

---

### Post by slamelov on 2011-01-30
Toshiba c660 10D
Everything Works, except wifi

---

### Post by NewUserFF on 2011-01-31
1)Version Of Ubuntu:ubuntu 10.10
2)Laptop Maker:HP
3)Laptop Model:Compaq nw8440
4)Known Issue:when i boot ubuntu,the screen splashed occasionally.What's more,sometimes i can't access the system:only a "-" displayed on the screen,and it'll splash forever..[COLOR="Red"].I THINK THAT IT'S THE BAD VIDEO DRIVER THAT MAKES THE PROBLEM[/COLOR].And update the video driver using the system is also non-helpful.My video is [COLOR="red"]ATI FireGL V5200[/COLOR].Thanks

---

### Post by DrJohn999 on 2011-02-01
Ubuntu 10.10
Asus
Eee 1215N

This is a fine netbook, but at this time there are a few problems I hope will be fixed in 11.04. Zero installation troubles (off a 4-GB USB drive made with Startup Disk Creator on my desktop 10.10 system). Installed 10.10 on the unused disk partition; left Win 7 in place for dual-boot.

1. nVidia optimus dual graphics. Only works with the basic Intel driver. Installing the offered nVidia driver just drops to a command prompt and thereby demands uninstalling the nVidia driver. Will try it again later.

2. Built-in ethernet wired lan goes belly-up in a hurry when any significant amount of data is passed. Checking out ifconfig showed over 4 x 10^6 errors when attempting to backup over the net. I have a spare Cisco USB 300M ethernet adapter and am using it instead with no hitches.

3. Battery life is about 3.5 hours (nothing to do with the graphics, this is under the Intel chip) -- somewhat short of the claimed 6 under Win 7. Again, maybe better in the future and not much of an issue for me anyway.

4. Most everything else seems to work just fine: sound, display / VGA switcher, screen brightness, suspend (including the Fn+Zz key), hibernate, restart, shutdown, wireless adapter toggle (hard switch on upper left). What's the running figure on Fn-space for?? Maybe save battery? I'll try it. Haven't tried multitouch, but again don't really need it.

---

### Post by Rowan_ on 2011-02-02
Ubuntu netbook 10.10
Acer
Aspire One 522, 
  with AMD C-50 dual core cpu, ATi Radeon HD 6250, and Atheros-AR9285 Wireless.

Unity interface not compatible with the ATI Catlyst drivers: creates a very sluggish operating environment.
Internal Atheros ethernet card does not work properly.  If wireless is turned on it will cause random freezes.

---

### Post by Rowan_ on 2011-02-02
Ubuntu Desktop 10.10 32bit
Acer
Aspire One 522, 
  with AMD C-50 dual core cpu, ATi Radeon HD 6250, and Atheros-AR9285 Wireless.

Permanent watermark when ATI restricted GPU drivers used.

Internal Atheros ethernet card does not work properly.  If wireless is turned on it will cause random freezes.

---

### Post by Kettu on 2011-02-05
Ubuntu 10.10 Desktop
eMachines netbook (don't know the model doesn't say anywhere)
N270 Intel Atom, 1GB memory, 160GB HDD, bought it with Win XP installed.
The only thing that doesn't seem to be working is when I plug my android phone or insert my SD media card my computer now doesn't read it, since I installed Ubuntu. Worked fine with Windows. Nothing shows up on my desktop or my menu that tells me I have a drive inserted. So I now have to email the pictures on my android and SD card to myself. Help?
And splash screens won't work. Also can't figure out how to install anything from the gnome art site but that's besides the point.:confused:

---

### Post by andrewthong on 2011-02-05
Ubuntu Desktop 10.10 32-bit
Acer Aspire One AO522-BZ499
AMD Fusion C-50, HD 6250

Can never get it to wake after closing lid
Letting Ubuntu get the display drivers results in the AMD-unsupported watermark. Installing the latest Catalyst manually does the trick here. Unfortunately, it won't play Youtube 720p- which is my main requirement
WiFi works, but for some reason refuses to show after 3rd-4th reinstall (had to go back to the bundled Win Starter)

Just need it to be able to handle 720p H.264... will attempt to get it to work next week before I have to return it. If anyone has any ideas, that would help!

---

### Post by srstrt on 2011-02-06
Hello All,

I'm using the Acer Aspire One 522. Both the wireless and the video do not work. I assume this is driver related. I tried this on Ubuntu 10.04.

---

### Post by Enter t'Ibex on 2011-02-08
fujitsu st4120 [and other variants]

intel i810 graphic chip not supported

runs fine in 'low resolution graphics mode', if u can get it there.

ubuntu 10.04 lts

---

### Post by Rowan_ on 2011-02-08
> **andrewthong said:**
> Ubuntu Desktop 10.10 32-bit
Acer Aspire One AO522-BZ499
AMD Fusion C-50, HD 6250

Can never get it to wake after closing lid
Letting Ubuntu get the display drivers results in the AMD-unsupported watermark. Installing the latest Catalyst manually does the trick here. Unfortunately, it won't play Youtube 720p- which is my main requirement
WiFi works, but for some reason refuses to show after 3rd-4th reinstall (had to go back to the bundled Win Starter)

Just need it to be able to handle 720p H.264... will attempt to get it to work next week before I have to return it. If anyone has any ideas, that would help!


I can help with the lid issue. The computer is set to suspend when you close the lid.  Click on the Battery icon on the panel and change the properties to only turn the screen off when the lid is closed.  Make sure you do this for both option tabs.

---

### Post by linuxser on 2011-02-09
=> Ubuntu Lucid 10.04 LTS
=> HP Mini
=> 110-3014TU
- Sound Doesn't work. But work normally after install ALSA Driver.
- WLAN Doesn't work. I've try any solution that given by Ubuntu, Forum member, and HP Forum, but nothing works. Please help me.
- Camera, Doesn't work. I don't know how to make camera work. This is my first day to have Netbook(i bought yesterday)

---

### Post by dsummy on 2011-02-09
> **andrewthong said:**
> Ubuntu Desktop 10.10 32-bit
Acer Aspire One AO522-BZ499
AMD Fusion C-50, HD 6250

Can never get it to wake after closing lid
Letting Ubuntu get the display drivers results in the AMD-unsupported watermark. Installing the latest Catalyst manually does the trick here. Unfortunately, it won't play Youtube 720p- which is my main requirement
WiFi works, but for some reason refuses to show after 3rd-4th reinstall (had to go back to the bundled Win Starter)

Just need it to be able to handle 720p H.264... will attempt to get it to work next week before I have to return it. If anyone has any ideas, that would help!

Hey, i just purchased an acer ao522 also and am having the same issue with the watermark. I installed windows 7 x64 for the time being and have been searching for a fix to the ubuntu driver issue. It seems amd has not yet released drivers to support the 6250 on linux yet? but i did find these drivers..don't know how to install them though 
[http://www.phoronix.com/scan.php?pag...item&px=OTA3Nw](http://www.phoronix.com/scan.php?pag...item&px=OTA3Nw)

If your back to Windows I'm not sure if this is the issue with the 720p but is directx updated and i found this [http://www.cccp-project.net/](http://www.cccp-project.net/) and have it installed and have no issues playing back 720.

I also seem to be having an over heating issue..today while on the train I had the netbook in my bag, not turned off, just sleeping and when I woke it up and closed some applications and when to turn on a movie..it got EXTREMELY hot in the bottom left corner of the screen and under the power button, Also, in the middle of the screen right by the letter 'a' in acer there a little circle the size of a screw that looks to have melted the plastic of the screen  going to talk to acer tomorrow.

---

### Post by tednix on 2011-02-09
Ubuntu Desktop 32 bit 10.10
Laptop: Toshiba Satellite A305-S6905
Problem: Suspend function very erratic

This laptop is now almost 2 years old so it may not be of much interest to viewers considering a new equipment purchase.  I can not find any issues with things like wifi,the camera, sound or graphics but have not tested every feature e.g. card reader.

Fn+F3 key will suspend the system as will using Suspend from the pull down menu.  The problem is that many times if suspend has been activated for a long time (say an hour or so) it either will not resume or I will find the computer partially active with a glowing dark screen and the cpu fan on high speed.  At this point it needs to be rebooted by holding down the power button to shut down and restarted.
There are many suggestions in the forums for suspend problems but so far things such as new powermangement packages from Synaptic and adding custom files to /etc/pm/ have all failed.

---

### Post by Dubslow on 2011-02-09
Ubuntu 10.10
Toshiba 
M750-S7212
The problem is random crashing of Ubuntu, as in it just completely freezes, my fan goes crazy, and I have to hard reboot. It crashes hard enough that the syslogs have so far been devoid of any outputs related to the crashes. I have seen suggestions that it might be temperature problems when my CPU is at a high load, but this often happens when I only have Chrome open and am reading a text page, so the CPU can't have been strained. My suspend and hibernate functions have also been erratic. The suspend sometimes works, sometimes doesn't, same as hibernate.
Other people with similar hardware have reported the same issues with 10.10, but then other people again have not had any problems with 10.10. I also know that one of the people the was having problems with 10.10 didn't have this random crashing problem with 10.04, and as such has switched back to Windows. I'll see about getting more detailed hardware info from the others having problems. (When I said similar hardware above, I meant Toshiba M7--.) This would be really nice if it was fixed in 11.04. I would have downgraded to 10.04 myself, except that total customization would take a few hours and I'd rather not do that.

Edit: Other users:
Toshiba M700 works fine with 10.10

---

### Post by mks1992 on 2011-02-09
1.)Ubuntu 10.04 and 10.10 (32 and 64 versions), Xubuntu 10.10 only 32 version 
2.)MSI
3.)MSI CX620MX
4.)Dual graphic card (Ati radeon HD545V and Intel's graphic card in CPU)

When I was booting up the laptop with Ubuntu I got an error on a virtual address.

Xubuntu was working fine until I installed graphic drivers for Ati. After that the laptop did't want to boot up.

---

### Post by BHEJU on 2011-02-09
Ubuntu 10.10 64bit
HP EliteBook (core I5, 6gig ram)

Fingerprint drivers not available for Validity Fingerprint Hardware.
lsusb recognizes it properly only after I update the lsusb.

Bheju

---

### Post by gufide on 2011-02-09
1) 10.10
2)Asus
3)G60Jx
4)Xserver freeze on startup on live cd, keyboard luminosity can't be change, can't suspend/hibernate

---

### Post by EJ42 on 2011-02-09
Ubuntu 10.10 Mawerick Meerkat

Medion Akoya E7214 laptop

Integrated webcam and integrated microphone are not being recognised at all

lsusb says:

ej@ej-E7214:/dev$ lsusb
Bus 002 Device 006: ID 043d:00ff Lexmark International, Inc. InkJet Color Printer
Bus 002 Device 005: ID 043d:007d Lexmark International, Inc. Photo 3150
Bus 002 Device 004: ID 045e:0023 Microsoft Corp. Trackball Optical
Bus 002 Device 003: ID 043d:007a Lexmark International, Inc. Generic Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ej@ej-E7214:/dev$

---

### Post by tsr2 on 2011-02-11
1)Lucid Lynx/Maverick Meerkat
2)Dell
3)Latitude E5510 (Core i3)
4)Unusable display. Grey screen only. CTRL-ALT-F1 does not get a text console.

---

### Post by lion9 on 2011-02-11
Asus F80C/Maverick Meerkat 
Live CD does not run at all.

---

### Post by epileftro85 on 2011-02-11
Hi, i recently migrate from win 7 to ubuntu 10.10, in an ACER ASPIRE 4736, the MICROPHONE doesn´t work, and the camera works in cheese but not in a video chat service, i´ve been trying to make it work whit any tutorial in internet, but it just don´t pleeeeeeeeessssssssssseeeeeeee i´m don´t want to go back to win7, i just like ubuntu:confused: thanks in advance

---

### Post by barrydrake on 2011-02-12
Affects any model using the Broadcom BCM 4132 wi-fi chipset.  There are reported problems connecting to a Belkin F6D4230-4 v1 router.  This is fully repeatable and independent of the router settings.  It is possible that other routers have the same problem which seems to be related to the Broadcom card, and or drivers.  The problem is seen with all available drivers including the Windows driver running under ndiswrapper.

---

### Post by flushed on 2011-02-12
System: Ubuntu 10.10 Maverick Meerkat 64-bit
Laptop: Toshiba Satellite Pro
Type: L500
Wi-fi works great, all other too, but microphone and webcam doesn't work.. Also graphic card: Intel GMA 4500MHD. I entered to Terminal glxgears, and it shows 62 FPS/s. But 3D acceleration is allowed.. I read, I must work with file xorg.conf in folder etc/X11/ but I can't find it! So it's normal, when I run 3d game and fps is for example 5 FPS/s..

---

### Post by gufide on 2011-02-12
> **epileftro85 said:**
> Hi, i recently migrate from win 7 to ubuntu 10.10, in an ACER ASPIRE 4736, the MICROPHONE doesn´t work, and the camera works in cheese but not in a video chat service, i´ve been trying to make it work whit any tutorial in internet, but it just don´t pleeeeeeeeessssssssssseeeeeeee i´m don´t want to go back to win7, i just like ubuntu:confused: thanks in advance

this is not the right place to ask a question, you must post new thread.

---

### Post by Eva34 on 2011-02-13
10.10 Ubuntu (maverick)
HP
Pavilion DV7-4060
problem; My touchpad is horrible, it is a multi touch (pad) but there are not any physical buttons on it, it just detects that if your touching the first key, then its a left click, if second then it assumes it is right, but ubuntu does not like that at all so I cannot right click at all :(
Also the fingerprint scanner does not work either.. thats not near as important as the touchpad to me though

---

### Post by NivStyle on 2011-02-17
Toshiba
T130
Ubuntu 10.10

problems:
1. My internal mic doesn't work, while on Windows it's working just fine.
2. Fn keys doesn't work.
3. For some reasons I hear sounds that reminds me of a grinder, Happens only when I'm using ubuntu and someone logs into Pidgin for example.
4. My mouse pad, Supposed to be Multi-Touch. so it's not working on ubuntu.

---

### Post by Guxx on 2011-02-26
Gateway LT2030u
Ubuntu 10.04
No USB drivers. When an application is installed a warning pops up that the installation failed, but the app installs successfully.

---

### Post by Ozsiix on 2011-03-10
Hi i have problem with my laptop 

1)Version Of Ubuntu : 10.10
2)Laptop Maker : DELL
3)Laptop Model : Vostro 1510
4)Known Issue  : Graphic card .. can't make the compiz work + the laptop sometimes Slow really down ... help !!



Thank you

---

### Post by ab19 on 2011-03-13
Ubuntu Version: 10.10
Laptop Maker: HP
Laptop Model: Pavillion dv6500z CTO
Known Issues:
1. Nvidia Geforce 7150M/Nforce 630m video card: Works well in LiveCD mode after installing proprietary driver and adjusting resolution (The resolution that is default for the monitor (1280x800) seems to be too big for Ubuntu, has to be lowered a bit to work correctly). Actual install to the hard drive yields complete freezing during boot, can't even get into the system. Ubuntu boot logo appears at bottom right corner of screen, never gets past that point, just sits there. During boot into LiveCD the boot screen is the same, with the logo at the bottom right corner, but it does eventually boot into LiveCD after waiting for a couple minutes.
2. Broadcom BCM4311 802.11b/g WLAN card. Simply does not work at all without proprietary driver (to no one's surprise). With proprietary driver it works fine (in LiveCD, anyway).

---

### Post by macstl on 2011-03-14
Im running ubuntu 10.10 on a laptop IBM t23 thinkpad pentium III.
Screen saver and no logout selections don't work. I got it to work ok on another ubuntu machine so I know how to operate it.

---

### Post by khanhnh088 on 2011-03-15
Hi.
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]Yeah, that's hard to say what might be happening there... but if it's not getting a log file at all then it is not getting very far into the loading. When you installed Pinnacle, was it from the setup package on the main website here: [http://www.pinnaclegameprofiler.com/download.html](http://www.pinnaclegameprofiler.com/download.html)[/FONT][/FONT][/COLOR]

---

### Post by macstl on 2011-03-15
> **khanhnh088 said:**
> Hi.
[COLOR=#000000][FONT=Times New Roman][FONT=verdana]Yeah, that's hard to say what might be happening there... but if it's not getting a log file at all then it is not getting very far into the loading. When you installed Pinnacle, was it from the setup package on the main website here: [http://www.pinnaclegameprofiler.com/download.html](http://www.pinnaclegameprofiler.com/download.html)[/FONT][/FONT][/COLOR]

Which post are you referring to?

---

### Post by mikimac on 2011-03-15
Hi i have problem with my laptop when work on battery i have:

Ubuntu 10.10
laptop: Asus X51R
When i unplug ac power after few seconds ubuntu freeze then i have to shut down and start with ac power back.

Tanks.

---

### Post by dugh on 2011-03-18
HP Touchsmart TM2T

and the 

Asus N61 series (N61jv)

Numerous issues with both because of the dual graphics cards (the first one ATI/Intel, the second one Nvidia Optimus/Intel).

Like:
[LIST]
[*]black screen on boot (hp)
[*]freezing after logging in (asus)
[*]black screen or stuff doesn't work after sleep (both)
[*]graphics card sucking battery life even when not in use (both)
[*]can't use compiz or play games since proprietary drivers don't work (both)
[/LIST]

Basically, don't get any laptop that has dual graphics cards (i.e. most new laptops nowadays, at least HP & Asus).

---

### Post by Wibowit on 2011-03-26
1) Version of Ubuntu: 11.04 Alpha 3
2) Laptop Maker: MSI
3) Laptop Model: Wind U270 (with AMD Fusion APU)
4) Known Issues:
- Bluetooth and **Webcam not recognized**,
- no reaction to User Button (ie. it is supposed to launch a user selected application) and Eco Button (ie. it is supposed to cycle through available power saving modes),
- baterry is rated at 3,5 hours (instead of about 8 hours by manufacturer),
- problems with Suspend/ Hibernate - either black screen (and no responses) or screen corruption,
- problems when connecting external monitor to VGA adapter - screen corruption,

Additionally Ubuntu 10.10 and 11.04 won't install from USB - there are some problems with installators. I had to install 10.04 and then upgrade to 10.10 and then to 11.04 Alpha 3.

Edit:
WebCam now magically happened to work. Trackpad sometimes doesn't work (not recognized?) - probably it's caused by beta status of my installed Ubuntu, so it's of lower priority. Anyway Eco Button support would be great.

---

### Post by barrieluv on 2011-03-26
> **Eva34 said:**
> 10.10 Ubuntu (maverick)
HP
Pavilion DV7-4060
problem; My touchpad is horrible, it is a multi touch (pad) but there are not any physical buttons on it, it just detects that if your touching the first key, then its a left click, if second then it assumes it is right, but ubuntu does not like that at all so I cannot right click at all 
Click [here](http://bigbrovar.aoizora.org/index.php/2010/10/10/how-to-enable-right-middle-click-on-clickpads-ubuntu-10-10/) for a workaround which will enable your right click.

---

### Post by MilouB on 2011-04-04
Trying to run 10.10 Maverick
Laptop is an HP
DV6-3154ef


So many issues... Not helped by being a complete Linux novice.

Webcam not active
Fingerprint reader not active
Synaptics pad has no config options
Power options (to suspend, shut down, hibernate and so on) are not recognised and almost random, shut down for instance just hangs and I have to press the power button for 15 sec)
Sound is not working right (for instance nothing on Skype video or sound works, although I can listen to music)

Even the System testing utility fails on everything except mouse and KB. It doesn't even open the documents

I really want this to work but I am running a virtual machine for MS Access. Any help out there? I'm a hair from going back to Win7...

= = =
Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6, especially when using the radeon.dpm=1 boot option: 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by leclerc65 on 2011-04-05
1) Version of Ubuntu: 10.04 
2) Laptop Maker: Samsung
3) Laptop Model: NF210-C03CA
4) Known Issues: Backlight (screen very dark)
Decidedly most Linux unfriendly computer to date (for me).

---

### Post by nayimsust on 2011-04-05
10.10 Ubuntu (maverick)
TOSHIBA
SATELLITE L500
MY COLLING FAN ALWAYS ON , FUNCTION KEY DID NOT WORK AND ITS GIVES ME LESS BATTERY TIME THAN OTHER OPERATING SYSTEM  , BUT  I LOVE LINUX SO MUCH THAN OTHERS , I THINK DEVELOPERS SHOULD KEEP EYES ON IT AND FIX IT IN 11.04 VERSION

---

### Post by demilord on 2011-04-07
> **nayimsust said:**
> 10.10 Ubuntu (maverick)
TOSHIBA
SATELLITE L500
MY COLLING FAN ALWAYS ON , FUNCTION KEY DID NOT WORK AND ITS GIVES ME LESS BATTERY TIME THAN OTHER OPERATING SYSTEM  , BUT  I LOVE LINUX SO MUCH THAN OTHERS , I THINK DEVELOPERS SHOULD KEEP EYES ON IT AND FIX IT IN 11.04 VERSION

Running Ubuntu Maverick Meerkat 10.10
Wow I have the same and everything works perfect out of the box.. :O
I know battery duration isnt very long but still all function keys work  fan works like it should do suspend hibernate wifi everything works perfect

can you give me the lspci i will post mine

```

[00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
14:00.0 Network controller: Intel Corporation WiFi Link 5100

```lsusb
```

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 006: ID 0fca:8004 Research In Motion, Ltd. 
Bus 002 Device 005: ID 04e8:5f06 Samsung Electronics Co., Ltd 
Bus 002 Device 004: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver
Bus 002 Device 003: ID 1131:1004 Integrated System Solution Corp. Bluetooth Device
Bus 002 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b128 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by demilord on 2011-04-07
> **demilord said:**
> Compaq mini 133
Wireless works.... 50/50..  sometimes it works sometimes doesnt.. it has a realtek wireless chipset..

further touchpad responses bad with tapping.. further everything works O.O.B...
there are 2 options you can choose in additional drivers idk which one i choose but i choose if im right the proprietary drivers which you need firmware for.. that one works excelent... Only have problems with not coming out of sleep tho.. but try the other driver it will download the firmware for you if you choose the other one.. hope it helps for you..
i got the exact same netbook  :)

---

### Post by demilord on 2011-04-07
> **Erich_ET said:**
> My notebook is a Philco model PHN 14118 and i use ubuntu 10.10
The ubuntu have no driver for 671 based sis chipset IGP
exist a driver but has no compilation for ubuntu:
[http://www.linuxconsulting.ro/xorg-drivers/](http://www.linuxconsulting.ro/xorg-drivers/)
sudo apt-get install build-essentials and compile it yourself :)

---

### Post by Insamity on 2011-04-07
Alienware area 51 amd processor nvidea graphic card 

I am stuck using 9.10 as I am unable to boot anything newer from cd or install it or upgrade to it. When I do I get a background and cursor but nothing else. I have always loved this laptop and hope when 11 comes out it is usable.

---

### Post by kiddfroster on 2011-04-10
I have an HP dm3t-3000 laptop. I can verify that Ubuntu 10.10 and 11.04 are not fully hardware compatible. Everything works except for the trackpad, which is a Synaptics Clickpad, and the screen brightness adjustment. It it stuck on full brightness all the time, and no driver is available to fix this.

---

### Post by talonthegeek on 2011-04-15
Dell Inspiron 710m
Not getting video with Intel 855

---

### Post by ashickur.noor on 2011-04-15
**Toshiba L650D**
No other Linux O/S works,, but **Only Ubuntu 10.04 and it's all variant works**.
But with a lot of problem 
Main one is **No LAN card Driver.**
 When I install Ubuntu restricted Extras no media file have sound.

---

### Post by funicorn on 2011-04-16
Version: Ubuntu 11.04

Manufacture: **Acer**

Model: _Aspire 4741G_ with Intel i3 and **NVIDIA 310M**

Issue: **NVIDIA**. of course it's **NVIDIA**.
Neither the offical Video driver provided by NVIDIA website nor the nvidia-current version
 from the apt source does NOT work. Each time I installed the video driver and reboot, system
is halted at the very beginning of the welcome screen with Ubuntu logo and bicker dots. If I 
install the video driver and directly restart the X server,  system goes into black screen.

The same bug appears since Ubuntu 10.10 about 6 months ago, I cannot believe it's still there!  
Shame on NVIDIA, shame on Ubuntu !

---

### Post by BELLION on 2011-04-24
I have a Samsung RV510 laptop with intel gma x4500 hd graphic chipset which is not working properly under the Ubuntu 10.10 latest version and 32 bit operating system I can not change the screen brightness...
Any help ?

---

### Post by vulle on 2011-04-25
1. Ubuntu 10.04 LTS
2. Acer
3. Aspire 5738ZG
4. Once touchpad is deactivated it can't be activated anymore, also if I suspend my lap-top my touchpad doesn't work anymore.

---

### Post by stalker145 on 2011-04-28
1)Version Of Ubuntu - 11.04
2)Laptop Maker - Dell
3)Laptop Model - Inspiron 1764
4)Known Issue - Broadcom Wireless fails install

orz

EDIT: I should have looked back on my previous posts. [This thread]("http://ubuntuforums.org/showthread.php?p=10735447#post10735447") has the answer to this problem.

---

### Post by enimga.linda on 2011-04-29
mouse touch pad
 my laptop is Snoy EA35FG
 the touchpad is Synaptics PS/2 Port Touch Pad
 after installation, when I boot up ubuntu 10.10, the mouse does not move at all.
 actually I have the same problem with backtrack as well...

---

### Post by The_Autonomist on 2011-04-30
I also own an HP dv6 series laptop. I've been having the EXACT same problems listed above, even on 10.10. My touchpad doesn't work like it should, my built-in webcam doesn't work, and my fingerprint reader doesn't work. 

Help?

= = = = = 
*Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6, especially when using the radeon.dpm=1 boot option: *
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by mhoober on 2011-04-30
1)11.04
2)Comnpaq
3)Mini CQ10-405DX
4)Known Issue

Installed nicely and was working well initially. Then began to have issues:

Netbook wont shut down w/o hanging. Have to force it off by holding the power key down. When it reboots it is fine.

Often when booting get "The disk drive for /dev/sdc1 is not redy yet or not present."

The Wifi On/Off key (f12) hangs the system.

The wifi connetion breaks intermittently.

Bummer, b/c I really like the new features. 

I see there might be a hopeful alternative by installing 10.10 and making modification per this post: [http://ubuntuforums.org/showthread.php?t=1635135](http://ubuntuforums.org/showthread.php?t=1635135)

---

### Post by JavaQueen on 2011-05-01
1) Ubuntu 10.10
2) Acer
3) Aspire 5253-BZ684
4) Monitor unknown

The laptop monitor is unrecognized by Ubuntu. Ubuntu sets the screen to a default 4.3 aspect ratio when the monitor is really a 16.9...leaving everything a bit stretched. Annoying. Unable to find a fix.

---

### Post by SpinningAround on 2011-05-04
1)Ubuntu 11.04 32bit
2)Asus
3)x51R
4)Known Issue

System freeze completely when unplugging AC-power or booting on battery power, forcing hard reset.
Adding following to boot line, make it possible to use the laptop while on battery power but WLAN card are unable to find networks and battery indicator applet is lost.
```
acpi=off
```

---

### Post by Total Noob on 2011-05-05
> **forestpiskie said:**
> [B]Welcome to the _Laptop_ Incompatibility List.
[/B]

Please Only List
1)Version Of Ubuntu
2)Laptop Maker
3)Laptop Model
4)Known Issue



1.  11.4
2.  Acer
3.  Aspire 3620 w/ Celeron M chip
4.  Wifi extremely sporadic in performing. Sometimes it finds my home wifi (at a distance of 1 foot from the router) and other networks, sometimes not. Various manipulations with software and trying new network managers fruitless. Possibly some regression or error with the wifi driver or the network manager used in the upgrade from 10.10 (where wifi worked well) to 11.4, but I suspect Ubuntu and Celeron M aren't a friendly combo.

---

### Post by jj97403 on 2011-05-06
1. 11.04
2. Dell
3. Inspiron 300m 
4. no video after grub.

Known issue with old intel 855 chipset (or something like that). 
My solution: At grub boot into recovery mode and choose "failsafeX" option which runs Ubuntu in "low graphics mode" which is fine for me.

---

### Post by DaddyLarry on 2011-05-07
1) 11.04
2) HP
3) Pavillion dv6700
4) Screen splits into several overlapping screens where the mouse doesn't line up with any of them.  It hasn't worked on this machine for the last three releases.  Have Nvidia graphics.

---

### Post by grabbindrivers on 2011-05-08
HP Dv9167nr 

Does not function completely under Ubuntu 11.04.

[LIST]
[*]Spotty external display detection
[*]Non-working nVidia drivers
[/LIST]

The external display connection is the most frustrating. If I fire up the laptop with an external display connected and it doesn't detect it, I have to disconnect the monitor and restart the computer before I can get the display working again.

If this continues to persist through the next few weeks I'll be downgrading to 10.10, which worked on my laptop flawlessly.

---

### Post by marcobiso on 2011-05-09
Version: Ubuntu 11.04
Maker: TOSHIBA
Model: SATELLITE C670D-109

Problem:

Just out of the box, works fine with windows7, no problems encountered with linux grml to backup partitions etc.

Installation process of ubuntu 11.04 seems good. After install, grub loads fine, then starts ubuntu, screen becomes black, after a couple of seconds I heard the sound of the login prompt, but screen still black. Tried fn-f6 (dim backlight) fn-f7 (light backlight) ctrl-alt-f1 ctrl-alt-f2, always black screen, no way to log in. Rebooted, windows still works ok. Rebooted again, tried ubuntu recovery mode, still black screen.

Tried VGA=normal kernel parameter, instead of blacking immediately a few rows of the boot process are shown. I filmed it: [http://www.youtube.com/watch?v=2n5A5rAUakg](http://www.youtube.com/watch?v=2n5A5rAUakg)

Can I do something to help solve the issue?

---

### Post by Xantares on 2011-05-09
Ubuntu 11.04 and Ubuntu 10.10 netbook remix
HP/Compaq 
Presario CQ42-122la

Live CD finish loading and then the screen go black and don't pass from there. The CDs work on other PCs.

---

### Post by Gunner2677 on 2011-05-12
> **trinityclare said:**
> Ubuntu 10.04 Lucid
Gateway
ID59C notebook

Problem #1: No brightness control, either through function keys, brightness applet, or power management settings.

Problem #2: No touchpad support -- no touchpad tab in Mouse options, no scrolling, no multitouch, no option to disable touchpad while typing (although Fn+F6 to disable the touchpad does work).

The lack of brightness control is a really bummer, otherwise I'd be spending way more time in Ubuntu and way less time in Windows.

Try this.


  sudo gedit /etc/default/grub


  Change the line GRUB_CMDLINE_LINUX="" into GRUB_CMDLINE_LINUX="acpi_osi=Linux"


  sudo update-grub


  Restart your linux

Works for me and my ID59C works flawlessly.

---

### Post by mikoyan25 on 2011-05-13
1)Version Of Ubuntu: Xubuntu 11.04
2)Laptop Maker: Toshiba
3)Laptop Model: Satellite M30
4)Known Issue: use of touchpad and touchpad buttons stops everything working except the mouse pointer within a few seconds of use. Nothing is clickable, and the keyboard doesn't do anything either. I have tried this with ubuntu and xubuntu back to 9.04 and get the same problem.

Edit: The same problem occurred with the installers.

---

### Post by malbzamora on 2011-05-14
Ubuntu version: 11.04 (both the 32 and 64 bits)
Toshiba Satellite M645
Processor: Intel Core i3 M380  2.3 Ghz
3.00 Gb RAM
Graphic Card: Nvidia GeForce GT 330M

Any of the procedures to installing Ubuntu on Windows doesn't work at all, when Ubuntu is choosen on Grub, the system is frozen (and Ubuntu is impossible to run).

---

### Post by danielelias22 on 2011-05-16
> **funicorn said:**
> Version: Ubuntu 11.04

Manufacture: **Acer**

Model: _Aspire 4741G_ with Intel i3 and **NVIDIA 310M**

Issue: **NVIDIA**. of course it's **NVIDIA**.
Neither the offical Video driver provided by NVIDIA website nor the nvidia-current version
 from the apt source does NOT work. Each time I installed the video driver and reboot, system
is halted at the very beginning of the welcome screen with Ubuntu logo and bicker dots. If I 
install the video driver and directly restart the X server,  system goes into black screen.

The same bug appears since Ubuntu 10.10 about 6 months ago, I cannot believe it's still there!  
Shame on NVIDIA, shame on Ubuntu !

I have the same laptop, do you use the 64bits version?

PLease answerme

THanks

---

### Post by Football Mania on 2011-05-19
Ubuntu 11.04 64 bit
Lenovo 3000 g530 4151/200

Wireless slows down when attached to the battery. However, without battery it works perfect. the only problem is internet connection is too slow when the battery is plugged.

My wireless adapter is broadcom 4312. Currently ubuntu installed as wireless driver as wl. Please solve it in the next ubuntu release.

---

### Post by dplehati on 2011-05-19
1) Version Of Ubuntu: 11.04
2) Laptop Maker: Lenovo
3) Laptop Model: V570
4) Known issues: nvidia optimus is not supported

---

### Post by decoherence on 2011-05-19
Ubuntu 11.04
Dell
Latitude D620
nVidia card is blacklisted, jockey shows "driver is activated but not in use"

Unity can be made to work by installing the 173 driver and setting UNITY_FORCE_START=1 in /etc/environment, as per info in this bug
[https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745](https://bugs.launchpad.net/ubuntu/+source/nux/+bug/728745)

however it can be a bit sluggish (also mentioned in the bug, i believe)

---

### Post by ZaHACKieL on 2011-05-20
1)11.04
2)Dell
3)XPS 17
4)- Nvidia GeForce GT 555M not working after installing restricted drivers.
  - Media card reader not working.
  - Random logouts
  - Possible random hangs

---

### Post by oldarney on 2011-05-20
1)11.04
2)Asus
3) UL30A-x4
4) Cannot sleep without freeze ups after waking up, unbearable mouse/system lag, requires restart.
Touch pad disable does not work hot key. Touch pad in general freezes to the point of being unuseable. It is worth noting that with the manufacturers touchpad driver, the mouse has very bad lag on windows. When we switch to default WDDM things work gloriously.

Edit:
[http://ubuntuforums.org/showthread.php?t=1321032&highlight=sleep+freeze](http://ubuntuforums.org/showthread.php?t=1321032&highlight=sleep+freeze)
fixed most resume issues with that.

---

### Post by aktivator on 2011-05-21
I have a Gateway 200 ARC PC Notebook which I inheirited. I installed a new HD and then Ubuntutu 10.10 which worked well. Unfortunately, I then upgraded to Ubuntu 11.04 and it looked OK until it restarted - No image on the screen. So I went back to 10.10. That works very well, except I haven't been able to get the built in wireless to work yet.

---

### Post by DJ-Jumbo on 2011-05-22
Brand: Acer
Type: Extensa 5220
Version: Ubuntu 11.04, with updates
Problem i found: i cannot get the wireless working. Even not with the "windows *.inf drivers"
it&#347; a broadband 4311 chipset onboard. When asking for "System check" he recognizes the chip, but drivers cannot communicate with him.

---

### Post by foxhead128 on 2011-05-23
Toshiba Satellite L505-S5990
Processor: Intel Core 2 Duo T6500 (2.10 GHz)
Memory: 2.8 GiB
Hard drive: 320 GB
Wireless card: Realtek RTL8192SE

Ubuntu 10.04:
Last time I checked, the wireless card isn't supported out of the box. The driver has to be compiled from source manually. It then suffers from the problem I've described for Ubuntu 10.10 and 11.04 below. Everything else seems to be okay, though.

EDIT:
Ubuntu 10.04.2, a revised version of 10.04, supports the wireless card out-of-the-box, but then runs into the same issues that 10.10 and 11.04 have with wireless Draft-N (802.11n).

Ubuntu 10.10 and 11.04:
The wireless card usually works, but when it comes to 802.11n routers, the connection can be frustratingly unstable. It tends to run slowly, and will randomly disconnect every now and then, often with increasing frequency as the session prolongs. Usually, it manages to reconnect after disconnecting, but in some cases, the only fix (without simply rebooting the computer) is to force-reload the driver by using modprobe. Other than that, I don't associate any problems I've had with the laptop itself.

---

### Post by Deltik on 2011-05-28
[CENTER][COLOR=Orange][SIZE=6]Ubuntu 11.04 Natty Narwhal[/SIZE]
[COLOR=Black][SIZE=1]on an[/SIZE]
[SIZE=5][COLOR=RoyalBlue]HP Pavilion dv7t[/COLOR][/SIZE][/COLOR][/COLOR]
[/CENTER]

_**Issues**_
[Click here]("http://ubuntuforums.org/showthread.php?t=1765283") to see a list of the issues.

---

### Post by colordrops on 2011-05-30
1)Version Of Ubuntu: Natty 11.04
2)Laptop Maker: HP
3)Laptop Model: dv4-3011
4)Known Issue:

  a) Trackpad does not work.  "GPointing Device Settings" shows as enabled, /var/log/Xorg.0.log shows that the driver loaded properly.  dmesg has tons of "psmouse.c: bad data from KBC - timeout" messages

  b) Radeon HD 6750M does not work.  Tried Open Source driver, fglrx from "Additional Drivers", and also downloaded 11.5 directly from AMD.  Drivers appear to be loaded (Radeon and fglrx) based on lsmod.  Tried using vgaswitcheroo for both immediate and delayed switching.  Immediate switch has no effect.  Delayed switch causes screen to go black upon X restart.  Powering DIS on and off DOES work though.  lspci reports "Unknown header type 7f".  Card is 6750, but reported as 6741.  Driver reports that it is loading "TURKS" microcode.   fglrx driver segfaults on glxinfo and glxgears.

  c) Intel i915 integrated video works, but with severe tearing and other strange effects.

  d) ACPI (I assume) has several issues.  Wifi doesn't work on battery power.  Suspend and hibernate are unrecoverable.
-- colordrops

---

### Post by erans on 2011-06-02
1) 11.04
2) Lenovo
3) Thinkpad Edge E420
4) Acer_wmi is loaded by default and blocks wireless connectivity. When disabled through rmmod and rfkill unblock all, the wireless connection is extremely poor. If drivers from the Realtek website are installed with acer_wmi blacklisted, Ubuntu will not boot. If drivers from Realtek are installed and the user runs ```
sudo su
rmmod -f acer_wmi
rfkill unblock all
```
the system locks up and has to be force reset. Basically, the wireless is unusable. Chipset is 8188ce.

Details here: [http://ubuntuforums.org/showthread.php?t=1770202](http://ubuntuforums.org/showthread.php?t=1770202)

---

### Post by tdm on 2011-06-03
Brand: HP
Model: dv4-3029tx
Specs: Intel Core i5. ATI 6750M 1GB (can switch between power-saver i5 GPU and ATI GPU. 4GB RAM. 650GB HDD. USB 3.0.

OS: Ubuntu 11.04 x64
Problems: In the live cd and wubi installs, 95% of the time it will just have a black screen straight after GRUB. Otherwise it works but the backlight is OFF so almost nothing is visible. Pressing Fn+F3 will turn the backlight back on and I can install. If I install, then it is just a black screen when I try to boot. If I boot in failsafe mode, it lists a whole lot of hex codes and [Radeon] at the end. And then freezes with flashing cursor. I have tried one other distribution, Pardus 2011 x64 Installation DVD. It also lists the hex and then freezes.

---

### Post by fi2 on 2011-06-03
ASUS K53SV
Ubuntu 11.04

nvidia GT540M - proprietary Nvidia driver does not work. Unity however starts and runs smoothly. 
Found the explanation [_[COLOR="Blue"]here[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=nvidia+optimus"). 

Compiz effects start with the care that is to be taken with 11.04.

New info: after recent update two finger scroll works.

New info: HDMI output: after recent automatic update HDMI works perfectly.

Standby mode is lazy to resume (about 1 minute).
So far I couldn't find any stable fix.

Overall performance is impressive, after several updates Ubuntu 11.04 seems to stabilize.

---

### Post by silverhaze06 on 2011-06-05
toshiba satellite L-655-S5150(64bit) w/64bit ubuntu 11.04

after freshly installing ubuntu the headphone jack does nothing, internal speakers just keep on going like nothing is plugged in to headphone jack.
that got fixed tho, as seen here [http://ubuntuforums.org/showthread.php?t=1774627]("http://ubuntuforums.org/showthread.php?t=1774627")

also, as with many toshiba laptops, the battery is not recognized due to kernel conflict it seems. there is a proposed fix that seems to work work here, [http://techinterplay.com/fix-toshiba-battery-issue-linux.html]("http://techinterplay.com/fix-toshiba-battery-issue-linux.html") it seems to work for quite a few people. but when i tried this my self, my computer kept freezing when it was almost done recompiling the kernel. so i can't seem to get this to work until it gets fixed in an update.

other than that the function key to turn the wifi antenna on/off does not work. the network manager is capable of doing this if you enable and disable it from there, but when it is off, the indicator light on the laptop remains on. but if i boot into windows and turn it off in there, the indicator light will go off. then when i reboot back into ubuntu, wifi is automatically on and picking up networks, but weather i turn it on or off from the network icon, the light is always off. then when i boot back into windows, it is off until i turn it back on



the wifi thing is not a huge issue in my opinion, but is a little annoying. the biggest thing though is the battery issue. that definitely needs to be fixed. and the headphone thing for other people is a pretty big issue it seems.

---

### Post by Simon Bateman on 2011-06-06
LENOVO 3000 G530 (MT 4151)
Ubuntu 11.04 (Natty) 32 bit

EDIT [F2] BIOS

SET ADMIN.Password only ********
**Disable** USER PASSWORD at boot

I get Unity login screen -> login and [COLOR="DarkRed"]CRASH to screen of bug text[/COLOR]

Switching 'Disable user password' OFF and after entering BIOS admin password and Natty works OK

---

### Post by user06 on 2011-06-11
Version Of Ubuntu: maverick 10.00 
2)Laptop Maker: c3cube
3)Laptop Model: Delgado (L11VP-2)
 Processor  : Intel Pentium SU3500 1.4GHz, Cache 3MB
 Chipset    : Intel Chipset GS40
 Memory     : 2GB DDR2 RAM
 Hard drive : 320GB SATA HDD
 Graphics : Integrated GMA 4500M HD Shared

4)Known Issue: can't intall and upgrade to natty 11.04

---

### Post by adonp on 2011-06-19
1)Version Of Ubuntu:9.10
2)Laptop Maker: Clevo
3)Laptop Model: M765s
4)Known Issue:

hardware:
processor:intel pentium dual T2390  @1.86Ghz
ram: 2GB DDR2 (PC2-5300)
Motherboard: SiSm7x0s, chipset: SiS672, southbridge: SiS968
Graphics: SiS Mirage 3 Graphics

no sound
no wireless card detected
video resolution (low 800x600 ) but fixable only till 1024x768 if xorg.inf modified

---

### Post by phasegen on 2011-06-19
I have a Toshiba Satellite L305-S5933. I just uninstalled Natty (11.04) and reinstalled Lucid (10.04) due to a cpu overtemp issue.  Natty couldn't find the temperature sensor, and Lucid, with updates, could.  Ubuntu has an ongoing issue with cpu temperature on this, and my last laptop, a Dell Inspiron. 
What do they keep doing to the kernel to cause this, and what can I do to help stop it?

---

### Post by grandmoo on 2011-06-21
1)Version Of Ubuntu:  11.4
2)Laptop Maker:  Dell
3)Laptop Model:  Inspiron 1520
4)Known Issue:  Bluetooth won't enable in spite of telling it to.  Makes me sad, everything else is going great - even got Unity to work with my nVidia graphics.

---

### Post by owiknowi on 2011-06-22
HP dv6-3185ED (man. 2010)

Wireless works sometimes but mostly fails, most function keys don't, reboot / shut down freezes the dv6 completely, proprietary ATI drivers leaves it unbootable, touch pad troubles, and so on.

Tried several species of penguins: (k, x)ubuntu 8 - 11, red hat (SL 6), mandriva, gentoo, unity-linux, pardus 2, mint 9 - 11, fedora 14, opensuse11.4 and none of them can get things more or less working or even boot...

For specs see:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02537266&prodTypeId=321957&prodSeriesId=4247579](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&objectID=c02537266&prodTypeId=321957&prodSeriesId=4247579)

= = = = =
*Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6, especially when using the radeon.dpm=1 boot option: *
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by japer855 on 2011-06-29
1)Ubuntu 11.04 / Xubuntu 11 (i think thats the xubuntu)
2)Samsung / Acer
3)RF711-S01AU / Acer Asipre One
4)Dual graphics donesnt work well, trying to use WINE to run windows games doesnt work either...
for aspire one, battery life droped from 3 hours to 20min...

---

### Post by jackbkjack on 2011-07-01
Lucid 10.04
Dell
Inspiron 1564
Issue: The video chip set is not supported.

---

### Post by nine9nine on 2011-07-02
1) Ubuntu 11.04

2) Toshiba

3) Satellite C655

4) It won't boot.  It seems to be a kernel issue since the old kernel booted after I upgraded, but the new kernel won't.  I also can't get into recovery mode after I tried to reconfigure x.  I guess I'll have to wait for the 2.6.39, which I hope will come in 11.10.

---

### Post by KingConnought on 2011-07-03
1)Ubuntu 11.04  desktop 32bit
2)Laptop - ASUS
3)Laptop f5GL / PRO50GL
4)Known Issue: Live CD starts but comp freezes.   WUBI wrecks boot area and MBR.  Lappy now boot loops from a restart. :(

---

### Post by KingConnought on 2011-07-03
[B]Recalibrate battery from Bios (if possible).
[/B]

" 			 		   		 		 		[COLOR=SlateGray][I]1)Ubuntu 11.04 / Xubuntu 11 (i think thats the xubuntu)
2)Samsung / Acer
3)RF711-S01AU / Acer Asipre One
4)Dual graphics donesnt work well, trying to use WINE to run windows games doesnt work either...
for aspire one, battery life droped from 3 hours to 20min..."[/I][/COLOR]

---

### Post by shanjay86 on 2011-07-04
Ubuntu 11.04
toshiba 
L500
cant get web came or BT to wrk had issues wid resolution which is fine after updates...

---

### Post by Sebastian-Li on 2011-07-05
Toshiba Satellite L750 with Nvidia chipset

1) integrated mic does not work

2) external analog sound output does not work (e.g., for headphones)

---

### Post by mybodya on 2011-07-08
1)lubuntu 11.04, and also EasyPeasy1.6 based on Ubuntu 10.04
have the same problems
2)Lenovo 
3)IdeaPad S10-3 (20039)
4) see [http://ubuntuforums.org/showthread.php?p=11026107#post11026107](http://ubuntuforums.org/showthread.php?p=11026107#post11026107)

---

### Post by AlexValex on 2011-07-09
1. OS: Ubuntu 11.04
2. Maker: Dell
3. Model: Vostro 3350 N Series (with Processor Intel I5 - 2470M, 2.3 GHz.)

Known Issues: 
1. The fingerprint reader: it is not identified by OS
2. The VGA card: the laptop has a dual-type VGA card: the processor has it's own, and for more elaborated tasks (video, games) it has a AMD/ATI Radeon HD 6470M. When installing the ATI Catalist driver I'm informed that it's not a proper version of the driver. This might be correlated to something I've read on another forum that the Ati VGA is in fact a 6490, not 6470.

See: [http://ubuntuforums.org/showthread.php?t=1800160](http://ubuntuforums.org/showthread.php?t=1800160)

---

### Post by joel.markshalayenka on 2011-07-09
[B]1. Ubuntu 11.04 64bit
2. HP
3. ProBook 4520s (i3 with intel graphics and fingerprint reader)
4. Trackpad and Fingerprint reader do not work[/B]

POOR COMPATIBILITY - - NOT RECOMMENDED - - CRITICAL TRACKPAD issues due to lack of x86-64 drivers.

Install from a USB stick, no problems. Wireless worked immediately.  Running dual boot with Win7 Pro 64bit which I installed first. Problems that are not present in Win7 (i.e. its not a hardware fault): 

[LIST]
[*]Trackpad right button does not work.
[*]Trackpad left  button is part of the overall trackpad, this means that clicking often  changes the pointer location by enough for you to 'miss' the object you  wanted to click on, or much worse and more common, the pointer 'jumps'  to the bottom left corner of the screen.
[*]Trackpad on-off button does not work.
[*]FINGERPRINT READER has no driver support at all.
[*]Will  not come out of hibernation. Requires a forced power-down and reboot.  Solved by requiring the computer to shut down on detecting critical  battery.
[/LIST]
HP were very unsupportive. They state that there are SuSe 32bit  drivers for the trackpad. If thats your distro, fine, although on a  machine that takes 8GB Ram, a 32bit OS is a strange choice. If you are using  64 bit linux then forget this laptop, its touchpad is junk until it gets  driver support.

---

### Post by DelusionalX on 2011-07-09
1. Ubuntu 11.04
2. Acer
3. Aspire 5920G
4. Big graphics driver bug with Nvidia 8600M GT (but not only that model).
This problem persists on a lot of nvidia cards. It's a compatibility issue with the kernel and the graphics drivers.

There are millions of laptop models affected (including an entire Macbook series) and I don't see why developers are neglecting this issue. 

It seems 11.04 was pushed out of the door without being tested first just to meet the deadline.

Let's hope tot 3.0 kernel fixes this so a large group of users can get passed 10.04.

---

### Post by trungvkvk on 2011-07-11
I have a Toshiba L455 with Ubuntu 10.04.
Ubuntu has an ongoing issue with cpu temperature on this, and my last laptop, a Dell Inspiron. 
What do they keep doing to the kernel to cause this, and what can I do to help stop it?

---

### Post by bouherve on 2011-07-12
1) Ubuntu 10.04 32 bits
2) Acer
3) Travelmate 630

With all Ubuntu based distributions, I have experienced complete freeze of the system. Only turning off is possible.
I've tried Ubuntu, Peppermint, Mint... This doesn't happen with OpenSuse, Puppy, Mandriva, Slitaz, PCLinuxOS on this hardware!

This 10 years old laptop has NVidia GeForce2, AMD 1.8 GHz, 512 Mb RAM.
I have tried some of the fixes from the forums (acpi, nohz, Vesa mode) from time to time, no solution up to now.

---

### Post by theupendra on 2011-07-17
Version: Ubuntu 11.04
Laptop Maker: Micro Star International [MSI]
Laptop Model - CR 400
Problems: The graphic is not supported so that the theme is old theme like on Ubuntu 10.04. I like to have Ubuntu 11.04 on my laptop but doesn't work. Any solutions?

---

### Post by dwitkin on 2011-07-18
1)Version Of Ubuntu: **Ubuntu 10.10**
2)Laptop Maker: **Sony**
3)Laptop Model: Vaio VGN-FW270J
4)Known Issue: laptop will not recover from suspend and hibernate.  Instead, laptop reboots (i.e., Sony screen appears, GRUB appears, etc.)

The system uses an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

I've tried some troubleshooting using the thread here:
[http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999).  I haven't gotten all the way through it, but no luck so far.

I've also tried this, but no luck:
[http://www.baudlabs.com/archives/1287](http://www.baudlabs.com/archives/1287)

I'd appreciate any suggestions.

---

### Post by trungvkvk on 2011-07-18
ubuntu 10.04 
Dell
Latitude D830
Wireless works and then doesn't work

= = =
Mörgæs 2014-12-19: 
For 14.10 it all works, Intel Wireless 4965 AG / AGN wifi card.

---

### Post by learner.k on 2011-07-31
hello,
OS:ubuntu 10.10
Maker:Dell
Model : XPS 15 L502X

Not getting GUI after installing nvidia graphics card drivers..

---

### Post by wsgut on 2011-08-01
my toshiba 1135 will not work on ubuntu 10.04,10.10,and 11.04:(

---

### Post by balkrish999 on 2011-08-03
I have a Compaq Presario CQ61-330SA

_**The D drive is NOT accessible**_   :(

I have Windows 7 and Ubuntu 11.04

---

### Post by santoos on 2011-08-03
even i own a lenovo laptop it is also incompatability

---

### Post by rememberme22222 on 2011-08-03
I have the same basic question as you, dont find a way to make a new  post in this most appropriate category...is this site a pick your brains site where you post the helpful solution to your problem, like a spambot, or are there any humans here who reply? I notice there are not replies visible to any of these laptop-problem issue threads here. 
Wondering if l455 toshiba will be a waste of time to purchase Ubuntu or not, before i do it. (Tried knoppix once on different toshiba, no modem, no fan, etc.)
Thanks for telling that the fan doesnt work..I suspected that and am not going to kill a brand new laptop just to have the desired linux on here. (Its a program that runs the fan, so that program is missing in Ubuntu...just like the touchpad program, and the battery charge level program that measures.) (I am so sick and tired of Windows monopoly and bad security...dont understand whats so hard about making linux work with a laptop and why someone hasnt worked it out yet...L455 is 2 years old (just bought, new old stock at dept. store)....amazing.

---

### Post by rememberme22222 on 2011-08-03
I was writing a reply to the thread on no fan/L455 Tosh Satellite...why did it get put way far away from the thread I replied to?
 
I just answered my own question about the pick your brains spambot/lack of opposing thumbs.

---

### Post by joebarker182 on 2011-08-14
asus a43sv [k43 family]

bluetooth is always disabled wont enabled.

---

### Post by pierreyy on 2011-08-15
1)Version Of Ubuntu: 11.04 natty norwhal
2)Laptop Maker: toshiba
3)Laptop Model: a665
4)Known Issue: backlite keyboard does not work on ubuntu/ it does on windows 7

---

### Post by Ollie13 on 2011-08-15
1)11.04
2)Acer
3)Travelmate 2310
4)No backlight.

---

### Post by mcstat on 2011-08-16
1) OS: Unbuntu 10.04 LTS (Ultimate Edition 2.7)
2) Make: HP
3) Model: 4530s
4) Issue: There are no sound, graphic card, HD webcam and finger print reader drivers.

---

### Post by Weird7 on 2011-08-16
1)Version Of Ubuntu: 11.04 natty norwhal
2)Laptop Maker: Gateway
3)Laptop Model: MT6705
4)Known Issue: Laptop freezes after about 1 hour inactivity.  Reboot is only way to get back in. Laptop works fine with 10.04 and 10.10

---

### Post by jn114ss on 2011-08-16
I am running Ubuntu 10.10 on a Dell Inspiron 17R (n7110). To make my Intel Centrino wireless-N 1030 WiFi card work i had to install kernel 2.6.38 and then update using  an ethernet connection. The biggest problem i have is with my Nvidia 525m video card. Installing the drivers that Ubuntu recommends will make you get a terminal prompt next time you start your machine again. running this 

~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
~$ sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

Instead of the one ubuntu recommends fixes the problem but you still wont be able to get special effects or compiz to work like there suppose to. Ive looked everywhere to try to fix this problem with no success. I might have to go back to Natty :confused: where they had better support for my video card. 
[B]
[/B]

---

### Post by starlegacy on 2011-08-17
1)Version Of Ubuntu
10.04

2)Laptop Maker
Toshiba

3)Laptop Model
Satellite L645

4)Known Issue:
Function (fn) button are not working, example, when i press FN + F8 it should turn on wireless / bluetooth on, but nothing changes.

Bluetooth not working.

Networking:
Network controllers detected, but not acknowledged by network connections:
-Broadcom Corporation Device 4727 (rev 01)
-Atheros Communciations AR8152 v1.1 Fast Ethernet (rev c1)

My laptop is Intel(R) Core(TM) i3 CPU M 330 @ 2.13 GHz

The installation done normally, but when selecting network connections, they said no network connections. While on interface lists only "lo interface" no other device. In my windows 7, everything works normally.

Thanks.

- Samuel -

---

### Post by KemKev on 2011-08-20
Laptop: HP Pavilion dv6110ca, AMD Turiton 64x2, Wireless card BCM4311
Install: Ubuntu 11.04 (dual booting with Windows 7)

Ubuntu installs and runs fine. However, IRQ issues (cannot request IRQ-0; probably buggy MP table) means no wireless - tried using wl and b43 - and the integrated webcam doesn't work. BIOS update and trying all the boot options failed to correct IRQ problems. 

UBS wireless adaptor and USB webcam work without need for additional driver install.

---

### Post by pauly2011 on 2011-08-20
I have a Compaq Presario C700 (C751NR to be exact)

I have installed Ubuntu 11.04, which runs fine,

but I also installed the KDE package and Kubuntu does not work with my wireless card (Atheros AR5001).

I haven't done much searching on how to fix it yet.

---

### Post by dwigyit on 2011-08-21
Ubuntu 10.10 / 11.04

Laptop: MSI GX660R

Compatibility: Installs and runs fine, but sound only plays through headphones or the subwoofer (partial fix below). MSI fan boost button works, but Eco power profiles do not. Also, in-built lights to not work. The last two are not Ubuntu issues, however, they simply arise from an absence of the MSI system control application which only runs on Windows.
Screen brightness control also does not work - there is a delay of several minutes before changes made using keyboard buttons take effect, though it will dim when on battery and relight when plugged in.

Sort-of-fix for the sound issue is contained in this thread, as well as a discussion on how to perhaps enhance it. Its limitations are also defined there. [http://ubuntuforums.org/showthread.php?t=1800700](http://ubuntuforums.org/showthread.php?t=1800700) Add the text contained in the code box to /etc/modprobe.d/alsa-base.conf (you will have to run gedit as root - alt+f2 then gksu gedit ;) )

---

### Post by netbook_helper on 2011-08-21
Emachine 350 Netbook
Ubuntu 11.04
No Microphone,
Suspend not working, after closing lid.
Every thing else good. :popcorn:

---

### Post by Finejason on 2011-08-23
Laptop: HP Pavilion dv6 6176sa, Intel Core i3 2310m
Issue: CPU Integrated Intel HD graphics and AMD Radeon switchable
Install: Ubuntu 11.04 (dual booting with Windows 7)

Ubuntu 11.04 Live dvd doesn't work - stops at Radeon graphics detection
Usb pendrive install boots to a blank screen. 
Mint 11 Live dvd boots fine. (DVD from LinuxMagazine)

Have not tried very hard to resolve yet.
Have read this so far - the screen resolution ( 1366 x 768 ) is not supported until next kernel release and the switchable graphics system is not supported by the open source radeon driver. This  causes excessive power consumption becuase the unused Radeon card 'runs' it's fan at full speed and can not be disabled in BIOS. 

Hopefully these issues will be resolved eventually. I do not want to run Windows 7 for very long!


= = = 
Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6, especially when using the radeon.dpm=1 boot option: 
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by milos_silni on 2011-08-24
> **jn114ss said:**
> I am running Ubuntu 10.10 on a Dell Inspiron 17R (n7110). To make my Intel Centrino wireless-N 1030 WiFi card work i had to install kernel 2.6.38 and then update using  an ethernet connection. The biggest problem i have is with my Nvidia 525m video card. Installing the drivers that Ubuntu recommends will make you get a terminal prompt next time you start your machine again. running this 

~$ sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
~$ sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

Instead of the one ubuntu recommends fixes the problem but you still wont be able to get special effects or compiz to work like there suppose to. Ive looked everywhere to try to fix this problem with no success. I might have to go back to Natty :confused: where they had better support for my video card. 
[B]
[/B]

Linux is not supporting nvidia optimus technology. 
only way to get your card working is with bumblebee 
try
[https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)

---

### Post by frankyyyy on 2011-09-04
1) OS: Unbuntu 11.04 LTS (automated detected AMD64 ver)
2) Make: Toshiba
3) Model: F750 (i7 2670qm 64bits)
4) Issue: Can't complete the installation. The kernel message looks no error, the final line it hangs is
[5.795250] usbhid:USB HID core driver

I also tried i386 version, and I saw crash in kernel message.
I know my laptop is quite new(released end of last month), would appreciate if someone could help on this. I really need to install Ubuntu into this laptop. Thanks a lot in advance.

---

### Post by ajardine on 2011-09-05
Dell Studio 1737
Quad core 64 bit intel processor
4 Gb. ram

I am unable to load 11.04 on the above machine. I did manage to load 10.04 then upgrade to 10.10 but numerous efforts to upgrade to 11.04 and all efforts to do a clean install of 11.04 have resulted in the system freezing after less than a minute of the loading starting. 
Does anyone else have this problem?  I am reluctant to try loading 11.10 in case I lose everything I have in 10.10.

---

### Post by letank on 2011-09-08
the gat2eway LT2802u (it is a rebranded ACER laptop)
10.4 LTS
no sounds, no microphone.... no network menu... reverting to what worked with wubi.

this is the atom n455, it worked very well w 9.04 off the box, audio, microphone (needed to select different hardware), skype worked, dimming almost worked, skype worked, wireless worked

---

### Post by lqlarry on 2011-09-12
1)Ubuntu 11.04 64bit & 11.10 Beta 64 Bit
2) Acer
3) Aspire 5750-6431
4) Have not found them all but...
Dimming (fixed with bug report)
No Touchpad tab in Mouse Settings
Scrolling does not work

Thanks

I installed 11.10 64 bit on 9/15 and it fixed the problem of the no touchpad tab and now the scrolling works.  I now need to find that bug report and fix the dimming issue.  I hope this helps others...Larry

---

### Post by maan81 on 2011-09-18
1)Ubuntu 10.04 64bit

2) MSI

3) MSI VR440

4) - Screen resolution incorrectly identified as 800x600 instead of 1280x800.
    - Created distorted and overblown display in graphical mode.
      Text seriously flickers in text mode, making it fully useless.

---

### Post by walding on 2011-09-18
HP DV6-3180EA
Ubuntu 11.04 64-bit

Installation works OK to start with, but freezes on shutdown (from the very first restart).  Only solution is to hold power button to turn off.
Will start up OK, but restricted driver for ATI graphics card cannot be installed without freezing OS entirely (will not shut down; will not boot up properly).
Mouse trackpad did not work properly on 1st Ubuntu install; did work on 2nd Ubuntu install - no idea why.
Everything else seems to be OK...perhaps all the problems are down to the graphics cards?
Fingerprint reader doesn't work, either. But I didn't really expect it to.
Naturally it all works out of the box with Windows 7, but it was designed with that in mind (closed drivers etc.)

= = = = =
[I]Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6, especially when using the radeon.dpm=1 boot option: 
[/I][https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by Belgoroth on 2011-09-20
> **mcstat said:**
> 1) OS: Unbuntu 10.04 LTS (Ultimate Edition 2.7)
2) Make: HP
3) Model: 4530s
4) Issue: There are no sound, graphic card, HD webcam and finger print reader drivers.

Same laptop running ubuntu 11.04 same issues for me too.
Fixed sound by updating the kernel, moving to kernel 3.1 rc 4 fixed webcam
Video drivers still an issue, even in normal desktop use. Using [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) made the it more usable and videos are working better still not much on 3d though

---

### Post by sean lyon on 2011-09-22
Ubuntu 11.04
Acer
Aspire 5332

when booting screen backlight fails to start 
never got beyond that

---

### Post by Gorros on 2011-09-24
1)Ubuntu 11.04 64 bit
 2)Laptop Maker: Lenovo
 3)Laptop Model: S205 Ideapad
 4)Wifi doesn't work :(

---

### Post by xabaras on 2011-09-24
Macbook 5,1 (aluminum)/ubuntu 11.04
touchpad works very badly
life battery is much shorter than on mac os x
it gets very hot quite easily
light coming from the screen can't be moduled
webcam doesn't work
cd/dvd burning works only sometimes (no problems in cd/dvd reading)

---

### Post by BlkIce on 2011-09-27
1. HP G70-250US Notebook PC
2. Windows 7 32-bit Professional
3. ubuntu 11.04

Wireless adapter INOP. Works fine when switching back to Win 7 but not using ubuntu.

---

### Post by hemna on 2011-09-28
Please Only List
1) 11.04 64bit 
2) HP
3)Elitebook 8560W
4)  cannot boot the install ISO.   modprobe pukes during boot.

nouveau_probe_i2c_addr

Also, the first line in the output of the kernel boot says

BUG: unable to handle kernel NULL pointer dereference at 0000000010

I can get it to boot by disabling nouveau.   When ubuntu install cd/iso is booting, hit ESC and go to the boot options.

hit F6 to alter the boot options and add
nouveau.modeset=0  to the end of the boot options line and then hit enter

This disables nouveau from being modprobed at boot up.

---

### Post by geesch on 2011-09-30
1) OS:    11.04 64bit 
 2) Make:  ASUS
 3) Model: N55SF
 4) Issue: LiveCD fails to start

hit F6 to alter the boot options and added
**nouveau.modeset=0 **
to the end of the boot options line and then hit enter.

This forces the use of the build-in Intel GPU instead of the 2nd NVIDIA 555M (Optimus) GPU. (Many thx to previous poster!)

---

### Post by garolou on 2011-10-05
> **Belgoroth said:**
> Same laptop running ubuntu 11.04 same issues for me too.
Fixed sound by updating the kernel, moving to kernel 3.1 rc 4 fixed webcam
Video drivers still an issue, even in normal desktop use. Using [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu) made the it more usable and videos are working better still not much on 3d though

Same model (deskpro 4530s)
Needed to delete the 2 HP partitions to make space for an Ubuntu/Windows dual boot.
Installed Ubuntu 11.04 64bit; Linux 2.6.38-11-generic

As of yet, it seems to work well - did get rid of 'unity' from the start.

Minor Issues discovered:
Touchpad on/off switch [left/upper corner of pad] does not work (a software switch can be implemented if I cared for it)
Fingerprint reader (I lived without it in the past, so don't care)

---

### Post by Tutoka on 2011-10-06
1. 11.04 32bit
2. HP
3. Pavilion DV6
4. Clickpad does not exert right clicks

---

### Post by asadullah on 2011-10-11
Toshiba Satellite c655-S5225
Ubuntu 11.04 11.10
Use boot repair to turn acpi = off then must push enter keyover
and over to boot into Ubuntu. 
Doesn't shut down all the way with shutdown command
Random reboots. 

All hardware except for what's mentioned works geat

---

### Post by booterror on 2011-10-13
Acer Aspire One 522
Xubuntu 11.10 64 bit
AMD c-50 processor

Locks up when wifi connects unless ethernet is also plugged in. Locks up at boot if ethernet isn't plugged in. Trying to install the video drivers through the driver installer fails. The official driver installer downloaded from the AMD website wrecks your OS. These are problems common to every distro of Linux I've tried. Avoid this POS at all costs.

---

### Post by alexthunder on 2011-10-14
HP Envy 
Core i7 Q720
Ati Mobility Radeon 5850

Ubuntu 11.10 x64

Can run Live CD. Installation goes on smoothly. Freezes on rebooting.

---

### Post by daraghfi on 2011-10-16
1. 11.10 Oneiric 32-bit
2. Sony VAIO
3. PCG-R505EL
4. Blank Screen 

X loads, but the screen shows an ethereal backlight pattern (not simply 'blank')

Wish I could get this dear friend up and running.

---

### Post by Medallish on 2011-10-17
1. 11.10 64-bit
2. HP
3. Probook 6465b(AMD Fusion, Llano laptop)
4. Only issue I can see is turning off the touchpad doesn't work the conventional way of double tapping in the upper left corner of it.

---

### Post by TREESofRIGHTEOUSNESS on 2011-10-17
Compaq Presario R3000

Must use acpi=off   to boot, haven't found any other options.
This is the biggest issue with this computer.  The others can be fixed, and are done automatically (now).
I would like to solve the acpi=off issue.  


in my update from 11.04 to 11.10 I had to re-run the b43 firmware installer, by removing it and installing it again.

11.10 detected my video card automatically and downloaded the nvidia driver, unlike previous versions.

otherwise the computer runs much better, and quicker than it did with winXP last year

---

### Post by fiddlefye on 2011-10-18
I have an HP tc 4200 and have been having issues with screen brightness under 11.10. All goes dim after sometimes as little as a few seconds. I can sometimes (but not always) bring the level back up in 'Screen' (where I find it suddenly at the lowest possible setting), but bringing up the output level is a hit-or-miss proposition. I note that I am not alone in this issue. I'm new to Linux (having used Macs since the dawn of time... don't laugh) so I'm afraid I'm not much help yet. I'll learn....

---

### Post by clash101 on 2011-10-18
Ubuntu 11.04
Gateway EC14D

Only one (1024x768 4:3) resolution available. I need 1366x768 resolution 16:9.

---

### Post by spaargo on 2011-10-18
1) ubuntu 11.04 and 11.10 (10.10 works fine)
2) emachines
3) E527
4) blank screen on usb boot. it boots fine, but as soon as it goes the splash screen (i assume) the screen seemingly turns off, but i know the system is still running because i can hear the startup sound

---

### Post by karthikn21 on 2011-10-19
hi guys i'm havin acer 4736 laptop 
jus now installed ubuntu 11.10 and the display is not working when it is booted in normal mode 
but it is working in the recovery mode....please help me with this . The same problem occurred when i used ubuntu 11.04....:(
then i came to the forums and tried the solution suggested but it didn't woked...
if any one can please give me the step by step procedures to recover from this problem [IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

thanks in advance[IMG]http://ubuntuforums.org/images/icons/icon7.gif[/IMG]

---

### Post by suwish on 2011-10-20
> **mdog said:**
> Alienware M15x (configured with i5-540m and gtx 260m) running Ubuntu Lucid Lynx 10.04 LTS
 
Most to least critical:
 
1. **No fan control (fan seems to always run at lowest setting)**
2. No CPU temperature readings
3. No sensors apart from Nvidia and SMART temperatures
 
"sensors-detect" finds nothing, there really should be basic support for my CPU and chipset.
 
The kernel does find some cooling devices, but "/proc/acpi/fan" is empty (dmesg output):
 
```

[    0.711573] processor LNXCPU:00: registered as cooling_device0
[    0.715086] processor LNXCPU:01: registered as cooling_device1
[    0.717449] processor LNXCPU:02: registered as cooling_device2
[    0.723684] processor LNXCPU:03: registered as cooling_device3
[    1.165893] acpi device:07: registered as cooling_device4

```
 [COLOR=#000000]When i using windows, it running well, the temperature is normal.[/COLOR]
[COLOR=#000000]But, when i want to installing ubuntu, laptop become so hot, event i can't touch my keyboard.[/COLOR]

---

### Post by andradx on 2011-10-22
1. Ubuntu 10.10
2. Toshiba
3. S10-11F
4. Wireless internet is experienced in bursts. After 30s~1m of connectivity follows a period of 1m~5m without it. DHCP works fine, wireshark displays several packets received regarding other computers, but packets incoming from my laptop are inexistent when connectivity does not exist. As far as I can tell, the problem does not exist with every wireless routers or access points. With 802.11n routers this problem is experienced. With 802.11b/g routers the wireless connection displays connectivity at all times. 

[EDIT] (The first time this problem aroused, connectivity in Ubuntu came and went, while a VM running Win7 on VirtualBox with a bridged connection holds connectivity).

---

### Post by Dear.Devil on 2011-10-22
1. Ubuntu 10.10
2. Acer
3. Aspire One 722
4. everything works well, except one thing.
i can't enabling desktop effect in this machine, until now i can't figure out how to fix it.
maybe some advice from you guys will make it. i need help, really!

just PM me if someone have something to figure it out :)

---

### Post by IWantFroyo on 2011-10-22
1) Ubuntu 10.10
2) Toshiba
3) T235D-S1360
4) ACPI problem fixed with adding "pci=noacpi" to grub.

---

### Post by fiazseo on 2011-10-25
I have a New laptop L455 with Ie8 10.04. The fan management with Ie8 doesn't operate, and none of the Purpose recommendations operate. Now, I can not listen to appear and my mic will not operate. Considering other choices now.......
Oh well.

---

### Post by Maintech on 2011-10-27
1- 11.10
2- HP-DV6Z
3- APU Radeon Video

I have 11.04 installed on this computer and everything seems to work fine. No issues with sound, web cam, touchpad, sensors, or video.

I have tried to run 11.10 using many different configurations but they all fail on video. Nomodeset keeps the video output from dieing but there is no GUI and it will not load the kernel modules for the Radeon.

11.10 is a broken release compared to 11.04.

---

### Post by hydroxph on 2011-11-03
HP Pavilion: DV6 1007 CA 
Latest working Ubuntu: 9.04 
Problems: Touch sensitivity wireless button locks up and can't be activated again.

---

### Post by lilkidz on 2011-11-04
Ubuntu 11.10
Asus 1215B
When I connect to a monitor via HDMI, there is no audio when HDMI output sound is selected.
Another problem is the suspend does not work.

---

### Post by mebss on 2011-11-04
-Kubuntu 11.10
-Toshiba
-Satellite C-650D
-Not fully compatible with the new AMD shipset, A lot of bugs.

---

### Post by QueSeYo on 2011-11-06
Ubuntu 11.10 x64 bits

Laptop Toshiba Qosmio X505

Crashes half way in. Looks like vido chipset not supported.

Same OS runs perfect on desktop machine.

---

### Post by BertN45 on 2011-11-06
Xubuntu 11.10
Dell CSx H500XT (PIII)
Sound chip Neomagic 256ZX (snd_nm256 driver) has a loud clicking sound during any usage.
Driver problem since 2005. Xubuntu itself runs very well in 384MB.

---

### Post by yzi on 2011-11-13
Os - Ubuntu 11.10 
Laptop - hp dm1

Problems:

1) Touchpad: Touchpad not fully compatible 

2) VGA connector: Plugging in external display or projector freezes the computer. However plugging them in when computer is switched off gives no problems.

3) Slow shutdown: shutdown times increase drastically when tomboy is running in the background (bug reported)

Minor issues:

4) Wifi and Mute diodes: wifi diode turns white on startup (which means it is active) and there is no way to disable it on startup. Mute diode activates when earphones are plugged in (probably the diode is linked with main speakers)

5) Computer stutters a lot when multitasking. 

6) Screen brightness fluctuates by small margin sometimes

---

### Post by Aditya Telang on 2011-11-17
Compaq Presario CQ61-420TU.
Does not recognize integrated graphics processor.
No driver support for Ubuntu by service provider.

:-({|=

---

### Post by audiomagnate on 2011-11-17
HP Pavillion dv9910US

Ubuntu 11.1

1. About 50% of the time the sound card is not recognized
2. Full screen video gives a blank white screen
3. Windows larger than about 4 inches by four inches become blank

---

### Post by vikos on 2011-11-18
Lenovo S205
[LIST]
[*]ACPI problems (Suspend, Restart), due to uEFI boot. It works with Win 7 64bit EFI image (Wubi install)!
[*]SD Card reader doesn't work
[*]Wireless (RT3090) works with Kernel 2.6.38+ (suspend problem), But doesn't work with Kernel 3+

[/LIST]

---

### Post by maxenzo2 on 2011-11-21
The laptop HP DV7-4040sp.
ubuntu has imcompatibility with the trackpad(it doesnt work properly at all),and the screen brightness goes down at every boot,besides is at max on the ubuntu 11.10 and the only way to turn it up is on the keyboard,and any hp laptop that at least uses this kind of trackpad doesnt work at all,i stopped using ubuntu(or any other linux distro) since last year i bought the laptop because of this 2 issues.But the rest of the hardware works well.Already after 3 distros and still no fix for both issues.

---

### Post by R3Porter_FX on 2011-11-22
1)Ubuntu 11.10
2)HP
3)Pavilion DV6-2190us
4)Issue:
        
       - Screen Brightness not Work
       - SD Card Reader doesn't Work
       - Headphone Jack not Working
       - Wireless Navigation LED is always Red(off) but Really is on at Works
- Internal Speakers not Disabled by headphones
- Connector in Sound Setting [OUTPUT TAB], is Just Analog Speaker and not show Analog Output


= = = = =
*Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6.*

---

### Post by r2dan on 2011-12-02
> **dwitkin said:**
> 1)Version Of Ubuntu: **Ubuntu 10.10**
2)Laptop Maker: **Sony**
3)Laptop Model: Vaio VGN-FW270J
4)Known Issue: laptop will not recover from suspend and hibernate.  Instead, laptop reboots (i.e., Sony screen appears, GRUB appears, etc.)

The system uses an Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07).

I've tried some troubleshooting using the thread here:
[http://ubuntuforums.org/showthread.php?t=1144999](http://ubuntuforums.org/showthread.php?t=1144999).  I haven't gotten all the way through it, but no luck so far.

I've also tried this, but no luck:
[http://www.baudlabs.com/archives/1287](http://www.baudlabs.com/archives/1287)

I'd appreciate any suggestions.

On my VAIO FW290 and Ubuntu version 11.10 with Gnome 3.2 shell there was the same problem with hibernation/suspend. What fixed the issue for me was:

1. Edit /etc/default/grub (as SU)
2. Find the line containing :
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
[/INDENT]3. Change this to the following:
[INDENT]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_sleep=nonvs"
[/INDENT]4. Then update GRUB configuration:
[INDENT]sudo update-grub

[/INDENT] 5. Reboot and try to suspend.

---

### Post by maghajan on 2011-12-10
I just bought a Dell E5520 with the i7 processor. Tried installing Ubuntu 11.10 amd64 using a flash drive as well as a CD, neither worked. Screen turns black with flashing cursor soon after the POST messages. Would be happy to list more hardware in this system if necessary.

---

### Post by stevets32 on 2011-12-14
Ubuntu 11.10
HP Mini
1030NR
Video HW: Intel 82945GM

Issue with System Info reporting "unknown" graphics device although Unity runs fairly well except for a few applications that do not resize (K) and the left side of the screen is in the middle of the screen, wraps around the right side back to the left during *nix shutdown system messages.  Not an upgrade...10.04 netbook remix completely removed and fresh 11.10 install done.

---

### Post by GnuHouse on 2011-12-19
1)Version Of Ubuntu - Ubuntu 11.10
2)Laptop Maker - Lenovo
3)Laptop Model - T61
4)Known Issue - After installing 11.10, trackpad (and related buttons) no longer works.  The pointing device on the keyboard still works, but trackpad doesn't

---

### Post by dlawrence10 on 2011-12-27
I have a Compal el80 machine (2007) running Ubuntu 11.10. It has an nVidia Geforce Go 7xxx graphics card. 

I upgraded a few days ago from 10.04 (which worked very well) to 11.10 (in increments, of course). There are major issues:
1) The laptop does not go to standby according to the power settings that I've set. It just runs constantly. Since these processors run very hot anyway, this is bad.
2) the battery is not charging, even though the power indicator in the menu bar reports that it is fully charged. 
3) the OS does not autodetect my display. It just reports as "Unknown" and apparently uses a generic driver.

While I like some of the features provided by 11.10, I' prepared to re-install back to 10.10 to resolve these issues. Has anyone had any success in running an el80 with 11.10?

Thanks

---

### Post by missingno on 2011-12-28
Lenovo IdeaPad Y570 - [Can't get the Nvidia GT 555m recognized, alternate Intel HD Graphics 3000 has lots of bugs making several games unplayable.](http://ubuntuforums.org/showthread.php?t=1900729) If anyone knows what's up with why the Nvidia chipset isn't working or at least knows a better driver solution for the Intel one, please help!

---

### Post by dako300 on 2011-12-29
IBM Thinkpad 600
ubuntu 11.10
Wont Install >:(

---

### Post by brion@cbkidder.com on 2011-12-29
Ubuntu version 11.10 (both 32-bit and 64-bit failed)
new Acer laptop 
Aspire 5250-0468 (part number LX.RJY02.080)

Issues:
1) pointer locks up at log-in screen or when typing the log in password. This happens using either the touchpad or an external USB mouse. Only remedy is reboot until can successfully log in.
2) wireless networking not available or intermittent

12/30/11 update - I can boot with wired network connection, but not with wireless. Version 10.04 is worse because although it doesn't crash, it doesn't have any network connectivity at all, wired or wireless. Ubuntu is useless on this machine.

---

### Post by neostar123 on 2011-12-31
1)Version Of Ubuntu: Maveric 10.10
2)Laptop Maker: Acer
3)Laptop Model: Aspire 5745
4)Known Issue: Battery Issue

Laptop battery not detected in Ubuntu 10.10..All the time it shows battery is full and suspend the session automatically when battery is discharged..And also Optical drive eject button doesn't work..

---

### Post by por7 on 2011-12-31
I have a laptop dell 1220.
my cdrom have a problem, i want to know how to install ubuntu from pendrive...

---

### Post by BC59 on 2011-12-31
1) I tried Ubuntu latest versions 10.10, 11.04, 11.10 all 64bits
2) HP 
3) Touchpad TM2
4) Known issue: Touchpad not working, the touchscreen cannot rotate and stays black until to close-open the lid.

---

### Post by frozenjake on 2012-01-01
1)Version Of Ubuntu: 10.04 (Tried 10.10 & 11.10, could not install)
2)Laptop Maker: MSI
3)Laptop Model: Whitebook 1761-ID1 Barebone w/Core i7 2720QM, 8GB Corsair PC3 10600 & Corsair Nova II 60GB NAND SATA drive

4)Known Issue: Wireless (Intel Centrino N130), soft-keys on laptop dashboard (CD eject)

Soft keys are no big deal, but the wireless issues are driving me nuts! What I *think* is my wireless card is listed as UNCLAIMED by LSHW, and although the latest kernel claims to support iwlagn, I will be darned if I can get it to work. Tried the MAC802.11/linuxwireless solution, and it can't get it to work either (fails on modprobe).

---

### Post by gabak on 2012-01-01
i found that linux mandriva 12 works well when ubuntu does nt work with the sound


> **corrytonapple said:**
> I have a Toshiba L455 with Ubuntu 10.04. The fan control with Ubuntu doesn't work, and none of the Function keys work. Now, I can not hear sound and my microphone will not work. Considering other options now.......
Oh well.

---

### Post by Kanehekili on 2012-01-02
Ubuntu/Xubuntu 11.10
Hardware: Toshiba Satellite 1130 with Intel 855GM GPU
Problem: graphic card
Can only be installed or run with "acpi=off". Otherwise installation or boot gets stuck with a black screen.  It looks like that the VESA driver is used. No dual monitor possible. The Laptop is very slow. 
The same installation (on an usb stick) works without problems on a Thinkpad R50e, which has the same GPU

---

### Post by rupert on 2012-01-04
1)Ubuntu 11.10
2)DELL
3)Latitude 5520
4)when ACPI is enabled the machine crashes at boot, acpi=off solves problem, but who wants to disable that on a notebook?

---

### Post by HeroOfCanton on 2012-01-05
1) Kubuntu 11.10
2) Gateway
3) M6752

Issue: KDE crashes constantly giving very generic program errors, updates hard lock system, and bug reporter crashes so proper reporting is impossible. Tried several installs.

Note: Adding ubuntu 11.10 and xubuntu 11.10 in the compatible list.

---

### Post by GTMoraes on 2012-01-06
HP Dm1
Ubuntu 11.10 Oneiric Ocelot

- Touchpad doesn't work out-of-the-box (That crappy HP's finger-detection-single-button touchpad). Needs to add a PPA which contains a synaptic fix for this, and still works badly
- Doesn't sleep, enters in coma. Must hold power button to restart. Sometimes Alt+PrtScr+R . E . I . S . U . B works, sometimes doesn't. There's a fix around
- Stutters a little for some reason. It's a pretty neat dual-core for this.

---

### Post by xpsunny on 2012-01-14
Ubuntu 11.10 (both x86 and x64)
Lenovo Ideapad U460 series


Issues:

1. Extremely slow wifi.
2. Cannot turn on/off ambient light sensor.
3. If ambient light sensor is turned on then the brightness fluctuates like HELL.
4. Cannot set the battery charging level.
5. Does not support Active Protection system for HDD.
6. Does not support Nvidia Switchable Graphics. 
7. Screen brightness is always RESET after restart.
8. Fan always runs at full speed. 
9. Lower battery life (when compared to Windows 7)
10. If Nvidia drivers are installed, the battery life drops further and the Laptop gets overheated.
11. If I play games with demanding graphics, the laptop starts stinking with the smell of burning plastic (this is something unacceptable!).

P.S. Avoid Ubuntu if you have Lenovo Ideapad U460 :(

---

### Post by 4muumia on 2012-01-22
- toshiba satellite c670d-11u
- lucid lynx lts (32 bit only, btw none of the later distros work)
- keyboard + mouse lock-up on login (occasional)
- no wlan
- only 4:3 video mode

workarounds:
- as mentioned, if 32bit lucid is ok > :)
- i managed to get wlan via usb, however, getting n to work is pain... b/g works right away
- amd drivers get external monitors to work in other video modes, but for laptop's own its just 4:3 :(

- cant recommend this machine, i optimistically deleted win7 recovery sections and am now wondering whether or not to order recovery disks from toshiba or just sit it out with handicapped lucid :(

---

### Post by tjhans on 2012-01-22
This is not exactly hardware, but the Samsung Recovery Solution (hold F4 while booting on most Samsung Laptops) is not compatible with grub.  If you open it once, it will over write grub and the next time you try to boot up you won't get any more than a black screen and you will have to re install grub.

---

### Post by xenon53 on 2012-01-28
ASUS K53TA with APU A4 3300 and 2nd discrete AMD Radeon HD 6650 graphic card

Issue>Black screen right after the OS boots up from the live usb/cd.The gpu sends the graphics to the HDMI port,not to the laptops screen.Tried Ubuntu,Mint,OpenSuse and Fedora,always appears this problem.

---

### Post by archangel2003 on 2012-02-18
[B][SIZE=3]
1) Version Of Ubuntu --- 11.10.

2) Laptop Maker is --- Toshiba.

3) Laptop Model is --- P775-S7320 with the 64 bit  i7-2670 CPU.

4) Known Issue is that --- the headphones only work if I pull the plug 1/2 way out of the socket. 

It was working before but I see posts referring to loss of sound after update and this might also be my problem.

It has and still does work fine in Windows 7.

Everything else seems fine.

24 hours later

Today it is working. I don't know if it was a temporary "reboot and now it works" type of thing or what.
[/SIZE][/B]

---

### Post by Teddy5090 on 2012-02-19
[FONT=Arial]I Have A Dell Inspiron 15R M5110 With An AMD-A8 3500M APU. The Graphics Card Is An AMD Radeon HD 6620G (Mobile Graphics Card). Apparently There Is No Graphics Driver For This Card On Ubuntu, Therefore There is a Blank Screen. This Happens Every Time I Put In My Ubuntu 11.10 CD. Fedora 15 Works, Although It Says "Could Not Find A Compatible Driver For Your Graphics Card. Because Your Graphics Card Is Not Compatible Fedora Switched You To GNOME 2 As A Fallback". I Hope Ubuntu Fixes This In The Next Release. I Can't Fix It Because I Can't See What I'm Doing! I Have Not Tried Hooking Up A External Monitor. Probably Wouldn't Work Anyway. I Have Ubuntu 11.04. I Have Not Tried It Yet. Here's The Problem With That: If 11.04 Does Work, (It Uses GNOME 2 For Unity) If I Try To Upgrade From 11.04 to 11.10 I'm Back To The Same Problem, A Blank Screen. Any Reply Would Be Helpful.[/FONT]

---

### Post by ricaxe on 2012-03-19
> **frankyyyy said:**
> 1) OS: Unbuntu 11.04 LTS (automated detected AMD64 ver)
2) Make: Toshiba
3) Model: F750 (i7 2670qm 64bits)
4) Issue: Can't complete the installation. The kernel message looks no error, the final line it hangs is
[5.795250] usbhid:USB HID core driver

I also tried i386 version, and I saw crash in kernel message.
I know my laptop is quite new(released end of last month), would appreciate if someone could help on this. I really need to install Ubuntu into this laptop. Thanks a lot in advance.

i now how you resolve that problem... 

if you are using a cd u press F6 on start and use nomodeset option.. then it will start.

on usb i dont no to user option on start.

then you will have problems with video card... i have the f750-120 and worked for me 

1º install nvidia card on aditional drivers
restart
2º make all updates (then the intell hd300 will be instaled)
3º to use the nvidia card you will have to install ironhide use these link [Optimus Support - Ironhide Project - Linux Mint Community]("http://community.linuxmint.com/tutorial/view/610") 

i hope that can hellp


after these i have some problems with webcam is to dark on skype, and because ironhide is not fully done some problems will ocure.. but the system works very well... mic and every thng else works... :D

---

### Post by thietkelogo on 2012-03-20
Yes,I also have a Toshiba Satellite and both the fan and the setting up in mousepad were not working.

---

### Post by sladden on 2012-03-20
Toshiba 
Model Number. PS427A-ON152
Serial Number. 20013324J
It came with winXP. Which it can still install.
It can take Puppy by CD or from its HD.
It can not take any other linux. Even Xubuntu.

---

### Post by istinspring on 2012-04-05
HP Pavilion g6 with AMD Radeon HD 6520G + 7450M Dual GPU

Ubuntu 11.10 - black screen on boot
10.10 works fine except i can't install ati catalist
headphones won't work
webcam - fail
audio - some issues

---

### Post by jashneel on 2012-04-16
ok so i have a laptop emachine E527 i have installed  (11.10) ubuntu in it using a external monitor because when whne i booted using the live use my laptop screen goes black automatically ... but if i see very carefully i am able to see the background and my ubuntu is working fine but it too dull and black to do any thing.... i adjusted the lighting but its still the same ... it the video driver playing up ... need help pliz

---

### Post by ronchi on 2012-04-17
Unbuntu Version:  11.10
Laptop Maker:  HP
Laptop Model:  Pavilion dv7
Known Problems:  2

Problem 1:  Known problems with the proprietary driver for the ATI/AMD Radeon HD 6700M series video card.  Using that video card creates problems with the 3.x version of Gnome and late versions of KDE as well as cause the laptop to run excessively hot (with commiserate fan speed noise and power consumption).  The easiest workaround is to use Unity.  However, the dv7 has *two* video cards, an Intel card and the Radueon 6700M.  Fortunately, you can shut the Radion card down and use the Intel card exclusively, which is the better fix unless and until Radeon fixes its Linux driver.  There are instructions on the Ubuntu Forum for shutting down the Radeon card.  

Problem 2:  The touchpad will not shut off.  You can disable the touchpad in Windows by double-tapping the upper left corner of the touchpad.  An orange light will appear and (in Windows) the touchpad will be diabled.  However, upon rebooting into Linux, the orange light remains, but the touchpad is enabled.  Double-tapping the upper left corner of the touchpad does *not* disable the touchpad.  Moreover, changing the touchpad settings in Gnome or Unity (such as diabling it while typing) has no effect.  There are no BIOS settings with which you can toggle to disable the touchpad.  If you use the keyboard often, the position and sensitivity of the touchpad can cause a wide range of typing errors that are very annoying (to say the least).  The only real way to disable the touchpad is to cover it with something stiff, like plastic, wood or metal so that the touchpad cannot get a signal.

---

### Post by d750 on 2012-04-18
1. Kubuntu 12.04 Beta 2.
2. Hp laptop.
3. hp pavilion g6-1201tx.

4. "Sleep" when i close the laptop the laptop doesn't go to sleep, instead it just pretends to   go in sleep by stop reading the hard disk. I need to restart it in such circumstances as just the black screen appears.

5. "Configurable graphics card", i don't want that the AMD Radeon 6470M to work continousely during normal work, it creates heating effact and low battery performance.

6. "Brightness" can't be controlled with, there is no affect of increasing or decreasing brightness.

Any guidance would be appreciated.
Thanks in advance.

---

### Post by Phil_Munck on 2012-04-23
I didn't get a complete install of 11.10 on a HP 210 mini netbook.  Most of it seems to work (so far) except the session bar does not appear on the bottom of the screen.  I can access the shutdown menu by cycling the power switch briefly.

---

### Post by ddude93 on 2012-04-23
The pot tackles the misery.

---

### Post by fattyz on 2012-04-28
Acer Aspire 5334 Black screen of death on upgrade to any Ubuntu version beyond 10.04.  I just checked today and found a thread by another guy who said 12.04 STILL has this same problem.  I can't believe this has been going on this long.  I am missing out on a bunch of functionality I need in the later versions and am unable to upgrade.

FattyZ

---

### Post by Herman Munster on 2012-05-02
Version:  12.04LTS
Laptop:  HP Compaq nc6220
Issue:  Will not suspend according to power management settings.  Power management worked well for this unit with versions 10.04LTS and 10.10.

---

### Post by MoebusNet on 2012-05-03
Dell Latitude D800 with Nvidia Geforce4 4200 32Mb video card [NV28]

Lubuntu 12.04 installs but Nouveau driver is not compatible with video card because of xorg. Desktop background is OK, but pointer is scrambled and difficult to see. 

Nvidia 96 driver has not yet been updated for 12.04.

EDIT: downgraded to previous xorg version to use Nvidia 96 driver. Everything working so far. Needed Lubuntu for non-PAE kernel.

---

### Post by rad_sci_guy on 2012-05-04
Acer Aspire 5040

Wifi cannot be activated in Ubuntu 12.04.  Hardware switch doesn't work and rfkill ublock won't activate wifi

---

### Post by roothorick on 2012-05-04
Ubuntu 12.04
HP Pavilion tx2000

There are four buttons on the face of the screen bezel; only two actually produce usable input events, or really, any input events at all. The other two may as well not exist.

Wifi and Bluetooth are on the same chip. Disabling one will automatically disable the other. Ubuntu doesn't seem to handle this very well; you may have to play around with rfkill from time to time if you turn them on/off often.

Mute button is supposed to turn orange when audio is muted. Under Ubuntu, pressing the button will mute/unmute audio as it's supposed to but the light remains blue at all times.

---

### Post by Kreaninw on 2012-05-05
Acer Aspire 4745G. Synaptics Touchpad doesn't work, screen brightness resets to max every time I reboot.

Ubuntu 12.04 LTS

**Update :** now my Synaptics Touchpad work fine now though it's mystery solved.

---

### Post by Herman Munster on 2012-05-05
> **Herman Munster said:**
> Version:  12.04LTS
Laptop:  HP Compaq nc6220
Issue:  Will not suspend according to power management settings.  Power management worked well for this unit with versions 10.04LTS and 10.10.

Forgot to add the Synaptics touch pad rarely keeps the pointer stationary.  Again, this is a new development with 12.04LTS.

---

### Post by EarlsFurniture on 2012-05-16
1)Version Of Ubuntu = 10.04x86, 12.04x86
2)Laptop Maker = Dell
3)Laptop Model = Inspiron 700m
4)Known Issue = Older Intel graphics chipset not supported out of the box on both versions, PAE support required by 12.04

Solution:

Graphics issue -

The Inspiron 700m has an older integrated Intel 8xx chipset.  This results in a black screen after booting up - no desktop and no console.

When using the LiveCD - hit F6, ESC, then add: i915.modeset=1 then hit [enter] to boot.
To make this change permanent, you need to edit grub per here: [http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

PAE issue -

12.04 installs a PAE kernel by default.  The Inspiron 700m does not support PAE (it only has a 2GiB capacity anyway) and thus otherwise you can't install Ubuntu newer than 11.10.

Use Xubuntu, Lubuntu (which both come with the non-PAE kernel by default) or the mini.iso of Ubuntu to install the non-PAE kernel.

Instructions for using the mini.iso with download link are here: [http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html](http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html)

---

### Post by EarlsFurniture on 2012-05-16
1)Version Of Ubuntu = 10.04x86
2)Laptop Maker = Dell
3)Laptop Model = Lattitude D505
4)Known Issue = Older Intel graphics chipset not supported out of the box

Solution:

The Lattitude D505 has an older integrated Intel 8xx chipset.  This  results in a black screen after booting up - no desktop and no console.

When using the LiveCD - hit F6, ESC, then add: i915.modeset=1 then hit [enter] to boot.
To make this change permanent, you need to edit grub per here: [http://ubuntu-tutorials.com/2010/05/...up-workaround/]("http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/")

---

### Post by EarlsFurniture on 2012-05-16
1)Version Of Ubuntu = 10.04x86
2)Laptop Maker = Compaq
3)Laptop Model = Presario 1270
4)Known Issue = CPU lacks CMOV instruction

The Presario 1270 has an AMD K6 processor which lacks the CMOV instruction that is required by Ubuntu, Lubuntu, and Xubuntu.  Thus it will not install - period.  (the installer reports this and then terminates)

Perhaps older versions before 10.04 may work - none were tried.

The only tested distros to install on this machine so far have been Debian Squeeze LXDE, TinyCore, and Classic Puppy. (2.x series)  Debian Squeeze is slow, but stable.  The other two are very spry and snappy but quite buggy.

(also tried but failed were Linux Mint 10 LXDE and XFCE)

---

### Post by e450 on 2012-05-18
Hi I have ASUS 1215b AMD E450 laptop and I cant install Ubuntu, Kbuntu, Lubuntu on it. But Xbuntu works.
Problem is with grub or something like that. Systems load fine on hard drive but at end of installation crashes, so it cant properly set up boot loader. This happens on 64bit systems.
I have the same problems with Cinnamon 64-bit from Linux MINT but then I trayed Cinamon 32-bit version and it works fine.

Also on all 4 systems I cant log in wireless network at our school. 
On this page ([http://www.arnes.si/pomoc-uporabnikom/eduroam/navodila-za-povezavo/prenosni-racunalniki/linux-debian-ubuntu-mandriva.html](http://www.arnes.si/pomoc-uporabnikom/eduroam/navodila-za-povezavo/prenosni-racunalniki/linux-debian-ubuntu-mandriva.html)) are connection settings for my school but they don't work. They were working fine with older versions of Ubuntu 10.04 (I haven't  test this on 32bit version yet)

---

### Post by dpfurlani on 2012-05-20
I installed Ubuntu 12.04 on a Toshiba Satellite C675D-S7109.  Mostly works with a few quirks:

- Occasionally the keyboard and touchpad won't work on boot.  Well, the keyboard may work in the BIOS or Grub menus but once the Ubuntu login screen appears it's useless.  Forcing a reboot fixes the problem.  I tried plugging in a USB mouse one time and that worked (although the laptop's keyboard and touchpad still did not).

- It can be difficult to power down the laptop sometimes -- it wants to reboot instead of power off.  Sometimes a few iterations of forcing power off (by holding the power button for 5 seconds) is needed before it stays off.

- Suspend does not work.  Or, it appears to, but there's no way to resume.  The only remedy in the zombie-suspend state is to force power off, remove power cord and battery, and restart.  Unless the battery is removed it stays in the zombie-suspend state -- can't even get a BIOS screen.

- Hibernate sort of works.  After re-enabling it in Unity (or using pm-hibernate), the laptop will write RAM to disk and spin down the hard drive, but it won't power off the laptop.  I have been listening for the HD spin-down and forcing power off when I want to hibernate.  Upon power-up (or on lid-open) it resumes from hibernate perfectly.  Unfortunately, sometimes it wants to resume on its own immediately after the forced power-off, which defeats the purpose of hibernating!

I submitted a bug report for the suspend issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1000016](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1000016)
[https://bugzilla.kernel.org/show_bug.cgi?id=43276](https://bugzilla.kernel.org/show_bug.cgi?id=43276)

**EDIT:**
Hibernate works much better after installing the uswsusp package, which provides s2disk and wires it into the hibernate menu option.  I edited /etc/uswsusp.conf to set "shutdown method = *shutdown*" (instead of *platform*, which is the default value).  That allows the laptop to actually power down on its own.  Also, the issue where the laptop reboots instead of shutting down only happens when the laptop is plugged in.  So as long as I'm unplugged and just running on battery power, hibernate works perfectly now!

---

### Post by Scozzar on 2012-06-09
I should probably add mine to the DL...

Ubuntu 12.04
Toshiba P755-S5269
Reason:  At the dual boot screen, allowing it to automatically load Linux caused catastrophic errors.  It would hang on the purple screen (blank, by the way) for a solid ten minutes.  After that I did a hard reset (held the power button).  I turned the computer back on and hit "Enter" and it got me passed the purple screen and into a black screen where lines of code were being thrown at me.  Once again, hard reset after 10 minutes of random code.  I plug in the LiveCD to remove Ubuntu when I get "MACHINE CHECK ERROR".  So I removed the Linux partitions through Windows Disk Manager and the System Repair Disc

---

### Post by mbuell on 2012-06-25
Lenovo IBM Thinkpad T60 Type 1952
Xubuntu 12.04

This box is mostly compatible. However, the internal modem is not, and the fingerprint reader is not. The internal modem is a conexant chip on the sound card, and getting it working would be a major pain, and it would not necessarily work even after following in the footsteps of recommended paths. The workaround is to get an external modem or a pcmcia modem that will work.

---

### Post by Makcum on 2012-06-27
1)Version Of Ubuntu: 12.04
2)Laptop Maker: ACER
3)Laptop Model: Aspire One 722
4)Known Issue: wifi/bluetooth, suspend/resume, microphone.

---

### Post by Rob_H on 2012-07-02
Dell Alienware M17x R4
Kubuntu 12.04

Mostly works, but...

[LIST=1]
[*]Ships with NVIDIA Optimus-based video, which you can only get to work with [Bumblebee]("https://github.com/Bumblebee-Project/Bumblebee/wiki/FAQ") if you're willing to put up with the nonesense of launching each graphic-intensive app with a special command. No BIOS option to disable the integrated Intel video.
[*]Volume control doesn't work properly and internal speakers won't mute when you plug in headphones. This appears to be due to [bug 5596]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=5596") in ALSA's Creative CA0132 support. Maybe it will be fixed by the time you read this.
[*]DisplayLink (video over USB 3.0) doesn't work using the Targus dock that Dell recommends for it. Can't get **xrandr** to recognize it as a connected video output.
[/LIST]
Not Kubuntu's fault, but I also found the colors on the internal LCD to be washed out.

---

### Post by infimax on 2012-07-09
1) Version Of Ubuntu: 12. 04 
2) Laptop Maker: ACER 
3) Laptop Model: Aspire 5935G
4) Known Issue: no sound at all

---

### Post by dnpate on 2012-07-22
OS:  ubuntu 12.04.  also tried with mint 11 and same problem
manufacurer:  HP
Model: envy 14 with dual graphics--intel and Radon hd 6630m
Issue:  no video whatsoever even on live boot

---

### Post by wahrschein on 2012-08-17
1) Ubuntu 11.04, 11.10 & 12.04
2) Acer
3) Aspire One 725
4) Frequent WiFi dropouts and touchpad doesn't work. After installing a particular driver it responds basically, but without multitouch

---

### Post by biswajitdey on 2012-08-22
Ubuntu 12.04 32 bit
Dell Inspiron N5010

Hello,

I am facing the following issues while using Ubuntu 12.04 :-

1) Sometimes while increasing/decreasing brightness/sound using keyboard, the system hangs and there is no way I can restart the system it unless I press the power key.

2) The system doesn't restore from sleep or for that case even after once the screen turns off , nothing works , the cursor moves but can't click on anything.

I am a big fan of Ubuntu and it used to work fine with previous versions(upto 10.04) but as now I am facing these problems, I am not too comfortable using it nowadays. Please someone can explain why this is happening and is there any way that this can be fixed.

Thanks.
Biswajit Dey.

---

### Post by llanitedave on 2012-08-23
Toshiba Satellite P-775 w/Optimus
12.04 Unity

Hard Freeze at random intervals -- everything stops, including the clock.  I have to hold down the power button until it reboots, losing whatever I was working on.

Also, multiple desktops fails in odd ways, sometimes losing the ability to switch completely, other times causing applications to disappear.

I'm getting a bit discouraged...

---

### Post by stefan231 on 2012-09-01
OS: Ubuntu 12.04 LTS 64bit

---

### Post by Herman Munster on 2012-09-15
> **Herman Munster said:**
> Forgot to add the Synaptics touch pad rarely keeps the pointer stationary. Again, this is a new development with 12.04LTS.
 
> **Herman Munster said:**
> Version: 12.04LTS
Laptop: HP Compaq nc6220
Issue: Will not suspend according to power management settings. Power management worked well for this unit with versions 10.04LTS and 10.10.
 
Both issues were resolved with 12.04.1 LTS.

---

### Post by VaGentry on 2012-09-16
1)Version Of Ubuntu: 12.04
2)Laptop Maker: ACER
3)Laptop Model: Aspire V5 -171
4)Known Issue: Broadcomm SD card reader won't mount SD cards.  Synaptic PS/2 touch pad won't allow drag and drop.

---

### Post by varunendra on 2012-09-16
1)Version Of Ubuntu --> Ubuntu 12.04 64bit (kernel 3.2.0-29)

2)Laptop Maker --> Asus

3)Laptop Model --> X54C-261D (15.6", i3-2330, 2+2GB RAM, 500GB HDD, Wifi AR9285, Ethernet AR8151)

4)Known Issue:
Bluetooth almost never worked with Ubuntu, (while it did with Knoppix, Slax, even Lubuntu).
**Workaround:** blacklisted asus_nb_wmi, due to which, asus_wmi also stopped being loaded.
**Side-Effects:** Although the BT now works perfectly, Fn+ combination key functions for volume control, mute, and touchpad enable/disable don't work now (due to absence of asus_nb_wmi). All other Fn+ combos work as usual.

Apart from this, the laptop is working great with 12.04, no additional tuning required. (oh, except that it sometimes fails to bring back the desktop after resuming from sleep, tty1 to 6 work though - a common issue I guess :))

---

### Post by morhin on 2012-09-18
Version 12.04
Acer
5250-BZ467
Won't load livecd.... stuck at the dots screen.

---

### Post by museic71 on 2012-09-24
1) Desktop 12.04
2) HP
3) Pavilion DV8000

known bugs :

- Frequent freezes.
- Wifi driver issue after updtate, can't connect to secured wifi. Won't ask the security key.
- Desktop issues, such as sidebar not loading properly or taskbar invisible/black.

- And last but not least, because of the freezes, hard reset has to be done which is known to be a source of problems with the Pavilion DV*000 serie. It may damage the motherboard, RAM and CPU. It may as well even prevent you from booting your laptop due to residual power to RAM and/of motherboard. (which is my case, I'm currently struggling to boot my computer)

](*,)

---

### Post by sclaes on 2012-09-24
The trackpoint pointing device (Lenovo Thinkpad L430) doesn't work with Ubuntu 12.04. :-(

---

### Post by mioimnida02 on 2012-09-27
1)Version Of Ubuntu: Precise 12.04 
2)Laptop Maker: Samsung
3)Laptop Model: Samsung N102-B05
4)Known Issue: Intel GMA 
Intel VESA is recognized instead Intel GMA 360. Resolution was fixed at 800x600 pixels.

---

### Post by ralphd11 on 2012-09-29
I have a eMachine em250 netbook and trying to get Lubuntu 12.04 wireless to work because of power.     
What's funny is that Ubuntu works fine on my machine.  I removed the hard drive and installed it in my wife's em250 and it works fine.  I must have a different chipset.  I tried to install Broadcom b43 but it says to install another but I cant remember which one...it doesn't work.  Here is another net mystery...when I plug in a cable browsers cant access the internet.  I can go to other computers on my home net.  The software center works though.  I am able to update and to download other browsers.  Any ideas?

---

### Post by ep66 on 2012-10-24
**[Disregard, memtest revealed millions of mem errors, warranty service it is **
[https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1070656](https://bugs.launchpad.net/xserver-xorg-video-intel/+bug/1070656)

---

### Post by npr77 on 2012-10-25
1)Version Of Ubuntu
 12.10 64bit

2)Laptop Maker
Dell

3)Laptop Model
XPS 14 Ultrabook

4)Known Issue
Heats up in about 30min, fans going crazy. Reason unknown. Cpu load average: 1,18, 1,74, 1,55

---

### Post by alainhenry on 2012-11-04
Laptop: Compaq / HP 6820s

Ubuntu 12.04 LTS works, but not 12.10 (32 bits) with Kernel 3.5.0-17-generic

However, install (upgrading from 12.04) works, and choosing kernel 3.2.0-32-generic from the GRUB boot menu makes 12.10 run on this laptop.

---

### Post by TDK800 on 2012-11-06
1)Ubuntu 12.10
2)Dell
3)Inspiron N5050
4) Booting up hangs on the loading screen with ubuntu logo with new kernels 3.5.0-17-generic and 3.5.0-18-generic, works with kernel 3.2.0-32-generic.
The newer kernels work with a Dell Vostro.

---

### Post by Carlos Araujo on 2012-11-06
1)Ubuntu 12.10
2)Dell
3)Inspiron 5423
4) Booting (UEFI with Windows Seven)
5. AMD/Intel Hybrid Graphics Don't Work

---

### Post by Carlos Araujo on 2012-11-07
remember the reasons not to buy equipment AMD / ATI. NEVER!

---

### Post by omjaijagdish on 2012-11-24
1)Version Of Ubuntu: Ubuntu 11.04 
2)Laptop Maker: Dell
3)Laptop Model: Inspiron 14R (N5010)
4)Laptop Battery Model: DELL W7H3N08
5)Technology: Lithium Ion
6)Known Issue: laptop battery back-up reduced from 2.5 hrs to 1 hr

---

### Post by ziqiang on 2012-11-28
Hi,my laptop is:
[DELL XPS L501x]("http://www.akkus-adapter.com/dell-xps-l501x.html"),Vermeiden Sie, dass Ihr Notebook unnotig die ganze Nacht am Ladegerat hangt. Ist der Akku DELL XPS L501x voll und Sie benutzen das Laptop nicht Dann entkoppeln Sie das Ladegerat/Netzteil und schalten Sie das Laptop aus. Das ist nicht so wichtig, um ein "uberladen" zu vermeiden - dagegen sind die meisten Akku DELL XPS L501x geschutzt-sondern viel mehr um ubermabige Hitze zu vermeiden.:P

---

### Post by axy_david on 2012-12-04
1)Version Of Ubuntu: Ubuntu 12.04 
2)Laptop Maker: Acer
3)Laptop Model: 5742G
6)Known Issue: it has Optimus.

---

### Post by uyulala on 2012-12-07
1)Version Of Ubuntu
12.10 amd64
2)Laptop Maker
ASUS
3)Laptop Model
ASUS ZENBOOK U500VZ 15.6" Full HD IPS
GT650, i7-3612QM, 8GB, 2x128GB SSD, WIN8

4)Known Issues

- Optimus Graphics card - not well supported in Linux yet. Well known problem (google it).
- Raid disks not supported. 2 SSD 128GB in FakeRAID RAID0 - not supported. Gets a I/O error from the Ubuntu Installer when copying files. Possible to turn off RAID in BIOS, but will then get  performance hit, and ruinexisting Windows 8 installation. Did not try this.
- HDMI not working out-of-the-box when runngin Live USB 

Besides this, I think the fan noise was somewhat annoying (constant, kind of high-pitched noise)

I send the ASUS back to the store, and got a SAMSUNG 900X4C instead.

---

### Post by csathya94 on 2012-12-22
i bought a laptop from "http://www.thevaluestore.in/supershop/Computers-Laptops/Laptops/HP-4430s-B2X48PA-Core-i5-2450-2.5Ghz-ProBook-14.0-Inch". This is an generation Core i5-3210M - 2.5 GHz TB upto 3.1GHz / 3MB L3 Cache, 6 GBDDR3 RAM ,750 GB HDD ... 14" LED Backlit ..... Stunning Looks - 11.6" LED HP BrightView HD Display- Light Weight, Just One-Inch Thin & Easy to carry 3.Upto 9.5om

---

### Post by mbuell on 2012-12-31
Toshiba Tecra M11
Ubuntu 12.04, Unity

The nouveau open-source nvidia drivers don't work properly. The nvidia drivers got broken by Unity. But, it seems other desktops (xfce) for 12.04 also won't work right for this nvidia graphics machine. This is a machine that worked like a champ for 10.04. [In 10.04 I had a wifi prob, but that turned out to be the network manager. Uninstalled that, installed wicd, and all was good.]

Outside of graphics issues, what worked in 10.04 seems to work in 12.04. But problem vid is enough to cancel my subscription, know what I mean? I can get 2-D to work, but still with multi-monitor setup issues. Too much work!

---

### Post by Mijuca on 2013-01-04
1. Ubuntu 12.04
2. Toshiba
3. Toshiba Satellite L850-18T 
4.  I recently bought notebook Toshiba Satellite l850-18t  - [SPECS]("http://bl.computers.toshiba-europe.com/innovation/jsp/supportMyProduct.do?service=BL&LNG=32&userAction=SMP_RESULTS_PAGE&partNumber=PSKDNE-00R00RY4&serialNumber=&USER_ACTION=Serial%20number#tab0;") and i have problem with 2 usb ports, i think with 2 usb 3.0 porst on the left side and with drivers for my ati radeon 7670m.

1. Only 1 usb port works, and other 2 on the left side dont work neither  with 2.0 or 3.0 usb drives... When i plug-in usb nothing happen...

2. I cant find drivers for my graphic card and linux finds some for ati radeon 6*** older version... 


please help me :smile:

---

### Post by lekevinio on 2013-02-02
1)Version Of Ubuntu 	12.10
2)Laptop Maker		Asus
3)Laptop Model		N53SV
4)Known Issue		There is no way to properly install the geforce gt450m drivers. After installing it in many ways the resolution is back to 800 x 600 and the only way to restore is is to uninstall the drivers and restore the original ubuntu drivers

---

### Post by psychok9 on 2013-02-04
1)Ubuntu 12.04.1 LTS
2)Sony
3)Vaio E series with AMD HD 7650M
4)Video doesn't works

---

### Post by gimchicoffee on 2013-02-07
1. ubuntu 11.10
2. toshiba
3. Satellite L655D
4. the touchpad never worked and haven't been able to get it to. the radeon 4200 graphics card is a serious problem, at its best its okay, at worst i have to do a reinstall of ubuntu. also it generally seems to run hot and noisy.

---

### Post by chahar on 2013-02-14
I have a Toshiba Satellite 1135 and neither the fan nor the built in mousepad are working.

---

### Post by Draugrs on 2013-02-16
1) Version Of Ubuntu 12.04 to recent
2) Laptop Maker Dell
3) Laptop Model XPS M1730
4) Known Issue Install from bootable CD/DVD/USB only provides a rotating screen of solid colors (ie green, blue, red, white, etc).  I have tried every post providing help for this model without success.  

I did find others had success with other versions of Linux such as Fedora so I will give some others a go and report back.  I really wish I could have had Ubuntu work on the laptop.

---

### Post by khatkarrohit on 2013-02-16
This laptop HP Pavilion g6-2313AX is completely incompatible with Ubuntu whereas it works nice even with windows 8 default installation. Here are its spces: 
**Hardware**
Product Name:	                    **g6-2313ax**
Microprocessor:	                    **2.3 GHz AMD Quad-Core A10-4600M**
Microprocessor Cache:	            **4 MB L2 cache**
Memory:	                            **6 GB 1600 MHz DDR3**
Video Graphics:	                    **AMD Radeon HD 7660G/7670M Dual GPU (2 GB DDR3 dedicated)**
Display:	                    **15.6" diagonal HD BrightView LED-backlit (1366 x 768)**
Hard Drive:	                    **1 TB 5400 rpm SATA**
Wireless Connectivity:	            **Bluetooth, 802.11b/g/n**
Keyboard:	                    **Full-size island-style keyboard**
Pointing Device	                    **TouchPad supporting multi-touch gestures and on/off button**
PC Card Slots:	                    **Multi-format digital media card reader for secure digital cards & multimedia cards**
Operating System:                   **FreeDOS**

OS installed: **Dual boot. Windows 8 64 bit and Ubuntu 12.10 64 bit**

[B]Starting with processor:2.3 GHz AMD Quad-Core A10-4600M
[/B]Processor always run on full power/speed while on Windows 8 processor remains silent and make even less noise while running heavy programs on Windows 8. On Ubuntu even if I open Software Sources than the processor goes wild and whole system goes slow and other application stops responding.

**Video Graphics:AMD Radeon HD 7660G/7670M Dual GPU (2 GB DDR3 dedicated)**:
Ubuntu System Details says unknown Graphics. It does not detect 7670M Graphics card.After installing ATI drivers from Software Center it gives option to use Open source driver or proprietary driver. After selecting proprietary driver GUI desktop does not boot. After removing fglrx from command line desktop again starts working after reboot.


**Display:15.6" diagonal HD BrightView LED-backlit (1366 x 768)**:
Brightness does not work at all. There is tweak to add few words in grup file. But that works only if upgraded kernel like 3.7.8 is installed.

**Wireless Connectivity:Bluetooth, 802.11b/g/n**
Neither wireless nor Bluetooth works with ubuntu. Wireless works with Ralink RT3290 firmware but only with upgraded Linux kernel to 3.7.8. Even after few minutes wifi stopped working and it says device not ready. Bluetooth never worked.

**Keyboard:Full-size island-style keyboard**
Keyboard works works fine except the wifi on/off button light indicator. But it is able to turn off and on the external wifi dongle. Brightness key works but brightness does not change on the screen.

**Pointing Device:TouchPad supporting multi-touch gestures and on/off button**
It works but TouchPad on.off button does not work.

Don't know about Card reader, HDMI output and other things. Very bad laptop. Waiting for the new release of Ubuntu 13.04 otherwise have to switch back to windows for this laptop to work for me. :-(
My desktop and other laptop with Intel board and processor without grapic card is running smooth from the day I bought them and nothing is supported on  AMD laptop from HP .Will never buy AMD again.

---

### Post by aratina_race on 2013-02-17
1. 12.10 64
2. Toshiba
3. Satellite L855-149
4. Standard graphics drivers are OK but a reboot is required after playing some full screen games. ATI driver cause the laptop to reboot into terminal mode. I have to purge fglrx to get back to unity.

---

### Post by aratina_race on 2013-02-17
1. 12.04 64
2. Toshiba
3. L855-149
4. trying to downgrade to LTS version from 12.10. I've tried booting from CD and USB but I get nothing after grub. CD and USB work fine in my desktop.

any suggestions will be gratefully received. 
thanks

---

### Post by LinuxFanBoi on 2013-02-20
ASUS R500A...

I complete and total fail...  UEFI seems to be the culprit.

= = = 
EDIT: As can be seen in [http://ubuntuforums.org/showthread.php?t=2119033](http://ubuntuforums.org/showthread.php?t=2119033) the complete and total fail was using a 32 bit ISO. The 64 bit seems to install without problems. / Mörgæs

---

### Post by evtux on 2013-03-04
> **mioimnida02 said:**
> 1)Version Of Ubuntu: Precise 12.04 
2)Laptop Maker: Samsung
3)Laptop Model: Samsung N102-B05
4)Known Issue: Intel GMA 
Intel VESA is recognized instead Intel GMA 360. Resolution was fixed at 800x600 pixels.


Netrunner 12.12.1 installs fine on N102s-B04.  Correct resolution. All other functions work.  The KDE effects, however always defaults to XRender, yet is stable.

The other distros tried, Kubuntu 12.10-64, Mint 14-64 Live CDs didn't boot.

---

### Post by susicox143 on 2013-03-18
Hi,

I have HP 1000 -  i3-2370M notebook. I tried to install ubuntu 12.04 and  12.10 but non of them gets installed. I have some success with 13.04  beta version. 

Actually when i try to boot from Ubuntu, it starts but after few second  screen become black and nothing happens. Then i tried with External LCD  then i was able to see ubuntu and it helped me to install Ubuntu. Once i  installed Both Laptop LCD and External LCD show me desktop and i can  work fine but when i remove external LCD and reboot Notebook then again  it stuck on Black Screen even ubuntu is installed and if again i add  external LCD then i can work on ubuntu.. But this process only work with  13.04 beta. 12.04 or 12.10. Does not work in any way. I tested 64 bit  ubuntu. 

If have window 7 and tried to install ubuntu then i download ubuntu but  when it extract then it give some error and install does not install  anything. 

Please look into this laptop and try to add in upcoming ubuntu 13.04. So i can use ubuntu. 
Here is HP 1000 Notebook Specification:

[B]HP 1000 Specifications:

[LIST]
[*]Intel® Core™ i3-2370M Processor (2.4 GHz, 3MB L3 Cache)
[*]Intel® HM75 Express Chipset
[*]Intel® HD Graphics 3000
[*]14.0-inch diagonal HD Bright View LED-Display (1366 x 768)
[*]2GB DDR3 System Memory
[*]HP 500GB 5400RPM Hard Disk Drive
[*]HP SuperMulti DVD Writer
[*]Integrated 10/100BASE-T Ethernet LAN 802.11b/g/n WLAN
[*]3 USB 2.0, HDMI, RJ-45, Headphone out, Microphone in HP 720p High Definition Webcam with integrated microphone
[*]Altec Lansing Internal Speakers
[*]6-Cell Lithium-Ion Battery
[*]HP 65W AC Adapter with Power Cable
[*]Notebook keyboard with Touchpad supporting Multi-Touch
[/LIST]

[/B]
I will wait for positive feedback from ubuntu officials.

---

### Post by tancrackers on 2013-03-21
HP Envy 15 (2nd gen) 3040nr:
I would say anything HP Envy of all 3 gens will have the same issues.
I've tried Ubuntu 12.04, Ubuntu 12.10, Arch, Opensuse 12.2, Fedora 17, Linux Mint 13, and so on.
The touchpad (synaptics clickpad) completely lacks functionality. If you keep a finger on the lower part, for eg, and try dragging to move the mouse this cannot be done. There isn't true multitouch. This makes the touchpad completely unsuable. It's extremely awkward.
Hybrid graphics is absolutely horrendous on Linux.
Beats audio on any device creates HUGE issues. The laptop will lock up for like 10 minutes after boot. This needs to be addressed. This really makes the laptop unusable.
Finally, the backlight does not automatically brighten at boot. It stays dim.
I notified the synaptics upstream developers, and they said that there's nothing that they can do.

---

### Post by roly33 on 2013-03-22
Toshiba Satellite C660-15
Ubuntu 13.04

As far as I can tell everything works fine, apparently the Battery can only charge to 30% Capacity, but other than that everything is fine.  Can't install intel Graphics driver Installer on 13.04, but was unable to install the intel drivers on 12.10 only the installer would install.

Roland

---

### Post by Feathers McGraw on 2013-04-15
1. Ubuntu 12.04 LTS
2. HP
3. Pavilion DV6 3122-SA
4. Open source graphics driver for ATI Mobility Radeon 5470 causes laptop to overheat, proprietary driver is incompatible with GNOME for some reason so the desktop won't appear when it is enabled. KDE & Proprietary driver combination works fine (i.e. install Kubuntu, then install proprietary driver :P)

Feathers

= = = = =
*Mörgæs 2014-10-13: Later releases (14.04 and newer) are more suitable for the dv6, especially when using the radeon.dpm=1 boot option: *
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by gmqqueen on 2013-04-17
OS Ver: 12.04/12.10/13.04 Ubuntu Desktop/Server/Studio/Gnome
Maker: Sony
Model: VIAO VPCZ1 [vpcz11cgx/x]
Issue: Dual Graphics-Card & SD/MS Slots

Defaults to the integrated graphics card, additional driver application can see the stand-alone nvidia driver but bugs when install'd, tried switching hardware switch between all 3 settings (stamina (aka integrated), speed (aka stand alone nvidia), and auto with no difference.) 

SD + Memory Stick slots do not show in any of the distro's or additional driver application.

Thanx

---

### Post by alainhenry on 2013-05-02
Ubuntu 12.10 / 13.04
HP 6820s
Do not work at all, the driver fior the graphic card is not anymore supported by the Kernel, if I understand well. 12.04LTS is working.

---

### Post by dankojoffrey on 2013-05-13
[COLOR=#000000]1) Version Of Ubuntu: **12.10**[/COLOR]
[COLOR=#000000]2) Laptop Maker: **Acer**[/COLOR]
[COLOR=#000000]3) Laptop Model: **Aspire 5738ZG**[/COLOR]
[COLOR=#000000]4) Known Issue: Ati Radeon HD 4570 proprietary driver doesn't work at all, only opensource, battery life 45min - 1h, overheating.[/COLOR]

---

### Post by whoever30 on 2013-06-15
13.04
acer
aspire e1
**[COLOR=#ff0000]TOUCHPAD [/COLOR]****[COLOR=#ff0000]DISABLED BY[/COLOR]** **[COLOR=#ff0000]DEFAU[/COLOR]****[COLOR=#ff0000]LT[/COLOR]** (and of course NOBODY helps)

---

### Post by Shahrukh36 on 2013-06-30
1) Version Of Ubuntu: Ubuntu 13.04 x64
2) Laptop Maker: HP
3) Laptop Model: Pavilion dv6-6113tx
4) Known Issue: Validity fingerprint reader does not work.


*Added my Mörgæs: Would be better to post this in Compatibility List, as it's only a minor problem. *

---

### Post by Xtyn on 2013-07-13
1. Ubuntu 13.04
2. Samsung
3. XE303C12 (ARM Chromebook)

Lots of problems, most of them solvable. The really big problems are some random freezes and kernel panics and lack of graphics acceleration. After plenty of tweaking it is usable, but barely. Some software is missing from the ARM repo, like Stellarium, which wouldn't work anyway, or it would be unbearably slow.

Anyway, the point is: if you want to run Ubuntu on this thing, you can expect to have plenty of work. It's a pity, as the hardware is awesome, it has a lot of potential, but the software is lame.

---

### Post by josvanr on 2013-07-13
hp envy 17 2110ed 
ubuntu 12.x 13.x

I've never spent so much time on getting basic things to work

* trouble booting
* trouble with suspend to ram
* overheating
* function keys dont work
* jumpy touchpad, almost enough so to just throw the thing out of the window and buy a samsung with windows 8

The booting/suspend/overheating problems stem from discrete graphics and trying to switch them off with vgaswitcheroo. If I turn off discrete graphics with vgaswitcheroo, there is no overheating. (though there is 'heating') But then suspend to ram doesnt work. (lock up)

Touchpad I partly fixed with xinput, but not entirely satisfactory

I use my own script for function keys for modifying screen brightness

the laptop looks very cool though.

Is linux ready for the desktop? Not if you have a laptop on your desktop. 

josvanr

---

### Post by josvanr on 2013-07-19
if you have a hp envy 17 and you want to do yourself a favor just smash it with a sledge hammer

---

### Post by mujjingun on 2013-08-11
1) Version Of Ubuntu = 12.04
2) Laptop Maker = HP
3) Laptop Model = HP Pavilion g6
4) Known Issue = WLAN not working, cpu overheating very quickly over 90C, graphics driver problem.

---

### Post by badr2 on 2013-08-16
1) Version Of Ubuntu: Ubuntu 13.04 x64
2) Laptop Maker: Toshiba 
3) Laptop Model: Satellite U500 - 18Q
4) Known Issue: The fan doesn't work as it should be, and the laptop got hot as hell. I need a solution for it :(:(

---

### Post by Linuxisfast on 2013-09-06
> **badr2 said:**
> 1) Version Of Ubuntu: Ubuntu 13.04 x64
2) Laptop Maker: Toshiba 
3) Laptop Model: Satellite U500 - 18Q
4) Known Issue: The fan doesn't work as it should be, and the laptop got hot as hell. I need a solution for it :(:(

Have you installed the proprietary hardware drivers?

---

### Post by rimez on 2013-10-05
[LIST=1]
[*]Ubuntu 13.10
[*]Lenovo
[*]Ideapad U430p
[*]Known Issues:
[LIST=1]
[*]WiFi drops often (with tons of output in syslog)
[LIST=1]
[*]Requires 3.11 kernel are newer to work at all - will not work with older kernels
[/LIST]

[*]Nvidia GT 730M GPU not accessible (though visible in lspci)
[*]Backlight turned off when booting (easily resolvable though)
[/LIST]
[/LIST]

---

### Post by Minh_Thanh_Nguyen on 2013-10-22
HP Elite book 8440p have setup OS [COLOR=#000000]Ubuntu ?[/COLOR]

---

### Post by pompel9 on 2013-10-22
> **Carlos Araujo said:**
> remember the reasons not to buy equipment AMD / ATI. NEVER!

I have equipement from AMD/ATI, and they work very good under ubuntu.

---

### Post by acodea on 2013-10-30
[COLOR=#000000]1) Version Of Ubuntu   12.04[/COLOR]
[COLOR=#000000]2) Laptop Maker          HP[/COLOR]
[COLOR=#000000]3) Laptop Model          G50-133us[/COLOR]
[COLOR=#000000]4) Known Issue(s) 
1. Locale (perl gives warning I hear is bogus, but it's annoying).
2. Has to be tweaked to cool it down. cpu governor
3. Installed Wubi after problems with installing it in it's own partition.
                                Can crash. If shut down using the "off" button often, "fsck" is started because it's told by Ubuntu,                                 you're having detected problems.[/COLOR][COLOR=#000000] Again annoying, and it could lose you your data.[/COLOR]
[COLOR=#000000]4. "fsck" initializes, and you are presented with the option of waiting for a lengthy scan or having                                    a nag screen before you can finish booting(can be disabled)[/COLOR]

---

### Post by Deaj on 2013-11-17
I have an ASUS Vivobook S400CA, Intel i5-3317U quad-core 1.7GHz CPU, 8GB RAM (upgraded from factory 4GB), 24GB SSD / 500 HDD hybrid drive, Intel integrated HD 4000 graphics w/ HDMI output,  Motorola WiFi a,b,g,n / Bluetooth 4.0 combo wireless card (upgraded from factory WiFi only card), Atheros Ethernet, USB 2.0 & 3.0, Realtek? sound, 14" 1366x768 touchscreen.

OS: Ubuntu 13.10 w/ Cinnamon GUI (ver. 2.0x if I recall correctly - typing this from my Android phone and my laptop isn't here). 

Note: I'm not currently using the SSD for anything. HDD performance has been quite good (using the SSD to cache the HDD would provide negligible gains IMO), the Swap is used only during suspend and it wakes up almost instantly (using the SSD would provide negligible gains here as well). The SSD will come n handy should I decide to set up a dual boot with Windows in the future. 

PROS:
Installation was glass smooth and drivers were provided for all hardware with only a couple tiny glitches. Performance is quick / snappy (as quick as or faster than the prior Windows 8 and 7 installations. This notebook is slated to replace my aging field tech laptop pending confirmation that I am able to use my existing software utilities (or equivalent Linux software) to perform any/all work for which I may use a field machine. I'll also be using this notebook for personal / leisure time and I'm very pleased with Ubuntu/Cinnamon - a nice change coming from Windows (and the issues that come with it). As I support mostly Windows systems I'll be running various versions as virtual machines when necessary.  

CONS: 
Well - only one con and it's hardware related. A few of the Fn (alternate function)  key functions are not recognized. Only one of these is an issue for me -  Numlock. Which leads us to....

HARDWARE INCOMPATIBILITY:
The functions assigned to keystrokes Fn + Home,  Fn + End,  Fn + Pg Up,  and Fn + Pg Dn do not work. The only one that really affects me in any way is the Fn + Home keystroke: Numlock. Numlock is used to set a portion  of the right side of the keyboard to function as a number pad. Upon completion of the Ubuntu 13.10 install Numlock was set to 'on' by default, only after the login password was entered and login succeeded. I was unable to address this using Numlock nor by any other means. I found a rather elaborate process of turning Numlock (I won't waste space here describing how unless requested). This was too cumbersome to work with daily and many logins per day. 

Fortunately the issue with Numlock defaulting to on cleared when I installed Cinnamon. The aforementioned alt function keystrokes still don't work. 

*NOTE: All of the other Fn + keystrokes for hardware controls (screen brightness, video internal/external switch, volume up/down/mute, etc.) work just as they should.

---

### Post by martinr on 2013-11-18
1) Version Of Ubuntu: XUbuntu 12.04.3 LTS (precise)
2) Laptop Maker:       Acer
3) Laptop Model:       Aspire, AS5502ZWXMi (5500Z series)
4) Known Issue:        Non functional touch-pad causes keyboard going haywire after resuming from suspend (power management).

After resume from suspend the touch-pad can't control the pointer any more and touching the touch-pad results in phantom keyboard input (see [this thread]("http://ubuntuforums.org/showthread.php?t=2189117") for a workaround).
(The same hardware ran Ubuntu 6.04*, 8.04 and 10.04 flawlessly.)

* [SIZE=1]Version 6.04 with two tweaks: noapic, 915display patch[/SIZE]

---

### Post by luchfilip on 2014-01-22
Ubuntu 12.04
HP Envy 3040nr 2nd Generation
Known issues:
1. Radeon HD 6790M  - lack of drivers, so i am left only with the internal graphic card, intel hd4000, which is enough for anything except games.
2. Beats audio with 6 speakers and a subwoofer, HP wireless audio - great sound using alsa drivers but anything that plays sound freezes in the first 10 minutes after booting
3. wake from sleep takes about 20-30 seconds, at least it goes fast to sleep

All in all i really enjoy everything, including the sound, as it is much better the the original one from windows with beats audio.

---

### Post by 7-webmaster on 2014-03-02
I am running Ubuntu 13.10.  Although I have diligently applied every fix that comes along, and tried every combination of drivers that I have learned about, my Dell Vostro 3555 laptop is unreliable.  In particular ACPI seems to be broken, possibly as a result of bad microcode from Dell, although obviously the laptop works fine with Windoze 7.  This particular model differs from most of the other Vostro 3500s in that it has an AMD microprocessor and consequently ATI graphics.  I have tried running it with both the closed driver from AMD and the open X driver.  With the open driver the laptop NEVER resumes from suspend.  With the closed driver it resumes about 75% of the time.  25% of the time the screen remains black when the lid is opened, and the only solution is to reboot.  Also frequently the system does not suspend when the lid is closed.

---

### Post by John_Dave_Balingit on 2014-03-05
1. Ubuntu 13.10
2. Acer
3. Acer Aspire V5-471G
4. Set graphics driver from NVIDIA GEFORCE 710M into its Graphics Processor

---

### Post by dcrooke on 2014-04-20
Nvidia FX 880M video card (e.g. NVIDIA Corporation GT216GLM [Quadro FX 880M] (rev a2))
Used in ThinkPad W510, some Asus laptops
Ubuntu 13.10, Nvidia driver v 319

This card is not well supported by the Nvidia drivers. It runs at a barely usable speed with the desktop, and video is out of the question. Applications that use the X display leak lots of CPU in user space.

---

### Post by chris_504 on 2014-04-23
1. Ubuntu 14.04 and 13.10
2. HP
3. HP Pavilion TouchSmart 15-n007tx
4. It fails to load. Period. In 13.10 it would begin loading and just freeze at a black screen with no info on it. In 14.04 I can hear the sound that it makes when it is on the desktop, but the screen is black. My best guess is it has some problem with the dual graphics display. Also, I'm running the latest firmware, which is F.62(release notes say compatiblity for ubuntu) as of now & i have also tried loading with UEFI turned off & on with no difference :(

---

### Post by cdeboden on 2014-04-29
[COLOR=#000000]1) Version Of Ubuntu: EDIT: All variants[/COLOR]
[COLOR=#000000]2) Laptop Maker: Medion[/COLOR]
[COLOR=#000000]3) Laptop Model: p8614[/COLOR]
[COLOR=#000000]4) Known Issue(s): [/COLOR]
Bad supported VGA and HDMI output
[I](VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV730/M96 [Mobility Radeon HD 4650/5165])
[/I]
14.04:
Computer will not boot with connected HDMI and/or VGA, pc freezes completely
Computer crashed completely when HDMI-cable was plugged in on a running desktop.

13.10(also Xubuntu 13.11):
No HDMI audio
EDIT: System freezes/crashes completely.

12.04 
EDIT: No HDMI audio
System freezes/crashes completely.

EDIT: All Ubuntu variants on this laptop: 'Kernel panic - Not Syncing: Fatal exception in interrupt', total crash + this message, involuntarily.
This seems broken hardware in this laptop, the CPU or the graphics card is probably damaged. 
The memory is tested with memtest86 and is ok. 
I am thinking of a faulty graphics card.

Time for a new machine.
This old laptop goes to the recycling center!!!

I can not live with Windows 7, it makes me sick.

ps. Sorry for my bad English, i'm a Dutch men.

---

### Post by Mike_Walsh on 2014-06-24
Hi, everybody.

The laptop in question is an elderly Dell Inspiron 1100 (circa 2003); I am currently running Lubuntu 14.04 on it 

The apparently known problem stems from an incompatablility between the kernel video drivers, and the Intel 82845 GL/GE/PE/PV graphics chipset. 

Anybody attempting to run Lubuntu on one of these beasties will find, as I did, that the desktop will NOT occupy the full screen (which is 768x1024 pixels resolution); instead, you will be stuck with a resolution of 640x480, and it will be jammed, resolutely, into the top left hand corner of the screen.

To quote, from my thread about this problem:-

"I have a 2003 Dell Inspiron 1100 laptop, on which I've just installed  Lubuntu 14.04. The O/S is working fine; however, I'm stuck with a  640x480 display in the top left quarter of the screen. Monitor Settings  offers no other options.

I've read this thread about my problem:- [http://ubuntuforums.org/showthread.php?t=2222349](http://ubuntuforums.org/showthread.php?t=2222349)
                                 and also this:- [http://ubuntuforums.org/showthread.php?t=2222014](http://ubuntuforums.org/showthread.php?t=2222014)

Doranwen in the first thread has got exactly my model and same hardware,  so I followed this through. At the bottom of the first post, his  solution has been added; I tried this, but the 'i845.modeset=0' didn't  work for me. So I tried the 'nomodeset' option, and, following Morgaes  advice in this thread ([http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)) I've edited the grub bootloader, and rebooted.

I now have the same 640x480 display, but in the centre of the screen, with a black border round it."

The best you can acheive, it seems, is to position the desktop centrally on the screen, instead of in the top left corner. The problem is that the icons, and windows, and everything else, is still full-size; so that you often can't access buttons that are positioned at the bottom of full-size windows.....scrolling has no effect, as it is NOT a minimised window!


Mike.

---

### Post by Adam_GUI on 2014-06-24
**_Dell Inspiron Mini 1010_**
_Distro_: XUbuntu 14.04.
**!!** Known problem graphics card.  GMA500 (Poulsbo) **!!**

System boots to the correct screen resolution.  1024x576 on this model.
XFCE Compositing works well enough.
Full Compiz hasn't been attempted.
Wireless works.
Multi-monitor not attempted.
Suspend not attempted.

I normally use cairo-dock.
Something with the graphics or xfce compositing caused labels on cairo-dock to not display text on background.

Swapped my usual cairo-dock for Docky and I get a similar enough experience for a drop-in.

Flash video playback:
Firefox with Adobe NNAPI: Slow to start, but smoothes itself after a moment when windowed.
Fullscreen video with this method acts similarly.  
Seems to be a wind-up for video processing to get the audio and video back into sync.

Using SMPLayer with the vaapi library for local playback:
Audio gets way ahead of video with MP4 playback.
Having something like WinFF to make the file smaller or change formats could help.
It did when I was running Linux Mint Debian Edition and had to view a vacation video.  
Haven't tried this with 14.04.

Skype:
Camera works.
Audio works - Scratchy playback.
There used to be a workaround setting the sound device to dell or manufacturer to fix that.
I don't rely on this machine for anything anymore.  Not worried about it.

There's a slight delay for programs to launch.
Battery seems to drain somewhat quickly.  Could just be age.

Otherwise, the machine seems fine for general typing and internet browsing.

---

### Post by kira-yamato-2008 on 2014-07-28
1) Version of Ubuntu: Ubuntu 12.04 and Lubuntu 14.04 (64-bit for both)
2) Laptop Maker: HP
3) Laptop Model: G60-120US (250gb HDD, 3gb DDR2 Ram, AMD Turion X2 @2.00 GHZ, NVIDIA GeForce 8200M G. (Internal wireless card removed, and thus has not been tested by me. External Rosewill RNX-N180UBE instead, functions perfect.))
4) Known Issue: Nouveau drivers have graphical tearing and flickering in OpenGL applications and some flash video applications(depending on the site, for me Hulu and only in the regular player, but not the pop-out player.) Use of the NVIDIA binary drivers(any of them) causes freezing when the GPU is accessed for OpenGL and video play back of any kind. Random freezing happens with all NVIDIA binary drivers. All previous issues affect both. Ubuntu 12.04(and probably later to current 14.04.1 Trusty Thar) specific issues: Unity DE causes freezing with NVIDIA binary drivers. X.org Nouveau driver causes tearing on Unity DE after install, but not when using LiveCD/DVD.

Side note: Everything else works fantastically as long as you use the X.org Nouveau driver.

---

### Post by AlexValex on 2014-07-31
Version of Ubuntu: 14.04 LTS
Laptop Maker: HP
Laptop model: Elitebook 840G1 (H5g26ea)
Not working:
- AMD Driver won't install - AMD Radeon HD 8750M (1 GB GDDR5 dedicated)
- Sound not working (IDT High Definition Audio) - and blocking the sound tester in system settings, when trying to test the sound.
- Camera and fingerprint reader not working. 

Detailes here: [http://ubuntuforums.org/showthread.php?t=2237217](http://ubuntuforums.org/showthread.php?t=2237217)

---

### Post by david-jefferson on 2014-08-04
[COLOR=#000000]1) kubuntu 14.04[/COLOR]
[COLOR=#000000]2) HP[/COLOR]
[COLOR=#000000]3) Pavilion 17-e123cl[/COLOR]
[COLOR=#000000]4) Won't allow installation. Has win 8.i listed as the FI OS in BIOS
If I get the IT guys to wipe out my HD, Can I get kubuntu drivers for the hardware. I didn't see the HP 17 TS listed on the  [/COLOR][COLOR=#333333][FONT=Ubuntu]Ubuntu Desktop certified hardware[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu] HP
can I remove the installed OS from BIOS. [/FONT][/COLOR]

---

### Post by varunendra on 2014-08-04
> **david-jefferson said:**
> ....
If I get the IT guys to wipe out my HD, Can I get kubuntu drivers for the hardware. I didn't see the HP 17 TS listed on the  Ubuntu Desktop certified hardware HP
can I remove the installed OS from BIOS. 

Welcome to the forums David!

You will have much better chance of getting useful answers to your questions if you ask it in the "[General Help]("http://ubuntuforums.org/forumdisplay.php?f=331")" section of the forums.

If it came with Windows 8 preinstalled, it means it (win8) is a UEFI based installation, and you should install Ubuntu/Kubuntu/whatever-you-like in the same (EFI) mode. Read this wiki to know more about EFI installations : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Most of the hardware drivers are already included in the Linux kernel that gets installed by default, so usually you don't need to install any driver manually. It is HIGHLY RECOMMENDED to test Ubuntu in a "Live Session" (Ubuntu booted directly from the DVD/USB, run in "Test" mode) before installing it on the hard disk. This allows you to not only verify whether your hardware will work or not, but also to see whether it works as you expect or not, and whether you like it or not.

Although keep in mind that the performance is a bit slow in Live Session, it will be relatively much faster when installed on hard disk.

If you need detailed or step-by-step help on any of these, I recommend starting a new thread (one per topic) in General Help section, or a section relevant to the topic - like "Installation & Upgrades" for installation issue, "Networking & Wireless" for network/wifi issue etc.

Best of Luck! Hope you'd enjoy the forums here. :)

---

### Post by Jessie_James_A._At on 2014-08-16
1. Ubuntu 14.04.1 with gnome 3.1.04, KDE 4
2. Acer
3. V3-571G
4. Dual graphics card Intel HD 4000 & Nvidia GT 630M, Nvidia Optimus. I can used nvidia as default GPU to run my whole system it'll breaks panel,launcher in unity the screen resolution too much for default 1366x768, unable to detect my monitor in nvidia settings. but in Intel it runs well with a couple of some problems

---

### Post by warlock3 on 2014-08-27
[COLOR=#000000]Version of Ubuntu: 14.04 LTS[/COLOR]
[COLOR=#000000]Laptop Maker: HP[/COLOR]
[COLOR=#000000]Laptop model: Envy DV7 ([/COLOR]7201sa)
[COLOR=#000000]Not working:[/COLOR]
[COLOR=#000000]- Whenever I install a nVidia driver, the laptop boots to the login screen.  On login, you get the wallpaper and mouse cursor but nothing else; menus (which were visible on the login screen) disappear.  This happens on compwiz + that other one (name temporarily escapes me as I'm pre-coffee) and "Ubuntu".

Laptop spec link: [/COLOR][http://h10025.www1.hp.com/ewfrf/wc/document?cc=uk&lc=en&docname=c03504388](http://h10025.www1.hp.com/ewfrf/wc/document?cc=uk&lc=en&docname=c03504388)

I've pretty much tried everything, installing drivers from the additional drivers tool, stopping lightdm and installing via command line...  It just absolutely refuses to work for me.

It's not the first beef I've had with this version of Ubuntu and graphics, either - I've got the same Ubuntu running on virtual machines in VirtualBox and they point blank refuse to use the 3d-accelerated driver in the guest additions.  It also crashes the latest VirtualBox.  But that's outside the scope of this post - it has made me seriously consider going back to 12.04, though, as that was fine on laptops, virtual machines and my home microserver - all of which are having grief with 14.04 in their own way.

---

### Post by v923z on 2014-09-03
Version Of Ubuntu: Trusty Tahr 14.04 
2)Laptop Maker: Lenovo
3)Laptop Model: Thinkpad E545
4)Known Issue: Video driver produces random glitches on screen. 

This laptop was ubuntu certified ([http://www.ubuntu.com/certification/hardware/201305-13496/](http://www.ubuntu.com/certification/hardware/201305-13496/)), but it seems that that is not quite valid.

---

### Post by EnglishElectricAndy on 2014-11-28
Hewlett Packard Pavilion g6-2213sa Notebook
AMD A8-4500M APU

Tested with 64-bit versions of:
Xubuntu 14.04.1 (full install)  added fglrx package later
Kubuntu 14.04.1 (full install)
Manjaro KDE 08.10 (live USB session) required Secure Boot to be disabled in EFI

In all cases suspend/resume functionality is completely broken.
Ctrl+Alt+Del allowed Manjaro KDE a 'soft' shutdown, both the full installs required a hard power switch shutdown.

---

### Post by entropius42 on 2014-12-30
Machine: HP Omen with the 512MB m.2 SSD
Tested with 64 bit versions of Ubuntu 14.04, Kubuntu 14.10, 14.10 Plasma 5, and Mint 16

Two main problems:

1) SSD *extremely* slow (install took two hours; hdparm gives read speed as 2 MB/sec)
2) Wireless marked as hard blocked in rfkill (there is no physical switch that should be hard blocking it)

---

### Post by Mike_Walsh on 2015-01-06
Machine: 2002 Dell Inspiron 1100.

Tested with ALL 'buntu variants (Ubuntu, Lubuntu, Xubuntu & Kubuntu).

They all WORK on this machine, although at only 1 GB, Unity, and to a certain extent, KDE, are really too much for it. The issue is the graphics card; the 'Brookdale'-cored, Intel 'Extreme' Graphics, 82845 G/GL/GE/PE/GV adapter. Every distro that I have tried WILL run; but the display ends up jammed into the top left-hand corner of the screen (640x480, in a 1024x768 screen). NOTHING that I have tried seems to be able to make the screen show the desktop at full resolution. 

The curious thing is, although the desktop display is in miniature, the desktop icons and windows are at the expected, normal size.....so very often, you can see part of a window, but cannot access the rest of it, as there are no sidebars indicating that you can scroll down to see the rest of it.....and indeed, you cannot.

The only partial 'fix' for this seems to be to use 'nomodeset'; which merely moves the miniature desktop into the centre of the display.

I have resorted to running Puppy Linux on this machine.....which, touch wood, works perfectly.

See here for the tribulations of a fellow 'sufferer' :-

[http://ubuntuforums.org/showthread.php?t=2259056](http://ubuntuforums.org/showthread.php?t=2259056)


Regards,

Mike.

Edit: No longer a problem! I installed the 14.04.2 point release of Lubuntu last night; everything is working PERFECTLY.....even the recalcitrant graphics adapter. I have a full screen display, at long last. Many thanks to Julien Lavergne & the team at Lubuntu. Brilliant work. Thanks!
(17/04/15)

---

### Post by thomaslhansen on 2015-01-09
Asus D550C with Ubuntu 14.04.1

Wireless interface wlan0 is hardware blocked by rfkill. There are some workaround, but it's not ideal. 

The hardware opun this computer is quite awfull. EVERYTHING is made out of plastik and doest fell any secure to use, it migt just fall apart. 

Overall do not buy this laptop. I dosent even work that well with Windows.


= = =
*Mörgæs 2015-01-10: Would be interesting to know how 14.10 and 15.04 behaves.*

---

### Post by slepowidzacy on 2015-05-04
Ralink rt 3290 bluetooth doesn't work on my asus laptop on latest kernel + 15.04

---

### Post by aaronfranke on 2015-05-22
Xubuntu 15.04, Dell Latitude E6400. The graphics drivers for the Quadro NVS 160M work well enough to provide a graphical desktop, but they do not work for 3D applications. Steam complains on startup, and games simply do not run, no error messages. Steam reports me playing a game for a split second. I'm using the drivers from the repository, via Additional Drivers and also apt-get installing nvidia-XXX drivers. On Windows, these things can run fine.

---

### Post by flitbee on 2015-06-20
Here's mine:

1) Ubuntu 15.04
2) HP
3) HP pavilion 11-n024tu 
4) Had to format the entire disk. However the showstopper is that it doesn't power off or reboot. Both get stuck and I have to switch it off using the POWER button. Cannot use without fixing that. Tried many solutions (googled). None of them work

---

### Post by Guy_Rouillier on 2015-07-04
This laptop (AMD Turion X2 TL-58 1.8 GHz) is ancient (2007), but with the hard drive replaced by an SSD, still runs acceptably.  Had Windows 7 and Ubuntu 14.10 running dual boot.  Did a release upgrade to 15.04.  Got several errors during the upgrade process related to corrupted compressed files.  When the upgrade completed, my BTRFS root filesystem was completely corrupted.

I then downloaded 15.04 and tried installing from both a USB drive and a DVD drive.  Both options refused to even boot up.  I then did a clean install of 14.10 successfully (from USB drive), and the system is working fine again.

So, some change in 15.04 has made Ubuntu completely incompatible with this laptop.  Do not attempt this upgrade.

---

### Post by heebiejeebies2 on 2015-08-06
> **flitbee said:**
> Here's mine:

1) Ubuntu 15.04
2) HP
3) HP pavilion 11-n024tu 
4) Had to format the entire disk. However the showstopper is that it doesn't power off or reboot. Both get stuck and I have to switch it off using the POWER button. Cannot use without fixing that. Tried many solutions (googled). None of them work

I had the same problem, I solved it.  See here:

[http://ubuntuforums.org/showthread.php?t=2269935](http://ubuntuforums.org/showthread.php?t=2269935)

---

### Post by david-flory on 2015-08-09
Ubuntu 15.04 desktop amd64
Lenovo ThinkPad W541

Will not install or run properly.  Reports driver problems: "mmc0 unknown controller version(3), You may experience problems"

---

### Post by Eder_Giovani_Savio on 2015-09-06
[COLOR=#000000]*Ubuntu 15.04*[/COLOR]
[COLOR=#000000][I]HP pavilion 11 x360
[/I][/COLOR]
[COLOR=#000000]*No zoom in touchscreen. No rotation screen.*[/COLOR]

---

### Post by husnainlatif on 2015-10-13
Here's mine:

1) Ubuntu 15.04 (and many other distros, versions)
2) Sony
3) Vaio duo 13
4) No connected standby support, can't suspend at all, freezes after suspension, the lowest point on brightness turns the screen off, no wifi (a partial fix is to copy [COLOR=#111111][FONT=Consolas]brcmfmac43241b4-sdio.txt[/FONT][/COLOR] to [COLOR=#111111][FONT=Consolas]/lib/firmware/brcm[/FONT][/COLOR])
Here are the issues that still persist, [http://askubuntu.com/questions/664786/sony-vaio-pro-duo-13-sdio-broadcom-bcm43241-not-recognized](http://askubuntu.com/questions/664786/sony-vaio-pro-duo-13-sdio-broadcom-bcm43241-not-recognized)
Also the active n-trig pen works but it has no palm rejection, the "wacom tablet settings" don't show any settings for n-trig, it might be time to rename them to pen/active digitizer settings.
None of the sensors (ALS, gyro/compass/accelero etc) are supported (or work out of the box).
Also there are times when the keyboard stops working altogether.
The laptop/hybrid is unusable with these issues.

---

### Post by michael337 on 2016-01-21
Vendor: Dell
Series: Latitude
Model: D420

Hardware issues:wifi won't work at all at all even if I use the solution possible for 14.10 & under if I do the method in 15.10, it will say after any installation: DKMS:installed &#128557;

---

### Post by globetrotter-roma on 2016-01-22
Ubuntu 16.04 LTS
kernel 4.3.x.xx
Acer Aspire 5610

Video memory corruption.
A black window partially cover the login area after boot.
Work well until kernel 4.2.x.xx

---

### Post by wooddavid88 on 2016-05-13
**_Asus Q400A _**
- 3632QM i7. 8GB DDR3, 850GB HDD, Intel Centrino 2230 Wifi, Qaulcomm 1gb Ethernet. IGPU HD 4000 with adjustable DDR3 up to 512mb Video Ram (System Memory allocated) (Adjustable in BIOS)

_**OS Version**_
Ubuntu 16.04 (Default Download) (Back to Ubuntu 12.04) 

_**Cons**_
Wifi Switch doesn't operate. (FN+F2) - Wifi toggle (on/off) Does nothing when pressed. 

_**Pros**_
Everything else works right out of the box and has since Ubuntu 12.04. 

Thank you for reading.

---

### Post by lhb1142 on 2016-05-15
Vendor: Alienware (Dell)
Model: AW17R3-7092SLV 17.3" FHD Laptop (6th Generation Intel Core i7, 16 GB RAM, 256 GB SSD + 1 TB HDD) NVIDIA GeForce GTX980M
Received: May 12, 2016
Operating System: Microsoft Windows 10 (Home)
Desired Operating System: Ubuntu Studio 16.04 'Xenial Xerus'

I received an **Alienware AW17R3-7092SLV 17.3" FHD Laptop (6th Generation Intel Core i7, 16 GB RAM, 256 GB SSD + 1 TB HDD) NVIDIA GeForce GTX980M ** *free of charge* (don't ask!) three days ago. It has Microsoft Windows 10 (Home) installed.

I would like to completely replace Windows with Ubuntu Studio 16.04.

However, when I run the 64-bit Live CD [DVD] disk (which is perfect, not corrupted in any way), everything seems to work - except the Wi-Fi.

I am even able, using an Ethernet cable, to access the Internet and install the proprietary NVidia drivers which are on this machine.

But I cannot, no matter what I do, get that computer to connect via Wi-Fi. (The Fn + F2 control doesn't work, except *sometimes* to show that the Wi-Fi is disabled via a hardware switch.) Even though I configure the Wi-Fi connection properly in the Network setting, it does not function.
 
When I first boot up the Live CD disk, I see a message that states:

**[     4.509440]  nouveau 0000:01:00.0: gr: failed to load fecs_inst** (See Image DSCF0104 below.)

I do not know if this has anything to do with the problem.

Then the Live CD loads, I can go to the Settings Manager -> Software & Updates -> Additional Drivers and see:

**NVIDIA Corporation: GM204M [GeForce GTX 980M]**

I can install that. This replaces the **X.Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)**; I suppose this is the cause of that initial error message.

There is a second notice there:

**Unknown: Unknown    Using Processor microcode firmware for Intel CPUs from Intel microcode (proprietary)**. (This replaces the selection **Do not use the device**)

I am able to install that Processor microcode firmware too. --Please remember that this is all being done from the Live CD. (Please see Image DSCF0105 below.)

I should also mention that I tried using the new Xubuntu 16.04 64-bit Live CD (also a DVD) with exactly the same results.

I suppose the logical thing to do would be to contact Alienware/Dell but, as many people have pointed out, this is generally fruitless.

Obviously, if the Live CD doesn't work properly, I do not want to install Ubuntu Studio to this computer - UNLESS there is someone here who can help me do so. I would wish to know exactly what the Wi-Fi connection problem is and how it can be rectified.

I thank anyone who can give me an answer to this problem.

[ATTACH=CONFIG]269097[/ATTACH][ATTACH=CONFIG]269098[/ATTACH]

---

### Post by st_ab on 2016-06-09
Lenovo Yoga 900 Business Edition:

SSD is not recognized by neither Ubuntu 16.04 nor Clonezilla.

See [https://forums.lenovo.com/t5/Linux-Discussion/Yoga-900-13ISK2-BIOS-update-for-setting-RAID-mode-for-missing/td-p/3339206/page/4](https://forums.lenovo.com/t5/Linux-Discussion/Yoga-900-13ISK2-BIOS-update-for-setting-RAID-mode-for-missing/td-p/3339206/page/4) for more information.

---

### Post by drm200 on 2016-06-19
Dell Vostro 3460  with Ubuntu 14.04.4 LTS
Intel Core i5 3210M @2.50GHz (2 cores - 4 threads)
Ram DDR3 - 8.00 Gb @ 798 MHz
Qualcomm Atheros AR8161/8165 PCI-E Gigabit Ethernet Controller (NDIS 6.20) 
Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
Kernel driver in use: wl

Bluetooth audio does not work.  It finds the speaker.  It pairs with the speaker. But the speaker does not show up in sound settings.

See: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003)

So I use Windows more and more.

---

### Post by kurt18947 on 2016-06-19
> **drm200 said:**
> Dell Vostro 3460  with Ubuntu 14.04.4 LTS
Intel Core i5 3210M @2.50GHz (2 cores - 4 threads)
Ram DDR3 - 8.00 Gb @ 798 MHz
Qualcomm Atheros AR8161/8165 PCI-E Gigabit Ethernet Controller (NDIS 6.20) 
Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
Subsystem: Dell Wireless 1704 802.11n + BT 4.0 [1028:0016]
Kernel driver in use: wl

Bluetooth audio does not work.  It finds the speaker.  It pairs with the speaker. But the speaker does not show up in sound settings.

See: [https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003](https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003)

So I use Windows more and more.

Dell has Ubuntu available as an option on some models. Is this one? And if so, does Dell offer Ubuntu software support for your model?

---

### Post by drm200 on 2016-06-20
> **kurt18947 said:**
> Dell has Ubuntu available as an option on some models. Is this one? And if so, does Dell offer Ubuntu software support for your model?

I purchased this model with Windows.   I installed Ubuntu Trusty two years ago as dual boot.  So Dell does not supply me with Ubuntu support.   But I did buy this machine as it was Ubuntu certified.

Interestingly,  Bluetooth worked fine up until March ... then it quit working after an update.  I can roll back the update by installing an old image from Mar 2016 and bluetooth works fine.  But then after updating Ubuntu it no longer works.  The problem is a well documented bug that has not been fixed ... 

[COLOR=#000000]*See: *[/COLOR][https://bugs.launchpad.net/ubuntu/+s...z/+bug/1283003]("https://bugs.launchpad.net/ubuntu/+source/bluez/+bug/1283003")

I've spent quite a few hours tracking down all the internet discussion on this ... I just don't have more time or energy for this problem any more.

thanks

---

### Post by SirPecanGum on 2016-06-21
Ubuntu 16.04
Asus 
E402MA

Random freezing (possibly Bay Trail related) bug report on Launchpad #1575467.
WiFi connection fails. The wifi card is 10ec:b723 Realtek RTL8723BE which has a bug report on Launchpad #1454843.
There is much help there and on askubuntu. With a few tweaks it does now appear to be working... fingers crossed.

Edit: I've since installed Ubuntu 14.04 on this laptop and it is working fine with the aforementioned WiFi tweak. Actually a very nice laptop for £130.

---

### Post by alf65 on 2016-10-02
Ubuntu 16.04 LTS
Macbook (from 2006)
Two finger right-click doesn't work.
Alternative is fn+shift+f10, but that won't work on desktop bar (launcher). You will only see a menu pop up for a split second sometimes, and you can't interact. If you want to unlock something from launcher, just throw it in bin.

---

### Post by alf65 on 2016-10-04
If you run synclient in terminal you can see that "RBCornerButton = 3", so if you tab your pad two times in the lower right corner you will right-click as well.
You can also tap the pad with two fingers at the same time to right-click. 

 Right-click by a two finger touch + one click doesn't work...........yet

---

### Post by 1jw on 2016-10-12
loaded Ubuntu [COLOR=#333333][FONT=&amp]16.04.1 LTS onto a [/FONT][/COLOR]Lenovo G40-30 laptop.    Wifi adapter did not function.  

HARDWARE:  Qualcom Atheros QCA9565/ AR9565  wifi chip set
DRIVER:  ath9k
note that this combination of chip set and driver are listed as working out of the box per: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsQualcomm](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsQualcomm)


SYMPTOMS:  
From within the GUI: the Network Manager would not turn on wifi (the slider switch stuck in the off position).  Additionally clicking on the top bar of the GUI and "enabling Wifi" turned the option from grey to white, but otherwise did not enable wifi.
From terminal session: "rfkill list all"  indicated that the Wireless LAN was "Hard Blocked".  This is generally indicative of either a) a physical switch on the laptop turning the wifi antenna off, or b) the wifi adapter is disabled in the BIOS.

Confirmed that the Lenovo G40-30 laptop model has no physical wifi antenna switch (or keyboard button with wifi disabling function).  Confirmed that the wifi adapter was enabled in the BIOS.

RESOLVED: 
Removing the "ideapad-laptop" module from the kernal via instructions found here:  [https://ubuntuforums.org/showthread.php?t=2238087](https://ubuntuforums.org/showthread.php?t=2238087) got the wifi working again.  I am not sure what other effect the removal of the module may have had.

NOTE:  it appears that a known issue with the "ideapad-laptop" module has persisted from Ubuntu version 14.04 through present.  I am not sure where (or how) to report the potential bug / hardware incompatibility to the Ubuntu development team.

---

### Post by mippo9 on 2016-12-18
Ubuntu 16.10
Asus
T100HA

After the grub, it shows a black screen.

---

### Post by fdanai on 2016-12-31
UBUNTU 16.04 LTS
DELL 
XPS15 9550 laptop, with preinstalled WIN10 Home, I7, 8GB RAM and **256GB SSD type: PC300 NVMe SK hynix-SMSNG PM951**.
I'd like to install alongside WIN10 the UBUNTU 16.04 using a properly made bootable UBUNTU 16.04 USB stick.
Using this USB stick I can boot and run the **live **version of UBUNTU 16.04 on RAM, but when I'm trying to install UBUNTU on this laptop **I can't see the internal SSD at all **and I can't install UBUNTU any further.

---

### Post by Crayboff on 2017-09-07
Lenovo Ideapad 320-15ABR
UBUNTU 16.04, 17.04, 17.10 beta daily build (Sept 7, 2017).

Trackpad doesn't work with default linux kernel bundled with ubuntu. Upgrading the kernel lets the computer identify the trackpad but it stops working after about 5 seconds.

Submitted bug report: [https://bugzilla.kernel.org/show_bug.cgi?id=196863](https://bugzilla.kernel.org/show_bug.cgi?id=196863)
Forum help post: [https://ubuntuforums.org/showthread.php?t=2370833](https://ubuntuforums.org/showthread.php?t=2370833)

Hopefully you from the future will find a fix at one of those two links!

---

### Post by thrwya on 2017-10-22
Acer Nitro 5 with GPU AMD RX 550 - unable to install Ubuntu ([https://ubuntuforums.org/showthread.php?t=2375169](https://ubuntuforums.org/showthread.php?t=2375169))

---

### Post by bill.schreyer on 2017-11-03
eePC after installing 17.04, I was asked to upgrade to 17.10 ArtfulArvark/Ububtu desktop. After installing 17.10, unable to use eePC. 
While booting Ubuntu is spread across the screen in rows of pixels (not able to read it but that's what previous version showed), the thinking dots appear at least 4 times across the screen.
After boot finishes, the expected login list is not readable (again pixelated), the icons at the top right of the screen are visible. When clicked the calendar is half cut off, the only usable icon is the power off.

---

### Post by alecz20 on 2018-05-25
Lenovo Thinkpad Twist s230u

Ubuntu 16.04.1 - worked fine with some tweaks: [http://www.thinkwiki.org/wiki/Installing_Ubuntu_12.10_on_Thinkpad_Twist](http://www.thinkwiki.org/wiki/Installing_Ubuntu_12.10_on_Thinkpad_Twist)
- custom script to toggle the touchpad
- grub GRUB_CMDLINE_LINUX to deal with invalid launchpad bug #1210748


Ubuntu 16.04.4 - multiple apparently unresolvable issues: random loss of mouse/keyboard and erratic power management (ACPI) behavior.
- does not stay suspended and wakes up or reboots instead of suspend/shutdown, shuts down if power cable is removed (with full battery)
- Bluetooth mouse stops working during regular use (bluetooh disabled, messages complain about missing firmware, adding said firmware does not work reliably - mouse is detected but not paired, mouse still disappears but no error messages?). Suspend/resume fixes mouse, bluetooh service restart sometimes works.
- USB keyboard and mouse disappear and not always detected on reconnecting. (built-in mouse still works): [https://ubuntuforums.org/showthread.php?t=2384486](https://ubuntuforums.org/showthread.php?t=2384486)

Shortly, is seems that after several Ubuntu 16.04 updates the laptop becomes a nuisance and constant googling and tinkering with config files and hacks is required.
I do not recommend running any Linux on this laptop unless you are a masochist or have the ability/desire to fix these bugs.

---

### Post by calcio-nit on 2018-05-26
1) Version Of Ubuntu: 18.04 LTS
2) Laptop Maker: acer
3) Laptop Model: Apire 7 - A715-71796T
4) Known Issue: After booting via Pendrive Keyboard and Mouse or Mouse pad froze. I can't click anywhere or type anything.

---

### Post by alexj on 2018-07-27
1) Version Of Ubuntu: 18.04 LTS
2) Laptop Maker: Metabox (Clevo)
3) Laptop Model: Metabox Alpha N850EJ (Clevo N850EJ)
4) Known Issue: Install freezes. Ubuntu Server installs OK, however installing ubuntu-desktop freezes the thing. Likely due to the BIOS Metabox provides - some other Clevo resellers (not in Australia) sell Clevo with Ubuntu

---

### Post by freedex on 2018-07-27
1) Version Of Ubuntu: 18.04 LTS LiveUSB
2) Laptop Maker: Apple
3) Laptop Model: Apple MacBook Pro (Mid 2009 MacBookPro5,4)
4) Known Issue: One of three things happens when booting

Computer boots and hangs on a black screen


  Computer tells me it can't find vmlinuz (vmlinuz.efi?)


  Computer boots to a black screen with a cursor in the top right
 - Tells me I can choose between trying to open Ubuntu with out installing, install Ubuntu, or some other things
 - When I try Ubuntu, it hangs on the loading screen

---

### Post by improgrammer on 2019-02-16
Thinkpad E480
wireless adapter incompatible with any version of ubuntu (or any release of linux)

---

### Post by fancydeveloper on 2019-07-09
> Please only list
1) Version Of Ubuntu
2) Laptop Maker
3) Laptop Model
4) Known Issue


[COLOR=Red]*NOTE* This thread is exclusively for the listing of  incompatible hardware. Any idle chatter or unrelated posts will be  moved/removed accordingly. *NOTE*
[/COLOR]
Thank you.
Thread text shamelessy lifted and edited from Frodon's Desktop threads.

Edit - [HardwareSupport/Machines/Netbooks wiki pa]("http://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks")[ge]("https://begamedev.com") 


1) 17.04 but most likely any
2) MSI
3) Apache Pro
4) Can't install via usb with dualboot on windows. I think there are no enough rights to install Grub. it fails after the install is done and it tries to implement boot loader or something

---

### Post by ilgaz on 2019-10-14
18.04
HP-Pavilion-13-x360 hp-pavilion-13-a200-x360-convertible-pc requires 2 parameters to be passed to kernel.

secure boot=off from BIOS so your wireless will load driver.

Grub (Linux) parameters.

acpi_osi=
(yes, nothing after equal sign)
So it doesn't claim to be Windows messing up everything&freezing hard on boot (brick like if you are coming from Android)
pci=biosirq (not absolutely sure that is needed after acpi runs but does cause no harm)

After these settings, even a Live USB will boot fine, requiring only wired connection for updates&internet. You will need broadcom-wl-dkms for wireless.

Bug reported see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1848017](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1848017)

---

### Post by wowbaggerbr on 2019-11-01
[COLOR=#000000]*Please only list*[/COLOR]
[COLOR=#000000]*1) Kubuntu 19.10*[/COLOR]
[COLOR=#000000]*2) Samsung*[/COLOR]
[COLOR=#000000]*3) Samsung Notebook 7 Force*[/COLOR]
[COLOR=#000000][I]4) Known Issues:

- Headphone jack doesn't work
- HDMI output doesn't work
- NVME drives are recognised only as SATA (sdb)
- BIOS is incredibly simple, with very few settings
[/I][/COLOR]

---

### Post by laurent-verdier-d on 2019-11-09
1) Version Of Ubuntu 18-04 ->
2) Laptop Maker : DELL
3) Laptop Model : inspiron 14 5000 2 in 1 2019 model (bought in october)
4) Known Issue : ubuntu 16-04 work without touchscreen, wifi. The other later version don't work (neither the usb live version). If i make an upgrade to 18-04, the boot stop with thoss informations :
[I]couldn't get size: 0x00....0e
new 0000:01:00:.0: DRM: failed to create kernel channel, -22
CPU0: Core temperature above threshold, cpu clock throttlrd (total events =1)[/I]

---

### Post by uRock on 2019-11-09
> **laurent-verdier-d said:**
> 1) Version Of Ubuntu 18-04 ->
2) Laptop Maker : DELL
3) Laptop Model : inspiron 14 5000 2 in 1 2019 model (bought in october)
4) Known Issue : ubuntu 16-04 work without touchscreen, wifi. The other later version don't work (neither the usb live version). If i make an upgrade to 18-04, the boot stop with thoss informations :
[I]couldn't get size: 0x00....0e
new 0000:01:00:.0: DRM: failed to create kernel channel, -22
CPU0: Core temperature above threshold, cpu clock throttlrd (total events =1)[/I]

I'm seeing posts on the internet where people have gotten that machine to work. I recommend starting a support thread for getting it working.

---

### Post by manjushri on 2019-11-20
Not sure if this is the right thread but i will try. :)
1. Do not know what vesrion to install
2. Toshiba Satellite L20-173

Any suggestions please? 
856 mb ram 1,4 CPU

Absolutely lost where to start and how to do it? Where should I begin? Thank you very much in advance for any information. :)

---

### Post by uRock on 2019-11-20
> **manjushri said:**
> Not sure if this is the right thread but i will try. :)
1. Do not know what vesrion to install
2. Toshiba Satellite L20-173

Any suggestions please? 
856 mb ram 1,4 CPU

Absolutely lost where to start and how to do it? Where should I begin? Thank you very much in advance for any information. :)

Start a new thread. This thread is for laptops that just don't work with ubuntu.

---

### Post by umbravitae on 2020-02-28
1) Version Of Ubuntu: 18.04 LTS 
2) Laptop Maker: Lenovo 
3) Laptop Model: Ideapad 330 
4) Issue(s): I`ve been using Ubuntu for a few weeks, no too intensively though; so far I have problem only with the keyboard, but a very frustrating one, particularly if you type a lot of text:
 The combination "Shift" + "Home" / "End" for selecting text doesn`t work in any text editor unless I press NumLock first.  When asked to save a file, pressing "Shift" + "Home" / "End" behaves as if pressed only "Home"/"End": it only moves the cursor at the beginning/end of the text without selecting any text. 

NOTE: I have used Ubuntu 14.04 briefly on a Fujitsu Siemens Notebook (Amilo series, I don`t remember the exact name of the model) and then I had the same problem, even worse: "Shift" + "Home" / "End"  did not work at all. However, when I logged in as a Guest User, the keyboard functioned properly.

---

### Post by devanghingu on 2020-03-18
1) Version :            **Ubuntu 18.04 LTS**
2) Laptop Maker  : **HP**
3) Laptop Model :  **15-R-036TU**
4) Known Issue
_____
issue 1  Till now i tried many version of ubuntu and other many flavor. but **Bluetooth** not detected till now.
issue 2: when i shutting down laptop, it **started to shutdown** process. **At end of process it hangs off**. and nothing work in laptop. **No keyboard and mouse work**(i tried to **Caps-lock on/off but not work**). it just showing last screen. i don't know why this kind of thing happen. at end of process i forced shutdown using long power button press.

 i m very biggest fan of** linux**. right now i m very _depressed_. because those two error i can't solved. if you want to anything like log and all i will provide it to you. please help..!!!

---

### Post by max-m-d on 2020-04-24
Version: Ubuntu 20.04 LTS
Laptop maker: Apple
Laptop model: MacBook Pro Mid2009 (8G RAM) 
Issues:
1. System freezing (I must use power button to force shutdown),
2. When I use NVIDIA driver, screen bottom blinking (must switch to Xorg).

---

### Post by Ruy Benton on 2020-09-16
> **monkeybrain20122 said:**
> All [Lenovos]("https://news.lenovo.com/pressroom/press-releases/lenovo-brings-linux-certification-to-thinkpad-and-thinkstation-workstation-portfolio-easing-deployment-for-developers-data-scientists/?fbclid=IwAR0Mfs8mDnppGAD5IOJbboujG-z_Rrg4SXTMJYNAf0-4kK5o_rbK721tS6A") are now Linux certified. :smile:  "Lenovo is moving to certify the full workstation portfolio for top  Linux  distributions from Ubuntu® and Red Hat® – every model, every   configuration."

We hope :grin:

Lenovo Yoga C930
Ubuntu and many other Linux.
Rotation and the pen in Gimp work

Microphone                      don't work
Speakers and SubWoofer   don't work

---

### Post by tushar321 on 2020-09-26
Version: Ubuntu 18.04 LTS

Laptop maker: HP

Laptop model: HP 15-R250TU
 
Issues:** WIFI card with RTL8723BE has no support, unable to get WIFI working no matter which Linux Distribution**

---

### Post by CelticWarrior on 2020-09-28
> **tushar321 said:**
> Version: Ubuntu 18.04 LTS

Laptop maker: HP

Laptop model: HP 15-R250TU
 
Issues:** WIFI card with RTL8723BE has no support, unable to get WIFI working no matter which Linux Distribution**

If the problem is only the WiFi and even when we're dealing with a problematic one indeed - it requires user installed drivers and/or specific tweaks - that's hardly an incompatibility issue.

---

### Post by scorp123 on 2020-09-28
> **freedex said:**
> Mid 2009 MacBookPro5,4 

Funny, since I got that very same MacBook Pro model and it's working tip top since Ubuntu was first released.
Only Ubuntu 20.04 required a minor tweak documented here:
[https://ubuntuforums.org/showthread.php?t=2449534]("https://ubuntuforums.org/showthread.php?t=2449534")

> **freedex said:**
> 
Computer boots and hangs on a black screen
Computer tells me it can't find vmlinuz (vmlinuz.efi?) 

Sounds like a defective, broken installation and has absolutely nothing to do with hardware compatibility.

---

### Post by UbuntuWho on 2020-12-30
**Ubuntu Version:** Ubuntu 18.04 LTS (most of these problems have existed since Ubuntu 14.04 LTS)
**Laptop Manufacturer:** Gateway
**Model:** NE56R41u

**Issues:**
[LIST]
[*]The SD card reader has a persistant issue. SDHC and SDXC cards randomly stall upon writing, giving a hardware error. [This Ask Ubuntu thread]("https://askubuntu.com/questions/695944/sd-card-doesnt-work-well-under-ubuntu-but-does-well-under-windows") fixed this issue, but causes everything to lag excessively when writing.
[*]Graphic-intensive games, like Portal, run very sluggishly, or don't work at all.
[*]Wireless networking most often disconnects without reconnecting; changed to WICD and that still didn't fix the issue.
[/LIST]

---

### Post by CelticWarrior on 2021-01-02
> 
[LIST]
[*]The SD card reader has a persistant issue. SDHC and SDXC cards randomly stall upon writing, giving a hardware error. [This Ask Ubuntu thread]("https://askubuntu.com/questions/695944/sd-card-doesnt-work-well-under-ubuntu-but-does-well-under-windows") fixed this issue, but causes everything to lag excessively when writing.
[/LIST]


Some hardware is just like that, I mean, bad. And it's doubtful it supports SDXC at all but if it does that would be a first generation with lots of quirks so, yes, it isn't surprising that a workaround was (and still is) needed for Linux to replicate some of the things present in the Windows drivers that masks, by software, the litany of hardware issues it has.


> 
[LIST]
[*]Graphic-intensive games, like Portal, run very sluggishly, or don't work at all.
[/LIST]
 A Gateway [COLOR=#000000]NE56R41u runs with a 2011 [/COLOR][COLOR=#000000][FONT=&quot]Intel Pentium B960 and its companion very underpowered Intel Graphics. Portal's system requirements ask for at minimum a discrete graphics, [/FONT][/COLOR][COLOR=#333333][FONT=&quot]NVIDIA GeForce3+ / ATI Radeon 8500+ or better. It isn't supposed to work with a old and underpowered integrated MOBILE Intel Graphics. This computer is NOT for gaming, it isn't a matter of incompatibility, just a matter of totally unrealistic expectations.


> [/FONT][/COLOR]

[LIST]
[*]Wireless networking most often disconnects without reconnecting; changed to WICD and that still didn't fix the issue.
[/LIST]
[COLOR=#333333][FONT=&quot]
[/FONT][/COLOR]
Changing to WICD can only make things worse. I suggest that you check your router's settings before anything else. It should be WPA2-AES, not any WPA/WPA2 mixed mode and especially not TKIP. If using the recommended settings doesn't improve the connection's stability then I suggest you open a thread at Networking & Wireless where experts can take a look at your specific situation. And again, this has nothing to do with incompatibility.

---

### Post by minhna on 2021-03-17
1) Version Of Ubuntu: 20.04
2) Laptop Maker: HP
3) Laptop Model: ZHAN 66 Pro A 14 G4 (HP Probook 445 G8), AMD Ryzen 5800u.
4) Known Issue:
- Screen brightness is not adjustable.
- HDMI port doesn't work
- USB-C doesn't work when connect to external display

---

### Post by 0x54 on 2021-04-02
1) Version Of Ubuntu = Xubuntu 20.04 and 20.10
2) Laptop Maker = Lenovo
3) Laptop Model Ideapad Flex 5 14ARE05
4) Known Issue: 
No touchpad at all, currently no fix present. !Only on this model! Others have fixes.
 Current wacom driver is bugged, can be replaced with source input-wacom as fix.
Suspend is mostly not working, one core has high load after resume, nothing visible in task manager, system lags.
Fingerprint reader not working, no fix.

---

### Post by genukie on 2021-04-12
[TABLE="class: tbl host_info highlight properties"]
[TR="bgcolor: #F4F4F4"]
[TH="align: left"]System[/TH]
[TD="bgcolor: #FEF9E7"][IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAADIAAAAyCAYAAAAeP4ixAAAABHNCSVQICAgIfAhkiAAAAAlwSFlzAAAOxAAADsQBlSsOGwAAACV0RVh0ZGF0ZTpjcmVhdGUAMjAyMC0wNS0zMFQwNjowNzozOCswMDowMJ7VPewAAAAldEVYdGRhdGU6bW9kaWZ5ADIwMjAtMDUtMzBUMDY6MDc6MzgrMDA6MDDviIVQAAAJqklEQVRogdWaf1DUZR7HX893gV3ABURA aWJmEA/SFH0UgS86ky7o5u5QyvvRrtrSsm70zSoqWsavQmvrubqdCzzqNE8h 6m1Mku7RJ/JYpo6hUqRIQiBInIssgu7Pe5P5aFXfa7yy7gzd17Zofl83ye5/P57PPr8 MRjBSKDiQjlGxUOR1BKjAeiAZCABCYkXwP1COpQhEnkepBinNrRkK8GFbvosNJYFuGIB/ErUMbRF5EUgq6EoqzaoeqytAMKTqcAbbngR8jhDJU4S6QUgX2YJPreTn3pL/d/TNk7b44lKBXECxGiOHNpidIKZHsRLWu4eX7rvjazXdlCg8tQcg3EEQMSUF/IWlDiJW8NHe7L yDG/JCaRCWcRsR8teDsQYHKmRNCGfuRPtnTEgA6a fokeVvuiiDSm3om9ewYv5Vm9s3g1ZWR5GaNcuhMjxRebjmbFsfnCyC 2X759n2 lmr/0cSng0V1KGWZ/HG7PaPbF43qh2I/b7agRAxWWTG60oO9Hrr6UTsGNRCsdXTGV6/ChtJkEOoV37WVke5mkcbUNeKA3qnYlMr5oPwNkmM53dNhdaWkwoD6aN0eTXKbB9UQqL02OYkWCkfPlUNuUlE2EIcGcWIpNQyy5eKA3y3RBLzCZ/ZsKBHlVyqqHDjf5Mzng3mk6B9/JTWHxnjBNNsHxmHPl3RmsLEORgidmk1aRzoxQeWoLCOi3mp cmIID66xZtQcBtMaHcPcF1BcSH6ZkUaeCOcaFEhQTS1tXDWz dzCInIxzotqk89kE1nd2qB2PENLIe/ZojJWddyC5Ma/fFodN/qXXErrv3Fp7LHc NbhuLd55nd9VVTTk/uz2K9x9O82go2K8KT9fQ3gutLHz33177I2nDZrnN Z5xXVr2y87NiPW9RgAEB r4xyNpPJoxVlPG8Uv9G15KSXtXD 1dPUjZfyZ5u0vf 8L7CWcfgAiUoFdcSQ6sPTAdnTgxUEpooMKlolmMDnbdgFJKnt1XR/HBS25yVsyKpbzexFfNnXT12JeIIUAhNSaEeUkRPJQeTUa80a1fh9XGuD8cw xpWQ1UAN0MirMqwXmPzF22CSFSBvJ3qxKTpYeFKa4njxCCe5JHE27Qsa/6mmNwEIKKyx00mqwuF2GPKmkyWTlW385bFU0c/uY6d8WGMs7Yfwh9fKGVbb7MiEMB1LEceWdnvyFFh5NA/sXTnFde6WBhSiRxYXq3tlmJRs42mTnfcgP8cL  udbF1pNNhATp EGiESEESZEG/vV1G5e9HCYDcCtzfrWdIyXXeveIbZk3L1aVsGJXDbYBroaUkqf21vLBV9obfzB0q5I1e2t5am8tUkqCdArb86cQHOijQy2EArZlAPaFL8gfrE/FZRNbKhp5YmZcH 21ow28drRhKDa44LWjDSSE61k9J4GkyGD ufQOGtpdZ0UCZbVtbKlocu1s1/150RvZVfsiMDUmhK9 Nx2AM40dzNh4mu7hOIROCFQEFQVTSY/14KYAX35n5vY/V7o3SHWyglCyfRW2PDO27/vqj2pHzAiwL7PVH3kPEFNjQogKCXRvEEq2giqn yJoVJDC0oxxAJxqMPFZbZv/2g6Cz2rbONXg7ng6oAhB1kQNv1GV0wN6EwWaEAKmRAUzI8HIwimRGPX2Q27HmZbha 0BO860ME3jjjFbbVQ2mDBbNe4YQWoA9mxHH8INOp7JHs MBCMZ8aMI1/BEb8ZsOI8tpaT66g3K602UX2qn/JKJc01mbwHa ADsKZs TIgwUJid6FGQlJKq5s6R03wAzjZ1ELX GK03evzpFq3gyDv5CJPF1ud23AzYVGi90e1fJyGCRyaV8z8ABYHZmdDZbaPLi9Nm1OswBNxs /3NNMlOpTeN2Yeaq11ErDtK9ltneH5/HZ/WXMNs7Q9fhRCkxvi1Gv1CrDGIrFvCCPbnx5J8HwDUAxOd6ZYeyaG66xyqu876A/ZbtzA7kXX33gLAvKQITl9xD2lHAg nx/DKgiSsNpUvGs0cq2/v 9S3eXQm6xUkVYMN3q1KSiqb pzGh9M9xNQjAMfYQTqFzAQjv707np2LU/n26ZlcLprJ7WM1VoOkSkERPuVZG9qtfHyxFYBp8UbmTRr5hOO8SRGal6ED0aGB1F3TmBVFnFSQ6kFfBW0 3tj3/dUFSQQqI5f DVQEry5I8spz/JKJDqvNvUGqBxV7fUJe9EXYyrv7Xfj02FEUz5/ohds/FM f6NXzBdhfc02DKi9SnFtj9z8kpQie8zbIsoyx/GhypAtt1ex4vm3r4vXPfU6aa2LV7HhWzY4HoMlkZd7WswQqgjC9jnBDAOEG 9 Pzrdq2EEpOAIrdCVI27OeosQ4YxB/WjDJjW6TaK9ZHxGoCIrnT2TV7HiEENhUydK/X/DdBZJSBV0JONJB9krRHk/8m/KSNbMoyz s9pjfGgzzkiKoKJjK6jkJCCGQUlKwu4ZPqrWWj0fscVS5nLTTrUPafjIwATF7Qhh5aVFuI/z 0295 2STG/2BlEimRIVwoLbN73TQxxc0lo4n2NNBfRlR12OnsGwHinjImSSAjXnJLHeK1TeWX HJ3do1zNKHUvn5HdF9skwW ylj1OsGLXI98WE1b55o9MrTbwg7KM5 xPGv655QrWuQtLnyQ8GuGjYft2/o98 18Js92kYoAnKT u8XIQRhhgDCDAE VeoWTokclKdXqTYU1jiT3EcvPLAERdk2kCyAxzJjebeyCYtNO8CZFjeKyienudGrmjvZe6GVFnM351s6eXpuoluiG xR4Jj1n2PpGSQXoKq/YEOuS0lO 2cqKtuCEIOW2gZibVYCf7zf9VKTUpKz5SyH6q730caEBHDk8btIiXZ3N aXnPO 4aV8m KcxwaStV1MfXMBUpb5qH8f7kke7UbbXdXqYgTA1c4e7i85R6PJtSwopSQh3D2b6cRQhr65QKtJ25AX862YDXlIeWIw5R3Q6wRzBiyXHpuk6BPtFE9dm4UF75yjvcse0lZcNjH7zTNs1TgJe404gdmQ56koOkgxdG8YoSE FUPvig2l8slpKE6bevPxKyzf5f2FRk5SOOPDDWw7/Z2XYqgsw2zwWgz1sTwds9GXPRMVEsAPJ43mnuQIMhON3PfXc3zX4Wf8PRBSvo2 uWB45WlnFB5YglD uw8GpFjJBt8eDPgeT27I3Y5CGpIdLuWnkYaUElX DZvlNl NgOE qhHiAbQKqkOB41ENunWOKpQ/GP4zJyGXoqqLUP4fnzlpwfHwTJIBMg3HwzMhggGQ8gbQwk16ePYfDdyY8vsRL0EAAAAASUVORK5CYII=[/IMG] Kubuntu 20.04[/TD]
[/TR]
[TR="bgcolor: white"]
[TH="align: left"]Arch[/TH]
[TD="bgcolor: #FEF9E7"]x86_64[/TD]
[/TR]
[TR="bgcolor: #F4F4F4"]
[TH="align: left"]Kernel[/TH]
[TD="bgcolor: #FEF9E7"]5.8.0-49-generic[/TD]
[/TR]
[TR="bgcolor: white"]
[TH="align: left"]Vendor[/TH]
[TD="class: pointer, bgcolor: #FEF9E7"]Micro-Star International Co., Ltd. [»]("https://linux-hardware.org/?view=computers&type=notebook&vendor=MSI")[/TD]
[/TR]
[TR="bgcolor: #F4F4F4"]
[TH="align: left"]Model[/TH]
[TD="class: pointer, bgcolor: #FEF9E7"]GX60 3CC [»]("https://linux-hardware.org/?view=computers&type=notebook&vendor=MSI&model=GX60+3CC")[/TD]
[/TR]
[TR="bgcolor: white"]
[TH="align: left"]Year[/TH]
[TD="bgcolor: #FEF9E7"]2014[/TD]
[/TR]
[TR="bgcolor: #F4F4F4"]
[TH="align: left"]HWid[/TH]
[TD="bgcolor: #FEF9E7"]220f9[/TD]
[/TR]
[TR="bgcolor: white"]
[TH="align: left"]Type[/TH]
[TD="bgcolor: #FEF9E7"]notebook[/TD]
[/TR]
[TR="bgcolor: #F4F4F4"]
[TH="align: left"]DE[/TH]
[TD="bgcolor: #FEF9E7"]ubuntu:GNOME (Wayland) - GDM
[/TD]
[/TR]
[/TABLE]

Laptop: MSI GX60 3CC
CPU: AMD A10 5750M
IGPU: 8650G
DGPU: HD8970M 
BIOS: Unlocked K16SOM




Sorry im new to ubuntu etc but i spent 10hrs getting this to work
So login freezes etc as soonas any gfx rendering is required, sometimes on login or afew secs after logging in basically gpu drivers dont work.
Can login with nomodeset but thats not a fix.

So the best distro I found that works right out of the box is Kali with KDE plasma, but its still very glitchy
So i went ubuntu where all my dramas start. Hours and hours of researching and trying out various repositories, bios settings, i ended up installing things over the network with terminal recovery. You need to use NetworkManager and setup a conf with your ssid and psk.

First i did a lot of testing with the BIOS and found these to work the best.
IGPU
Mode = auto (This crashes)
Powerplan = Perfornance

DGPU
Mode = Power Express (This needs to be on for it to be active crashes)
Dynamic mode = Disabled (This crashes)
Backlight ctrl = VBIOS (Also crashes when it isnt)

_OHC to PCI0 = Enabled (Not sure why but enabling this causes laptop to take 5mins to boot bios, but taking battery out and charger out, holding the power button for 30secs fixes this)

Fast boot = Disabled
Secure boot = Disabled

Ive tried disabling these features one by one and they crash.

now your grub should reflect what gpu etc you run im on the AMD A10 APU 8650G and HD8970M
No idea what that means but i just switched between 1s n 0s until it was stable
Your grub needs to add these in like below radeon/amdgpu whether it be 1 or 0 idk at this stage you still dont have drivers installed even tho doing lshw or lspci or w/e says radeon. You cant sudo atp update xorg or ppa w/e cause apparently no file found. So mesa, Vulkan etc isnt there. Trying to install propietry for amd didnt work either. ./amdgpu-install wasnt found blah blah. But what did worked was doing this in this order and it sent me the amdgpu fg86x what evers i needed. 

I dont know, i thought i'd add it here incase someone wanted to add it somewhere for the fix or install guide, i went through kernals and hw-probes, there were only 3 other laptops running with working gpu, kinda sucks you cant communicate with them. hw-probe should have a feature where you can msg or atleast ping the person for driver sources etc

sudo add-apt-repository ppa:ernstp/mesarc
sudo apt-get update
Sudo apt upgrade 
[COLOR=#000000][FONT=VeraMono]GRUB_DEFAULT=0GRUB_TIMEOUT_STYLE=hiddenGRUB_TIMEOUT=0GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"GRUB_CMDLINE_LINUX_DEFAULT="splash radeon.si_support=1 amdgpu.si_support=0 radeon.cik_support=1 amdgpu.cik_support=0"GRUB_CMDLINE_LINUX=""GRUB_CMDLINE_LINUX=""
[/FONT][/COLOR]

---

### Post by genukie on 2021-04-13
****update instaslled kde plasma and now everything is broken, the initial brokeness i remember was after changing login screen.
*****Update disabled gpu special features and enabled dynamic switching, has fixed it but trying unigine bench mark the gpu seems to be doing nothing

---

### Post by geekykhan on 2021-04-29
> **genukie said:**
> ****update instaslled kde plasma and now everything is broken, the initial brokeness i remember was after changing login screen.
*****Update disabled gpu special features and enabled dynamic switching, has fixed it but trying unigine bench mark the gpu seems to be doing nothing
[COLOR=#000000][FONT=Arial]To be honest, it is quite rare that the gpu don't do anything once you try to unigine the bench mark.[/FONT][/COLOR]

---

### Post by steve949 on 2021-05-13
[SIZE=2][FONT=arial]Dell XPS 13 9305 (i7), which I understand to be internally identical to the 'supported' XPS 13 9310 other than the screen dimensions (16x9 rather than 16x10 for the 9310).

Have tried installing both 20.04 LTS and 21.04 (full install, not dual boot), with LVM and full disk encryption with Secure Boot enabled. In either case, everything appears to work fine ***apart from*** the Goodix fingerprint reader - no fingerprint authentication option is available under Users. I knew these devices were problematic under linux but I had hoped this machine would be compatible.

lsusb lists it as: ID 27c6:5335 Shenzhen Goodix Technology Co.,Ltd. Goodix Fingerprint Device

fprintd-enroll gives the following error: Impossible to enroll: GDBuss.Error:net.reactivated.Fprint.Error.NoSuchDevice: No devices available

Procedures tried without success:

a) fingerprint authentication option ticked in pam-auth-update
b) tried adding somerville libraries and installing drivers according to the Dell forum post by DanielNTX: [https://www.dell.com/community/XPS/XPS-13-9300-Does-fingerprint-reader-work-on-linux/td-p/7514958](https://www.dell.com/community/XPS/XPS-13-9300-Does-fingerprint-reader-work-on-linux/td-p/7514958)
c) tried adding somerville libraries and installing drivers according to this post: [https://mrcoffee.io/blog/setting-up-fingerprint-reader-ubuntu-20-and-dell-xps](https://mrcoffee.io/blog/setting-up-fingerprint-reader-ubuntu-20-and-dell-xps)
d) [SIZE=2][FONT=arial]tried adding the Modalias [SIZE=2][FONT=arial][SIZE=2][FONT=arial]usb:v27C6p5335* to a modified version of the [/FONT][/SIZE][/FONT][/SIZE]libfprint-2-tod1-goodix debian  package referenced in the links above, and then repackaging and reinstalling - **FYI **the stock version of this package contains the following specific Modaliases:  hwe(usb:v27C6p533C*, usb:v27C6p538C*, usb:v27C6p530C*, usb:v27C6p5840*)
[/FONT][/SIZE]
I'm unclear whether the problem is:
 
a) No suitable drivers are available for Ubuntu and the exercise is futile?
b) The device is compatible but I'm installing the wrong drivers?
c) I'm installing the correct drivers but have not signed them properly for operation under Secure Boot?
d) There's some other installation or configuration procedure I'm missing?

Other Observations:

1) The machine's TPM2 device does seem to be recognised and operating correctly. I understand it is possible to store the disk encryption key in the TPM to avoid having to enter it on each boot, but it appears to be an inordinately complicated and risky procedure ([https://run.tournament.org.il/ubuntu-18-04-and-tpm2-encrypted-system-disk/](https://run.tournament.org.il/ubuntu-18-04-and-tpm2-encrypted-system-disk/)  c.f. on Windows Bitlocker it's largely transparent to the end user). I have succeeded in getting this to work based on this unofficial link, but it would be great if Canonical could publish a definitive procedure for this.
2) The MOKManager blue screen key enrollment process on first installation rather threw me, as this doesn't appear to be covered anywhere in the standard Canonical installation wiki (though it is referenced in the technical literature). The "Enrol key" option prompts you for a password without clarifying which password is required. I tried entering the user password, disk encryption password and recovery key but none of these worked. Eventually by ploughing through the forums I discovered that this is actually expecting the root password. Once I'd set the root password in 'Try Ubuntu' mode, I was able to proceed with the installation and enrol the assigned Secure Boot MOK key successfully, but it was a needlessly painful process. Again, it would be useful if the standard installation wikis could cover this.

So close, but no cigar. I'd happily pay money for a fully compatible and supported dist of Ubuntu as in all other respects it's fantastic.[/FONT][/SIZE]

---

### Post by lesgar2 on 2021-08-27
Chuwi gemibook 

Ubuntu kernel 5.11.0-16-generic work, lattest frozen laptop

---

### Post by jclen on 2022-11-14
Ubuntu 22.04 has numerous issues with the 2022 Spectre x360, 13.5", Core i7 (tested October 2022):
[LIST]
[*]Lid open/close and screen orientation events put it into airplane mode.  This thread points to some tips that reduce the issue: [https://askubuntu.com/questions/1426028/22-04-airplane-mode-activated-whenever-lid-closes-opens-screen-switches-orienta](https://askubuntu.com/questions/1426028/22-04-airplane-mode-activated-whenever-lid-closes-opens-screen-switches-orienta) 
[*]The laptop even boots into airplane mode, probably due to the power-up-on-lid-open event.  I was able to fix that with a startup script turning of airplane mode:
[FONT=courier new]nmcli radio all on[/FONT] 
[*]There are suspend/hibernate problems when closing and opening the lid: [https://www.reddit.com/r/spectrex360/comments/wyjix5/linux_ubuntu_problems_on_new_14_spectre/.]("https://www.reddit.com/r/spectrex360/comments/wyjix5/linux_ubuntu_problems_on_new_14_spectre/") Using xorg seems to solve it. 
[*]Wayland does not detect screen rotation events - use xorg. 
[*]The camera would not work with cheese or zoom.  I think it may be common to the new "Windows Hello" compatible camera systems - the new Yoga 9i camera(s) also didn't work. 
[/LIST]

I had been hoping for better results, since my old Spectre x360 13-w063nr works well with 18.04.  Guess I'll keep "old faithful" a bit longer, update the OS to 22.04, and keep hunting for a Linux compatible 13" 2-in1 with a similar performance i7.

---

### Post by svin2 on 2022-11-19
1) Ubuntu 22.10
2) HP
3) Envy x360 eu0009nv
4) The device is a 2 in 1 but has a hard time telling when its in tablet mode(used to enable autorotation of the display on desktops like KDE)
In addition to that this device comes with a peripheral stylus, (ELAN [SIZE=2]04F3:29F5 [/SIZE]) which always reports itself with 1% battery when it shouldn't even report it at all.
Other than that you will have a hard time doing a right click with both the touchscreen and touchpad but it is possible(although i do not think it should be that hard)

---

### Post by mustahids1 on 2022-12-06
I have an Avita Essential Notebook PC. I have installed ubuntu KDE plasma in it and I don't get any sound. I also have Windows 10 OS installed in it and the sound works just fine when I run my PC with that. My Ubuntu is updated and I have tried some solutions taken from google but with no avail. The audio device is Intel Corporation Celeron/Pentium Silver Processor High Definition Audio.

---

### Post by cigtoxdoc on 2023-02-08
I have a similar problem with my DELL Precision 7720.  Sound always works with Win 11 Pro.  Sound sometimes works with Ubuntu 22.10.  Pulse Audio Volume shows sound ia coming from streaming internet radio on Firefox, but often there is no sound from built-in speakers.  Sometimes rebooting will get sound, but other times, rebooting will not give sound.

John

---

### Post by yorakal on 2023-03-16
[COLOR=#000000]Laptop: Lenovo IdeaPad Flex 3 11ADA05[/COLOR]
[COLOR=#000000]CPU: AMD Athlon Silver 3050e[/COLOR]
[COLOR=#000000]IGPU: AMD Radeon Vega[/COLOR]
[COLOR=#000000]BIOS: FPCN21WW[/COLOR]

[COLOR=#000000]Can boot into the Ubuntu installer and fully complete the install with erase disk but on reboot get nothing more than a black screen. This laptop has a very buggy UEFI boot system (secure boot off and tried everything else) and does not automatically boot Ubuntu or has some kind of problem with it.[/COLOR]

[COLOR=#000000]Curiously Kubuntu had the same fate but Lubuntu did not, this correctly booted, once on Lubuntu desktop I also discovered that the built in mouse/touchpad doesn't work, but everything else seems to. After a lot of experimentation I noticed there were a number of EFI boot entries more than the screen could even display, cleaning these out is dangerous and can render laptop bricked if not careful, there is definitely something wrong with how the bios/UEFI manages the boot order of OS.[/COLOR]

---

### Post by raiinzen on 2023-06-17
1) Kubuntu 22.04 - though I've also tested on Ubuntu as well
2) Dell
3) XPS 17 7930
4) Realtek ALC711-CB - Soundcard Not detectable 

I hired and worked with a Linux expert for 6 hours attempting to get it to recognize and use the sof-firmware drivers, but it kept giving an error message, so it isn't recognizing my realtek soundcard and therefore has no sound. In my 3 weeks of research, no one with this model of Dell XPS has been able to resolve this issue either.

---

### Post by cigtoxdoc on 2023-06-17
My Dell Precision 7720 Mobile Workstation is my Main PC.  It is dual-boot Ubuntu 23.04/Windows 11 Insider Build.  I had some sound problems until 23.04 was released.  So, at least DELL should not be on the hardware incompatibility list as a brand, as some models do work.  I also have a Dell Vostro 3500 that I retired last year, and it was working with what that current version of Ubuntu was at that time.

John

---

### Post by meeliss on 2023-10-25
1) Kubuntu 23.10
2) Lenovo
3) Legion Slim 5 Gen 8 (16" AMD)
4) Above normal Idle power draw ~30Wh

EnvyControl Optimus GPU Switcher is set to integrated graphics 780M in 7840HS. Bluetooth off. WiFi on. 1600p 240Hz 500nit screen at 20% brightness and 60Hz. Idle power draw is ~30Wh.

---

### Post by frikkieh on 2023-11-16
.

---

### Post by rkaalma on 2023-11-17
> **raiinzen said:**
> 1) Kubuntu 22.04 - though I've also tested on Ubuntu as well
2) Dell
3) XPS 17 7930
4) Realtek ALC711-CB - Soundcard Not detectable 

I hired and worked with a Linux expert for 6 hours attempting to get it to recognize and use the sof-firmware drivers, but it kept giving an error message, so it isn't recognizing my realtek soundcard and therefore has no sound. In my 3 weeks of research, no one with this model of Dell XPS has been able to resolve this issue either.

I have the same issue here with Ubuntu 22.04.3 LTS. Haven't hired a Linux expert myself but hoping to get some insight here: [https://ubuntuforums.org/showthread.php?t=2492601](https://ubuntuforums.org/showthread.php?t=2492601)

---

### Post by codrin1 on 2023-11-22
1) Ubuntu 23.10
2) HP
3) dc1020nq
4) can't switch to performance mode in power control

---

### Post by povej on 2023-12-19
There is no connection with Ubuntu and fan control system.

---

### Post by waggers1 on 2024-01-04
1) Kubuntu 23.10
2) Dell
3) Inspiron 13 5330 (Core Ultra 5 125H)
4) No wifi - hardware not detected, no bluetooth - hardware not detected, Arc graphics not detected

---

### Post by abmmhasan on 2024-10-03
[COLOR=#000000]1) Ubuntu 24.04[/COLOR]
[COLOR=#000000]2) ASUS[/COLOR]
[COLOR=#000000]3) Zenbook S16 (um5606) 2024 Edition[/COLOR]
[COLOR=#000000]4) Sound Problem + Several Other Issues
For a detailed list: [/COLOR]https://ubuntuforums.org/showthread.php?t=2500992

---

