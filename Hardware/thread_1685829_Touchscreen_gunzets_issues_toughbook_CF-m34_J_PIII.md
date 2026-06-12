---
title: "Touchscreen gunzets issues toughbook CF-m34 J PIII 400mhz"
date: 2011-02-11
forum: Hardware
---

### Post by petebarchetta on 2011-02-11
Hello All,

Can someone shed some light on a current issue i have with my Toughbook.
I'm currently trying to get the touchscreen working on my CF-M34, i know the driver involved is the gunzets driver, but i cant seem to find any Xorg configuration that would allow it to work. From what i gather its a wacom screen overlay

---

### Post by petebarchetta on 2012-02-28
Has anyone had any joy with the touchscreen elements of oneric? As it's geared more for tablets and the like it would be good to see who has got any element of a touchscreen setup working.

---

### Post by Favux on 2012-02-28
Hi petebarchetta,

Could you provide the output of lsusb so we can see what's there?

---

### Post by petebarchetta on 2012-02-28
output of lsusb:
user@ToughBuntu:~$ lsusb
Bus 001 Device 002: ID 0409:55ab NEC Corp. Hub [iMac/iTouch kbd]
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
user@ToughBuntu:~$ 

i have the latest gunzets 1.4 driver from:
[http://www.ar.linux.it/pub/gunzets/](http://www.ar.linux.it/pub/gunzets/)[http://www.ar.linux.it/pub/gunzets/]("http://www.ar.linux.it/pub/gunzets/")

also output of xorg.conf
  GNU nano 2.2.2              File: xorg.conf                                   

#Option         "Device"                "/dev/ttyS3
##Option        "DeviceType"            "serial"
#Option         "BaudRate"              "9600"
##Option        "CalibrationFile"       "/etc/gunzets.calib"
#Option         "Smoothness"            "9"
#Option         "TappingDelay"          "0"
#Option         "JitterDelay"           "50"
#Option         "DebugLevel"            "0"
#Option         "Res12Bit"              "False"
#Option         "SendCoreEvents"

#EndSection

# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#Section "InputDevice"
#       Identifier      "Synaptics Touchpad"
#       Driver          "synaptics"
#       Option          "SendCoreEvents"        "true"
#       Option          "Device"                "/dev/psaux"
#       Option          "Protocol"              "auto-dev"
#       Option          "HorizEdgeScroll"       "0"
#EndSection

Section "Device"
        Identifier      "Silicon Motion, Inc. SM710 LynxEM"
        Driver          "siliconmotion"
        BusID           "PCI:0:2:0"
#       Identifier      "Configured Video Device"

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-40
        VertRefresh     43-60
#       Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Motion, Inc. SM710 LynxEM"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600"
        EndSubSection
#       Identifier      "Default Screen"
#       Monitor         "Configured Monitor"
#       Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
# commented out by update-manager, HAL is now used and auto-detects devices
# Keyboard settings are now read from /etc/default/console-setup
#       InputDevice     "Synaptics Touchpad"
#       InputDevice     "TouchScreen0"
EndSection

Any suggestions would be great

---

### Post by Favux on 2012-02-28
Alright, so this is a serial instead of usb touchscreen?

The *lsusb* doesn't have anything.  I was wondering if this wasn't an ED like with the Panasonic Toughbook CF-H2:
```
Bus 002 Device 005: ID 056a:00ed Wacom Co., Ltd
```
Because you mentioned "its a wacom screen overlay".  We were able to get the stylus working but not the touchscreen.  Panasonic said it was a "Gunze" touchscreen with the Wacom digitizer.  We weren't sure.  So it is actually a Gunzets?  Does it have a stylus?

So how did you determine it is on ttyS3?

You might want to do an attributes walk on ttyS3 and see what it pulls up:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS3)
```

---

### Post by petebarchetta on 2012-02-29
> **Favux said:**
> Alright, so this is a serial instead of usb touchscreen?

The *lsusb* doesn't have anything.  I was wondering if this wasn't an ED like with the Panasonic Toughbook CF-H2:
```
Bus 002 Device 005: ID 056a:00ed Wacom Co., Ltd
```
Because you mentioned "its a wacom screen overlay".  We were able to get the stylus working but not the touchscreen.  Panasonic said it was a "Gunze" touchscreen with the Wacom digitizer.  We weren't sure.  So it is actually a Gunzets?  Does it have a stylus?

So how did you determine it is on ttyS3?

You might want to do an attributes walk on ttyS3 and see what it pulls up:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS3)
```


