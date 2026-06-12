---
title: "&quot;Disable touchpad while typing&quot; does NOT work"
date: 2011-04-23
forum: Hardware
---

### Post by roosh on 2011-04-23
I'm using a Compaq CQ62-418NR.

The touchpad is not automatically disabled when I type, even though I have checked the "disable touchpad while typing" box in mouse preferences.

Any help?

---

### Post by roosh on 2011-05-12
I think that upgrading to 11.04 has fixed the problem.

But 11.04 introduces the new problem of additional bugginess and unity :(. I'm thinking about switching to mint...

---

### Post by roosh on 2011-05-15
Update: I switched to mint (11 RC) on my laptop and things are looking fine; the touchpad disable feature works fine on it and I don't have to deal with unity :)

I am marking this thread as fixed, as updating to 11.04 did technically fix the touchpad problem.

---

### Post by justoneOS on 2011-05-15
Hello all,
My first post. I purchased a laptop today, a HP G7-1070us. Just finished an install of 
11.04. Per this thread title, on this laptop the disable touchpad while typing option really does not work. Even worse, this model does not include a physical switch to give the user a choice about the touchpad being on or off. 

I did take the time to create a usb-flash-drive and tested the laptop in the store prior to purchase. Many laptops I tried lacked some feature or another "out of the box", many would not boot at all, some would boot if the acpi=off option is selected at boot. This HP model had some of the more essential pieces working on boot. Power management (screen brightness control, battery status) worked, Wifi - could see, but did not have logins (my best guess) so could not access the local hot spot, but could see it and several other secured networks, I concluded it was working, and I would not have any trouble at home.

My discovery of this issue has occurred now at home as I did not bring a mouse with me on testing. In the store I had to use the touchpad, so the issue went unnoticed. 

I hope my post assists others seeking info on this laptop and it's suitability.

I thought about this and lacking a real switch on the laptop, I can see a desire for some kind of keyboard short cut to toggle this feature being rather desirable. Example - wireless mouse battery dies and you can not use the more to turn on the touchpad. 

I respectfully ask for assistance. 
thanks to all

---

### Post by donalgodon on 2011-05-19
I'd really LOVE to find a working solution to disable while typing. It doesn't work for me either on a HP dv6 3150US.

---

### Post by belltown on 2011-05-19
> **donalgodon said:**
> I'd really LOVE to find a working solution to disable while typing. It doesn't work for me either on a HP dv6 3150US.

What model of touchpad do you have? What's the output from:

```
dmesg|grep -i touchpad
``````
grep -i touchpad /var/log/Xorg.0.log
```

---

### Post by Xinu38 on 2011-05-19
```
stoke@stoke-laptop:~$ dmesg | grep -i touchpad
stoke@stoke-laptop:~$ dmesg|grep -i touchpad
stoke@stoke-laptop:~$ grep -i touchpad /var/log/Xorg.0.log
[   407.323] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[   407.323] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[   407.323] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[   407.323] (II) Synaptics touchpad driver version 1.2.2
[   407.323] (II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5888
[   407.323] (II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4844
[   407.323] (II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[   407.323] (II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
[   407.324] (II) SynPS/2 Synaptics TouchPad: buttons: left right
[   407.324] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   407.324] (**) SynPS/2 Synaptics TouchPad: always reports core events
[   407.324] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
[   407.324] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[   407.324] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 0
[   407.324] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[   407.324] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[   407.324] (--) SynPS/2 Synaptics TouchPad: touchpad found
[   407.324] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
stoke@stoke-laptop:~$ dmesg|grep -i touchpad
stoke@stoke-laptop:~$ 

```im also using a compaq, which is also HP, so most likely its the same mousepad as the previous posters, the synaptics touchpad.

not only does it annoy the hell out of me while typing, it is highly sensitive. you cant have 2 fingers on it without the mouse literally bouncing all over the screen. but im down for finding a solution here. it worked to a point in 11.04, but i want it to work on 10.10.

---

### Post by belltown on 2011-05-20
The synaptics touchpads are not very well supported in Ubuntu. An openSUSE developer came out with some patches 9 months ago to enable functionality that was broken (left click to drag not working, right-click not working, tap-to-disable not working, etc.) The patches have not made it into the main Ubuntu distributions yet. The best I've come up with so far is some patches that have been ported from openSUSE, described in [https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809?comments=all](https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809?comments=all). In particular, see [Comment #144]("https://bugs.launchpad.net/ubuntu-release-notes/+bug/582809/comments/144")

I have the same Synaptics touchpad and followed the instructions exactly as laid out in Comment #144 and now have a much more usable touchpad. I'm using Ubuntu 11.04. I'm not sure whether the patches would work on 10.10.

If you do try following these instructions note that in the line that says "ls -1 2*.patch >> series", the "-1" refers to the number 1 not the letter l. That was the only issue I ran into when trying it out.

---

### Post by bach on 2011-05-26
I also have this problem (erratic jumping cursor). I am running Ubuntu 11.04 (64 bit) on a DELL Latitude E6510 notebook. I've had the problem with Ubuntu 10.04 and 10.10 as well. I have no output with 


cribari@darwin:~$ dmesg|grep -i touchpad
cribari@darwin:~$ grep -i touchpad /var/log/Xorg.0.log
cribari@darwin:~$ 

I also don't have the option "disable touchpad while typing" in the mouse preferences configuration. 

Tips are welcome. Thank you.

---

### Post by whakim on 2011-05-26
No such luck. I have an erratic cursor that jumps all over the place, & when I use a USB mouse the scroll wheel randomly locks up. But when I follow the instructions listed in [Comment 144]("https://bugs.launchpad.net/ubuntu- release-notes/+bug/582809/comments/144") as described, this is what I get after the next-to-last line:

```
whakim@xx:~/tmpbuild/xserver-xorg-input-synaptics-1.3.99+git20110116.0e27ce3a$ dpkg-buildpackage -us -uc -rfakeroot
dpkg-buildpackage: export CFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export CPPFLAGS from dpkg-buildflags (origin: vendor): 
dpkg-buildpackage: export CXXFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export FFLAGS from dpkg-buildflags (origin: vendor): -g -O2
dpkg-buildpackage: export LDFLAGS from dpkg-buildflags (origin: vendor): -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package xserver-xorg-input-synaptics
dpkg-buildpackage: source version 1.3.99+git20110116.0e27ce3a-0ubuntu12
dpkg-buildpackage: source changed by Chase Douglas <chase.douglas@ubuntu.com>
dpkg-buildpackage: host architecture amd64
 dpkg-source --before-build xserver-xorg-input-synaptics-1.3.99+git20110116.0e27ce3a
 fakeroot debian/rules clean
rm -f stampdir/genscripts
rm -f debian/*.config \
	      debian/*.postinst \
	      debian/*.postrm \
	      debian/*.preinst \
	      debian/*.prerm
rm -f stampdir/patch
Unapplying patches...Failed to patch temporary files
failed! (check stampdir/log/unpatch for details)
make: *** [unpatch] Error 1
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2


```

So it fails to create the .deb needed for the next step, and I am still stuck with a jumpy cursor. 

I have a Dell Inspiron 1545 with Ubuntu 11.04 amd64, & a Synaptics  touchpad. I've checked the "disable touchpad while typing" option. No real help, the cursor still moves around randomly, freezes randomly. 

I have 3 other laptops running Natty, but they are all i386 & this is the only one with problems.

---

### Post by bach on 2011-05-26
More info: 


cribari@darwin:/usr/share/icons$ cat /proc/bus/input/devices 
I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
U: Uniq=
H: Handlers=event0 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
U: Uniq=
H: Handlers=kbd event2 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=1100f02902002 8380307cf910f001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=05ca Product=1814 Version=0129
N: Name="Laptop_Integrated_Webcam_3M"
P: Phys=usb-0000:00:1a.0-1.4/button
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0011 Vendor=0002 Product=0005 Version=7326
N: Name="ImPS/2 ALPS GlidePoint"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event7 
B: PROP=0
B: EV=7
B: KEY=70000 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0000 Version=0000
N: Name="Dell WMI hotkeys"
P: Phys=wmi/input0
S: Sysfs=/devices/virtual/input/input8
U: Uniq=
H: Handlers=kbd event8 
B: PROP=0
B: EV=13
B: KEY=1101b00000400 100000 e000000000000 0
B: MSC=10

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:02/input/input9
U: Uniq=
H: Handlers=kbd event9 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Sep Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Mic at Ext Right Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
U: Uniq=
H: Handlers=event11 
B: PROP=0
B: EV=21
B: SW=10

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel Line Out at Sep Left Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
U: Uniq=
H: Handlers=event12 
B: PROP=0
B: EV=21
B: SW=40

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel HP Out at Ext Right Jack"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input13
U: Uniq=
H: Handlers=event13 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0003 Vendor=0458 Product=003a Version=0110
N: Name="Genius Optical Mouse"
P: Phys=usb-0000:00:1d.0-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.1/2-1.1:1.0/input/input15
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=70000 0 0 0 0
B: REL=103
B: MSC=10

---

### Post by belltown on 2011-05-27
> **whakim said:**
> No such luck. I have an erratic cursor that jumps all over the place, & when I use a USB mouse the scroll wheel randomly locks up. But when I follow the instructions listed in [Comment 144]("https://bugs.launchpad.net/ubuntu-%20release-notes/+bug/582809/comments/144") as described, this is what I get after the next-to-last line:

So it fails to create the .deb needed for the next step, and I am still stuck with a jumpy cursor. 

I have a Dell Inspiron 1545 with Ubuntu 11.04 amd64, & a Synaptics  touchpad. I've checked the "disable touchpad while typing" option. No real help, the cursor still moves around randomly, freezes randomly. 

I have 3 other laptops running Natty, but they are all i386 & this is the only one with problems.

Try downloading the deb file from [http://www.fileden.com/files/2009/12/6/2678292/synaptics-patch-amd64.deb](http://www.fileden.com/files/2009/12/6/2678292/synaptics-patch-amd64.deb) or [http://ubuntuone.com/p/w2H/](http://ubuntuone.com/p/w2H/) Then go to the folder where you downloaded it and type: sudo dpkg -i synaptics-patch-amd64.deb

---

### Post by cymene on 2012-04-22
I am running Ubuntu 11.10 on a HP dm4-2050us laptop, and have the same problem.
There is a "Mouse/Touchpad" under the Dash home. 
In the setting, there are options to disable touch while typing, enable mouse click with touchpad. But those options don't do any thing.
Really appreciate if there is a solution to this.

---

### Post by wolfsden3 on 2013-04-13
I'm on 13.04 Ubuntu Desktop x64 with the "latest" synaptics touchpad drivers and this is NOT F'ING WORKING!  I'm getting pissed.  How could something so F'ING basic be a bug?  I've been dealing with this horse $*#(* for well over 2 weeks now and nothing has been done to patch something so simple (simple to an Ubuntu developer I suppose :P).

Dell Inspiron 15z
x64
Ubuntu 13.04

dmesg|grep -i touchpad
[   18.633753] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x26c00, board id: 2313, fw id: 1232777
[   18.668168] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input11


COME ON!  Can we get a lil help here?  One person said it's working on Mint but who the hell cares about Mint :P  I like Unity, I think it's great and I don't want to downgrade to some other Debian distro just so I have a functional mouse :-(

---

### Post by yamagami on 2013-05-25
Hi
After tearing hair and sharing your pain here, I found this.
This command will turn on the 'disable while typing' functionality: 

syndaemon -i 1 -K -d 

(with delay of 1 second after starting to type - you can change this). 

Put that in /etc/rc.local to have the daemon run on startup. 

Works a treat :)

---

### Post by lviggiani on 2013-07-02
That solved my problem too!
Thanks!

---

### Post by russomarco on 2014-05-07
> **yamagami said:**
> Hi
After tearing hair and sharing your pain here, I found this.
This command will turn on the 'disable while typing' functionality: 

syndaemon -i 1 -K -d 

(with delay of 1 second after starting to type - you can change this). 

Put that in /etc/rc.local to have the daemon run on startup. 

Works a treat :)

This worked for me too! Thanks a lot!! :D

---

### Post by Dolmio on 2015-01-12
> **yamagami said:**
> 
syndaemon -i 1 -K -d 
Put that in /etc/rc.local to have the daemon run on startup. 


Same problem in Linux Mint 17.1 Cinnamon 64-bit.

Your solution worked perfektly.

Thanks a lot :D

---

### Post by johny why on 2015-06-18
the syndaemon solution worked for me too!
however, the "-d" option froze my mouse completely. I had to remove the -d option to get desired behavior. 
another issue, this solution disables all the touch features of my touchpad-- i cannot tap, i must click. I cannot drag or scroll with touch, i must click-to-drag. 
it's a drag :)

thx!

---

### Post by slawa-09121992 on 2015-08-13
Thank [QUOTE=yamagami;12663324]

syndaemon -i 1 -K -d 
Put that in /etc/rc.local to have the daemon run on startup. 
/QUOTE]

That's solution works on elementary OS Freya.

---

