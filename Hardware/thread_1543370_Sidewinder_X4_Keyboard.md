---
title: "Sidewinder X4 Keyboard"
date: 2010-08-01
forum: Hardware
---

### Post by rawlinc on 2010-08-01
I'm thinking of purchasing the Microsoft Sidewinder X4 keyboard and wanted to know if anybody has had experience using one under Ubuntu.  I'm specifically interested to know whether or not the volume up/down keys and other media control keys (play/pause, next/previous track) work properly. Thanks.

---

### Post by hansdown on 2010-08-01
Hi rawlinc.

I don't know about that one, but I use a logitec access 600, and everything works great.

I got it for $20 at staples.

[http://reviews.logitech.com/7061/2996/reviews.htm](http://reviews.logitech.com/7061/2996/reviews.htm)

---

### Post by tolga9009 on 2010-09-12
Hello!

I was using the Microsoft X4 Keyboard about 2 weeks ago with Ubuntu 10.04. Everything is working fine except the programmable S1 - S6 keys, the bank switcher ("123"-key) and the record key. I also tried out different methods to get those keys working, but they don't send any scancodes (tried with getscancode, showkeys, and dmesg | tail) to map. So, someone has to write a driver to get those special keys working.

I've spent some hours analyzing the traffic between the Sidewinder X4 and my PC. That's what I found out:

> Microsoft Sidewinder X4:

    VID: 045e
    PID: 0768
    REV: 0150

Devices:

    1. VID_045e&PID_0768&REV0150        # USB Composite Device
    2. VID_045e&PID_0768&REV0150&MI_00    # Keyboard / HID
    3. VID_045e&PID_0768&REV0150&MI_01    # Consumer Control Device (S1 - S6, Record, Bank Switch, Play/Pause, Backward, Forward, Mute, Volume Down, Volume Up)

Raw Communication:

Key		Raw Code
________________________________________________________________

S1 - 08 01 00 00 00 08 00 00 00 00
S2 - 08 02 00 00 00 08 00 00 00 00
S3 - 08 04 00 00 00 08 00 00 00 00
S4 - 08 08 00 00 00 08 00 00 00 00
S5 - 08 10 00 00 00 08 00 00 00 00
S6 - 08 20 00 00 00 08 00 00 00 00
Bank Switch - 01 00 00 00 00 00 14 00 01 00 00 00 00 00 00 00
Record - 01 00 00 00 00 00 11 00 01 00 00 00 00 00 00 00
Play/Pause - 01 cd 00 00 00 00 00 00 01 00 00 00 00 00 00 00
Backward - 01 b6 00 00 00 00 00 00 01 00 00 00 00 00 00 00
Forward - 01 b5 00 00 00 00 00 00 01 00 00 00 00 00 00 00
Mute - 01 e2 00 00 00 00 00 00 01 00 00 00 00 00 00 00
Volume Down - 01 ea 00 00 00 00 00 00 01 00 00 00 00 00 00 00
Volume Up - 01 e9 00 00 00 00 00 00 01 00 00 00 00 00 00 00


Status
_______________________________

Bank 1:			07 04
Bank 2:			07 09
Bank 3:			07 11
Auto:			07 0A
Record B1:		07 64
Record B1 (blink):	07 44
Record B2:		07 69
Record B2 (blink):	07 49
Record B3:		07 71
Record B3 (blink):	07 51

The communication between Host and Device while switching the Bank (Bank 2 to Bank 3):

> 000424: Bulk or Interrupt Transfer (UP), 12.09.2010 12:18:10.012 +10.686. Status: 0x00000000
Pipe Handle: 0x500f858 (Endpoint Address: 0x83)
Get 0x8 bytes from the device
 01 00 00 00 00 00 14 00

000426: Class-Specific Request (DOWN), 12.09.2010 12:18:10.012 +0.0
Destination: Interface, Index 1
Reserved Bits: 34
Request: 0x1
Value: 0x307
Get 0x2 bytes from the device

000427: Control Transfer (UP), 12.09.2010 12:18:10.027 +0.015. Status: 0x00000000
Pipe Handle: 0x4ff18a0
 07 09
Setup Packet
 A1 01 07 03 01 00 02 00
Recipient: Interface
Request Type: Class
Direction: Device->Host
Request: 0x1 (Unknown)
Value: 0x307
Index: 0x1
Length: 0x2

000428: Class-Specific Request (DOWN), 12.09.2010 12:18:10.027 +0.0
Destination: Interface, Index 1
Reserved Bits: 34
Request: 0x9
Value: 0x307
Send 0x2 bytes to the device
 07 11

000429: Control Transfer (UP), 12.09.2010 12:18:10.027 +0.0. Status: 0x00000000
Pipe Handle: 0x4ff18a0
 07 11
Setup Packet
 21 09 07 03 01 00 02 00
Recipient: Interface
Request Type: Class
Direction: Host->Device
Request: 0x9 (Unknown)
Value: 0x307
Index: 0x1
Length: 0x2

000430: Bulk or Interrupt Transfer (UP), 12.09.2010 12:18:10.105 +0.078. Status: 0x00000000
Pipe Handle: 0x500f858 (Endpoint Address: 0x83)
Get 0x8 bytes from the device
 01 00 00 00 00 00 00 00

So, the most part is done by IntelliType Pro. S1-S6 (and other special keys) are always sending out the same RAW Data over USB. Depending on which Bank is active, IntelliType can assign different commands. That means for Linux, there should be at least 8 keys, that could be implemented easily (S1-S6, record and bank switcher). On the other hand, (with some effort) we could even make 3 x 6 = 18 (3 Banks, S1-S6), maybe even 3 x 7 = 21 (3 Banks, S1-S6 + record key) or 4 x 7 = 28 (3 Banks + 1 Auto status, S1-S6 + record key) keys work.

If there is someone, who shares the same interest in getting the X4 (and X6) fully working under Linux, please tell me.

Tolga

---

### Post by PowerSource on 2010-10-13
status update please?

---

### Post by tolga9009 on 2010-10-15
> status update please?
I found out, that the G15 / G15v2 / G110 / G19 are very similar to the SideWinder X4, so I tried to customize parts of the code (libg15), so the SideWinder X4 can "talk" with the G15daemon. However, I'm not experienced in coding and reverse engineering at all. After compiling / installing the customized libg15, I started the g15daemon: my keyboard didn't worked anymore. I must have made something wrong, but I'm not sure, what it is. I've also posted on the g15tools forums, but they haven't answered yet (after 4 weeks).

I've done all I could do, but it doesn't work. So, more or less, I gave it up; for now at least.

---

### Post by Shuhushu on 2010-11-09
> **tolga9009 said:**
> I found out, that the G15 / G15v2 / G110 / G19 are very similar to the SideWinder X4, so I tried to customize parts of the code (libg15), so the SideWinder X4 can "talk" with the G15daemon. However, I'm not experienced in coding and reverse engineering at all. After compiling / installing the customized libg15, I started the g15daemon: my keyboard didn't worked anymore. I must have made something wrong, but I'm not sure, what it is. I've also posted on the g15tools forums, but they haven't answered yet (after 4 weeks).

I've done all I could do, but it doesn't work. So, more or less, I gave it up; for now at least.

I tried the same with the same result also.In case someone is interested, here is the patch to libg15 I used:
```
Index: libg15.c
===================================================================
--- libg15.c    (Revision 321)
+++ libg15.c    (Arbeitskopie)
@@ -30,7 +30,7 @@
 #include "config.h"
 
 static usb_dev_handle *keyboard_device = 0;
-static int libg15_debugging_enabled = 0;
+static int libg15_debugging_enabled = 1;
 static int enospc_slowdown = 0;
 
 static int found_devicetype = -1;
@@ -48,6 +48,7 @@
     DEVICE("Logitech G15 v2",0x46d,0xc227,G15_LCD|G15_KEYS|G15_DEVICE_5BYTE_RETURN),
     DEVICE("Logitech Gamepanel",0x46d,0xc251,G15_LCD|G15_KEYS|G15_DEVICE_IS_SHARED),
     DEVICE("Logitech G13",0x46d,0xc21c,G15_LCD|G15_KEYS|G15_DEVICE_G13),
+    DEVICE("Microsoft Sidewinder X4",0x45e,0x768,G15_DEVICE_IS_SHARED),
     DEVICE(NULL,0,0,0)
 };
```
I have been experimenting with G15_DEVICE_IS_SHARED and all the other possiblities all with same result

---

### Post by bart13 on 2011-01-09
Maybe a small bump, but did someone get this to work? I was also trying to get my SideWinder to work with Ubu, but I've failed..

---

### Post by joshuafcole on 2011-02-17
Big bump! Would be interested in helping code up a solution to this. I ought to have some free time in the latter half of March to get started on the problem. There looks to be a lot of good information here, and while I don't currently specialize in C/++, i'm sure it can't be a big leap after becoming mostly fluent umpteen other programming languages. =P 

If any of the OP's who provided the treasure troves of information are still interested in working on this, i'd love to chat via email or IRC to brainstorm.

Hope this goes well! (My other plan was to hardware bash a middle man to listen for the codes... not exactly the easiest project for someone who's only worked in analog circuits!)

---

### Post by ghost18uk on 2011-04-02
Did anyone get anywhere with this?

---

### Post by Cerealklr on 2011-04-03
No one has gotten back to me, but i'm still very interested in getting this worked on. As I've already said, I have no driver experience and prefer higher level languages (e.g. Python, LISP), but would be more than happy to buckle down in C or even ASM if I had to in order to get access to the macro keys. I'm a bit of an automation buff and it'd be awesome to have a control set built into my keyboard rather than having to build my own hardware console. =]

---

### Post by tolga9009 on 2011-04-28
I worked on it a bit more, but I more or less gave it up, since I had no success. In the meantime, erazor_de has worked on Roccat hardware and got them working on Linux, including the Arvo.
Roccat Arvo is a gaming keyboard with 3 extra buttons; I don't know how they work, since I don't have an Arvo, but I'd recommend to look at it a bit. He also published usb_revtools; reverse engineering tools he used for his projects. U can visit his project here: [http://sourceforge.net/projects/roccat/](http://sourceforge.net/projects/roccat/). This could be another possibility to get the X4 running!
Personally, I still don't have the time nor the knowledge to work on this now. The SideWinder X4 became very popular in the past months and I think it's just a matter of time, until someone get this one working.

---

### Post by BoogeyCz on 2011-06-13
Hello I've started working on developing driver for SideWinder X4. Please contact me and help me. I will send you the driver for testing ;)

Thank you so much.

Contact:
jabber: boogey(at)jabbim(dot)cz    preffered
icq: 286(-)799(-)529

---

### Post by joshuafcole on 2011-06-13
Added! I'll ping you momentarily. Alternatively, ping me at joshua<the letter f>cole@jabber.org

---

### Post by Da-mog on 2012-01-28
BUMP: are there any drivers for the M$ sidewinder 4, works great in win7, just tried in unbuntu didn't know if you can get the marco keys/recprd to work?

help anybody?:confused:

---

### Post by BoogeyCz on 2012-01-28
[https://gitorious.org/microsoft-sidewinder-x4](https://gitorious.org/microsoft-sidewinder-x4)

Check this. It's driver I've done. But now it is possible only control LED(1, 2, 3, AUTO) and S1-S6 keys are working but no action is related to them. I don't have so much knowledge to do this work but I start it. Anyone is able to improve it?

---

### Post by SemiJew on 2012-01-29
Is there any way to get the macroing software (intellitype) to work on Linux? I have an X4 and recently switched to Ubuntu but the faggots at M$ aren't distributing a Linux version.

I guess I'll just try running it under Wine.

---

### Post by BoogeyCz on 2012-01-29
Yes but I think that we need kernel module(driver) and user-space utlity to support macro keys.

---

### Post by joshuafcole on 2012-02-01
Heyo! Compiled it with make modules && sudo make modules_install, but it doesnt' seem to be picking up my keyboard! I visually inspected the code and it looks fine. Any ideas? (or notes on what debug information might be helpful?)

Note: The LED indicator lights are not functioning and XEV reports nothing when I press the macro key and S1-6.

Of potential interest:


> josh@Hyperion [07:36:12] [~/repos/external/modules] 
-> % sudo modprobe hid-microsoft-sidewinder
FATAL: Module hid_microsoft_sidewinder not found.

josh@Hyperion [07:36:20] [~/repos/external/modules] 
-> % sudo modprobe hid-microsoft-sidewinder-x4 
FATAL: Module hid_microsoft_sidewinder_x4 not found.

And more info:
Loaded the compiled drivers manually via insmod. lsmod looks good now. Unplugged and replugged the device. Got a clean hit in kern.log
> Feb  1 19:41:12 Hyperion kernel: [ 1921.656060] usb 6-2: USB disconnect, device number 2
Feb  1 19:41:15 Hyperion kernel: [ 1925.296039] usb 6-2: new full speed USB device number 3 using uhci_hcd
Feb  1 19:41:16 Hyperion kernel: [ 1925.528439] input: Microsoft Microsoft® SiderWinderTM X4 Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.0/input/input7
Feb  1 19:41:16 Hyperion kernel: [ 1925.528572] generic-usb 0003:045E:0768.0004: input,hidraw1: USB HID v1.11 Keyboard [Microsoft Microsoft® SiderWinderTM X4 Keyboard] on usb-0000:00:1d.0-2/input0
Feb  1 19:41:16 Hyperion kernel: [ 1925.544203] input: Microsoft Microsoft® SiderWinderTM X4 Keyboard as /devices/pci0000:00/0000:00:1d.0/usb6/6-2/6-2:1.1/input/input8
Feb  1 19:41:16 Hyperion kernel: [ 1925.544335] generic-usb 0003:045E:0768.0005: input,hidraw2: USB HID v1.11 Keyboard [Microsoft Microsoft® SiderWinderTM X4 Keyboard] on usb-0000:00:1d.0-2/input1

But still no interactivity with the special keys. Curious.

And finally,
I added it to my /etc/modules so it'd be loaded at startup and swapped over to TTY1 to try showkey. Still nothing.

---

### Post by joshuafcole on 2012-02-01
Okay, we got it figured out! The solution was to add this code to the file:
/etc/udev/rules.d/90-microsoft-sidewinder-x4.rules

```
SUBSYSTEM=="hid", DRIVER=="generic-usb", ATTRS{idVendor}=="045e", ATTRS{idProduct}=="0768", ACTION=="add", RUN+="/bin/sh -c '/sbin/modprobe hid-microsoft-sidewinder-x4; if test -d /sys/bus/hid/drivers/generic-usb; then /bin/echo -n %k >/sys/bus/hid/drivers/generic-usb/unbind
```

In order to change the status of the macro LEDs, change the contents of the file:
/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.1/0003:045E:0768.0005/sidewinder-x4/sidewinder-x4_0/actual_profile

to "0", "1", "2", or "3" respectively, with 0 being "auto" and 1-3 being self explanatory. Now to write a daemon (or patch the driver... haven't decided yet) to toggle between the bank of 3 sets of special keys.

NOTE: The file is dependent on the USB port your device is plugged into, and potentially other things. To find the appropriate path, use the command
```
find /sys -name actual_profile
```
And find the entry with "sidewinder-x4" in the file path.

Update:
Mapped all the keys sanely to F13-F20 and set up everything but a single line for automatic profile tracking. Don't uncomment that line yet. There's a rogue mutex or something that locks the system down AFTER it updates the LED. 0.o No idea what's up with it. Will try and work with Boogey tomorrow on it. 

Cheers!

Update:
Pushed my changes to boogey's repository.

---

### Post by tolga9009 on 2012-02-12
I love you guys! Great work ;)! In the meantime, Roccat released a beautiful keyboard (Isku), with hardware macros - so there is no need for Linux drivers. I was tired of waiting and bought it - but I will probably switch over to the SideWinder X4 again ;)!

Keep it up :D! This is going to be interesting :popcorn:!

---

### Post by joshuafcole on 2012-02-12
Update: Turns out the issue with tracking the profile changes in the driver is larger than anticipated! We get a fun deathloop after it updates the LED and I'm not familiar enough with debugging at that low of a level to figure out how to resolve it. I'll probably just write a userspace daemon and have udev grant it control over the keyboard to keep track of the profile. That'll also enable the macro-recording (though I'm thinking I'll include a way to disable that for people that just want 18 regular macro keys like I do). =P

---

### Post by Evilandi666 on 2012-03-20
Funny, didn't notice that there were updates since Post #13. Meanwhile I wrote a daemon to catch all the keys, it is called "x4daemon", you find it here: [http://geekparadise.de/x4daemon/](http://geekparadise.de/x4daemon/)

But I didn't get the LEDs working, because there are some missing initialisation codes (or something like that) in your usb captures. While searching howto sniff usb devices in Windows 7 I found the updates here, so next version of x4daemon will include working leds, hopefully. But I will seperate them from the banks, because there is no need (for me) to use three keybanks - I want to use them as status leds, for new notifications (email,chat,etc.). 

Thx for your great work on capturing those things! =D>

Edit: Still no luck getting the leds to work with libusb. Don't know what I am doing wrong here...

---

### Post by tolga9009 on 2012-03-25
Hi Evilandi ;)!