Most of the detective work was done from this site,
[http://users.libero.it/hpstr/cfm34-linux.html]("http://users.libero.it/hpstr/cfm34-linux.html")

They cover the wacom unit, my machine is a slightly more youthful unit the cf-m34 jadse p3 400mhz. But to all intents and purposes for the Linux and touchscreen the same should apply.
I've commented out the lines in xorg whilst I iron out the kinks, but any assistance here would be great.

---

### Post by petebarchetta on 2012-02-29
Should have added, 
The unit doesn't come with a stylus, it should respond with any pointy object :)

---

### Post by Favux on 2012-02-29
> The unit doesn't come with a stylus, it should respond with any pointy object 
So a resistive touchscreen not a Wacom digitizer.  A Wacom stylus has an antennae.
> Most of the detective work was done from this site,
[http://users.libero.it/hpstr/cfm34-linux.html](http://users.libero.it/hpstr/cfm34-linux.html)

Helpful.  So the Toughbook CF-m34 is an old model dating from around 2003.  You should have mentioned that.  So it would be serial which is why lsusb is showing so little.

You cannot rely on the fact that Stroebel found it on the ttyS3 port.  That HOW TO is from 2003 on Debian Woody.  You need to verify what port it is on.  Try:
```
sudo dmesg | grep ttyS
```
That will likely tell you which port is in use.  You can verify raw data is coming in over that port with xxd or evtest.

Additionally the Gunzets driver newest version 1.4 dates from 2002.  Frankly I am amazed you can get it to compile given the kernel and X server changes since then.  And if compiled I highly doubt it is functional.  From this I gather Gunze stopped supporting linux or these older models or else the current drivers haven't been found.

In the README I notice it talks about the USB kernel driver communicating in PS/2 protocol.  I suspect the only way forward would be to use [inputattach]("http://sourceforge.net/projects/linuxconsole/") to convert your serial input into usb input that the evdev driver could then pick up.  If I recall there is an inputattach option for a PS/2 mouse.  That might work.  We've been able to support some old serial tablets by using inputattach and trying the various mouse and touchscreen options until we get a protocol that "works".  You may need to add a udev rule and an xorg.conf.d .conf file to match it to evdev also.

---

### Post by djszapi on 2012-05-09
Did you get the touchscreen working, if I may ask ? I am now having the  same issue with the same model. Please help! :-P Thank you in advance!

---

### Post by Favux on 2012-05-09
Hi djszapi,

Welcome to Ubuntu forums!

While we're waiting for petebarchetta to respond you could run the dmesg command:
```
sudo dmesg | grep ttyS
```
to find out which serial port it is on.

That's something useful to know whether you want to try inputattach or not.

---

### Post by AndyBacker on 2012-07-16
hello :)

i have the same problem, but i installed lubuntu 12.04 on panasonic cf m34v. the results for 

sudo dmesg | grep ttyS is:

[    0.574362] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.668970] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.709252] serial8250: ttyS2 at I/O 0x3e8 (irq = 4) is a 16550A
[    0.802768] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.840888] 00:09: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[    0.929479] 00:0a: ttyS2 at I/O 0x3e8 (irq = 7) is a 16550A

is it helpful?

---

### Post by Favux on 2012-07-16
From your dmesg output at a guess the touchscreen is on ttyS0.  You can check by using **xxd**.
```
xxd /dev/ttyS0
```
**xxd** (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  In your case dmesg.  Bring your finger or pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to use in xorg.conf.

---

### Post by AndyBacker on 2012-07-25
hello Favux, thanx for your precious answer!

I've done what you said:

xxd /dev/ttyS0
xxd /dev/ttyS1

and nothing happens on terminal.

but when i've tried 

xxd /dev/ttyS2

when i touched the screen, the terminal display a lot of number.

so i think that ttyS2 is my touchscreen.

now i try to configure my xorg.conf and i will let you know asap

thanks again :)

