---
title: "Gateway Tablet"
date: 2009-01-24
forum: Hardware
---

### Post by redxine on 2009-01-24
I have a Gateway CX210X Convertible computer and have recently perfected the installation of Ubuntu Intrepid, With the exception of the tablet.
I've installed the fpit drivers, used setserial to invoke:
```
# setserial /dev/ttyS0 port 0x06A8 uart 16954 irq 4 baud_base 38400
```  

And added this to my /etc/X11/xorg.conf:
```
Section "InputDevice"
	Identifier "Tablet"
	Driver "fpit"
	Option "Device" "/dev/ttyS0"
	Option "AlwaysCore" "on"
	Option "InvertY"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
	Option "Passive" "false"
	Option "SendCoreEvents"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Tablet"
EndSection
```

After restarting X, I put the tablet to the screen, and the mouse immediately goes straight to the bottom-right corner of the screen. Clicking works with the exception of right-click.

Any suggestions? All help is appreciated.

-Cheers

---

### Post by Favux on 2009-01-24
Hi redxine,

Forgive my ignorance.  Why install the "fpit" drivers?  Aren't those for Fujitsu Stylistic Tablet PC's?  Is the reason why that your digitizer is the same and you learned somewhere that fpit would work for the Gateway CX210X?  Also why do you need setserial?  Did you try to detect serial input on ttyS0,1,2,3 first?

If you are suppose to be using fpit the following will be of only academic interest to you.

It looks like your not following the correct Xorg syntax for a serial tablet in your xorg.conf.  Do you know if it is a Wacom digitizer?  If not do you know the manufacturer and model?

What features are offered?  The options are stylus, side-switch, eraser, and touch.

You probably need the linuxwacom drivers from the Linux Wacom Project.  Many non-Wacom digitizers emulate a Wacom well enough to work.

Please see:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

There are sample xorg.conf's at the bottom of both HOW TO's.  Loic2's wiki's also have sample xorg.conf's and describe how to configure.  To then rotate the screen to tablet mode please see:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

I hope this is helpful.  Please feel free to ask any questions.

---

