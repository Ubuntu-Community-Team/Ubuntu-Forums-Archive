---
title: "dell precision m4500 touchpad probs"
date: 2010-06-13
forum: Hardware
---

### Post by tempo500 on 2010-06-13
hi, got a dell precision, everything seems to work fine except the alps touchpad on ubuntu 10.04. moving the mouse, double tap, touchpad buttons work. the default mouse/touchpad application does recognize the touchpad, but the options do not change the behavior of the device. i would like to have the side scrolling thing enabled... thanks, phil

tried this without success

[https://wiki.ubuntu.com/X/Config/Input#Input Configuration with udev (Ubuntu 10.04)]("https://wiki.ubuntu.com/X/Config/Input#Input Configuration with udev (Ubuntu 10.04)")
[http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html]("http://www.bhagwad.com/blog/2010/technology/alps-synaptics-touchpad-configuration-in-lucid-lynx-ubuntu-10-04.html")

---

### Post by francoisclermont on 2010-06-18
Hello,

I have a Dell m4500

For the horizontal scrolling, the only solution I found is to emulate the wheel by a button:

xinput -set-int-prop 'PS/2 Mouse' 'Evdev Wheel Emulation' 8 1
xinput -set-int-prop 'PS/2 Mouse' 'Evdev Wheel Emulation Button' 8 2

This script allows using horizontal scrolling by pressing the middle button (located just above the touchpad) and by using the touchpad to scroll

Of course, it is possible to run the script automatically

Francois

---

### Post by francoisclermont on 2010-06-19
Hello

May be, you also want to use TouchFreeze on Dell m4500 in order to avoid typing the touchpad when you use the keyboard.

Here is the method I propose to use TouchFreeze on m4500. On my laptop, it works with TouchFreeze 0.2.3 (on Kubuntu 10.04).

1) rename the file usr/bin/synclient (eg., usr/bin/synclient-alps)

2) create a new file usr/bin/synclient with the following content:

#!/bin/sh

if [ $# != 1 ]
then
  echo nothing
else

  if [ $1 = "TouchpadOff=0" ]
  then
  xinput --set-button-map "PS/2 Mouse" 1 2 3 4 5
  fi

  if [ $1 = "TouchpadOff=2" ]
  then
  xinput --set-button-map "PS/2 Mouse" 0 2 3 4 5
  fi

fi

3) install and run touchfreeze

Francois

---

### Post by svinchon on 2010-06-24
Hello,
 
I've got a DELL m4500 (i7 processor) too, on which I would like to install Ubuntu 10.04.
 
When I try to boot from a 10.04 Live CD I get the screen allowing to choose between running Ubuntu from the CD or installing.
 
Whatever I choose between those two, noting seems to happen (except the CD drive seems to become more active during a few seconds).
 
Any idea what could be happening?
 
Is there a known incompatibility between the i7 and 10.04.
 
Any help would be very much appreciated...

---

### Post by tempo500 on 2010-06-24
thanks francoisclermont, ill get back to you soon.
svinchon, tomboy notes...
nouveau problems
live cd grub change
&#8226; nomodset
after install
&#8226; edit default boot entry in grub
&#8226; add nouveau.modset=0

---

### Post by dino99 on 2010-06-24
goto synaptic and install: tpconfig

---

### Post by tempo500 on 2010-06-24
i am having serious problems with this machine, i am getting random freezes, mostly by installing packages, but i also had one while logging in. i had two full working days on this machine without a freeze, working in nuke playing massive files from the hd and maya. the freezes are not often and random. so i gave fedora 13 a shot and at the end of the day after installing all sorts of stuff i had two freezes again.

precision m4500
quadro m1800
128gb samsung ssd
!alps touchpad!

ubuntu 10.04 64bit 
2.6.32-22-generic and v2.6.34-lucid from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
nvidia 256.25
ext4
fedora 13 64bit
2.6.33
nvidia 256.35
ext4

i installed win for a bios update

update P02
1. Corrects an issue with the A01 BIOS which prevents the successful updating of the Intel Manageability Engine firmware.
2. Addresses a flash update issue under 64-bit operating systems.

update A03
1. Added support for newer versions of Intel processors.
2. Updated the PXE option ROM to version 1.3.52.1.
3. Updated the manageability engine firmware to version 6.1.0.1042.
4. Added support for Encrypted Hard Drives.
5. Addressed flash update issue under 64-bit operating systems.

i will revert to ubuntu again, but before i will cancel out all the feautures in the bios i dont need, firewire, expresscard etc...