---

### Post by AndyBacker on 2012-07-25
mmmmmmmmm

i use lubuntu 12.04,

my /etc/X11/xorg.conf file is empty :S
my /usr/bin/X11 folder is a link
in my /usr/share/X11 show three folders (locale, xkb, xorg.conf.d) and link (rgb.txt) and two files (XErrorDB, xman.help)

what and where i have to write?

i already done "Xorg -configure" from root prompt, but still empty...

---

### Post by Favux on 2012-07-25
Hi AndyBacker

petebarchetta gave us a sample xorg.conf we could probably use with some modifications.  But rather than a xorg.conf we should try to make a .conf file for it in xorg.conf.d which is the preferred curent way of doing configuration.

So let's get a little more information.  Run this command in a terminal and post the output.
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS2)
```

You've already installed a driver for the touchscreen?

---

### Post by AndyBacker on 2012-07-26
hi Favux!

i made a fresh instalation (no dual boot) in this pc and i never installed any driver for touchscreen.

However, in ubuntu 12 precise should be WACOM driver preinstalled; though i don`t have a wacom tablet connected to my pc, that have a built-in capacitive touchscreen.

the graphical interfaces works well, i see and use icons, taskbar, open and close windows etc etc... but touch don`t work.
in windows the touchscreen works well.

so 

in /usr/share/X11/xorg.conf.d there are 7 different files. 
Each file, if i open it with gedit, seems a xorg configuration:
10-evdev.conf
11-evdev-quirks.conf
11-evdev-trackpoint.conf
50-synaptics.conf
50-vmmouse.conf
50-wacom.conf
51-synaptics.conf

:confused:

in this thread in which we are writing i read that i have to install GUNZETS drivers from here [http://www.linux.it/~rubini/software/gunzets/gunzets.html](http://www.linux.it/~rubini/software/gunzets/gunzets.html) 

but for this drivers i have to install BEFORE xFree86 (latest versions is 4.8.0)
[http://www.xfree86.org/4.8.0/Install2.html#2](http://www.xfree86.org/4.8.0/Install2.html#2)

is it true?

however, here`s the code you ask me before

```
root@xxxxxxx:/# udevadm info -q path -n /dev/ttyS2
      
      /devices/pnp0/00:0a/tty/ttyS2
```

---

### Post by Favux on 2012-07-26
You bring up several issues.
> root@xxxxxxx:/# udevadm info -q path -n /dev/ttyS2
      
      /devices/pnp0/00:0a/tty/ttyS2