### Post by redxine on 2009-01-24
I am certain that the pen does in fact run through /dev/ttyS0, as when I cat it, I get output from it only when the pen is near the screen. I have gotten the pen to work on Fedora Core 7/8, but when 9 came out, the same configuration did a good job at crashing the X server. I used the post [http://ubuntuforums.org/showthread.php?t=429701](http://ubuntuforums.org/showthread.php?t=429701) to get it running, but no luck. It claims that gateway uses the same protocol as Fujitsu. They also said the the buttons on the front of the computer use a different IRQ on ttyS0, but I'm working more towards getting the tablet running.

I know that the wacom drivers would not work because they use the PCI bus to get input from the tablet. I have nothing on my lspci that screams "Tablet", let alone input device.

I also noted that cating /dev/ttyS0 while Xorg is reading it causes the system to lock up.

---

### Post by Favux on 2009-01-24
Hi redxine,

I did some research because I was curious.  The Gateway CX210X uses the Finepoint Innovations Tablet PC Digitizer and so requires fpit, which you already knew.  It just calls it the "Executive Pen" or something.

If I take the following literally:
> I've installed the fpit drivers, used setserial to invoke:
```
# setserial /dev/ttyS0 port 0x06A8 uart 16954 irq 4 baud_base 38400
```
Then maybe I see a problem.  The line you want to add to your /etc/setserial.conf should be:
```
/dev/ttyS0 port 0x06A8 uart 16954 irq 4 baud_base 38400
```
unless this is what you already have.  Furthermore the line may in fact be:
```
/dev/ttyS0 port 0x03F8 irq 4 baud_base 38400
```
This is based on the Laptop Testing team's:

[https://wiki.ubuntu.com/LaptopTestingTeam/GatewayCX2618]("https://wiki.ubuntu.com/LaptopTestingTeam/GatewayCX2618")

At least this model seems similar to yours.

How recent is your version of fpit?  From what you're describing it sounds like the more recent versions of Xserver aren't compatible with it.

I hope this makes some sense.

---

### Post by Favux on 2009-01-25
Hi again redxine,

Good news.  It turns out there is a newer fpit driver, one that's only about 10 months old.  And there still seems to be development going on.  The new version is 1.2.0 and yours is X11 R7 1.1.0.  So your's might not even be 1.1.0, it may be a release candidate.  The line to google with was "xf86-input-fpit driver".  It's home is:

[http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/]("http://cgit.freedesktop.org/xorg/driver/xf86-input-fpit/")

Even better there is a deb of 1.2.0-1 at the Debian site, which given the "-1" seems current:

[http://packages.debian.org/sid/xserver-xorg-input-fpit]("http://packages.debian.org/sid/xserver-xorg-input-fpit")

And better still, Synaptic Package Manager has it.  Search "fpit" and you get 1:1.2.0-1 build 1.  So the Synaptic version may be slightly older than the Debian deb.  I'd say it's your choice which to install.

It should be relatively easy to find out what /dev/ttyS line to add to your /etc/setserial.conf.  In a terminal type:
```
sudo dmesg | grep ttyS
```
and that should give you the information you need.  Apparently setserial can interfere with this, so you might have to temporarily disable it.

Then some minor xorg.conf tweaking and you should be setup!

---

### Post by liljoe2284 on 2009-02-20
I am having the same problems with my gateway laptop. It is the same laptop as the one in the thread. I wanted to try these ideas, but do not know anything out setserial. How do you temporarily disable setserial? It might also be important for me to know how to enable setserial as well. Thanks for all your help.

---

### Post by Favux on 2009-02-20
Hi liljoe2284,

You should be able to get set up with a little patience and luck.  I don't know if setserial can be disabled because I don't know for sure which start up scripts are invoking it.  You may have to uninstall it and then reinstall it.

The readme in the fpit source is about two years old and is for v. 1.1.0 of the fpit driver.  Which source of fpit 1.2 are you planning to use?

To find serial output try:
```
dmesg | grep ttyS
```
or
```
sudo dmesg | grep ttyS
```
It should be giving output something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

```
Which you would then add to your serial.conf file something like:
```
/dev/ttyS0 uart 16550A port 0x3f8 irq 4 baud_base 34800
```
And of course make sure in your xorg.conf it reads ttyS0 or whatever was returned.  As you know setserial can interfere with dmesg.  Some folks get the output without any trouble while others don't seem to be able to get it whatever they do.  I don't know why.

You also want the output of:
```
ls /dev/ttyS*
```
Most likely ttyS0 is going to be what you need.

Do you know how to use xxd? Notice xxd will exit for devices not listed, otherwise CTRL and C to quit. Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc. Bring the pen to the screen an move it around. You know you have the right ttyS* when you see a reaction with an output of characters. That's the ttyS* you want to use in xorg.conf. In a terminal type:
```
xxd /dev/ttyS0
```
The readme says also to check:
```
/proc/ioports
```
and
```
/sys/devices/pnp0/*
```

Here are some wiki's that may be helpful:
[https://wiki.ubuntu.com/LaptopTestingTeam/GatewayCX2618]("https://wiki.ubuntu.com/LaptopTestingTeam/GatewayCX2618")
[https://help.ubuntu.com/community/FujitsuStylus]("https://help.ubuntu.com/community/FujitsuStylus")

You'll also need to correctly configure your xorg.conf.  If you attach it to your next post I should be able to help you with it.

Hopefully this should help get you set up.

---

### Post by liljoe2284 on 2009-02-20
Favux,

 I am installed the fpit from synaptic package manager gui. I ran the commands 

dmesg | grep ttyS

and 

sudo dmesg | grep ttyS.

I received no output both times. Do you happen to have any other advice? Thank you for your help so far.

---

### Post by Favux on 2009-02-21
So you have fpit 1.2.0-1 build 1.  Did you already install setserial?  If so try uninstalling it.  Do the complete uninstall.  Otherwise we'll have to try guessing it, probably from the thread or the two wiki's.  That may require repeated tries before you luck out.

---

### Post by liljoe2284 on 2009-02-21
Favux,

 I went into synaptic package manager and it appears that setserial is not installed. Should I try installing it and see if that helps? Once again thanks for all your help. Yes I do have fpit 1.2.0-1 build 1.

Joe

---

### Post by Favux on 2009-02-21
Hi liljoe2284,

No, don't install setserial yet.  Reboot and try the dmesg again.  Dmesg queries the kernel buffer.  Any output with the other commands?  Also please attach your xorg.conf.

---

### Post by liljoe2284 on 2009-02-21
Favux,

 I attached a copy of my xorg.conf. I also ran the command dmesg by itself and found this next line in part of the list that followed 

[    1.790759] Serial: 8250/16550 driver4 ports, IRQ sharing enabled

I still have no message appearing when I run the command dmesg | grep ttyS. Hope all of this provides enough information for you.

Joe

---

### Post by Favux on 2009-02-21
Hi liljoe2284,

I think its just telling you you have 4 serial ports.  Usually S0 to S3.  Try without and with sudo:
```
dmesg | grep ttyS*
```
Anything on those other output commands I gave you?

Using your xorg.conf I've added the finepoint modifications.  Be sure to back yours up!  Read and compare them.  There is a lot of information in the new one.  Have you looked at the links yet?

I'll be back in a few hours.

---

### Post by liljoe2284 on 2009-02-21
Favux,

 I tried the dmesg | grep ttyS* without and with sudo and got the same response:


joe@joe-laptop:~$ dmesg | grep ttyS*
[    0.004000] console [tty0] enabled
[    1.797426] tty ptyr9: hash matches.


I tried the other commands you gave me in each of the three places you mentioned. Nothing worked with the pen. All I needed to do was type xxd /dev/ttyS0 and move the pen to try it right? Also, I was wandering what I needed to do in order to back up my xorg.conf file. Do I simply save it as a text document and then I can always save that over xorg.conf? Also is this something that I need to backup my whole computer to try. I haven't carried out a recent backup and just wanted to make sure.

Thanks again for all your help.

liljoe2284

---

### Post by Favux on 2009-02-21
Hi liljoe2284,

> Also, I was wandering what I needed to do in order to back up my xorg.conf file. Do I simply save it as a text document and then I can always save that over xorg.conf?
To backup xorg.conf choose a backup name like my_xorg.conf.bak:
```
sudo cp /etc/X11/xorg.conf /etc/X11/my_xorg.conf.bak
```
and then to restore:
```
sudo cp /etc/X11/my_xorg.conf.bak /etc/X11/xorg.conf
```
Then use Nautilus to verify that the backup is successful.  Backing up is a big topic.  There is a Backup thread in the Tips and Tutorial forum.  Also Ubuntu has a project called TimeVault, but I think development has slowed or stopped on it.

All right, why can't it be easy?  Last thing I can think of, try:
```
more /proc/bus/input/devices
```
You know the type of line we're looking for.

---

### Post by liljoe2284 on 2009-02-21
Favux,

 I received the two following outputs that dealt with mice or mice-like input devices. The last one looks like it might be something we are looking for. Also, I have not fixed the xconf file yet. Would this be affecting anything right now? If so, do I need to back up the whole computer or just the xconf?

I: Bus=0011 Vendor=0002 Product=0007 Version=23b3
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003



I: Bus=0011 Vendor=0002 Product=0007 Version=23b3
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input8
U: Uniq=
H: Handlers=mouse1 event8 
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003


Thanks again
liljoe2284

---

### Post by Favux on 2009-02-21
Nope, still not what we're looking for.  It should look something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```

Where are you?  Have you made the changes to xorg.conf and rebooted yet?  Tried to get the output again?

Also check and see if you have a serial.conf in /etc.

---

### Post by liljoe2284 on 2009-02-21
I made the changes to xconf and have rebooted. I tried the same commands to no avail. Also, I do not have a serial.conf in my .etc file. I don't think they are going to make it easy at all for us to do this. I really do appreciate all the help.

liljoe2284

---

### Post by Favux on 2009-02-21
Yep, it sure is looking that way.  But we should be able to hammer through this.

OK at this point I can't see anything to lose by installing setserial.  Then try messing around with the dmesg commands, etc. again.  See if now you get something.

Also be a good idea to go to the Laptop Testing Team wiki on the CX2618 (the closest I can find to your model) and look at the notes section at the bottom.

---

### Post by liljoe2284 on 2009-03-02
Favux,

 Nothing worked with the setserial either. At this point, I think I am going to wait and try a little later. I have a lot of work starting to pile up.

Thanks for your help though.

Joe

---

### Post by redxine on 2009-09-13
I can happily report that my tablet is completely working in Intrepid. Unfortunately Jaunty has moved completely to HAL so this method _will not_ work by following the tutorial here: [http://ubuntuforums.org/showthread.php?t=942109](http://ubuntuforums.org/showthread.php?t=942109)

1. Install/Enable the SetSerial service.
2. [B]sudo touch /etc/setserial.conf
&#65279;*&#65279;*&#65279;&#65279;&#65279;sudo echo "/dev/ttyS0 port 0x06A8 uart 16954 irq 4 baud_base 38400" > /etc/setserial.conf[/B]
3. Download the fpit driver from here: [http://ubuntuforums.org/attachment.php?attachmentid=68137&d=1209568540](http://ubuntuforums.org/attachment.php?attachmentid=68137&d=1209568540)
4. Extract driver and run: **sudo mv fpit_drv.so /usr/lib/xorg/modules/input/**
5. Backup your xorg.conf file with **sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**
6. Edit your /etc/X11/xorg.conf file to read:
```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Identifier "Tablet"
	Driver "fpit"
	Option "Device" "/dev/ttyS0"
	Option "InvertY"
	Option "MaximumXPosition" "12550"
	Option "MaximumYPosition" "7650"
	Option "MinimumXPosition" "400"
	Option "MinimumYPosition" "400"
	Option "SendCoreEvents" "true"
	Option "Passive" "false"
	Option "TrackRandR" "on"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice	"Tablet"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

```
7. Reboot

Sometimes the pen will send random right/left clicks when near the top 160 or so pixels of the screen (and sometimes it won't). Another problem is that the driver causes X to freak out when it is killed and results in a strange video patern. Sometimes it will cause the entire system to lock up requiring a hard reset. Will also interfere with the shutdown usplash, and it reacts differently depending on the install (?) for example right now the usplash at shutdown will display 2 copies of itself on the screen, and they are both scaled down to 1/2 size.

---