ps.: the touchpad had the same problems in fedora...

---

### Post by tempo500 on 2010-06-24
all seems good now, just finished installing all the stuff i need, and no obvious error messages or freezes. lets hope it stays this way! i did a few things since the last ubuntu install.

update the bios to a03
disabled some features in the bios,
pc-card, express-card, ieee, sd/mini card, smart cards, modem, dell power on thing and some other things, i can write a complete list if anybody wants to know.

ubuntu 10.04 - standard kernel - x-swat ppa for nvidia 256

i am attaching my work in progress tomboy notes. ill give the touchpad another try tomorrow

```
**wacom config 10.04**
sudo gedit /usr/lib/X11/xorg.conf.d/10-wacom.conf
Section "InputClass"
        Identifier "Wacom class"
        MatchProduct "Wacom|WACOM"
        MatchDevicePath "/dev/input/event*"
        Driver "wacom"
        Option "Button2" "3"
        Option "Button3" "2"
        Option "KeepShape" "on"
EndSection

[B]nouveau problems
live cd[/B]
• f6
• nomodset
**after install when booting**
hold shift to enter grub
• press e for edit
• add nouveau.modset=0
**permanent entry in grub**
• sudo gedit /etc/default/grub
• #GRUB_HIDDEN_TIMEOUT=0
• GRUB_HIDDEN_TIMEOUT_QUIET=true
• GRUB_TIMEOUT=10
• GRUB_CMDLINE_LINUX="nouveau.modset=0"
sudo update-grub

**nvidia x-swat**
https://launchpad.net/~ubuntu-x-swat/+archive/x-updates

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

? sudo gedit /etc/modprobe.d/blacklist.conf
blacklist nouveau ?
```

---

### Post by francoisclermont on 2010-06-26
Hello [svinchon,]("http://ubuntuforums.org/member.php?u=1101198")

For your black screen issue:

I have solved the problem by connecting an external screen to my laptop (and rebooting)... Kubuntu was on this 2nd screen (and not on the internal screen).

Then, I have installed the Nvidia driver and configured the screen. 

If you want to use  two screens with your m4500, I posted a message about this aspect:
[http://forum.ubuntu-fr.org/viewtopic.php?pid=3556557](http://forum.ubuntu-fr.org/viewtopic.php?pid=3556557)
(the message is in french)

François

---

### Post by tempo500 on 2010-06-26
xinput --set-button-map "PS/2 Mouse" 1 2 3 4 5xinput --set-button-map "PS/2 Mouse" 1 2 3 4 5all good now! i guess the bios update did some magic, maybe the 64bit thing they fixed. i have one acpi error while the power cable is plugged. and mmc slot errors are gone cause i turned it off in the bios. will post the remaining errors soon.
suspend, hibernate work out of the box
still have to check mic and webcam 
using right now a scroll extension in my browser, is ok for me.
ill check the touchfreeze soon.
phil

ps: i just tried the xinput commands in the terminal, both of them did not change anything, also touchfreeze wont enable/disable the pad...

---

### Post by francoisclermont on 2010-06-27
Hi Phil,

On my laptop, the command 

xinput -set-button-map "PS/2 Mouse" 0 2 3 4 5 

disables (onl)y the left button of the touchpad:

François

---

### Post by tempo500 on 2010-06-27
hi,

i got the scrolling working for me in the browser with an axtension. when i do heavy work i anyway use my wacom tablet and would like to just have a script or something else to turn the touchpad on/off...maybe you can help me out? 
thanks, phil

---

### Post by francoisclermont on 2010-06-27
Hi Phil,

There is an option in the BIOS to disable the touchpad when a USB mouse is connected to the laptop. May be, this also works when a wacom tablet is connected

You can disable the touchpad with xinput. Unfortunately, this will disable the mouse (and probably the wacom tablet) too because the Ubuntu touchpad driver does not work with m4500:

xinput -set-int-prop "PS/2 Mouse" "Device Enabled" 8 0
(disable the touchpad/mouse)

xinput -set-int-prop "PS/2 Mouse" "Device Enabled" 8 1
(enable the touchpad/mouse)

François

---

### Post by tempo500 on 2010-06-28
great thanks - thats perfect!
wacom still works, touchpad/stick is disabled. ill make an icon :)

this machine feels stable to me now. its quiet, fast, main functions work out of the box. i will slowly enable the devices in the bios again, and look if the bios update fixed my freeze issue.

i hope we still can find a solution for the microphone!

thanks, phil

---

