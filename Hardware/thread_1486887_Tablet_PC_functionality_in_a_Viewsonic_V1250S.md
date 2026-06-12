---
title: "Tablet PC functionality in a Viewsonic V1250S"
date: 2010-05-18
forum: Hardware
---

### Post by Ziris on 2010-05-18
Hello all,

So I recently came into possession of a Viewsonic V1250S tablet PC.  Long story short, I'm in an OS conundrum.  The only OS I can get to work on this computer with full tablet PC functionality is Windows Vista, which is everybody's favorite OS, I know!  I've been trying incessantly to get Ubuntu to find and use the Wacom hardware, but under every circumstance it fails to even recognize that it's even attached (as far as I can tell anyway).  There was one time on a fresh install where the mouse would sputter into the top left corner a little when I put the stylus to the screen, but an update made sure to eliminate even that.  I believe the OS I was using was Ubuntu 9.10, but it also could have been Fedora 12, I've tried so many I've lost track.  Anyway, I've dug through these forums in an attempt to get it working, following various how-tos and guides, all leading to a failure in some form or another.  Right now I'm on Ubuntu Netbook Remix 10.04, and really liking it, so I would love to see the tablet PC part start working, but if I can't then it's back to Vista *shudder*.  So I guess my question is:  since Ubuntu apparently is not even recognizing that a Wacom device is even plugged in, is this whole project of mine a nonstarter?  Or if anyone has any suggestions/info, could you point me in the right direction??  Thanks for any help!