Thanks for your great works! You're the people who move everything forward. I'm sure, there are more people out there, waiting for a SideWinder X4/X6 (which are btw. very popular keyboards) driver, but either aren't aware of the work already done, or are just to lazy to register here on these forums and thank you :)!
As for the USB capture, I had used the trial version of USB Monitor from HHD Software from [http://www.hhdsoftware.com/usb-monitor](http://www.hhdsoftware.com/usb-monitor). I tried alot of alternatives on both, Linux and Windows, and USB Monitor seemed to be the most comfortable one. If you want to sniff USB for yourself, you might try that one ;)!

Good luck and keep up the good work ;)!

---

### Post by hurinth on 2012-06-14
Tolga, did you get the Roccat Isku to work with ubuntu at a 100%?

Thanks mate.

---

### Post by tolga9009 on 2012-06-17
> Tolga, did you get the Roccat Isku to work with ubuntu at a 100%?

Sorry, I've never tried it with Ubuntu; I'm using Arch Linux for quite some time now. You need the GUI Tool to configure your macros (Windows Tool, or use roccat-tool from sourceforge.net) - the macros will be executed without the need of a driver. You just need them for configuration.
For a Linux-only system, you need roccat-tools for proper configuration; the driver modules are already included in the 3.0+ Linux Kernels. I installed the roccat-tools from AUR (which is Arch Linux specific) [https://aur.archlinux.org/packages.php?ID=57300](https://aur.archlinux.org/packages.php?ID=57300). As for Ubuntu, download the source from [http://sourceforge.net/projects/roccat/files/roccat-tools/](http://sourceforge.net/projects/roccat/files/roccat-tools/), compile and install it.

Good luck,
Tolga

---

### Post by KRavEN on 2012-10-17
> **joshuafcole said:**
> Heyo! Compiled it with make modules && sudo make modules_install, but it doesnt' seem to be picking up my keyboard! I visually inspected the code and it looks fine. Any ideas? (or notes on what debug information might be helpful?)

Note: The LED indicator lights are not functioning and XEV reports nothing when I press the macro key and S1-6.

Of potential interest:




And more info:
Loaded the compiled drivers manually via insmod. lsmod looks good now. Unplugged and replugged the device. Got a clean hit in kern.log


But still no interactivity with the special keys. Curious.

And finally,
I added it to my /etc/modules so it'd be loaded at startup and swapped over to TTY1 to try showkey. Still nothing.

Just FYI, after installing the modules do "sudo depmod" and the modprobe commands will then work.

---

### Post by KRavEN on 2012-10-17
Here's what I've tried on Ubuntu 12.04

I cloned the git repo and did the following:
```

make modules
sudo make modules_install
sudo depmod
sudo modprobe hid-microsoft-sidewinder-x4

lsmod | grep sidewinder
hid_microsoft_sidewinder_x4    13110  0 
hid_microsoft_sidewinder    13582  1 hid_microsoft_sidewinder_x4
hid                    99559  2 hid_microsoft_sidewinder_x4,usbhid

```
Everything looks good and I have sidewinder-x4 in /sys/bus/hid/drivers

Now I add the 90-microsoft-sidewinder-x4.rules file to /etc/udev/rules.d

Here's the content.  joshuafcole's post didn't have the full command so maybe I'm missing something?
```
ACTION=="add", SUBSYSTEM=="hid", DRIVER=="generic-usb", ATTRS{idVendor}=="045e", ATTRS{idProduct}=="0768",  RUN+="/bin/sh -c '/sbin/modprobe hid-microsoft-sidewinder-x4; if test -d /sys/bus/hid/drivers/generic-usb; then /bin/echo -n %k >/sys/bus/hid/drivers/generic-usb/unbind;fi'"
```

Now I reboot and the keyboard doesn't work.  Remove the udev rule and I'm okay.

Am I missing something?  Anyone else have this driver working?

---

### Post by morrcahn on 2013-02-11
I am going to assume that this thread is still running since it isn't closed.

I just purchased this exact keyboard and the audio keys all work. I am currently looking around to see if I can get the macro keys to work. Hopefully I can find a driver already installed or to download to get those to work.

---

### Post by blueshirt3k on 2013-03-14
I just summarize things those who need to use [this]("https://gitorious.org/microsoft-sidewinder-x4") useful driver on Linux Kernel 3.8 (Ubuntu 13.04).

```

git clone https://gitorious.org/microsoft-sidewinder-x4
cd microsoft-siderwinder-x4
make
sudo make modules_install
sudo depmod -a

```

Created this udev rule file:
/etc/udev/rules.d/90-microsoft-sidewinder-x4.rules

```
ACTION=="add", SUBSYSTEM=="hid", DRIVER=="hid-generic", ATTRS{idVendor}=="045e", ATTRS{idProduct}=="0768",  RUN+="/bin/sh -c '/sbin/modprobe hid-microsoft-sidewinder-x4; if test -d /sys/bus/hid/drivers/hid-generic && test -d /sys/bus/hid/drivers/sidewinder-x4; then /bin/echo -n %k > /sys/bus/hid/drivers/hid-generic/unbind; /bin/echo -n %k > /sys/bus/hid/drivers/sidewinder-x4/bind;fi'"
```

---

### Post by Briesmi on 2013-04-18
> **blueshirt3k said:**
> 
```

git clone https://gitorious.org/microsoft-sidewinder-x4

```

Hello blueshirt,

when i try the command i'll geht the error:

```
Cloning into 'microsoft-sidewinder-x4'... fatal: https://gitorious.org/microsoft-sidewinder-x4/info/refs not found: did you run git update-server-info on the server?
```

Do u know howto fix it?

Thx!

---

### Post by linoskoczek on 2013-04-23
Try this:

```
git clone git://gitorious.org/microsoft-sidewinder-x4/microsoft-sidewinder-x4.git
```

---

### Post by nick-dimizas on 2013-08-03
Is anyone aware of this? [https://github.com/Wattos/LinuxSidewinderX6.git](https://github.com/Wattos/LinuxSidewinderX6.git) 
I tested it against the x4 but it does not work. It seems to be very close to the solution for the x4

---

### Post by tolga9009 on 2013-11-06
Sorry everyone, I had technical issues logging in - but I finally got it working. Thank you nick-dimizas, I'll look into it will try get it working on the Sidewinder X4 this weekend.

---

### Post by tolga9009 on 2013-11-09
Good news, I got the LEDs working for profile switching. Now, I'm gonna try to get the bank-switch button to work and try out profile switching. Kudos to Wattos! He got really cool drivers there!

//Edit: Holy mother of God! I finally got it working! The code is uber dirty, but hey; it's working! I'm not a Dev, so sorry for dirty code, but it can be a starting point for the Devs from now on. I've worked on x4daemon; I'm currently preparing some last modifications. The cool news: I've currently set up 6 profiles (1, 2, 3 and 1+Auto, 2+Auto, 3+Auto); but it's possible to enable more than 1 LED at a time! You can for example enable LED 1+2 or 1+3 and enable more profiles.

This is how it works: Bank 1 LED is 0x0704 (the last part is the interesting part); 0x04 is 0000 0100 in binary. The "1" in this particular position stands for LED1. LED2 is 0000 1000; which is 0x08 (0x09 also works for LED2 - but I don't know, what the last Bit does). LED 3 is 0001 0000, which is 0x10. LED Auto is 0000 0010, which is 0x02. So, if i want to enable Auto and LED 3 for example, I need to calculate 0001 0000 + 0000 0010, which is 0001 0010 or 12. This way, you can enable almost every single combination of LEDs. Alright guys, now it's time for us to get really advanced setups. Again, this is a quick-and-dirty solution, but I will work on a solution like Wattos' drivers - but this may take time, because I'm just starting with C. Thank You Andreas and Wattos for your great Job!!

//Edit2: Here is a quick demonstration of 12 profiles: [http://www.youtube.com/watch?v=GNv5AfFCQk4](http://www.youtube.com/watch?v=GNv5AfFCQk4).

profiles.patch (I have added it here, so you don't have to register in order to download it - it can be downloaded as profiles.txt for registered users):
```
--- x4daemon.c	Wed Sep  5 13:24:58 2012
+++ x4daemon-profiles.c	Sat Nov  9 21:32:04 2013
@@ -40,11 +40,11 @@
 // Change to your own values if you like to, possible values
 // are found in /usr/include/linux/input.h.
 // You can also use integer values like 113 (stands for KEY_MUTE)
-int keys[15] = {KEY_PROG1,KEY_PROG2,KEY_WWW,
-                        KEY_MAIL,KEY_COMPUTER,KEY_PHONE,KEY_MEDIA,
-                        KEY_RECORD,KEY_PLAYPAUSE,KEY_PREVIOUSSONG,
-                        KEY_NEXTSONG, KEY_MUTE,KEY_VOLUMEUP,
-                        KEY_VOLUMEDOWN,KEY_CALC};
+int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
 
 // Numbers have to be converted from hex to integer
 // Exmplae: For calculator button you get when pressing&releasing:
@@ -103,7 +103,9 @@
 int ret; // variable for return values
 int j; // some variable for loops
 pid_t pid,sid;
-int max_tries=3; // how often probe for automatic loaded uinput module to show up
+int max_tries = 3; // how often probe for automatic loaded uinput module to show up
+uint8_t profile = 1; // set profile
+bool changed = false; // for bank-switch detecting
 
 // Prints message to syslog or stdout 
 // as Warning if warning is true && debug is true
@@ -476,84 +478,219 @@
         return gleich;
 }
 
+// Profile switching
+void set_profile()
+{
+	output("Setting profile", false, false, true, true);
+
+	uint8_t data[2];
+	data[0] = 0x7;
+
+	if (profile == 1)
+	{
+		data[1] = 0x4; // LED 1
+		// here you can set profile specific hotkeys
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 2)
+	{
+		data[1] = 0x8; // LED 2
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 3)
+	{
+		data[1] = 0x10; // LED 3
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 4)
+	{
+		data[1] = 0x6; // LED 1 + LED A
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 5)
+	{
+		data[1] = 0xA; // LED 2 + LED A
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 6)
+	{
+		data[1] = 0x12; // LED 3 + LED A
+		// here you can set profile specific hotkeys
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 7)
+	{
+		data[1] = 0xC; // LED 1 + LED 2
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 8)
+	{
+		data[1] = 0x14; // LED 1 + LED 3
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 9)
+	{
+		data[1] = 0x18; // LED 2 + LED 3
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 10)
+	{
+		data[1] = 0x1C; // LED 1 + LED 2 + LED 3
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else if (profile == 11)
+	{
+		data[1] = 0x1E; // LED 1 + LED 2 + LED 3 + LED A
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+	else // profile 12
+	{
+		data[1] = 0x7E; // LED 1 + LED 2 + LED 3 + LED A + LED R
+		int keys[15] = {KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1,KEY_PROG1,
+                        KEY_PROG1,KEY_PROG1};
+	}
+
+	libusb_control_transfer(ludh,
+							LIBUSB_REQUEST_TYPE_CLASS | LIBUSB_RECIPIENT_INTERFACE | LIBUSB_ENDPOINT_OUT,
+							LIBUSB_REQUEST_SET_CONFIGURATION, 0x307, 0x1, data, sizeof(data), 0);
+
+	return;
+}
+
 // decides which button was pressed
 // and calls send_keycode with the correct keycode from keys[]
 // release codes are ignored
 void decide(unsigned char *buffer, int transferred)
 {
         if (compare(buffer, s1, transferred))
-       {
-                output("Button pressed:S1", false, false, true, true);
+        {
+                output("Button pressed: S1", false, false, true, true);
                 send_keycode(keys[0]);
         }
         else if (compare(buffer, s2, transferred))
         {
-                output("Button pressed:S2", false, false, true, true);
+                output("Button pressed: S2", false, false, true, true);
                 send_keycode(keys[1]);
         }
         else if (compare(buffer, s3, transferred))
         {
-                output("Button pressed:S3", false, false, true, true);
+                output("Button pressed: S3", false, false, true, true);
                 send_keycode(keys[2]);
         }
         else if (compare(buffer, s4, transferred))
         {
-                output("Button pressed:S4", false, false, true, true);
+                output("Button pressed: S4", false, false, true, true);
                 send_keycode(keys[3]);
         }
         else if (compare(buffer, s5, transferred))
         {
-                output("Button pressed:S5", false, false, true, true);
+                output("Button pressed: S5", false, false, true, true);
                 send_keycode(keys[4]);
         }
         else if (compare(buffer, s6, transferred))
         {
-                output("Button pressed:S6", false, false, true, true);
+                output("Button pressed: S6", false, false, true, true);
                 send_keycode(keys[5]);
         }
         else if (compare(buffer, bank_switch, transferred))
         {
-                output("Button pressed:Bank_Switch", false, false, true, true);
-                send_keycode(keys[6]);
+                output("Button pressed: Bank_Switch", false, false, true, true);
+                if (profile < 12) // check if profile count is under the profile limit; OPTIONAL: new variable to set profile limit
+                {
+					profile++;
+				}
+                else
+                {
+					profile = 1; // if profile reached the limit, set it to first profile
+				}
+				changed = true;
+				printf("Profile: %u\n", profile);
         }
         else if (compare(buffer, record, transferred))
         {
-                output("Button pressed:Record", false, false, true, true);
+                output("Button pressed: Record", false, false, true, true);
                 send_keycode(keys[7]);
         }
         else if (compare(buffer, play_pause, transferred))
         {
-                output("Button pressed:Play/Pause", false, false, true, true);
+                output("Button pressed: Play/Pause", false, false, true, true);
                 send_keycode(keys[8]);
         }
         else if (compare(buffer, prev, transferred))
         {
-                output("Button pressed:Previous", false, false, true, true);
+                output("Button pressed: Previous", false, false, true, true);
                 send_keycode(keys[9]);
         }
         else if (compare(buffer, next, transferred))
         {
-                output("Button pressed:Next", false, false, true, true);
+                output("Button pressed: Next", false, false, true, true);
                 send_keycode(keys[10]);
         }
         else if (compare(buffer, mute, transferred))
         {
-                output("Button pressed:Mute", false, false, true, true);
+                output("Button pressed: Mute", false, false, true, true);
                 send_keycode(keys[11]);
         }
         else if (compare(buffer, vol_up, transferred))
         {
-                output("Button pressed:Volume_Up", false, false, true, true);
+                output("Button pressed: Volume_Up", false, false, true, true);
                 send_keycode(keys[12]);
         }
         else if (compare(buffer, vol_down, transferred))
         {
-                output("Button pressed:Volume_Down", false, false, true, true);
+                output("Button pressed: Volume_Down", false, false, true, true);
                 send_keycode(keys[13]);
         }
         else if (compare(buffer, calc, transferred))
         {
-                output("Button pressed:Calculator", false, false, true, true);
+                output("Button pressed: Calculator", false, false, true, true);
                 send_keycode(keys[14]);
         }
         else if (compare(buffer, s_release, transferred))
@@ -667,7 +804,7 @@
         }  
         else
         {
-                output("Sucessfully claimed interface..", false, false, true, true);
+                output("Successfully claimed interface...", false, false, true, true);
                 return true;
         }
 }
@@ -804,6 +941,8 @@
 
                 ret=libusb_submit_transfer(lt);
 
+				set_profile();
+
                 if(ret)
                 {
                         output("Can't submit libusb interrupt transfer.#1", false, true, false, true);
@@ -845,5 +984,10 @@
         while (1)
         {
                 libusb_handle_events(luc); //blocking, no sleep() needed
+                if(changed)
+				{
+					set_profile();
+					changed = false;
+				}
         }
 }
```

//Edit3: I think the best way to get the X4 properly working would be writing a kernel driver, to enable basic functionality of extra keys (so they send keycodes - this includes profile switching; Bank 1 + S1 should generate a different Keycode than Bank 2 + S1 and so on) and to have an API for other programs to get access to the LEDs (like for Mail Notification etc. - especially Auto and Record (Solid + Blinking)). Then, we should try to get it into upstream Kernel. I think that's the cleanest way of doing it; better than having a daemon running. For macros, we can use external programs - there are plenty of them.

---

### Post by tolga9009 on 2013-11-17
I've tried creating a kernel driver with no luck. The best option would be to dig into the Code of erazor_de ([http://sourceforge.net/projects/roccat/?source=directory](http://sourceforge.net/projects/roccat/?source=directory)) and make the Sidewinder X4 compatible with the Roccat Tool. He already got his code in upstream Linux Kernel! If we could get the SideWinder X4 flawlessly work with his tools, I'm sure, he'd add our kernel module, too. He already wrote drivers for several keyboards, similar to the Sidewinder X4; it shouldn't be big trouble I think. His latest drivers are the Ryos ones. Definitely check them out! Hopefully, we can have a fully working solution, soon!

---

### Post by tolga9009 on 2013-12-05
I'm attempting another try this weekend. I have greatly improved on C and Linux kernel module development. Gonna work on BoogeyCz's and joshuafcole's code and gonna do a little bit more reverse engineering. Still, we have a working x4daemon now as a fallback - I'll write another, small patch for it this weekend, cleaning up the code a bit, setting up 3 profiles as default and assigning S1 - S6 to F13 - F18 on bank 1, F14 - F19 on bank 2 and F20 - F25 on bank 3. This is a pretty generic way of doing it, I think. As for macros, there are tons of external applications, we don't need our own solution.

---

### Post by joshuafcole on 2013-12-05
Hey there. Just writing in to mention that I'm available to help interpret the old code and support somebody else taking the reigns on the project. I apologize that I fell off the map, but the project hadn't really gained much steam at the time and work and life cropped up. At any rate, feel free to shoot me a message if you'd like to chat about the code and possible avenues of improvement. Either way, good luck!

---

### Post by tolga9009 on 2013-12-08
Thank you for your support; I'll definitely come back to you, when I need some help ;)! Unfortunately, I couldn't really work on the code this weekend, because I was only fighting with getting the current version to work. Using the udev rules and loading the modules with modprobe and depmod didn't really worked. So didn't loading the modules via insmod. I'm currently running ArchLinux x64 Kernel 3.12 - I've also tried Ubuntu 13.10 without any luck. The problem is, I'm running a very bleeding edge notebook, so I can't really go back to Ubuntu 13.04 - which might work, I don't know. I've also tried rewriting linux/drivers/hid/hid-microsoft.c (really, the ergonomic keyboard's extra keys seem to have the same USB code transferred as the Sidewinder X4's extra keys!), but again, no way getting it to work (ofc, I've added the hid id) - I can compile it, I can insmod / modprobe it, but there is no way the Sidewinder is interacting with the module. I've written some basic modules and a hello world module, to check functionality - they're working. But there seems to be something odd with this module. I'm trying to set it up with DKMS now.

But the good news is, that x4daemon really runs very well. Everything is working fine. There are some issues left, but I'll get it done soon. Still, since there are no F25 - F30 keys declared in input.h, I had to improvise with FN+F7 - FN+F12. Else, it's working totally fine.

---

### Post by stefan_achatz on 2013-12-09
If you haven't blacklisted the device in the generic driver it's not enough to just load the module. You have to manually unbind/rebind the device from one driver to another.

---

### Post by tolga9009 on 2013-12-09
Stefan, thank you sooo much! I'm really new to this kind of stuff and I'm really happy about the help! With your advice, I got it working in about 10 minutes, without any udev rules or any hacking. Simply loading the modules, unbind/bind and everything works :)! Im gonna write a little script to automate it for the whole process; but for now, everything is working fine! I've also loaded the hid-microsoft.c driver, which is already a kernel module, written for some Microsoft hardware; including the Ergonomic Keyboard 4000, which has similar Extra keys to the Sidewinder X4. And guess what: Bank Switch Button, Record Button and S1 is working almost out of the box (after adding the PID to hid-ids.h and to hid-microsoft.c)! I think we need VERY little effort to make S2 - S6 work too; the positive thing about hid-microsoft.c: as soon as we got it done, we can get in touch with the maintainer of it and get it to the upstream Linux kernel very fast! I'll learn from joshuafcole's and BoogeCz's code and implement it to hid-microsoft.c. But again: I'm not very experienced - I'm just getting started; I'll eventually get a working solution, but you guys need to review and optimize it, before it can get upstream.

Also, does anyone have an idea what we could do with the Auto LED and Record LED + Record Button (WWW / E-Mail / Prog1 / [?]) ? I have no idea what to do with them, since they have no real function without a userspace program.

//Edit: Wow, this was fast. I just wanted to say, that I got S1 - S6 working with hid-microsoft.c now! Gonna work on the LEDs tomorrow! This looks promising!

//Edit 2: So far, I have a semi-working setup for the profiles and the S1 - S6 keys. I have implemented nested switches, to differentiate between which button + which profile. It works. However, I haven't implemented a solution for the bank switching. A simple "profile++" won't cut it, because it's out of the scope; we would need a global variable, which is not welcome in kernel development. The best solution is to write 2 sysfs functions: ms_sidewinder_set_profile() and ms_sidewinder_get_profile(). This way, we can dynamically set and read the profile from sysfs - maybe it's even the only way to do it properly. I haven't worked on optimizations, if you have any suggestions, please tell me.

You can download the .patch as .txt attachment. I'll additionally add it here in CODE brackets.

hid-microsoft.patch
```
--- hid-microsoft.c.orig	2013-12-10 23:59:20.912828927 +0100
+++ hid-microsoft.c	2013-12-10 23:57:18.516427231 +0100
@@ -29,6 +29,7 @@
 #define MS_NOGET		0x10
 #define MS_DUPLICATE_USAGES	0x20
 #define MS_RDESC_3K		0x40
+#define MS_SIDEWINDER	0x80
 
 static __u8 *ms_report_fixup(struct hid_device *hdev, __u8 *rdesc,
 		unsigned int *rsize)
@@ -95,6 +96,82 @@
 	return 1;
 }
 
+static int ms_sidewinder_kb_quirk(struct hid_input *hi, struct hid_usage *usage,
+		unsigned long **bit, int *max)
+{
+	int sidewinder_profile = 1; /* Initial profile. Soon to be replaced by sysfs. */
+	set_bit(EV_REP, hi->input->evbit);
+	switch (usage->hid & HID_USAGE) {
+	/* We need sysfs profile switchting here.
+	 * Todo: write function ms_sidewinder_set_profile() and
+	 * ms_sidewinder_get_profile(), then replace sidewinder_profile
+	 * with ms_sidewinder_get_profile(). Talking with the leds is an
+	 * easy task; we will get it done after sysfs.
+	 *
+	 * This is the Bank_Switch button: case 0xfd15.
+	 * 
+	 * Still needing ideas for the Record button.
+	 */
+	case 0xfb01: /* S1 */
+		switch (sidewinder_profile) {
+			case 1: ms_map_key_clear(KEY_F13);	break; /* Bank 1 */
+			case 2: ms_map_key_clear(KEY_F19);	break; /* Bank 2 */
+			case 3: ms_map_key_clear(KEY_FN_F1);	break; /* Bank 3 */
+			default:
+				return 0;
+		}
+		break;
+	case 0xfb02: /* S2 */
+		switch (sidewinder_profile) {
+			case 1: ms_map_key_clear(KEY_F14);	break;
+			case 2: ms_map_key_clear(KEY_F20);	break;
+			case 3: ms_map_key_clear(KEY_FN_F2);	break;
+			default:
+				return 0;
+		}
+		break;
+	case 0xfb03: /* S3 */
+		switch (sidewinder_profile) {
+			case 1: ms_map_key_clear(KEY_F15);	break;
+			case 2: ms_map_key_clear(KEY_F21);	break;
+			case 3: ms_map_key_clear(KEY_FN_F3);	break;
+			default:
+				return 0;
+		}
+		break;
+	case 0xfb04: /* S4 */
+		switch (sidewinder_profile) {
+			case 1: ms_map_key_clear(KEY_F16);	break;
+			case 2: ms_map_key_clear(KEY_F22);	break;
+			case 3: ms_map_key_clear(KEY_FN_F4);	break;
+			default:
+				return 0;
+		}
+		break;
+	case 0xfb05: /* S5 */
+		switch (sidewinder_profile) {
+			case 1: ms_map_key_clear(KEY_F17);	break;
+			case 2: ms_map_key_clear(KEY_F23);	break;
+			case 3: ms_map_key_clear(KEY_FN_F5);	break;
+			default:
+				return 0;
+		}
+		break;
+	case 0xfb06: /* S6 */
+		switch (sidewinder_profile) {
+			case 1: ms_map_key_clear(KEY_F18);	break;
+			case 2: ms_map_key_clear(KEY_F24);	break;
+			case 3: ms_map_key_clear(KEY_FN_F6);	break;
+			default:
+				return 0;
+		}
+		break;
+	default:
+		return 0;
+	}
+	return 1;
+}
+
 static int ms_input_mapping(struct hid_device *hdev, struct hid_input *hi,
 		struct hid_field *field, struct hid_usage *usage,
 		unsigned long **bit, int *max)
@@ -104,15 +181,17 @@
 	if ((usage->hid & HID_USAGE_PAGE) != HID_UP_MSVENDOR)
 		return 0;
 
-	if (quirks & MS_ERGONOMY) {
-		int ret = ms_ergonomy_kb_quirk(hi, usage, bit, max);
-		if (ret)
-			return ret;
-	}
+	if ((quirks & MS_ERGONOMY) &&
+			ms_ergonomy_kb_quirk(hi, usage, bit, max))
+		return 1;
 
 	if ((quirks & MS_PRESENTER) &&
 			ms_presenter_8k_quirk(hi, usage, bit, max))
 		return 1;
+		
+	if ((quirks & MS_SIDEWINDER) &&
+			ms_sidewinder_kb_quirk(hi, usage, bit, max))
+		return 1;
 
 	return 0;
 }
@@ -193,6 +272,8 @@
 static const struct hid_device_id ms_devices[] = {
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_SIDEWINDER_GV),
 		.driver_data = MS_HIDINPUT },
+	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_SIDEWINDER_X4),
+		.driver_data = MS_SIDEWINDER },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_NE4K),
 		.driver_data = MS_ERGONOMY },
 	{ HID_USB_DEVICE(USB_VENDOR_ID_MICROSOFT, USB_DEVICE_ID_MS_NE4K_JP),

```

---

### Post by tolga9009 on 2013-12-12
Ok everyone, I'm really happy to finally tell you, that I got a working solution now. There are still some flaws (e.g. profile switching counts backward, instead of forward) and todos (LEDs), but the major problems, like profile switching and the S1-S6 keys are working without any problem. I still havent binded the Record key, still waiting for some input. Also, I've created a new repository: [https://github.com/tolga9009/hid-sidewinder-x4](https://github.com/tolga9009/hid-sidewinder-x4). All files, which I used, are included. I've been working with Arch Linux x64 kernel 3.12; but the procedure should be similar with other Linuxes. In order to get it working, you have to execute the following commands (no udev rules needed; really, just these commands below) - you need linux-headers and build-devel packages (or the corresponding for your distro):

```

cd /path/to/hid-sidewinder-x4
sudo make
sudo modprobe hid
sudo depmod -a
sudo make reload

# eventually - if you haven't connected your keyboard yet, you probably don't need to do this; modify the file to match your paths, if it doesn't work
sudo sh ./bind.sh

```

The full TODO list:
- Implement LED-states
- Create KEY_F25 - KEY_F30 scancodes (these are not defined per default in input.h; we need to generate our own scancodes - you're welcome, if you have a clue, how to generate new keycodes)
- Remove KEY_FN_F7 - KEY_FN_F12 and use KEY_F25 - KEY_F30 instead
- Fix backward counting of ms_sidewinder_profile_status() (this is due to ms_event getting called upon "press" and "release;
so it gets called 2 times -> if profile = 1, we count like:
1 + 1 = 2 //first call upon press
2 + 1 = 3 //second call upon release
outcome: 3. So we switched from 1 to 3. Next:
3 + 1 = 1 //first call; "if" profile is greater than 3, set it to one
1 + 1 = 2 //second call.
outcome: 2. All in all, we switched from 1 -> 3 -> 2. My fix: implement a counter, which has 6 instead of 3 states. I'll return the same value for 2 successive integers. OR: somehow ignore / eliminate the second call.

- Sysfs driver would be nice, but is not a must-have (we can almost copy & paste BoogeyCz / joshuafcole's Code - I'll look into this, when I'm done with everything else)
- MAJOR clean up and optimizations
- Last but not least: get the code in upstream Linux kernel

I'd be glad, if someone could review the code and give me hints for improvisations etc. I'm really new to kernel module programming, I was not very sure, what exactly is allowed and what not.

Again, Thank you everyone, especially BoogeyCz, joshuafcole and stefan_achatz! I've learned so much, it's incredible and so much fun! (though I had to hard reset my Laptop for about 50 times, due to kernel panics o.O - damn, I need to get a VirtualMachine (any advices for a good, free & open source VM (not VirtualBox!))

I'll leave this project on halt until December 20, then I'll pick up the work again. I'm quite busy with exams atm.

---

### Post by tolga9009 on 2013-12-18
Hey all,

I had little time to work on the kernel module, and I got the LEDs working. However, inside of the ms_event() function, changing the LED via a function call will result in an infinite loop. I don't know why, but it happens. This also happens with Joshua Cole's and BoogeyCz's kernel module, it's the same problem - they're also calling inside of ms_event(). Changing / setting the LED inside of the init function for example, will change the LED successfully. I really got sick of my laptop freezing up, so I couldn't investigate this problem further, but my theories so far are: ms_event is called 2 times upon one keypress (press and release button). It might be, that our LED change (which in turn works via usb_control_msg) gets called a second time, before it can return a finish-state. Or maybe, it's due to ms_event() beeing a hid function itself and calling our led function (and talking to the keyboard via usb_control_msg) will get in conflict with it. My last exam is on 20th december; I'll now concentrate on it. After that, I'll setup KVM + QEMU for a smoother development environment and investigate the problem. At the moment, I'm trying to get my hands on a Sidewinder X6, so I can get them both working. Also, I have noticed, that Joshua Cole's and BoogeyCz's kernel module has exactly the same problem with profile switching (counting with 2 increments). I'll get this working ;)!

//Edit: So, I've found an odd thing. As I said before, ms_event is called 2 times upon a keypress, which makes our profile-counter switch from 1 -> 3. However, the module crashes after switching the LED to 2.

//Edit2: Finally, the VM was able to give me some error messages. My laptop didn't show them, since they disappeared too fast. I'm getting:
```
BUG: scheduling while atomic: swapper/0/0/0x00010002
bad: scheduling from the idle thread!
```
After some Google, I found out, that this bug happens, whenever we call sleep() inside an interrupt - this is not allowed. I'm not quite sure, but I think usb_control_msg() uses such a sleep() function, because you can set a timeout.

//Edit3: I've got Wireshark + usbmon hooked up and tried it again to further investigate. Usually, ms_event gets called 2 times. However, when doing the LED stuff inside ms_event, according to the USB protocol, ms_event seems to crash after the first call; the USB transfer is successful (keypress and setting LED - no unresponded USB packets). So, the USB transfer code is definitely correct. I'm gonna update github master branch to my latest code.

I got an idea, how this could work, but I don't know, if it's allowed in kernel modules: upon profile change, a new boolean variable "changed" will change to true. I will call a while(1) function from ms_sidewinder_kb_quirks(), which will get the profile via ms_sidewinder_profile(1) ("1" for get, "0" for "set next profile and return new profile number") and set the LED, if "changed" is true and will set it to "false" again.
But I don't know, if while(1) functions are allowed in kernel modules and I also think, that this is a quite hacky and ineffective way. I also found out, that the event handler uses a spinlock; that's why we are not allowed to sleep inside event.

//Edit4: Ok, a quick Google search showed me, that while(1) loops in kernel modules are a bad idea. Damn. I'll look for another hid_driver hook.

//Edit5: Here are my latest findings: usb_control_msg() is definitely the culprit. I've commented it out and everything worked. So, I've looked for alternatives and found usb_submit_urb(), which may be called at interrupts! This looks promising ;)!

//Edit6: Ouch, couldn't get usb_submit_urb() working. The usbkbd module uses the same pattern, also for LED (of Numlock, Capslock and Scrolllock - but the purpose is the same here!). I'm on the right way, but I couldn't figure out how to get it working yet. It is possible, I know it, but couldn't get it to work. I'll upload my latest Code to branch "vm_sync" (which is obviously virtual machine syncing branch). I'm gonna work on the code later; we need many copy & pastes from usbkbd.

//Edit7: Veeery good news! I've played around with usbkbd.c and could finally get the LEDs working on keypress! So, basically, everything is there - it now needs to be put into a single module and then needs to be optimized.

//Edit8: Again, some very good news: I've just found a way to count the profile in the right order. There is a variable "value", which is 1 on keypress and 0 on release. So, with an "if" statement, we can check, whether the button is pressed or released. Now, I got everything I need to make this work, it's just a matter of time now ;)!

---

### Post by tolga9009 on 2013-12-24
Sorry for the Doublepost, but I think, this is something REALLY important: I finally got it working! I've fixed the profile counter (now counting forward, by eliminating the second call upon Key-release) and finally got the LED working, when pressing the Bank Switch button (so far, I have only done LED1, but LED2 and LED3 are a piece of cake now)! Wow, this is such a great feeling! Is there someone in the Ubuntu Community with a Sidewinder X6? We could probably get it working there, too!

Updated Todo list (I consider LEDs and Bank_Switching as Done):
- Create KEY_F25 - KEY_F30 scancodes (these are not defined per default in input.h; we need to generate our own scancodes - you're welcome, if you have a clue, how to generate new keycodes)
- Remove KEY_FN_F7 - KEY_FN_F12 for Bank 1 and use KEY_F25 - KEY_F30 instead
- SysFS drivers to talk with LED-Auto and LED-Record, so external applications can talk with our keyboard.
- Record LED + Record Button

//Edit: Github Repo is updated ;)! Everyone is welcome to review!

Explaining the Record LED behavior:
1. When the Record button has been pressed, the Record LED needs to light up (solid-mode)
2. Now when we press S1 - S6, we need to change the LED from solid to blink-mode.
3. When the Record button gets pressed a second time, we need to shut down the LED, no matter which mode it was before.

Be careful about the LEDs. Example: LED1 + Blinking Record LED isn't the same as LED2 + Blinking Record LED. We need to use masks. LEDs are set with 2 bytes:
0x07 0x00. 0x07 is unknown. The 2nd byte can set all modes we wish:

0x02 or 0000 0010 - LED Auto
0x04 or 0000 0100 - LED 1
0x08 or 0000 1000 - LED 2
0x10 or 0001 0000 - LED 3
0x20 or 0010 0000 - LED Breath (very slow blink, with fade-in and fade-out - not used by the Windows drivers)
0x40 or 0100 0000 - LED Blink
0x60 or 0110 0000 - LED Solid

The last bit is ignored; I haven't tried out setting 0x80 yet.
Example: If you want to set LED1: 0x0704.

Or if you want to set LED2 + LED Auto + LED Solid, use bitwise OR for masking:

0000 0010 - LED Auto |
0000 1000 - LED 2 |
0110 0000 - LED Solid
==================
0110 1010 = 0x6A

So, we'd need to send 0x076A. Hope setting LEDs become a bit clearer now :)!

//Edit2: Okay, I kinda got the Record LED working. As of now, only Record LED solid on / off is working, no blinking LED so far, when pressing S1 - S6. That's going to be not too difficult, since S1 - S6 keys are handled by ms_event upon keypress; we could simply add a check, whether the record led is on or off and either do nothing (when record led is off) or make the record led blink (when record led is solid).

Tomorrow, I'm going to work on Documentation, so other people can understand my Code and to make it more comfortable to work with the code (optimize), without having the keyboard in front of you.

//Edit3: Just slept over it and I think it's a bad idea to put Record LED handling in the kernel driver. It should be used for interacting with an external macro program. I'm exporting the Auto and Record LED to SysFS, so they can take care of them. LED1 - LED3 won't be setable via SysFS, because they're needed for internale profile switching. We still need keycode / scancode generation. Someone has an idea?

//Edit4: Wonderful news! All this usb_submit_urb() stuff for setting the LEDs can be done in about 5 lines of code with hid_hw_request(). This will eliminate TONS of code, making it eaiser to understand ;)!

//Edit5: I've stripped down the code a bit and worked on the new hid_hw_request method to make the LEDs work. Now, we are working with masks, it's easily possible to set LED1 + LED2 now. Check out [https://github.com/tolga9009/hid-sidewinder-x4/tree/vm_sync](https://github.com/tolga9009/hid-sidewinder-x4/tree/vm_sync). Still, I need to find a way to set the initial LED-status; it gives me error codes in ms_probe() (I've also noticed, that the USB transfer isn't correct, when setting LEDs in ms_probe()).

//Edit6: feature_mapping did the job. I've also modified the set_led function, so it sends the USB control packet only, if there is any change, to avoid packet spamming. To me, the kernel module looks quite usable in it's current form. I've optimized large blocks of code; still would be happy about any help I could get. If you want to have a usable kernel module right now, go for the master branch -> [http://www.github.com/tolga9009](http://www.github.com/tolga9009).

//Edit7: Just wanted to let you know, that I began the work on SysFS. I have a first prototype for it. Still need to fully understand SysFS, so I can optimize it. This will probably take some time. I'm working on setting / showing Auto_LED, Record_LED and Profile_Count via SysFS. This will give us the tools to let external applications take control over the device LEDs / profile counter.

//Edit8: My prototype is working now; I'm working on optimizations. It's only a matter of time now; at the moment, there are no lockups and major features are fully working. The driver is going to be finished in the next days.

//Edit9: Sysfs fully working now! I've merged an optimized and fixed version to master; you can get it from my github account. Everything is working so far (Profile Switching, Setting Profile LEDs, Auto LED and Record LED).
At the moment, I'm fighting with a small problem: when I set the Auto / Record LED via Sysfs, then change profile, the Auto / Record LED state is gone. I have to find a way to fix this.

---

### Post by tolga9009 on 2014-01-06
Okay, this will probably be my last post in this lengthy monologue (did everyone lost interest in these drivers out of a sudden?): I'm done with the drivers so far. At least, I've reached my limits. I've almost imitated the Windows Drivers 100%.

What is working:
- Profile Switching
- S1 - S6 Buttons (partly)
- Record Buttons
- Profile LEDs (also via Sysfs)
- Record LED via Sysfs only
- Auto LED via Sysfs only

What is not working (afaik):
- S2 - S6 on Profile 3

Unfortunately, I wasn't able to generate my own keycodes. I've tried out many different keys; some of them are sending out keycodes, some of them don't, it's kinda random. Only KEY_F13 - KEY_F24 seem to fit and work consistently. I don't want to have KEY_BOOKMARKS, KEY_SELECT and such stuff on Bank 3; that would be "hacking". I want some clean way to accept to send our own keycodes. KEY_FN_F* is not working, when assigned to Bank 3, only when it's on Bank 1. However, while the F13 - F24 keys have a scancode, FN+F* keys don't. The users would need to assign them on their own, which is REALLY unpractical, because the kernel module sets the profile to 1 after a restart. This would mean, that users would need to assign scancodes to keycodes OR switch profiles on every single reboot. So, I simply assigned BTN_0 - BTN_5 to S1 - S6 on Bank 3. This works for BTN_0 only, because it has keycode 256. For some reason, input_event doesn't accept keycodes higher than 256 - it doesn't recognize them. I wasn't able to fix this, eventhough I deeply looked it up - I need your help. As soon as we fix this, we're 100% done with these drivers.

I'm not going to update this post as long as I'm the only one here.

---

### Post by aleksi.mat on 2014-01-10
Hello tolga9009!

I was searching how to get all the buttons working on my x4 keyboard and I found this thread.
But I'm new to Ubuntu and I couldn't install the drivers. So I need some instructions :P
I tried this
```
[COLOR=#000000][FONT=Ubuntu Mono]cd /path/to/hid-sidewinder-x4[/FONT][/COLOR]sudo make
sudo modprobe hid
sudo depmod -a 
sudo make reload 

```
And I got an error message.

```
aleksi@aleksi-pc:~/Lataukset/hid-sidewinder-x4-master$ sudo make reloadrmmod hid-microsoft --force || true
ERROR: Removing 'hid_microsoft': No such file or directory
insmod hid-microsoft.ko
insmod: can't read 'hid-microsoft.ko': No such file or directory
make: *** [reload] Virhe 1

```

Thanks!

---

### Post by tolga9009 on 2014-01-11
Hi there!

> insmod: can't read 'hid-microsoft.ko': No such file or directory
This line looks like, that "sudo make" wasn't run successfully, so the module hasn't been generated. I'll check my code on a Ubuntu LiveCD and give you instructions for Ubuntu. May take a while.

//Edit: I couldn't get it to work with a non-updated 13.10. I'm trying out the latest 14.04 nightly now to investigate, if this is a Linux 3.11 problem, or a Ubuntu-specific one.

//Edit: Okay, 14.04 nightly with Linux 3.13 is running fine! Everything's working, like on my Dev system. Well, it either was a Linux 3.11 problem or a Ubuntu 13.10. So, if you're having any trouble after successfully compiling and loading the drivers, please wait for 14.04.
I don't know, if the build-tools are installed by default (they were on the LiveCD though) - so you should definitely check that.
Delete all your Sidewinder X4 related files and extracted files in your Downloads directory. Just make sure to start from scratch, to avoid any problems. Do these steps one by one (and correct them, if necessary) with a freshly rebooted system:
1. Download [https://codeload.github.com/tolga9009/hid-sidewinder-x4/zip/master](https://codeload.github.com/tolga9009/hid-sidewinder-x4/zip/master). This will download the latest code for the Sidewinder X4 keyboard.
2. Launch a terminal and install build-tools: sudo apt-get install build-essential.
3. Command: cd ~
4. Command: cd Downloads
5. Command: unzip hid-sidewinder-x4-master.zip - this will create a new folder called hid-sidewinder-x4-master and extract everything inside there.
6. Command: cd hid-sidewinder-x4-master (you might need to repeat this command, if unzip extracts the files in nested directories, I don't know 100% atm)
7. Command: make (look out for error messages. Usually, the output should be around 7 - 8 lines, without any warnings or error messages).
8. Command: sudo modprobe hid
9. Command: sudo modprobe usbhid
10. Command: sudo depmod -a
11. Command: sudo make reload
Plug in your Sidewinder X4 keyboard right now. Profile LED1 should light up. If it was already plugged in, or your Sidewinder X4 doesn't show Profile-LED1, execute the following command:
12. Command: sudo sh bind.sh

This should usually do the job. If this works, you have to find a solution to automatically load the drivers at the start - there should be plenty of information about that on the internet (and in this thread, too). I'm currently working on optimizations (more error handling for example) and on the S1 - S6 keycodes on profile 3 atm. As soon as I'm done, I'll submit the patch, so likely for Linux 3.14 or 3.15 (unfortunately, this means Ubuntu 14.10 :(), you won't need to do these steps, as the driver will work out of the box.

---

### Post by aleksi.mat on 2014-01-11
I got to step 7 without any problems but the make command didn't work quite right.

```
aleksi@aleksi-pc:~/Lataukset/hid-sidewinder-x4-master$ make
make -C "/lib/modules/3.2.0-58-generic-pae/build" M="/home/aleksi/Lataukset/hid-sidewinder-x4-master" modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-58-generic-pae'
  CC [M]  /home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.o
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c: In function &#8216;ms_sidewinder_set_leds&#8217;:
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c:138:3: error: implicit declaration of function &#8216;hid_hw_request&#8217; [-Werror=implicit-function-declaration]
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c: At top level:
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c:564:1: warning: data definition has no type or storage class [enabled by default]
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c:564:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;module_hid_driver&#8217; [-Wimplicit-int]
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c:564:1: warning: parameter names (without types) in function declaration [enabled by default]
/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.c:553:26: warning: &#8216;ms_driver&#8217; defined but not used [-Wunused-variable]
cc1: some warnings being treated as errors
make[2]: *** [/home/aleksi/Lataukset/hid-sidewinder-x4-master/hid-microsoft.o] Error 1
make[1]: *** [_module_/home/aleksi/Lataukset/hid-sidewinder-x4-master] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-58-generic-pae'
make: *** [modules] Error 2
```

After that I tried proceeding anyway but didn't get very far.

```
 aleksi@aleksi-pc:~/Lataukset/hid-sidewinder-x4-master$ sudo modprobe ushid
FATAL: Module ushid not found.
```

---

### Post by tolga9009 on 2014-01-11
Yes, your make command doesn't run successfully. This is due to your Linux kernel beeing totally outdated, as seen by this line:
> /lib/modules/3.2.0-58-generic-pae/build
Linux 3.2 was released at the beginnung of 2012; I've worked with the latest kernel 3.12. The code I've written depends on new functions, which were introduced somewhen after the Linux 3.2 release. I recommend you to update your system _or_ trying out x4daemon ([http://geekparadise.de/x4daemon/](http://geekparadise.de/x4daemon/)). It will probably work, since it is not a kernel module, but a standalone program. But definitely consider updating your operating system (make sure to backup important stuff prior updating) - it's really outdated.

By the way: I've just finished the drivers. Everything is working now; the scancodes, keycodes, sysfs files, all buttons, all profiles and all leds. I'm now depending on you guys, to further optimize the code (to do the same, with less code / less instructions / less memory), eliminate bugs, memory leaks and add error handling. But all in all, it's kinda done. I've merged my latest code to master: [https://github.com/tolga9009/hid-sidewinder-x4](https://github.com/tolga9009/hid-sidewinder-x4). I'm trying to get my hands on a Sidewinder X6 these days.

---

### Post by tolga9009 on 2014-01-19
I now got my hands on a used Sidewinder X6. I'm going to start developing the kernel module in the upcoming days. I'll wait with the patch submission, until I'm completely done.

---

### Post by tolga9009 on 2014-01-23
My laptop failed. All data is backed up and my work will go on, once it's back from repair. But for now, the Development will be postponed for about 1 week - 1.5 weeks.

---

### Post by tolga9009 on 2014-02-05
Small update: my notebook is back from repair, but I got new problems now. This project is currently on hold. Because I have a Radeon HD7970 in my desktop computer, I've to wait for the stable 3.13 kernel to move into core repository (Arch Linux). At the moment, I'm unable to run Linux on my dekstop to pick up development. 3.13 will make Linux work on my desktop again (thanks to the Radeon-related patches) - probably beeing available in around 3 - 4 days, please stay patient.

My plans are:
- Reverse engineer and implement missing SideWinder X6 features
- Add advanced error handling
- Optimizations - same result with less code / work / functions / memory-usage / cpu-usage.
- Check for memory leaks and advanced memory handling
- Double and triple check for bugs; also use it on other Linux systems
- Submit for review

---

### Post by tolga9009 on 2014-03-03
Well, Arch Linux had it own problems with releasing 3.13 kernel, which was postponed for about 2 weeks and finally went into core repo last week. I've got my hands on a new notebook now. In the meantime, I've set up a USB sniffer under Windows 7 - it was okay, but nowhere near productive as the Linux solution with usbmon + Wireshark. Still, these are my findings about the Sidewinder X6:

Differencies between Sidewinder X4 and X6:
- X6 offers "1|2" button, which switches S1-S6 buttons to S7-S12 buttons. USB code changes, this is something hardware side - which means, that we don't have to do anything in software, awesome! Doesn't affect S13-S30 keys - PHEW!
- X6 offers "Game Center" button, which is basically just another hotkey, with an own USB code. Simple to extend current functionality, no problem.
- [Working now! Look at "Edit"] X6 offers "Cruiser" button. You have to hold down Cruiser + any key and the key will automatically be hold down, while the LED stands on. We have to read out the LED code (was not possible with my current setup) and adjust it. This is probably done on hardware level, cause pressing the button on its own doesn't produce any USB code. We probably just have to drive the LED on a specific USB code, which should be simple aswell.
- X6 has a removable macro pad. You may put it on either side; with a specific USB packet, you can either run the macro pad in numpad mode or macro key mode, featuring the S13 - S30 buttons. Numpad and macro pad are generating different USB codes, this is done on hardware level. We have to send the USB code, to either set numpad or macro mode. Now that's a design question. Either, we could use "Game Center" Key to switch between macro and numpad mode, or bind specific profiles to macro mode (profile 1 = numpad, profile 2 & 3 = macro), or simply doing nothing internal, but wirting a sysfs file for it - maximizing customization and liberty, but lowering the comfort for the average user. That's something I'll decide about later. This might be the toughest part - but I can do this ;)!

That's about it. The main challenge is not coding the kernel module, but having a good module design. It's possible to set up about 90 macro keys on the Sidewinder X6. That's something, I have to deal with; I can't hard code every single of these 90 buttons, that's going to be a challenge for me. If you have any ideas, comments or suggestions, let me know ;)! [https://github.com/tolga9009/hid-sidewinder-x4](https://github.com/tolga9009/hid-sidewinder-x4)

Now the nasty stuff ;):

"1|2" Toggle on - USB Code - HID usage
S7 - 08 40 00 00 00 - fb07
S8 - 08 80 00 00 00 - fb08
S9 - 08 00 01 00 00 - fb09
S10 - 08 00 02 00 00 - fb0a
S11 - 08 00 04 00 00 - fb0b
S12 - 08 00 08 00 00 - fb0c

S13 - 08 00 10 00 00 - fb0d
S14 - 08 00 20 00 00 - fb0e
S15 - 08 00 40 00 00 - fb0f
S16 - 08 00 80 00 00 - fb10
S17 - 08 00 00 01 00 - fb11
S18 - 08 00 00 02 00 - fb12
S19 - 08 00 00 04 00 - fb13
S20 - 08 00 00 08 00 - fb14
S21 - 08 00 00 10 00 - fb15
S22 - 08 00 00 20 00 - fb16
S23 - 08 00 00 40 00 - fb17
S24 - 08 00 00 80 00 - fb18
S25 - 08 00 00 00 01 - fb19
S26 - 08 00 00 00 02 - fb1a
S27 - 08 00 00 00 04 - fb1b
S28 - 08 00 00 00 08 - fb1c
S29 - 08 00 00 00 10 - fb1d
S30 - 08 00 00 00 20 - fb1e

Game Center - 01 00 00 00 00 00 10 00
Cruiser Key - 01 00 00 00 00 00 00 00

Cruiser Key seems weird to me, I'm going to recap it with Linux tools, else everything looks good! I've to fully understand macro / numpad mode setting, but that will probably get clear with the Linux usbmon sniffing. I'll continue research tomorrow.

//Edit: WOW! Everything, that is working on the Sidewinder X4 is already working on the Sidewinder X6! I've only added the USB VID / PID to the hid-ids.h, that was it! Cruiser Key is working, eventhough there is no USB code - it's something on hardware level - even driving the LED. I didn't had to do anything, it's working ;)!

//Edit2: Omg, I love this device! Numpad / macro block mode is implemented in LED setup code. I'll show you, what I mean:
0x02 or 0000 0010 - LED Auto
0x04 or 0000 0100 - LED 1
0x08 or 0000 1000 - LED 2
0x10 or 0001 0000 - LED 3
0x20 or 0010 0000 - LED Breath (very slow blink, with fade-in and fade-out - not used by the Windows drivers)
0x40 or 0100 0000 - LED Blink
0x60 or 0110 0000 - LED Solid

See that last bit, which stays 0 on all LED statuses? It is used for: 0 -> Numpad, 1 -> Macro Block. Rest is done in hardware. This is SUPER easy to implement, because most of the work is done. I think, I've done a good job at analyzing the Windows drivers ^_^. I'll try to get the kernel module ready for submission these days.

---

### Post by tolga9009 on 2014-03-07
I've just submitted the patch to linux-input mailing list:
[http://www.spinics.net/lists/linux-input/msg30159.html](http://www.spinics.net/lists/linux-input/msg30159.html)

Design decisions, I had to make:
Eliminate keycode generation in favor of key_mask. Keycodes would've been hardcoded to the keys, which is not the default behaviour under Windows. Now, I've implemented a sysfs file called "key_mask" which can be used to read pressed special keys (multiple special keys can be pressed at the same time). I'll get in contact with Wattos and EvilAndi after the patch has been reviewed (and probably corrected / changed), so we can work on a good user-space solution. This should be fairly easy, since almost everything we need is already done for other open source software projects and we just need to puzzle some snippets. It's time to get hyped ;)!

My next project will be reverse engineering the Elgato Game Capture HD. I already got some USB sniffing, but currently busy with completing Sidewinder Linux support and some exams, but I'll definitely have time around end-March for this one! Now get more hyped please ;)!

---

### Post by Rijnhard on 2014-04-28
just wanted to say thank you for this, much appreciated. Created an account just for that. 

Proper instructions could be useful (I already figured it out though) and please keep us posted on the kernel patch status. 
I am however getting get a weir error, modprobe isn't compiling the .ko.  I'm running OpenSUSE 13.1 with Kernel 3.14.0-2

At the moment it looks like you have a lot of rewriting to do. Rather you then me - i hate C headers. argh - now I must go back to my C++ templates XD 

But jsut again, thanks for the effort, I know I'm not the only, just one of the few who actually bothered to sign up.

---

### Post by tolga9009 on 2014-05-10
Hi Rijnhard,

thank you for your kind words! Could you post me your error messages? I've only tested the patch on Arch Linux 3.12 / 3.13 / 3.14 and Ubuntu Beta 3.12 so far. So, there might still be some issues.

The kernel patch status is rather frustrating. My first patch got completely ignored, so I changed a few things and resent it. They don't want to accept a new ABI (key_mask, which is needed for recognizing keypresses by a minimalistic daemon) and I don't have any other way to get both, the Sidewinder X6 and Sidewinder X4 working. I would need to hard-code around 90 different keycodes into the driver, which is just nonsense. Also, they didn't like they way of handling the LEDs, I need to make use of leds.h. I haven't decided yet, what to do next. But it doesn't seem, that the patch will get accepted in a state, which would be useful for us. I'd love to discuss about a solution, about design decisions, but no one seems to get seriously involved.

One option would be dropping the Sidewinder X6 support completely and hardcoding 3x6 keycodes in the kernel module, but this approach is quite hacky and doesn't really mimic the Windows behaviour. Unfortunately, I'm out of ideas and there is nothing comparable already done in kernel space to get any ideas from (besides Roccat Arvo; for some reason they don't seem to be bothered about the same key_mask ABI there...).

A great idea would be merging Wattos' Sidewinder X6 and EvilAndi's X4Daemon. Microsoft is using XML for saving / creating macro's (the .mhm files in User/Documents/Microsoft Hardware), so it would be possible to create a userland daemon, which could use these files. Since I finally know, how these keyboards work and fully deciphered the USB packets, it should be no problem to get such a solution working. However, it has it's downsides, as it has to be downloaded, installed and you have to let another daemon running in the background, which takes care of special keypresses and macros.

It's not like deciding about which fits better, but about deciding which is less worse. I'm really split.

The instructions for the kernel module compilation differ from system to system, but in a nutshell, it's:
1. Compile the module using make
2. Load the module (for example by using "make reload" or insmod)
3. Unbind the Sidewinder X4 from hid-generic (echo your-usb-device > /sys/bus/hid/drivers/hid-generic/unbind - alternatively run bind.sh)
4. Bind Sidewinder X4 to microsoft (echo your-usb-device > /sys/bus/hid/drivers/microsoft/bind)

The code, which can be found on GitHub works, but is not in a usable state - you won't be able to get any keypresses recognized (you'd lack a daemon, which checks key_mask for changes). Keypresses will get written to a sysfs file as of the latest commit. If you don't mind messing around, try this commit: [https://github.com/tolga9009/hid-sidewinder/commit/da60a220ea2bd7c06008307de09dd3a3a01a09e5](https://github.com/tolga9009/hid-sidewinder/commit/da60a220ea2bd7c06008307de09dd3a3a01a09e5) and delete all Sidewinder X6 related stuff (like S7 - S30 key handling). This should give you an out-of-the-box working profile switch and hardcoded S1 - S6 keys (including all 3 banks).

I'll have some free time next weekend. I'll get my hands dirty and work on a userland tool - that's all I can do for now (until anyone else writes a similar gaming keyboard kernel driver, which gets accepted).

Greetings,
Tolga

//Edit: I've started working on the new user-land programm, called sidewinderd for Sidewinder daemon. You can track progress here: [https://github.com/tolga9009/sidewinderd](https://github.com/tolga9009/sidewinderd)

---

### Post by tolga9009 on 2014-05-17
Okay, after few hours of research, I've come to the conclusion to use hidraw in order to write the userland application. This will make life much easier and won't need libusb as a dependency. I have a working prototype right now, this shouldn't take to long, until feature parity is reached with kernel drivers.

//Edit 1: I've now a working prototype, which gets the device node via libudev and reads / writes the keyboard via hidraw. No functionality as of right now, just a working proof-of-concept, more or less. I'm now cleaning up a bit and will then upload it on GitHub. That's a good check-point, from where we can move on.

//Edit 2: Currently, the driver finds the hidraw devnode via libudev and recognizes keypresses via hidraw. There is a function to set LEDs. The main loop currently got a dirty hack, which stops it from consuming the CPU at 100%, also it's lacking key events and much much more. But it's a good checkpoint.

Next TODOs on my list are:
- main loop using inotify, which stops consuming the CPU at full load and triggers the main event only on file changes. This should improve code quality. I'm also reading about mutex / semaphore and will see, if that's what I was looking for (sett loop -> idle, until a key on the Sidewinders USB Interface number 1 (S1 - S6/S30, profile switch, game center key, record key, media control keys) is pressed).
- understand uinput and input and send key events
- read configuration file; config keys via user conf file

The most difficult part is writing a minimalistic, fast and lightweight code for the main loop. I want to save as many resources as possible, without loosing stability and reliability. The rest of the code is more or less already done within kernel drivers and also by Wattos and Andi.

These are future plans for this project:
1. Macro recorder
- fully controllable via the keyboard, without the need of a GUI
- saving macros in XML format, which will be compatible to Microsoft's keyboard center drivers
- reading macros, which have been saved as .mhm-files (XML files) with the official Windows drivers

2. Configuration
- a default configuration will set keys S1 - S6 on profile 1. You will be able to expand / modify this default configuration by a system-wide /etc/*.conf file and also by a user conf file
[COLOR=#008000]- switchable macropad (X6 only) by pressing Game Center key. /* DONE */[/COLOR]

3. Adaptability
- easily make similar keyboards work with this software, so others don't need to fork this project once it's completed, but actively develop and improve it. I'm open for any kind of suggestions and patches, just E-Mail me (look up my E-Mail adress at GitHub or at the source code of sidewinderd.c)

The ultimate goal is to reach feature parity with Microsoft's drivers, excluding the GUI.

Eventhough I hate it, I have to ask for your patience again. I have "wasted" lots of time developing the kernel drivers (actually, it was no waste, I have learned TONS of things!! But if you look at the result, yes, it was a waste, since it didn't got accepted and it was simply wrong to put this kind of driver into kernel space). This project will probably reach a usable state really fast, but programming parts like the macro recorder will simply take time! I've other projects running and I'm also studying (including exams -.-), so time's short. Also, I have to do lots and lots of reading, since I'm kinda new to C and Linux programming, this takes time, too. However, be sure that I'm trying to deliver the best code I can, eventhough it may take it's time.

Thanks for your patience and kind words so far!!

//Edit 3: I've learned more about efficiently watching over the hidraw device - inotify is not suited for this kind of things, but rather epoll. Epoll is a Linux API, which watches over files / sockets / whatever and blocks the loop, until the socket / file / whatever changes. This will greatly reduce the CPU load, maybe make it even unnoticeable. I'll work on it now and report back, as soon as I'm done.

//Edit 4: Quick & Dirty setup of uinput done! It's working!

//Edit 5: Added support for configuration. Everything is basicly setup, but there is still much work to be done. Next step will be setting up the macro-player. The user configuration points to different xml / mhm files, which are used for storing / reading the macros. I need to write a function, which parses the macro, saves it in buffer and plays it from buffer.
Unfortunately, due to the difference in Linux' and Windows' design, I will need implement 2 kinds of mhm / xml files. One, which is human-readable and modifyable and another one, which shares the Windows design. This whole step will take quite some time, so don't expect any results very soon. I will need every time I can get to finish this part.

//Edit 6: Work is on hold until friday. I will have time next weekend to further work on this driver. Plans are made, I just need to write everything down. The next problem is security. To have full access to the keyboard, the daemon needs to run as root user (or what it takes to have access to keyboard events). This might lead to potential security risks. I'm still trying to figure out a way how to catch keyboard events without root access.

//Edit 7: I've picked up the work on the driver again.

//Edit 8: Now we have a basic macro player. In order to use it, you have to manually edit the xml files. Currently, only sample.xml is read and used for all S-Keys, but reading and interpreting the config file to make other xml files work is currently on my TODO list. Still lots of work to be done, but I still like the speed of development ;)! Even in this state, we have reached more, than we could reach with a kernel module based solution.

//Edit 9: I just wanted to let you know, that I have little to no time at the moment to work on the drivers, due to exams. Luckily, after 4th July, I have about 3 months of holiday and I will finish this project then. Also, I'm currently working on a personal website, where I will keep you updated about the development status and where you will have easier options to give me feedback than here on ubuntu forums.

//Edit 10: I have picked up the work again. Currently, I'm working on the macro recording function. Unfortunately, hidraw doesn't read the keys as I wanted. Reading the correct /dev/input/eventX file would make life so much easier, however, I haven't found a good and reliable way to claim the correct event file yet. Reading the keyboard via hidraw would require me to reinvent the wheel and write a translation layer between hidraw and the Linux input system, so we can interpret which key was pressed. This is way too complicated though and I'm trying to find another approach. If you have any ideas, please share with me.

I'm done with the website and waiting for my webhosting provider to unlock my webspace.

//Edit 11: Website is done, project page is up. Please either use [https://github.com/tolga9009/sidewinderd](https://github.com/tolga9009/sidewinderd) or the new project page on [http://cevel.net/projects/sidewinderd/](http://cevel.net/projects/sidewinderd/) to share your thoughts and report issues. Thank you.

---

### Post by tolga9009 on 2014-11-12
Hi there,

I've finally released a version, which I think is in a usable state. Please download, test and report: [https://github.com/tolga9009/sidewinderd](https://github.com/tolga9009/sidewinderd). Arch Linux users can find a an AUR version here: [https://aur.archlinux.org/packages/sidewinderd/](https://aur.archlinux.org/packages/sidewinderd/). Currently, it is only working in conjunction with systemd. I'm working on a compability mode using fork(). You will need to install git, cmake, libconfig, clang and systemd in order to run this daemon. TinyXML2 is provided as a static lib. Follow the following instructions:

1. Download a release version on GitHub
2. Extract the archive and open up a terminal inside the extracted folder
3. $ mkdir build
4. $ cd build
5. $ cmake ..
6. $ make
7. $ sudo make install
8. $ sudo systemctl start sidewinderd
9. $ sudo systemctl enable sidewinderd

Any problems? Please share.

Cheers,
Tolga

---

### Post by arunce on 2015-05-03
Thank you Tolga.

My Sidewinder X4 keyboard is now working thanks to your code.

I had a few bumps: 
1. My prefix was: /usr/local
Service wasn't starting until I found that the ExecStart path at "/usr/local/lib/systemd/system/sidewinderd.service" was pointing to "/usr/bin/sidewinderd" instead of "/usr/local/bin/sidewinderd"

2. As my user folder is encrypted, it is necessary to restart the service to give it access to the home directory after login.
(this was after setting up the user in /etc/sidewinderd.conf)

---

### Post by tolga9009 on 2015-06-21
Hi arunce,

sorry for the late answer, I'm not checking this thread so often anymore. Please refer to the official Git repository on [https://github.com/tolga9009/sidewinderd](https://github.com/tolga9009/sidewinderd) for future issues. Thank you for the informative bugs, I'm gonna fix these issues. Need to take care of environment variables. As for your second issue, I think this can be fixed by letting sidewinderd.service wait for your harddrive decryption to finish. I will look into it, once I have time.

Cheers,
Tolga

---