Since xxd showed the touchscreen on ttyS2 I would expect more information.  You might want to try some other ports like ttyS0 S1 S3 S4 and see if anything shows up.  Also you do not need to run the udevadm info command as root.  And please run the command as:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS2)
```
The Wacom driver does not have anything to do with your touchscreen since it is apparently a Gunzet touchscreen.

[http://www.xfree86.org/4.8.0/Install2.html#2](http://www.xfree86.org/4.8.0/Install2.html#2) does not appear to be the Gunzets drivers.  It appears to be the XFree86 4.8.0 OS?

The Gunzets drivers from [http://www.linux.it/~rubini/software/gunzets/gunzets.html](http://www.linux.it/~rubini/software/gunzets/gunzets.html) are very old [http://www.ar.linux.it/pub/gunzets/](http://www.ar.linux.it/pub/gunzets/).  I do not see anything more recent then November 2003.  That's called gunzets-latest and apparently comes after 1.4.  It is not a tar though so I am not sure what it is.  By the way that appears to be Rafi Rubin who has done a lot of work on the N-Trig touchscreens kernel driver.  Anyway I doubt very much that a driver that old would work.

Unless there is a much more recent version I don't think the Gunzets driver would help.  Did someone say they compiled it and it worked?

I do notice that the page describing the drivers says the usb Gunzets touchscreen uses a PS/2 protocol.  I believe input-attach supplies some PS/2 protocol serio drivers, maybe even for touchscreens.  That may be something to look at.  See if you can convert the serial port data to a serio input event and maybe then it would work on evdev as the X driver.

---

### Post by nrKist on 2012-07-26
Sorry to poke my nose in here, but a) you seem to be pretty well versed in touchscreen issues Favux, and b) I've yet to get even one response in my own [[COLOR="Blue"]Toughbook touchscreen post[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2032332"). Do you have any suggestions to offer someone who's touchscreen worked flawlessly under evtouch and 10.04lts but works woefully inaccurately within 12.04lts and... whatever driver 12.04 is using?

Thanks!

We now return you to your regularly scheduled thread.

---

### Post by mutnik on 2012-07-26
I have just pulled out my Panasonic CF-VDL02 touchscreen LCD to use as a remote display for my CF-19 tablet.  The CF-VDL02 is also a Gunze serial device, like the CF-M34.

I know my touchscreen is connected to ttyS0.  If I issue 'inputattach -dump /dev/ttyS0' I can see the touchscreen output.  However none of the inputattach modes seem to be compatible with this Gunze screen.

Years ago it was common to configure GPM as a console mouse daemon and then piggyback XFree86 onto GPM.  If I recall, the primary reason that I did this was to avoid having to shut down GPM when starting X.  I have just installed GPM.  It appears to still support the Gunze serial devices.  I am currently having success on the console with 'gpm -m /dev/ttyS0 -t gunze -b 9600'.

Now to see if Xorg can piggyback onto GPM the way XFree86 used to do....

---

### Post by AndyBacker on 2012-07-27
Hi guys 

probably i`m mistaken, but reading around i understand that:

The panasonic cf m34 is an old pc buit around 2002-2003.
If gunzets drivers was buit in the same years, perhaps they will work... 