Additional Info on PC:
[http://ftp.viewsonic.com/support/mobilewireless/tabletpc/tabletpcv1250s/](http://ftp.viewsonic.com/support/mobilewireless/tabletpc/tabletpcv1250s/)

---

### Post by Favux on 2010-05-19
Hi Ziris,

Welcome to Ubuntu forums!

If it is a Wacom digitizer (and I know some were) you should be able to get it to work.  I'll guess, given it's age, it has a serial internal connection rather than usb.  And that's the problem, it may need some extra configuration.

In a terminal enter:
```
lspci
```
and see if it shows up.  Also try:
```
grep -i name /proc/bus/input/devices
```
And let's see if:
```
dmesg | grep ttyS
```
shows anything.

---

### Post by Ziris on 2010-05-19
Hi there!  Thanks for hearing my plight!

I ran those commands, and nothing showed up outside of the usual suspects.  Here's what I came up with, just in case I missed anything:

lspci
```
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 83)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 03)
02:01.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
02:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:09.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ac)
02:09.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 04)
02:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```grep -i name /proc/bus/input/devices
```
N: Name="Lid Switch"
N: Name="Sleep Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="SynPS/2 Synaptics TouchPad"
```And "dmesg | grep ttyS" comes up with nothing.

Also, I believe you are right in assuming that it is a serial rather than usb internal connection, as, though the spec sheet doesn't indicate, vista reports it as a "Wacom Serial" device.

---

### Post by Ziris on 2010-05-19
Also, in my /dev folder, there are 3 ttyS* devices, so I don't know if that helps.  Plus, I did a little digging on serial devices in linux, and found this, [http://accesio.com/go.cgi?p=../software/linuxserial.html](http://accesio.com/go.cgi?p=../software/linuxserial.html), suggesting that I need to use a command called "setserial" to assign a serial port to a device.  Is is possible that my serial tablet device isn't properly being assigned a port on a device, hence the reason why it isn't showing up in any of the lists?

---

### Post by Favux on 2010-05-19
Short answer is yes.  But we'd like the dmesg output before installing setserial.  It gives us our parameters.  So try:
```
sudo dmesg | grep ttyS
```
first.  If no output then install setserial and let's see what:
```
setserial -g /dev/ttyS*
```
gives us.

What did you see with?:
```
ls /dev/ttyS*
```
Let's also try:
```
ls -la /dev/tablet-event
```
It seems to me we should be seeing something.

---

### Post by Ziris on 2010-05-19
Yeah, I had already tried sudoing all of those previous commands and came up with nothing different, and yes, I agree that we should be seeing SOMEthing at least, which is why I raised my initial concern that this project is potentially a nonstarter.  Anyway,  running setserial gives me

```
setserial -g /dev/ttyS*
/dev/ttyS0, UART: unknown, Port: 0x06f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```These are my 3 serial devices in /dev

```
/dev/ttyS0  /dev/ttyS1  /dev/ttyS2  /dev/ttyS3
```And the tablet-event directory doesn't exist.

Moreover, I went back into windows to see if I could get any useful device info from there, and this seems to me to be the only generic info I found:

```
hardware ID: 
ACPI\WACF004 
 
I/O Range: 
06F8 - 06FF 
 
IRQ: 
0x00000004
```

I noticed from here that this is being IDed as an ACPI device, and I've read in a few spots that older computers don't properly handle ACPI events.  Could that possibly be the problem or part of the problem you think?  Also, what parameters are we looking for from this device?  If I knew what we were looking for, I could hop back into windows and see if I could dig up the relevant info.

---

### Post by Favux on 2010-05-19
Beautiful.  You've identified the digitizer's PnP identifier, namely WACF004.

The info. we need to place a serial line in serial.conf so setserial can work with it would look something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
Then we'd add something like this line to the serial.conf file in "/etc/serial.conf":
```
/dev/ttyS0 uart 16550a port 0x3f8 irq 4 baud_base 34800
```

But let's see if the problem is that the serial identifier line in 10-wacom.conf is case specific first.  It should be located in /usr/lib/X11/xorg.conf.d/.  And the serial snippet/section should look like:
```
Section "InputClass"
	Identifier "Wacom serial class identifiers"
	MatchProduct "WACf|FUJ02e5|FUJ02e7"
	Driver "wacom"
	Option "ForceDevice" "ISDV4"
EndSection
```
What happens if you change the MatchProduct line to:
```
	MatchProduct "WACf|WACF|FUJ02e5|FUJ02e7"
```
and reboot?

---

### Post by Ziris on 2010-05-19
Yay!  I love it when I'm useful to my own cause!  Anyway, I tried your second suggestion concerning changing the matchproduct line first and came up with nothing.  I then went to change the /etc/serial.conf file, only to find that it didn't exist.  The only serial.conf file I found resided in /etc/bluetooth/.  So for fun I created /etc/serial.conf and added those two lines you showed me, changing the I/0 line to 0x06f8 on both of them, and nothing happened.  So I moved on to add those two lines to the preexisting serial.conf file, again changing the I/O line on both, and still nothing happened.  So I went back and re-ran setserial and discovered that ttyS0 no longer showed anything attached:

```
setserial -g /dev/ttyS*
/dev/ttyS0: No such device
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3
```whoops.

So I went and tried the lines in both files respectively exactly as you had given them to me, and still nothing, and setserial is still reporting "no such device" on ttyS0.  Oh, and I rebooted after changing each individual item.

---

### Post by Favux on 2010-05-19
Hmmm.  You only want one line in serial.conf.  Since we don't know the baud_base you could use autoconfig.  So for ttyS0, given what you got from 'setserial -g /dev/ttyS*' it would be something like:
```
/dev/ttyS0 port 0x06f8 irq 4 autoconfig
```
or for ttyS1:
```
/dev/ttyS0 port 0x02f8 irq 3 autoconfig
```
etc.  Then you generally use:
```
sudo /etc/init.d/setserial reload
```
and also probably have to reboot.

To determine which tty the digitizer is on you can use:
```
xxd /dev/ttyS0
```
xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to use.

---

### Post by Ziris on 2010-05-19
Ok, so I changed both serial.conf files to have only the line "/dev/ttyS0 port 0x06f8 irq 4 autoconfig", ran the setserial reload, rebooted, and ran the xxd application on all ttyS* devices.  Nothing seemed to work.  The xxd app exited immediately on all devices, so it's apparently not initialized or something.  I also sudoed the xxd app for good measure.  Just to make sure I'm on the right track here, when we find a solution that will work, the tablet pc functionality will just start automatically, right?  Just reboot and it'll start working?  Or is there something I have to do to start the service?  Also, I don't know if this will make a difference, but I'm running ubuntu from a Wubi install.  I'm not sure how it works exactly, but when it says "hard drive performance is reduced" it leaves me with the impression that Windows is still running somehow.  A wubi install wouldn't be interfering with it would it?

---

### Post by Favux on 2010-05-19
Hi Ziris,

Your serial digitizer should work out of the box in Lucid.  Provided the upstream udev rules are configuring the serial stuff correctly and the serial snippet in wacom.conf recognizes it.  We're trying to figure out why it doesn't.

Serial digitizers can be idiosyncratic so maybe the udev rules aren't configuring it correctly, not covering your digitizer's specific case.  So we're trying to set it up manually (the old way) with setserial and a serial line in serial.conf.

And yes, when we have a solution it should start working after a reboot.

I don't know if WUBI interferes or not.  It looks like it maybe does because we didn't get anything with the dmesg command.  And xxd isn't picking up input on any of the 4 terminals.  It's possible it isn't providing the appropriate serial services.

---

### Post by Ziris on 2010-05-19
I appreciate all the help you're giving me Favux.  Yeah, that would be nice if it worked out of the box.  I'll do a fresh install from the CD and see if that eliminates the problem.  At the very least it'll eliminate any potential for wubi to interfere.  It was just easier to install from wubi in case I wanted to uninstall.  BUT, before I do that, I have one more thought on why my tablet isn't working in the least.  In order for me to be able to install ubuntu at all, I had to enable an option called "nomodeset", apparently due to needing access to older graphics drivers.  It's not sounding like it would cause interference due to it being a display driver option only, but am I wrong?  Is me using "nomodeset" screwing my ability to use the tablet feature?

---

### Post by Favux on 2010-05-19
Not a problem.

That shouldn't have anything to do with it.  It just tells boot up not to use "kernel mode setting" for your video chipset.  Since that's a new feature it doesn't yet work with some video.  So you just remove it as default and go to older, maybe slower, video drivers.

---

### Post by Ziris on 2010-05-21
Hey, sorry for the delay.  I ran into a bit of a speedbump when I was installing from CD.  I was rudely reminded that it wasn't nomodeset that I was using, it was actually xforcevesa.  Either way, it still doesn't sound like it would have anything to do with tablet features.  Anyway, after I did a fresh install and updated it, I tried the tablet and got nothing.  Running xxd on each of the ttyS* devices ended in failure too.  However, after that I ran sudo dmesg | grep ttyS* and actually got something:

```
grep: ttyS1: Input/output error
grep: ttyS2: Input/output error
grep: ttyS3: Input/output error
```

That makes me feel slightly happier, now that it's reporting that SOMEthing is happening out there.  I was thinking installing setserial and doing those steps would be my next course of action.  Is this the right idea, or should I take another approach now that dmesg gave us results?

---

### Post by Favux on 2010-05-21
I'm confused by what you are seeing.  Your ttyS0 seems to have disappeared, and that's usually the one the digitizer is on.  But not always.  The dmesg output should look something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
I agree it's encouraging that there is some sort of reaction.  I think you're right.  Try setserial and the other steps with that and see where that gets you.

---

### Post by Ziris on 2010-05-21
Well, don't worry, those I/O errors being reported went away, so I'm back at square one.  I went through all the other steps we had and ended up in the same boat we were in before I reinstalled, thus I've successfully ruled out Wubi as being the cause of the problem.  None of the other steps we did produced any sort of reaction on anything.  The only thing that produces any sort of reaction is when I change the config line in serial.conf from

```
/dev/ttyS0 port 0x06f8 irq 4 autoconfig
```to

```
/dev/ttyS0 uart 16550a port 0x06f8 irq 4 baud_base 34800
```This causes setserial -g /dev/ttyS* output to go from

```
/dev/ttyS0, UART: unknown, Port: 0x06f8, IRQ: 4
```to

```
/dev/ttyS0: No such device
```So could this mean that this is kind of the right track?  That if we were to declare ttyS0 correctly in serial.conf that it would start positively identifying it as it should?  I'll admit that I'm pretty much out of ideas here.  I've been doing some reading and research and haven't come up with anything new here.

---

### Post by Favux on 2010-05-21
Hi Ziris,

Try adding UART to lines for S1 and up.  It seems to me I've also seen one on S4, which you don't have of course.  I'm puzzled as to why xxd isn't showing us any active device.  We know it works in Vista.

I can see why you couldn't set up on previous releases.  It shouldn't be this hard.

To see if the digitizer is recognized, but we are just not configuring it correctly, we could try to wade through udevadm info.:
```
udevadm info --export-db > $HOME/udevadm-info.txt
```
and see if it is there.  Open it in Text Editor and use find for tty or serial, etc..

Hopefully I'm not leading us down the rabbit hole but I'm wondering if the problem isn't with the kernel.  If the digitizer isn't in udevadm info. then the following would be more likely.  In older releases there was a kernel driver called something like PNP8250.ko.  This was the serial PnP (plug and play) identifier driver.  It has tables of all serial devices.  When the device is recognized by the driver it is setup in the kernel so the kernel can communicate about it.  A few releases ago, Intrepid/Jaunty(?), it was brought directly into the kernel.  Could it be your serial digitizer isn't listed in the tables, or there's a typo?

Hopefully I'm wrong and it is something downstream from the kernel.  If we can figure it out.

---

### Post by Ziris on 2010-05-21
Hi again Favux,

So adding those uart lines to the serial.conf file only succeeded in making all ttyS* devices report "No such device".  BUT, I did get a glimmer of hope upon checking out the udevadm info, assuming I'm reading it right and also assuming that what I found wasn't put in there by me somehow.  I searched for ttyS0 and found it, and also actually found a wacom entry right above it.  Here's what I got:

```
P: /devices/pnp0/00:06
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:06
E: DRIVER=serial
E: SUBSYSTEM=pnp
E: NAME=Serial Wacom Tablet
E: ID_INPUT=1
E: ID_INPUT_TABLET=1

P: /devices/pnp0/00:06/tty/ttyS0
N: ttyS0
S: char/4:64
E: UDEV_LOG=3
E: DEVPATH=/devices/pnp0/00:06/tty/ttyS0
E: MAJOR=4
E: MINOR=64
E: DEVNAME=/dev/ttyS0
E: SUBSYSTEM=tty
E: ID_INPUT=1
E: ID_INPUT_TABLET=1
E: DEVLINKS=/dev/char/4:64
```Now, assuming I'm not the one who made it look like that, this is telling us that Ubuntu is not only identifying that device ttyS0 is a tablet device, but is also IDing it as being a Serial Wacom Tablet.  So, again assuming I'm interpreting this correctly, there's nothing wrong with the kernel and there's just something else we're missing.

Also, I found another command that'll tell us what's going on behind the scenes while Ubuntu is trying to initialize the Wacom tablet (I think).  Here's what I've got:

grep -i wacom /var/log/Xorg.0.log

```
(II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
(**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
(II) Serial Wacom Tablet: other types will be automatically added.
(**) Serial Wacom Tablet: always reports core events
(II) Serial Wacom Tablet: hotplugging dependent devices.
(**) Serial Wacom Tablet eraser: always reports core events
(II) XINPUT: Adding extended input device "Serial Wacom Tablet eraser" (type: ERASER)
(EE) Serial Wacom Tablet eraser: wcmWriteWait error : Input/output error
(EE) Serial Wacom Tablet eraser: wcmWriteWait error : Input/output error
(II) Serial Wacom Tablet eraser: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet eraser"
(II) UnloadModule: "wacom"
(II) Serial Wacom Tablet: hotplugging completed.
(II) XINPUT: Adding extended input device "Serial Wacom Tablet" (type: STYLUS)
(EE) Serial Wacom Tablet: wcmWriteWait error : Input/output error
(EE) Serial Wacom Tablet: wcmWriteWait error : Input/output error
(II) Serial Wacom Tablet: serial tablet id 0x90.
(EE) Couldn't init device "Serial Wacom Tablet"
(II) Serial Wacom Tablet: removing automatically added devices.
(II) UnloadModule: "wacom"
```So, according to this report, Ubuntu is having trouble initializing parts of it, and other parts don't seem to be defined properly ("(EE) Couldn't init device "Serial Wacom Tablet eraser"" and "(II) Serial Wacom Tablet: type not specified, assuming 'stylus'.", respectively.)

---

### Post by Favux on 2010-05-21
Beautiful!  :)  It looks like we have it.