### Post by francoisclermont on 2010-06-29
ok

Today, I did a test with an external mouse [I]

xinput -set-int-prop "PS/2 Mouse" "Device Enabled" 8 0[/I]
disables only the touchpad and not the external mouse...

François

---

### Post by francoisclermont on 2010-07-01
Just another point,

Today, I have updated Kubuntu

After this update, the name associated to the mouse driver has changed

old name : "PS/2 Mouse" 
new name : "PS/2 Generic Mouse" 

On my system, I have changed the driver name in the xinput commands.

General remark : command to know the name associated to the drivers :
xinput -list

---

### Post by tempo500 on 2010-07-01
i got the mic working!

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```
Insert this line at the bottom:
```
options snd-hda-intel model=dell-s14
```

Save. Close. Reboot. Check levels in alsamixer - no need default is fine
```
alsamixer
```

source:
[http://ubuntuforums.org/showpost.php?p=9240042&postcount=9]("http://ubuntuforums.org/showpost.php?p=9240042&postcount=9")

---

### Post by francoisclermont on 2010-07-03
Thank you very much Phil!!!!

I have tried this method and it works very well

The next issue is the SR card reader

François

---

### Post by tempo500 on 2010-07-03
hi thanks, update did the same changes on ubuntu...
> old name : "PS/2 Mouse" 
new name : "PS/2 Generic Mouse"

as for the sd-card reader... ill give it a try soon, and turn it back on in the bios...lets see what happens. greets, phil

---

### Post by francoisclermont on 2010-07-06
Some people seem to be interested in our problem

[https://bugzilla.redhat.com/show_bug.cgi?id=596475](https://bugzilla.redhat.com/show_bug.cgi?id=596475)

a solution seems to be found for the sd card reader (I do not tested - a kernel recompilation is needed)

François

---

### Post by tempo500 on 2010-07-07
yes i can remember getting the same message > mmc0: unexpected interrupt if you really need that device you could try the mainline kernel stuff [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

there is a 2.6.35 deb, but i normally do not touch such stuff...

---

### Post by mio1 on 2010-09-16
> **dino99 said:**
> goto synaptic and install: tpconfig

I did that on my Precision 4500 (Ubuntu 10.04).

After that, a Touchpad is apparently found:
```

$ sudo tpconfig
Found Synaptics Touchpad.
Firmware: 8.96 (multiple-byte mode).

```

But
```

$ sudo tpconfig --tapmode=0

```
doesn't have any effect at all.

I also don't see a "touchpad" tab on System -> Preferences -> Mouse.

Thx

---

### Post by tempo500 on 2010-09-16
ill give it a try later.... but this [http://changelogs.ubuntu.com/changelogs/pool/universe/t/tpconfig/tpconfig_3.1.3-9/changelog]("http://changelogs.ubuntu.com/changelogs/pool/universe/t/tpconfig/tpconfig_3.1.3-9/changelog") says this prog was last modified 2006....

---

### Post by kordzik on 2010-10-06
I'm having the same problems with the touchpad on my M4400. It seems that the fundamental problem is that the kernel does not recognize M4400's touchpad as a touchpad device at all. According to this page [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) executing 

```
$ cat /proc/bus/input/devices >~/device
```

should result in a list containing a Touchpad device. This is not a case on my machine, I only see "PS/2 Generic Mouse". Perhaps we should raise an issue with the Kernel team then? It is very annoying not to be able to use all the touchpad features (in particular disabling of the touchpad while typing, out of the box)

---

### Post by tempo500 on 2010-10-06
same here

```
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: EV=120013
B: KEY=500f02902003 8380307cf910f001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=056a Product=00b7 Version=0116
N: Name="Wacom Intuos3 4x6"
P: Phys=
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: EV=1f
B: KEY=1cff 1f000f 0 0 0 0
B: REL=100
B: ABS=1000f00016f
B: MSC=1

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: EV=3
B: KEY=1101b00000400 100000 e000000000000 0

I: Bus=0003 Vendor=05ca Product=1814 Version=0331
N: Name="Laptop_Integrated_Webcam_3M"
P: Phys=usb-0000:00:1a.0-1.4/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:00/LNXVIDEO:00/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Front Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: EV=21
B: SW=4

I: Bus=0011 Vendor=0002 Product=0001 Version=0000
N: Name="PS/2 Generic Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input12
U: Uniq=
H: Handlers=mouse1 event12 
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=3