but in the instructions for installation of gunzets in the first section `device support` here [http://www.linux.it/~rubini/software/gunzets/gunzets.html](http://www.linux.it/~rubini/software/gunzets/gunzets.html), 
is written that they work under Xfree86 (that is the old predecessor of Xorg x window manager of all old linux distro)

so if we want to install gunzets we have to install xfree86 before, is it true?

someone get the cf m34`s touchscreen works in some way?

@Favux: sorry i don`t understand :( if you say that we can get touch work without installing gunzets and xfree86? 

```

$:/ udevadm info -a -p $(udevadm info -q path -n /dev/ttyS2)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pnp0/00:0a/tty/ttyS2':
    KERNEL=="ttyS2"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0a':
    KERNELS=="00:0a"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="PNP0501"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

```

@Mutnik: this happens in terminal when i digit `inputattach -dump /dev/ttyS2` (i think ttyS2 is my device) and i touch the screen with fingers or pen

```
#
:/home/andrea# inputattach -dump /dev/ttyS2
33 (3) 
a2 (x) 2a (*) 43 (C) 18 (x) fc (x) 
88 (x) 2b (+) 19 (x) aa (x) fc (x) 
42 (B) 
4b (K) 43 (C) 42 (B) fc (x) 
b0 (x) 
b9 (x) 63 (c) 03 (x) 42 (B) 40 (@) 3c (<) 82 (x) 33 (3) 
b3 (x) 
6a (j) 4b (K) 62 (b) 19 (x) 3a (:) 83 (x) 23 (#) c8 (x) 
ddg33 (3) 
d3 (x) 31 (1) b2 (x) 8a (x) 46 (F) 4b (K) 73 (s) 25 (%) 
74 (t) 2b (+) a2 (x) 40 (@) 43 (C) 9d (x) 33 (3) 27 (') 
9d (x) 
33 (3) 
88 (x) 
33 (3) 
32 (2) 
f7 (x) 
e7 (x) 
02 (x) 40 (@) 42 (B) 9d (x) b3 (x) 27 (') d4 (x) 

```

guys don`t say me that i have to use ndiswrapper :(

---

### Post by mutnik on 2012-07-27
> **AndyBacker said:**
> 
@Mutnik: this happens in terminal when i digit `inputattach -dump /dev/ttyS2` (i think ttyS2 is my device) and i touch the screen with fingers or pen

```
#
:/home/andrea# inputattach -dump /dev/ttyS2
33 (3) 
a2 (x) 2a (*) 43 (C) 18 (x) fc (x) 
88 (x) 2b (+) 19 (x) aa (x) fc (x) 
42 (B) 
4b (K) 43 (C) 42 (B) fc (x) 
b0 (x) 
b9 (x) 63 (c) 03 (x) 42 (B) 40 (@) 3c (<) 82 (x) 33 (3) 
b3 (x) 
6a (j) 4b (K) 62 (b) 19 (x) 3a (:) 83 (x) 23 (#) c8 (x) 
ddg33 (3) 
d3 (x) 31 (1) b2 (x) 8a (x) 46 (F) 4b (K) 73 (s) 25 (%) 
74 (t) 2b (+) a2 (x) 40 (@) 43 (C) 9d (x) 33 (3) 27 (') 
9d (x) 
33 (3) 
88 (x) 
33 (3) 
32 (2) 
f7 (x) 
e7 (x) 
02 (x) 40 (@) 42 (B) 9d (x) b3 (x) 27 (') d4 (x) 

```



Yes.  That is what I see as well from my touchscreen.  I could not find any inputattach 'modes' that properly understood that protocol.  Some of them, however, did result in the mouse cursor jumping wildly around when touching the screen.  It should be possible to patch inputattach with gunze support.  Possibly some insight into doing so could be obtained from viewing the gunzets code, or from the current gpm code.

In fact gpm works pretty good on a text console with the gunze screen.  It still needs some calibration, but definitely understands the touchscreen's protocol.  I have gotten a little bit closer to using gpm as a pass-through for Xorg.  Adding the '-Rraw' option like this: 'gpm -m /dev/ttyS0 -t gunze -b 9600 -Rraw' results in gpm creating a fifo called /dev/gpmdata.  That fifo should be able to provide an input into Xorg.  I am currently researching how to add /dev/gpmdata as an input device using the files under /usr/share/X11/xorg.conf.d.  Unfortunately I am quite sure that gpm is not providing any protocol translation on /dev/gpmdata.  It seems unlikely that Xorg will be able to understand the touchscreen data even if it sees it.

Ultimately, adding 'serial gunze' support to inputattach seems the likely best solution.  You won't hear me suggesting ndiswrapper!

---

### Post by Favux on 2012-07-27
Hi AndyBacker,

Looks like ttyS2 is correct.  Your udevadm info looks right for a serial device and output is like mutnik's.
> you say that we can get touch work without installing gunzets and xfree86? 
Right, in fact you probably have to.  What you likely need is a new serio kernel driver.

To follow what mutnik and me are talking about you need to know input-attach got a new home a little while ago.  It is now part of the Linux Console project:  [http://sourceforge.net/projects/linuxconsole/](http://sourceforge.net/projects/linuxconsole/)

You can see a new serio driver being added to input-attach there, the Linux Wacom project's wacom_w8001.ko in input-wacom, also see:  [http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/input-wacom;a=summary](http://linuxwacom.git.sourceforge.net/git/gitweb.cgi?p=linuxwacom/input-wacom;a=summary)  Or the new Wacom legacy serial graphics tablets serio drivers wacom_serial.ko and wacom_serial5.ko located here:  [http://ubuntuforums.org/showthread.php?p=10928556](http://ubuntuforums.org/showthread.php?p=10928556)

And for GPM see:  [http://en.wikipedia.org/wiki/GPM_%28software%29](http://en.wikipedia.org/wiki/GPM_%28software%29)

---

### Post by mutnik on 2012-07-27
A little update on the gpm-passthrough front...

Turns out there are instructions located in /usr/share/doc/gpm/README.gunze.gz that outline configuring gpmdata as an XFree86 input using the Summa module.  Unfortunately it looks like xserver-xorg-input-summa was removed from Debian and Ubuntu repos back in may of 2009.

---

### Post by Favux on 2012-07-27
> Unfortunately it looks like xserver-xorg-input-summa was removed from Debian and Ubuntu repos back in may of 2009. 
Right.  Summa Sketch is no more.  That is another tablet you see questions about that needs a serio driver.  At least I've never seen anyone try to update its serial X driver.

---