Apparently ttyS0 is disappearing because that's where the digitizer is.  Not quite sure why that's happening.

You are right, udevadm info clearly shows it is recognized (PnP good).  And Xorg.0.log shows it is trying to set up on it.  So there is a valid Wacom digitizer on ttyS0.  The errors seem to refer to too long waits on the asynchronous signal response times.  That could mean we just need to play with the baud rates and find the correct one.  Is the udevadm info from default or did you have a serial line in serial.conf?  If so what was it?  We may be able to dispense with setserial.

I guess another possibility for the errors is your digitizer is old enough that it does not support the ISD4 protocol correctly.  You could try commenting it out (#) in the serial snippet in 10-wacom.conf and reboot and see what happens.

I was chasing down the possibility that your digitizer was on ttyS4 and found another Wacom tablet pc, an Acer, that was on ttyS4:  [http://forum.tabletpcreview.com/news-headlines/4843-running-ubuntu-linux-acer-tablet-pcs-part-iii.html](http://forum.tabletpcreview.com/news-headlines/4843-running-ubuntu-linux-acer-tablet-pcs-part-iii.html)  So I didn't hallucinate that.  Then I was trying to figure out how to add ttyS4 and found it:  [http://tldp.org/HOWTO/Serial-HOWTO-16.html#nr_ports](http://tldp.org/HOWTO/Serial-HOWTO-16.html#nr_ports)  A simple parameter on the kernel boot line.  By the way that's from the linux serial "bible":  [http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html)

---

### Post by Ziris on 2010-05-21
Thanks for the references!  I have a feeling I'll be reading those quite a bit.  On to business, the udevadm info was from me having the following in the serial.conf file:

```
/dev/ttyS0 uart 16550a port 0x06f8 irq 4 autoconfig
/dev/ttyS1 uart 16550a port 0x02f8 irq 3 autoconfig
/dev/ttyS2 uart 16550a port 0x03e8 irq 4 autoconfig
/dev/ttyS3 uart 16550a port 0x02e8 irq 3 autoconfig
```

I commented them out as well as the ISD4 line in 10-wacom.conf and nothing resulted short of removing the "No such device" message from setserial.  I have some running around to do, but later this evening I'll do some digging and see if I can turn up the baud rate for this bad boy and start adding that into the serial.conf file to see what happens.

---

### Post by Favux on 2010-05-21
You should only have one line in the serial.conf at a time I think, unless you are actually setting up more than one device.

I think what I would do first is remove serial.conf and setserial and then repeat udevadm info.  If the digitizer is there like before you probably don't need to be setting it up manually.

You could try commenting out ISD4 again at that point.  The baud rate option for a .fdi was:
```
<merge key="input.x11_options.BaudRate" type="string">38400</merge>
```
So I think for the 10-wacom.conf serial snippet it may look like:
```
Option "BaudRate" "38400"
```
Default is 9600.  I don't think lower ones were ever really used, like 2400 and 4800.  So probably 19200, 28800, and 38400 are the other options.  I don't know if that's a valid option for a xorg.conf.d .conf file though.  Here's some links on the new .conf files:
[https://fedoraproject.org/wiki/Input_device_configuration](https://fedoraproject.org/wiki/Input_device_configuration)
[http://who-t.blogspot.com/2010/01/new-configuration-world-order.html](http://who-t.blogspot.com/2010/01/new-configuration-world-order.html)

The xorg.conf.d .conf files are like the xorg.conf.  Easy to break X.  So be sure to backup the working 10-wacom.conf and be ready to restore it from the command line if needed.  For whatever reason with the .fdi files it was tough to break X.

---

### Post by Ziris on 2010-05-22
Ok, so I'm playing around with both my xorg.conf and 10-wacom.conf files and I'm not getting anything new.  Figured an extra set of eyes might help me if I'm missing something.  Anyway, here are the files:

10-wacom.conf - I added the baud rates in here, commented out the ISDV4 sections, and manually added the entire "Wacom serial class identifiier" section from what we discussed before.
```
Section "InputClass"
    Identifier "Wacom class"
    MatchProduct "Wacom|WACOM"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection

Section "InputClass"
    Identifier "Wacom serial class"
    MatchProduct "Serial Wacom Tablet"
    Driver "wacom"
#    Option "ForceDevice" "ISDV4"
    Option "BaudRate" "38400"
EndSection

Section "InputClass"
    Identifier "Wacom serial class identifiers"
    MatchProduct "WACf|WACF|FUJ02e5|FUJ02e7"
    Driver "wacom"
#    Option "ForceDevice" "ISDV4"
    Option "BaudRate" "38400"
EndSection

# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
    Identifier "Wacom N-Trig class"
    MatchProduct "HID 1b96:0001"
    MatchDevicePath "/dev/input/event*"
    Driver "wacom"
EndSection
```xorg.conf - Every input device I added, as I read that they need to be declared in here from somewhere.  I also added the "autoserverlayout" section, since I was told that each input device needed to be declared in the "serverlayout" section of this file which was nonexistant, and "autoserverlayout" did it for me anyway.

```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option    "AutoServerLayout"    "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option    "AutoServerLayout"    "on"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option    "AutoServerLayout"    "on"
EndSection


Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```Also, I found this:  [https://lists.launchpad.net/ubuntu-x-swat/msg44975.html](https://lists.launchpad.net/ubuntu-x-swat/msg44975.html), which sounds kinda cool, but since I don't have an xf86-input-wacom rules file, I can't really follow this solution.  Suggestions/comments?  I'm rather tired, so I'm fairly confident I'm forgetting something or misunderstanding something.

Plus, one more thing.  Correct me if I'm wrong, but the way I'm understanding how X works is that it reads everything in xorg.conf first, then moves on to any config files in /usr/lib/X11/xorg.conf.d/, and reads those.  So it wouldn't really matter if I declare something in one location or the other, since it'll be read one way or another?

Oh, and I went ahead and uninstalled setserial and deleted the serial.conf file, and everything still shows up as before, including in udevadm.  I have a feeling you are right about setserial, as it isn't a problem with ubuntu recognizing it, but just a problem of initializing it.

---

### Post by Favux on 2010-05-22
> Oh, and I went ahead and uninstalled setserial and deleted the serial.conf file, and everything still shows up as before, including in udevadm. I have a feeling you are right about setserial, as it isn't a problem with ubuntu recognizing it, but just a problem of initializing it.
That's what I suspected, glad you confirmed it.
> the way I'm understanding how X works is that it reads everything in xorg.conf first, then moves on to any config files in /usr/lib/X11/xorg.conf.d/, and reads those.
Actually that isn't 100% clear to me.  What runs last should control.  I think the way it works is the Xserver starts to read xorg.conf and then is diverted to xorg.conf.d where the .conf files and their snippets act as xorg.conf sections.  Then Xserver finishes reading xorg.conf.  So you can think of it as xorg.conf.d .conf files run first followed by xorg.conf, meaning xorg.conf entries will control.  See if what you're reading gibes with that interpretation.

In your 10-wacom.conf you now have two serial snippets.  You probably only want one, although the two apparently aren't breaking X.

I'm not real confident about:
```
  Option    "AutoServerLayout"    "on"

```
Remember the author is commenting on an alpha or beta version of xorg.conf.d and I haven't seen that elsewhere.  So let's just use a standard "ServerLayout".  I think your xorg.conf should look more like:
```
Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option        "BaudRate"      "38400"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"          # SERIAL ONLY
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Serial Tablet PC ONLY
  Option        "BaudRate"      "38400"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "vesa"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"X.org Configured"
	InputDevice	"stylus"
	InputDevice	"eraser"
EndSection
```
And if you use the baud rate in xorg.conf you can remove it from the 10-wacom.conf.

I'm not sure we need to worry about serial tablet udev rules, but that was a good find.  Right now the current rules on your system seem to be good enough to get your digitizer recognized and the Wacom tablet trying to set up on it.

---

### Post by Ziris on 2010-05-24
Good evening!

So I took the time and made my xorg.conf file the way you posted and came up with nothing.  I then proceeded to test out all listed baud rates one by one, then disabled the ISDV4 option and tested each baud rate again, and still came up with nothing.  Absolutely nothing.  This is about a billion times harder than I thought it would be, and a billion times harder than it SHOULD be.  I've been doing some reading around, and I'm wondering if the hardware support has been deprecated in the kernel.  Even though it is properly identifying it, maybe it just can't properly handle it.  What do you think the likelihood of that is?  I'm almost tempted to get my hands on an older copy of ubuntu (8.10 or earlier) and see if the tablet works in there.  If you've got any more ideas on what could possibly be going wrong and how to possibly fix it (download and locally compile the latest wacom driver?), I'm all ears.  Aside from that, I think installing an older version to me seems like a good next step.  I've read about people who've had working tablets, did an upgrade and was fine, but when they did a clean install it stopped working.  So maybe I can get lucky and trick it into working.  Comments?  Suggestions?  Thanks again for all the help!

---

### Post by Favux on 2010-05-25
I totally agee with you.  I hope I'm not missing something obvious.

It seems something should have worked.

There are two ways to go.  Say install Hardy Heron (8.04 LTS) or file a bug report at the LWP (linux wacom project) or perhaps post on linuxwacom discuss and see if someone can help you.

---

### Post by Ziris on 2010-05-30
Hello Favux,

So I've been in contact with someone from the linux wacom project, and really didn't come up with anything new.  Here's how our correspondance went:

```
If you can not xxd the port, the port is not ready/available.   Something is wrong.  Are comfortable with building a kernel driver for  your kernel? 
  
 If you are comfortable, please update 8250_pnp.c as described at [http://linuxwacom.sourceforge.net/index.php/howto/tabletpc](http://linuxwacom.sourceforge.net/index.php/howto/tabletpc) 
  -------------------------------------------  
If you have installed the kernel source that your system was  based on, check the source under drivers/serial to see if you have  8250_pnp.c or not. If the file exists, please add:  
[INDENT]	/* Wacom tablets */
	{	"WACFXXX",		0	},
[/INDENT] to the end of pnp_dev_table (or replace all entries that start with  WACF). Then compile and install your kernel from source. Once you launch  the newly installed kernel, your serial tablet should be mapped to a  ttyS port. Use xxd to decide which port is associated with your  device. 
  ------------------------------------
 Ping

 On Tue, May 25, 2010 at 2:42 PM, adam vest <[EMAIL="foxmulder2004@yahoo.com"]foxmulder2004@yahoo.com[/EMAIL]>  wrote:
  Hi Ping, thanks for the timely response!  xxd exits  immediately when trying it on any ttyS* device.  I've got my xorg.conf  and Xorg.0.log attached, along with an Xorg.0.log file with only wacom  entries.
  


  

    From: Ping Cheng <[EMAIL="pinglinux@gmail.com"]pinglinux@gmail.com[/EMAIL]>
To: adam vest <[EMAIL="foxmulder2004@yahoo.com"]foxmulder2004@yahoo.com[/EMAIL]>
Sent: Tue, May 25, 2010  1:10:01 PM
Subject:  Re: WACOM on a Viewsonic  V1250S configure troubles

   
Hi Adam,
  
 I see you have a WACF004 mapped onto /dev/ttyS0. That's all good  signs (a Wacom serial pen only device on serial port 1). 
  
 Let's focus on the xorg.conf to see where we get.  email me your  xorg.conf and Xorg.0.log first.
  
 Also, when you issue "xxd /dev/ttyS0" then move the pen on the  tablet, do you get any output?
  
 Ping

 On Mon, May 24, 2010 at 11:03 PM, adam vest <[EMAIL="foxmulder2004@yahoo.com"]foxmulder2004@yahoo.com[/EMAIL]>  wrote:
      [COLOR=Red]
[/COLOR]      [COLOR=Red]
[/COLOR]     [COLOR=Red]
[/COLOR]    [COLOR=Red]Hey there!  So I've been trying for quite some time to get my  tablet PC working in the latest version of Ubuntu (10.04).  My PC in  question is a [Viewsonic  V1250S]("http://ftp.viewsonic.com/support/mobilewireless/tabletpc/tabletpcv1250s/").  I've been at it since before 10.04 was released, trying  also on 9.10.  The best I can tell is that the OS can tell that there is  a serial tablet device plugged in, but can't seem to do anything with  it.  Always comes back as saying it "Couldn't init device".  Just  recently I started a thread in the Ubuntu forums, and myself and a guy  (Favux) have been at it for about a week and have made no progress  whatsoever.  [Here's the thread]("http://ubuntuforums.org/showthread.php?t=1486887") if  you care to take a gander at what we've done and possibly offer some  insight into the current situation.  I would MUCH appreciate it, as I'm  ready to be done trying to make this work.  I hope to hear from you  soon.

-Adam[/COLOR] 


```

I looked, and found that our setserial command was just the manual way of compiling into the kernel, and figured since one way wasn't working, and I really don't know how to compile my kernel, even though I'm willing to.  Anyway, this is becoming more trouble than it's worth.  This is probably a very unique case, as I'm figuring not many Viewsonic V1250S's are still out there.  And besides, I already have it working in Vista.  I was just saying thanks for helping me out, and if anybody has any more observations or whatever, feel free to pick up where this left off.

---

### Post by ehisey on 2010-10-10
> **Ziris said:**
> Hello Favux,

So I've been in contact with someone from the linux wacom project, and really didn't come up with anything new.  Here's how our correspondance went:

```
If you can not xxd the port, the port is not ready/available.   Something is wrong.  Are comfortable with building a kernel driver for  your kernel? 
  
 If you are comfortable, please update 8250_pnp.c as described at [http://linuxwacom.sourceforge.net/index.php/howto/tabletpc](http://linuxwacom.sourceforge.net/index.php/howto/tabletpc) 
  -------------------------------------------  
If you have installed the kernel source that your system was  based on, check the source under drivers/serial to see if you have  8250_pnp.c or not. If the file exists, please add:  
[INDENT]	/* Wacom tablets */
	{	"WACFXXX",		0	},
[/INDENT] to the end of pnp_dev_table (or replace all entries that start with  WACF). Then compile and install your kernel from source. Once you launch  the newly installed kernel, your serial tablet should be mapped to a  ttyS port. Use xxd to decide which port is associated with your  device. 
  ------------------------------------
 Ping

 On Tue, May 25, 2010 at 2:42 PM, adam vest <[EMAIL="foxmulder2004@yahoo.com"]foxmulder2004@yahoo.com[/EMAIL]>  wrote:
  Hi Ping, thanks for the timely response!  xxd exits  immediately when trying it on any ttyS* device.  I've got my xorg.conf  and Xorg.0.log attached, along with an Xorg.0.log file with only wacom  entries.
  


  

    From: Ping Cheng <[EMAIL="pinglinux@gmail.com"]pinglinux@gmail.com[/EMAIL]>
To: adam vest <[EMAIL="foxmulder2004@yahoo.com"]foxmulder2004@yahoo.com[/EMAIL]>
Sent: Tue, May 25, 2010  1:10:01 PM
Subject:  Re: WACOM on a Viewsonic  V1250S configure troubles

   
Hi Adam,
  
 I see you have a WACF004 mapped onto /dev/ttyS0. That's all good  signs (a Wacom serial pen only device on serial port 1). 
  
 Let's focus on the xorg.conf to see where we get.  email me your  xorg.conf and Xorg.0.log first.
  
 Also, when you issue "xxd /dev/ttyS0" then move the pen on the  tablet, do you get any output?
  
 Ping

 On Mon, May 24, 2010 at 11:03 PM, adam vest <[EMAIL="foxmulder2004@yahoo.com"]foxmulder2004@yahoo.com[/EMAIL]>  wrote:
      [COLOR=Red]
[/COLOR]      [COLOR=Red]
[/COLOR]     [COLOR=Red]
[/COLOR]    [COLOR=Red]Hey there!  So I've been trying for quite some time to get my  tablet PC working in the latest version of Ubuntu (10.04).  My PC in  question is a [Viewsonic  V1250S]("http://ftp.viewsonic.com/support/mobilewireless/tabletpc/tabletpcv1250s/").  I've been at it since before 10.04 was released, trying  also on 9.10.  The best I can tell is that the OS can tell that there is  a serial tablet device plugged in, but can't seem to do anything with  it.  Always comes back as saying it "Couldn't init device".  Just  recently I started a thread in the Ubuntu forums, and myself and a guy  (Favux) have been at it for about a week and have made no progress  whatsoever.  [Here's the thread]("http://ubuntuforums.org/showthread.php?t=1486887") if  you care to take a gander at what we've done and possibly offer some  insight into the current situation.  I would MUCH appreciate it, as I'm  ready to be done trying to make this work.  I hope to hear from you  soon.

-Adam[/COLOR] 


```

I looked, and found that our setserial command was just the manual way of compiling into the kernel, and figured since one way wasn't working, and I really don't know how to compile my kernel, even though I'm willing to.  Anyway, this is becoming more trouble than it's worth.  This is probably a very unique case, as I'm figuring not many Viewsonic V1250S's are still out there.  And besides, I already have it working in Vista.  I was just saying thanks for helping me out, and if anybody has any more observations or whatever, feel free to pick up where this left off.

Well Favux, If you still are willing to hammer at this I still have one of my ViewSonics to tinker with. ( Now I wish I had not tossed the other one).

---

### Post by Favux on 2010-10-11
Hi ehisey,

Welcome to Ubuntu forums!

Sure, why not?

It's too late tonight for me to reread the thread and get back up to speed though.  In the meantime did you have any new thoughts?

---

### Post by Ziris on 2011-01-13
Believe it or not, I've been keeping an eye on this thread from time to time, hoping someone else might be willing to take up this cause.  I'm currently running Vista without issue, though, to be fair, it's just waaay too heavy of an OS for this poor computer.  Not being able to get Ubuntu running on this computer has always been nagging at the back of my mind.  Now that there's someone else with this computer, I'd be game for jumping back in the fray here and settling this once and for all!!  This unfinished business crap is driving me nuts!  If you're still there ehisey, what say we tackle this together?

---

### Post by Ziris on 2011-01-13
Believe it or not, I've been keeping an eye on this thread from time to time, hoping someone else might be willing to take up this cause.  I'm currently running Vista without issue, though, to be fair, it's just waaay too heavy of an OS for this poor computer.  Not being able to get Ubuntu running on this computer has always been nagging at the back of my mind.  Now that there's someone else with this computer, I'd be game for jumping back in the fray here and settling this once and for all!!  This unfinished business crap is driving me nuts!  If you're still there ehisey, what say we tackle this together?

---

### Post by Ziris on 2011-02-16
Well!  In either case I've restarted this project, again installing from scratch on 10.10 x86.  No wubi install or anything, Ubuntu is the only existing OS.  I've been doing quite a bit of research on the topic here, and for a while I was chasing down the prospect that the bug listed here ([https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/522318](https://bugs.launchpad.net/ubuntu/+source/xf86-input-wacom/+bug/522318)) was the cause of all my grief.  However, I soon read that this fix was actually included in the xf86-input-wacom drivers install thing, so it actually made no sense to continue down that path.  However, when I installed 10.10 initially, I was already receiving different results than before.  Namely, it was being more specific about what was going wrong.  Here's my Xorg.0.log file:
```
[    18.030] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS0)
[    18.030] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    18.030] (II) LoadModule: "wacom"
[    18.030] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    18.030] (II) Module wacom: vendor="X.Org Foundation"
[    18.031] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    18.031] (II) Serial Wacom Tablet: other types will be automatically added.
[    18.031] (**) Serial Wacom Tablet stylus: always reports core events
[    18.031] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    18.031] (WW) Serial Wacom Tablet stylus: Query failed with 19200 baud. Trying 38400.
[    18.031] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    18.031] (II) Serial Wacom Tablet stylus: serial tablet id 0x90.
[    18.031] (II) UnloadModule: "wacom"
[    18.031] (EE) PreInit returned NULL for "Serial Wacom Tablet"
```It now not only appears to be recognizing it, but at least putting a good effort into initializing the device.  As evidenced in the code above, it seems that it can't quite get the baud rate right.  All attempts at installing the latest and greatest xf86-input-wacom drivers, while successful, did nothing to quell this problem.  So it seems to me the next logical step would be to find a way to manually set the baud rate to the appropriate figure (probably via trial and error), and that seems to mean going back to setserial. 

I also found a fun new way of using udevadm, and that is to test the ttyS0 device, showing all rules applying to it and what happens with it.  Doesn't appear to give much useful info (at least to me).  In any case, here's what I get when running "udevadm test /class/tty/ttyS0":
```
run_command: calling: test
udevadm_test: version 163
This program is for debugging only, it does not run any program,
specified by a RUN key. It may show incorrect results, because
some values may be different, or not available at a simulation run.

parse_file: reading '/lib/udev/rules.d/40-fuse-utils.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-gnupg.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-hplip.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ia64.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libgphoto2-2.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-libsane.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-ppc.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-usb-media-players.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-usb_modeswitch.rules' as rules file
parse_file: reading '/lib/udev/rules.d/40-xserver-xorg-video-intel.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-fuse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/45-libmtp8.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-firmware.rules' as rules file
parse_file: reading '/lib/udev/rules.d/50-udev-default.rules' as rules file
parse_file: reading '/lib/udev/rules.d/55-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/56-hpmud_support.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-cdrom_id.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-floppy.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-input.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-serial.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-dm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage-tape.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-storage.rules' as rules file
parse_file: reading '/lib/udev/rules.d/60-persistent-v4l.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-gnome-bluetooth-rfkill.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-mobile-action.rules' as rules file
parse_file: reading '/lib/udev/rules.d/61-persistent-storage-edd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/64-xorg-xkb.rules' as rules file
parse_file: reading '/lib/udev/rules.d/65-xorg-wacom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/66-xorg-synaptics.rules' as rules file
parse_file: reading '/lib/udev/rules.d/69-xorg-vmmouse.rules' as rules file
parse_file: reading '/lib/udev/rules.d/69-xserver-xorg-input-wacom.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-acl.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-hid2hci.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-cd.rules' as rules file
parse_file: reading '/etc/udev/rules.d/70-persistent-net.rules' as rules file
parse_file: reading '/lib/udev/rules.d/70-printers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-cd-aliases-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-net-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-persistent-net-generator.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-probe_mtd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/75-tty-description.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-ericsson-mbm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-longcheer-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-pcmcia-device-blacklist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-platform-serial-whitelist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-simtech-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-usb-device-blacklist.rules' as rules file
parse_file: reading '/lib/udev/rules.d/77-mm-zte-port-types.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-graphics-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/78-sound-card.rules' as rules file
parse_file: reading '/lib/udev/rules.d/79-fstab_import.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-alsa.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-drivers.rules' as rules file
parse_file: reading '/lib/udev/rules.d/80-udisks.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-brltty.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-console-setup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hdparm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-hplj10xx.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-pcmcia.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-regulatory.rules' as rules file
parse_file: reading '/lib/udev/rules.d/85-usbmuxd.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-libgpod.rules' as rules file
parse_file: reading '/lib/udev/rules.d/90-pulseaudio.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keyboard-force-release.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-keymap.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-udev-late.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-dell.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-fujitsu.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-gateway.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-ibm.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-lenovo.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-battery-recall-toshiba.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-csr.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-hid.rules' as rules file
parse_file: reading '/lib/udev/rules.d/95-upower-wup.rules' as rules file
parse_file: reading '/lib/udev/rules.d/97-bluetooth.rules' as rules file
parse_file: reading '/dev/.udev/rules.d/root.rules' as rules file
udev_rules_new: rules use 233652 bytes tokens (19471 * 12 bytes), 37549 bytes buffer
udev_rules_new: temporary index used 63140 bytes (3157 * 20 bytes)
udev_device_new_from_syspath: device 0x218410a0 has devpath '/devices/pnp0/00:06/tty/ttyS0'
udev_device_new_from_syspath: device 0x218592f0 has devpath '/devices/pnp0/00:06/tty/ttyS0'
udev_device_read_db: device 0x218592f0 filled with db file data
udev_rules_apply_to_event: LINK 'char/4:64' /lib/udev/rules.d/50-udev-default.rules:4
udev_rules_apply_to_event: GROUP 20 /lib/udev/rules.d/50-udev-default.rules:14
udev_device_new_from_syspath: device 0x21859858 has devpath '/devices/pnp0/00:06'
udev_device_new_from_syspath: device 0x21859b08 has devpath '/devices/pnp0'
udev_event_execute_rules: no node name set, will use kernel supplied name 'ttyS0'
udev_device_update_db: created db file for '/devices/pnp0/00:06/tty/ttyS0' in '/dev/.udev/db/tty:ttyS0'
udev_node_add: creating device node '/dev/ttyS0', devnum=4:64, mode=0660, uid=0, gid=20
udev_node_mknod: preserve file '/dev/ttyS0', because it has correct dev_t
udev_node_mknod: preserve permissions /dev/ttyS0, 020660, uid=0, gid=20
node_symlink: preserve already existing symlink '/dev/char/4:64' to '../ttyS0'
udevadm_test: UDEV_LOG=6
udevadm_test: DEVPATH=/devices/pnp0/00:06/tty/ttyS0
udevadm_test: MAJOR=4
udevadm_test: MINOR=64
udevadm_test: DEVNAME=/dev/ttyS0
udevadm_test: ACTION=add
udevadm_test: SUBSYSTEM=tty
udevadm_test: DEVLINKS=/dev/char/4:64
udevadm_test: ID_INPUT=1
udevadm_test: ID_INPUT_TABLET=1
udevadm_test: x11_driver=wacom

```And that's where I'm at right now.  I'll explore my options concerning this and report back if anything becomes of anything.

---

### Post by Favux on 2011-02-17
Hi Ziris,

The issue appears to be whether your Viewsonic is actually an ISDV4 protocol serial device and not a serial wacom tablet.

If you look at wcmISDV4.c in the /xf86-input-wacom/src/ directory you'll see it says an ISDV4 must be 19200 or 38400.  So they are under the impression those are the only two valid baud rates for an ISDV4 device (serial tablet pc).  As far as I know all serial tablet pc's are ISDV4.  But maybe Viewsonic is the exception?

So when did they start and stop manufacturing the Viewsonic?  We can check to see when the ISDV4 protocol came out.  If it is but uses a different baud rate we should be able to fix it in the code and they should be notified there are three, not two, cases.

If it is a serial digitizer there is a patch set to get it working 10.04 and with another patch for 10.10's X server, Maverick too.  It's definitely a little tricky both to compile and to get to work even when installed correctly, so it's worth while to try and find out what the baud rate of a Viewsonic is.  It must be out there somewhere.

---

### Post by Ziris on 2011-02-18
Hey favux, nice to hear from you again.  I would be game for simply experimenting with baud rates to see if we can hit on the right one.  Viewsonic started manufacturing this thing sometime in '04, and it didn't last too long, so I wouldn't say it was in production any later than the end of '05.  Finding info on it is hard, especially since it's quite difficult to find support for it on viewsonic's own website.  I could go ahead and email support to see if they could give me some tech specs, but I somehow get the feeling I'd be better off asking my questions to a brick wall.  Worth a shot though I suppose.

I explored that wcmISDV4.c file you mentioned, and even toyed around with changing the baud rates in there and compiling it.  Didn't seem to do anything though, as my Xorg.0.log was still referencing the standard baud rates, so I must still be missing something.  In either case I'd be game for either toying with baud rates some more or trying that patch you mentioned.

---

### Post by segfaultex on 2011-08-17
Have you made any progress on this? 
I also have a V1250s and would love to get this functionality working.

---

### Post by Favux on 2011-08-17
Hi segfaultex,

Welcome to Ubuntu forums!

What do you see when you run?
```
sudo dmesg | grep ttyS
```

---

### Post by segfaultex on 2011-08-26
> **Favux said:**
> Hi segfaultex,

Welcome to Ubuntu forums!

What do you see when you run?
```
sudo dmesg | grep ttyS
```


I don't see anything i'm running natty currently.

---

### Post by Favux on 2011-08-26
What I'm wondering is if the ViewSonic is on another ttyS.  I'm not sure we established for sure which one it is on.

There should just be four ttyS's to test (ttyS0 to ttyS3), but for some reason Natty now has 32?  I don't understand what's going on and can't find any documentation.  They just decided the old default of 4 ports was too limiting and expanded it?  You can check by entering in a terminal:
```
ls /dev/ttyS*
```
What would be good to know is what serial port the digitizer is on.  Since dmesg didn't tell us we can try xxd.  Enter in a terminal:
```
xxd /dev/ttyS0
```
xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to use in xorg.conf.

I seem to dimly remember several serial tablet PCs were on ttyS4.  In releases prior to Natty you would have to add a kernel boot line to add the additional port.  I think one might have even been on ttyS5 or 6.  The IRQ and ttyS are set by jumpers on the hardware, or at least were in the old days.

I suppose another way to find out would be to query udev with a little attributes walk, e.g.:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
and see if a digitizer identifier such as WACf* or something shows up.

---