```

---

### Post by kordzik on 2010-10-08
10.10 is (hopefully) around the corner, let's wait for it and file a bug if it doesn't fix the problem!

---

### Post by tempo500 on 2010-10-08
i would not count on it... i have the kernel ....2.6.35-14 installed and it did not change a thing.... but i dont know which kernel will be the default with the new ubuntu...

---

### Post by dutchslab on 2010-10-13
2.6.32-25 is not fixing it either.  This is super frustrating, as the touchpad is getting in the way . . . any way to tell when this will actually be addressed?

---

### Post by tempo500 on 2010-10-13
> **kordzik said:**
> 10.10 is (hopefully) around the corner, let's wait for it and file a bug if it doesn't fix the problem!

hey kordzik, could you file a bug report? i dunno how and where todo that.

by the way, the mic still has same probs on new version. old fix works tough

sudo gedit /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=dell-s14

---

### Post by dutchslab on 2010-10-19
A brutal workaround I found was to use rmmod to pull the PS2 mouse drive from the kernel, using this command as root:

sudo modprobe -r psmouse

It disables the touchpad, keeps by USB wireless mouse working, but as you can imagine is a half-assed bandaid.  ;)

any status on getting the real fix in (correctly detecting the touchpad) so it can be configured via the system tools?

btw, still broken in 2.6.35-22-generic

---

### Post by dutchslab on 2010-10-20
Actually, for some reason, [PHP]modprobe -r psmouse[/PHP] seems to kill my keyboard after a certain amount of time.  Weird.  So I wouldn't reccomend that workaround afterall . . . :(

---

### Post by dutchslab on 2010-11-04
Hi all-  

Any foresight on when this may be fixed?  Not being able to disable the touchpad (while keeping the pointing stick enabled) is totally rendering Ubuntu incredibly difficult to use on my M4500 (I got fat fingers ;)

---

### Post by terdon on 2010-11-04
While we're at it, has anyone managed (or tried) to get two finger scrolling on the M4500?

---

### Post by dutchslab on 2010-11-04
Educated speculation, but I think any touchpad specific functionality, such as scrolling, will be broken until this is fixed, as this bug in general revolves around the system detecting the mouse interface as a touchpad, not as a ps2 mouse.

---

### Post by terdon on 2010-11-04
Fair enough. Thanks

---

### Post by mio1 on 2010-11-04
FYI, there is a bug named "Trackpad detected as PS/2 Generic Mouse" on the bug tracker which looks like it might be the one discussed here:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359363](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/359363)

---

### Post by dutchslab on 2010-11-04
Yup, whats kind of frustrating is that its not officially queued to be fixed, and its a major issue affecting many users . . . but, its not the only one, so I understand, I just wish to understand how one would get it prioritized it for a fix better.

---

### Post by mio1 on 2010-11-04
> **dutchslab said:**
> I just wish to understand how one would get it prioritized it for a fix better.

I think that's what the "Does this bug affect you?" link on top of the bug page is meant for.

---

### Post by dutchslab on 2010-11-05
Fantastic . . . thanks for pointing that out to me.  I will be sure to ack that link ;)

---

### Post by mattmann72 on 2010-12-11
Any update on this? I have spent the last 2 weeks trying to get my precision 4500 touchpad working. I have had no luck. 

Is there any way to tell edev that this is a synaptics touchpad and then tell it to use the synaptics driver????

---

### Post by tempo500 on 2010-12-14
the last entry with the patched psmouse.ko enables vert scrolling, tap click doesnt work, but i rather have vert scrolling then tap ;)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/+index?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/+index?comments=all)

---

### Post by mattmann72 on 2010-12-21
IIRC there used to be a way in udev to pull the ID of a device and map that ID to a different driver. Is this possible in edev?

---

### Post by Rezista on 2011-01-30
Performing the operations here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/248](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/550625/comments/248) fixes the vertical scrolling issue. Unfortunately suspend/resume stops working :(

---

### Post by jpthank on 2011-05-02
> **dutchslab said:**
> Actually, for some reason, [PHP]modprobe -r psmouse[/PHP] seems to kill my keyboard after a certain amount of time.  Weird.  So I wouldn't reccomend that workaround afterall . . . :(


  i confirmed that i had the same issue.

using sudo modprobe -r psmouse may cause the keyboard dead.:confused:

---

### Post by mio1 on 2011-10-03
just as a pointer for those who still find this old thread, there's a new driver which works without a flaw on my M4500 with 11.04 x64, see

[https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/550625/comments/466](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/550625/comments/466)

main features for me are:
- disable trackpad when typing
- two-finger scrolling

---

