---
title: "Wacom digitizer not working on ThinkPad X200 Tablet - lubuntu 11.04"
date: 2011-08-25
forum: Hardware
---

### Post by enough98 on 2011-08-25
Hello all,

Recently I bought this tablet and put lubuntu on. Unfortunately I have some problems with Wacom device.

I would be really happy if someone could point me on the right track, because currently I don't even know where to start fixing the problem.

Here are some outputs which might be helpful.

cat /var/log/Xorg.0.log :

```

[    12.103] 
X.Org X Server 1.10.1
Release Date: 2011-04-15
[    12.103] X Protocol Version 11, Revision 0
[    12.103] Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
[    12.103] Current Operating System: Linux tpx200t 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64
...
[    13.261] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    13.261] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    13.261] (II) LoadModule: "wacom"
[    13.261] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.261] (II) Module wacom: vendor="X.Org Foundation"
[    13.261]    compiled for 1.10.0, module version = 0.10.11
[    13.261]    Module class: X.Org XInput Driver
[    13.261]    ABI class: X.Org XInput driver, version 12.3
[    13.261] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    13.261] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.261] (**) Serial Wacom Tablet: always reports core events
[    13.261] (**) Option "Device" "/dev/ttyS4"
[    13.262] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    13.262] (II) Serial Wacom Tablet: other types will be automatically added.
[    13.262] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    13.262] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[    13.262] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    13.262] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    13.262] (II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
[    13.262] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    13.262] (II) UnloadModule: "wacom"
[    13.262] (II) Unloading wacom
...

```

dmesg | grep ttyS4 :

```

[    1.103184] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
[   12.092284] ttyS4: LSR safety check engaged!
[   12.092865] ttyS4: LSR safety check engaged!
[   13.262023] ttyS4: LSR safety check engaged!

```

As far as I understand this the problem is that the device gets it's IO/IRQ addresses but later on, when the driver wants to communicate with it, it's no longer there. Is that so? If yes, why is this happening?

What else can I check? What would be the first steps for fixing this?

Thank you.

---

### Post by Favux on 2011-08-25
Hi enough98,

Welcome to Ubuntu forums!

I believe the serial port you want is ttyS0.  I don't know why the driver is trying to use ttyS4.

Are you configuring it for ttyS4 somewhere?  Say in the 50-wacom.conf at xorg.conf.d or xorg.conf?

---

### Post by enough98 on 2011-08-26
I don't think I'm referring to ttyS4 in 50-wacom.conf :

```
Section "InputClass"
	Identifier "Wacom class"
# WALTOP needs a patched kernel driver, that isn't in mainline lk yet,
# so for now just let it fall through and be picked up by evdev instead.
#	MatchProduct "Wacom|WALTOP|WACOM"
	MatchProduct "Wacom|WACOM|"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
        #Option "Button2" "2"
        #Option "Button3" "3"
        Option "KeepShape" "on"
EndSection

Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection


# N-Trig Duosense Electromagnetic Digitizer
Section "InputClass"
	Identifier "Wacom N-Trig class"
	MatchProduct "HID 1b96:0001|N-Trig Pen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
	Option "Button2" "3"
EndSection


```

Looking at dmesg it seems nothing is on ttyS0 :

```
dmesg | grep ttyS
[    1.103184] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
[    1.123620] 0000:00:03.3: ttyS5 at I/O 0x1830 (irq = 17) is a 16550A
[   12.092284] ttyS4: LSR safety check engaged!
[   12.092865] ttyS4: LSR safety check engaged!
[   13.262023] ttyS4: LSR safety check engaged!

```

---

### Post by Favux on 2011-08-26
I believe the error is telling us that there is nothing on the ttyS4 port for the driver to read.  We need to find the port it is on.

There should just be four ttyS's to test (ttyS0 to ttyS3), but for some reason Natty now has 32?  The ttyS4 port used to not be available unless you added a kernel boot line switch to create it.  I don't understand what's going on and can't find any documentation.  They just decided to add more?  You can check by entering in a terminal:
```
ls /dev/ttyS*
```
The dmesg should have told us what/which ttyS port is active.  Since it didn't tell us we can try xxd.  Enter in a terminal:
```
xxd /dev/ttyS0
```
xxd (hidrawX hexdump) will exit for devices not listed, otherwise CTRL and C to quit.  Run through each device listed by "ls /dev/ttyS*" eg. ttyS0, ttyS1, etc.  Bring the pen to the screen and move it around.  You know you have the right ttyS* when you see a reaction with an output of characters.  That's the ttyS* you want to use in xorg.conf.

I suppose another way to find out would be to query udev with a little attributes walk, e.g.:
```
udevadm info -a -p $(udevadm info -q path -n /dev/ttyS0)
```
and see if a digitizer identifier WACf* shows up on one of them.  The PnP identifier should begin with that as you can see from the serial tablet PC snippets:
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
        Option "ForceDevice" "ISDV4"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
EndSection

```
Does *xinput list* show the tablet?

Can we just add the option to whichever serial tablet snippet is matching your X200t's digitizer?
```
Option "Device" "/dev/ttyS0"
```

Edit:  Oh, I just realized one of your snippets has the deprecated ISDV4 line.  You should be able to comment (#) that out.  It isn't used anymore.
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
#        Option "ForceDevice" "ISDV4"
EndSection
```

---

### Post by Favux on 2011-08-28
Hmmm.  Now that's interesting.

Just had a X61t also in Natty (2.6.38 ) that is apparently on ttyS4 too.  You can verify you are on X server 1.10 with:
```
Xorg -version
```
I double checked and xorg.conf's and lshal's for both the X61t and the X200t on previous releases had them both on ttyS0 like I thought.  I even have a X200t udevadmin info file that shows ttyS0.  So the changes to the serial stack in Natty apparently "redirect" from ttyS0 to ttyS4?  If so it is for reasons I don't understand.

So it looks like we can assume xf86-input-wacom is correct with ttyS4 and what we need to figure out is why it isn't handling it correctly.  Obviously it would be good if first we can confirm ttyS4 is the actual serial port the digitizer is on.

---

### Post by enough98 on 2011-08-29
Looks like Wacom actually is on ttyS4.

udevadm info -a -p $(udevadm info -q path -n /dev/ttyS4):
```


  looking at device '/devices/pnp0/00:0a/tty/ttyS4':
    KERNEL=="ttyS4"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pnp0/00:0a':
    KERNELS=="00:0a"
    SUBSYSTEMS=="pnp"
    DRIVERS=="serial"
    ATTRS{id}=="WACf00c"

  looking at parent device '/devices/pnp0':
    KERNELS=="pnp0"
    SUBSYSTEMS==""
    DRIVERS==""

```

xinput list doesn't show the tablet:
```

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                   	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; UVC Camera (17ef:480c)                  	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=12	[slave  keyboard (3)]

```

Xorg -version shows:
```
Xorg -version

X.Org X Server 1.10.1
Release Date: 2011-04-15
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux tpx200t 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-11-generic root=UUID=d776240f-7122-4113-9874-612773366823 ro quiet splash vt.handoff=7
Build Date: 11 August 2011  03:43:05PM
xorg-server 2:1.10.1-1ubuntu1.2 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.20.2
	Before reporting problems, check http://wiki.x.org

```

---

### Post by Favux on 2011-08-29
What happens if we tell it what the baud rate should be?  I'm not sure which snippet is working so both?
```
Section "InputClass"
	Identifier "Wacom serial class"
	MatchProduct "Serial Wacom Tablet"
	Driver "wacom"
        Option "BaudRate" "38400"
EndSection

Section "InputClass"
        Identifier "Wacom serial class identifiers"
        MatchProduct "WACf|FUJ02e5|FUJ02e7"
        Driver "wacom"
        Option "BaudRate" "38400"
EndSection
```

---

### Post by enough98 on 2011-08-30
No difference. This is corresponding Xorg.0.log output:

```
[    14.141] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    14.141] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    14.141] (II) LoadModule: "wacom"
[    14.141] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    14.141] (II) Module wacom: vendor="X.Org Foundation"
[    14.141] 	compiled for 1.10.0, module version = 0.10.11
[    14.141] 	Module class: X.Org XInput Driver
[    14.142] 	ABI class: X.Org XInput driver, version 12.3
[    14.142] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    14.142] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    14.142] (**) Serial Wacom Tablet: always reports core events
[    14.142] (**) Option "Device" "/dev/ttyS4"
[    14.142] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    14.142] (II) Serial Wacom Tablet: other types will be automatically added.
[    14.142] (**) Option "BaudRate" "38400"
[    14.142] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    14.142] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[    14.142] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    14.142] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    14.142] (II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
[    14.142] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    14.142] (II) UnloadModule: "wacom"
[    14.142] (II) Unloading wacom

```

Maybe this could be helpful:

```

dmesg | grep 00:0a
[    0.854034] pnp 00:0a: Plug and Play ACPI device, IDs WACf00c (disabled)
[    1.072141] serial 00:0a: [io  0x0200-0x0207]
[    1.072213] serial 00:0a: [irq 5]
[    1.072484] serial 00:0a: activated
[    1.093189] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A

```

---

### Post by enough98 on 2011-09-05
Sorry for bumping this one but I would really like to fix this.

---

### Post by Favux on 2011-09-05
We've established that the Wacom digitizer is on ttyS4 and udev is able to get information from it because we see the correct PnP identifier "WACf00c".

First thought is there was a problem with the xf86-input-wacom driver installation for whatever reason.  Find the xserver-xorg-input-wacom package in Synaptic Package Manager and tell it to reinstall it.  Then reboot.  Maybe a few times.

If that doesn't work let's next try updating the driver.  There have been several code changes/bug fixes for ISDV4 serial tablets since 0.10.11 came out.  See if that makes a difference.  To clone the xf86-input-wacom git repository follow the instructions at the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") part II. c or the [linuxwacom HOW TO]("http://ubuntuforums.org/showthread.php?t=1038949").

Have you established the hardware works, i.e. does it work with another OS like Windows?

Since it seems like the problem is with the driver and not the serial port or an IRQ conflict checking the BIOS probably won't help.  But just in case, especially if you made some recent change, you might want to look at the relevant settings.  For example is Plug n' Play disabled?  Is IRQ conflict resolution set?  And so on.  The:
```
dmesg | grep 00:0a
[    0.854034] pnp 00:0a: Plug and Play ACPI device, IDs WACf00c (disabled)

```
and
```
dmesg | grep ttyS
[    1.103184] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
.....
[   12.092284] ttyS4: LSR safety check engaged!

```
has me wondering a little.  I guess the disabled could just be coming from the X driver failure.

---

### Post by enough98 on 2011-09-05
Unfortunately it's still not working.

I have done as you requested (firstly reinstalling via Synaptic Package Manager and rebooting (a few times) and after that updating the driver via git).

```
...
[    13.341] (II) config/udev: Adding input device Serial Wacom Tablet (/dev/ttyS4)
[    13.341] (**) Serial Wacom Tablet: Applying InputClass "Wacom serial class"
[    13.341] (II) LoadModule: "wacom"
[    13.342] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.342] (II) Module wacom: vendor="X.Org Foundation"
[    13.342] 	compiled for 1.10.1, module version = 0.11.99
[    13.342] 	Module class: X.Org XInput Driver
[    13.342] 	ABI class: X.Org XInput driver, version 12.3
[    13.342] (II) Using input driver 'wacom' for 'Serial Wacom Tablet'
[    13.342] (II) Loading /usr/lib/xorg/modules/input/wacom_drv.so
[    13.342] (**) Serial Wacom Tablet: always reports core events
[    13.342] (**) Option "Device" "/dev/ttyS4"
[    13.342] (II) Serial Wacom Tablet: type not specified, assuming 'stylus'.
[    13.342] (II) Serial Wacom Tablet: other types will be automatically added.
[    13.342] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    13.342] (WW) Serial Wacom Tablet stylus: Query failed with 38400 baud. Trying 19200.
[    13.342] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    13.342] (EE) Serial Wacom Tablet stylus: wcmWriteWait error : Input/output error
[    13.342] (II) Serial Wacom Tablet stylus: serial tablet id 0xE3.
[    13.342] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"
[    13.342] (II) UnloadModule: "wacom"
[    13.342] (II) Unloading wacom
...

```

BIOS looks OK and other PnP devices are active:

```
...
[    0.860544] pnp 00:04: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.860554] pnp 00:05: [io  0x0061]
[    0.860587] pnp 00:05: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.860597] pnp 00:06: [io  0x00f0]
[    0.860609] pnp 00:06: [irq 13]
[    0.860649] pnp 00:06: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.860659] pnp 00:07: [io  0x0070-0x0071]
[    0.860665] pnp 00:07: [irq 8]
[    0.860699] pnp 00:07: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.860710] pnp 00:08: [io  0x0060]
[    0.860712] pnp 00:08: [io  0x0064]
[    0.860718] pnp 00:08: [irq 1]
[    0.860758] pnp 00:08: Plug and Play ACPI device, IDs LEN0010 PNP0303 (active)
[    0.860772] pnp 00:09: [irq 12]
[    0.860809] pnp 00:09: Plug and Play ACPI device, IDs IBM3780 PNP0f13 (active)
[    0.860912] pnp 00:0a: Plug and Play ACPI device, IDs WACf00c (disabled)
[    0.881300] pnp 00:0b: [mem 0xfed40000-0xfed44fff]
[    0.881358] pnp 00:0b: Plug and Play ACPI device, IDs PNP0c31 (active)
[    0.881887] pnp: PnP ACPI: found 12 devices
...

```

Previously I had ubuntu 11.04 and Wacom worked out of the box which is not the case with lubuntu.

---

### Post by Favux on 2011-09-05
```
[    13.342] (EE) PreInit returned 8 for "Serial Wacom Tablet stylus"

```
Tells us the device isn't being added which we already knew.
> Previously I had ubuntu 11.04 and Wacom worked out of the box which is not the case with lubuntu. 
I agree, it seems unlikely the hardware failed in the meantime.

So all I can come up with is the lubuntu has a bug.  At least in that it hasn't totally accommodated the serial stack change in Natty.  I'm guessing it just doesn't know how to handle a serial port above ttyS3.  Somehow it isn't able to allocate resources.  Needs a kernel change?

I guess the other option is that there is a problem with the line discipline.  We could try going down the rabbit hole of adding setserial and trying to set up ttyS4 through that.  Is setserial installed on your system?

---

### Post by enough98 on 2011-09-06
Thank you for helping me.

setserial is on my system. Here's some output it might be helpfu:

```

sudo setserial -g /dev/ttyS4
/dev/ttyS4, UART: 16550A, Port: 0x1808, IRQ: 17

sudo setserial -g /dev/ttyS5
/dev/ttyS5, UART: 16550A, Port: 0x1830, IRQ: 17

setserial -g /dev/ttyS5
/dev/ttyS5, UART: 16550A, Port: 0x1830, IRQ: 17

setserial -g /dev/ttyS4
/dev/ttyS4: No such device

```

Notice that ttyS4 and ttyS5 both share the same IRQ and the difference if sudo is used or not.

---

### Post by enough98 on 2011-09-06
Right after the booting the parameters of ttyS4 were different:

```
dmesg | grep ttyS4
[    1.123194] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
[   12.170652] ttyS4: LSR safety check engaged!
[   12.171509] ttyS4: LSR safety check engaged!
[   13.342362] ttyS4: LSR safety check engaged!
[ 6043.971595] ttyS4: LSR safety check engaged!
[ 6079.732071] ttyS4: LSR safety check engaged!
[ 6108.451762] ttyS4: LSR safety check engaged!
[ 6158.131631] ttyS4: LSR safety check engaged!
[ 7541.122531] ttyS4: LSR safety check engaged!
[ 7575.872690] ttyS4: LSR safety check engaged!
[ 7604.602609] ttyS4: LSR safety check engaged!
[ 7608.862758] ttyS4: LSR safety check engaged!
[ 7668.862800] ttyS4: LSR safety check engaged!
[ 7723.162613] ttyS4: LSR safety check engaged!
[ 7724.542741] ttyS4: LSR safety check engaged!
[ 7725.812540] ttyS4: LSR safety check engaged!
[ 7735.798115] ttyS4: LSR safety check engaged!
[ 7738.911504] ttyS4: LSR safety check engaged!
[ 7756.462642] ttyS4: LSR safety check engaged!
[ 8450.951837] ttyS4: LSR safety check engaged!
[ 8450.951894] ttyS4: LSR safety check engaged!
[ 8450.951925] ttyS4: LSR safety check engaged!
[ 8450.951940] ttyS4: LSR safety check engaged!
[ 8455.242808] ttyS4: LSR safety check engaged!
[ 8460.271660] ttyS4: LSR safety check engaged!
[ 8498.751730] ttyS4: LSR safety check engaged!
[ 8586.151852] ttyS4: LSR safety check engaged!
[ 8586.151882] ttyS4: LSR safety check engaged!
[ 8586.151898] ttyS4: LSR safety check engaged!

 dmesg | grep 00:0a
[    0.860912] pnp 00:0a: Plug and Play ACPI device, IDs WACf00c (disabled)
[    1.102148] serial 00:0a: [io  0x0200-0x0207]
[    1.102221] serial 00:0a: [irq 5]
[    1.102488] serial 00:0a: activated
[    1.123194] 00:0a: ttyS4 at I/O 0x200 (irq = 5) is a 16550A
[ 1558.370245] serial 00:0a: disabled
[ 1560.751875] serial 00:0a: activated
[ 4608.270243] serial 00:0a: disabled
[ 4610.720590] serial 00:0a: activated

```

---

### Post by Favux on 2011-09-06
So we see the weird disabled and activated thing in dmesg.  And two different versions of ttyS4; the dmesg one and the setserial one.  Wonder if that isn't the problem right there?

So why not try adding to  "/etc/serial.conf":
```
/dev/ttyS4 port 0x200 irq 5 baud_base 34800
```
and see if that straightens things out.  Or you could try the other way if that doesn't work:
```
/dev/ttyS4 port 0x1808 irq 17 baud_base 34800
```

Actually what is strange is you are able to pull the port and irq through dmesg without using sudo.  Some folks can but most need:
```
sudo dmesg | grep ttyS4
```
It's never been clear why a serial port would seem to have different permissions like that.  In your case how does it go from "no such device" to a conflicting device?  If the device is there shouldn't it complain about permissions?

---

### Post by enough98 on 2011-09-06
> **Favux said:**
> 
It's never been clear why a serial port would seem to have different permissions like that.  In your case how does it go from "no such device" to a conflicting device?  If the device is there shouldn't it complain about permissions?

Indeed that's strange.

However, making serial.conf with
```
/dev/ttyS4 port 0x200 irq 5 baud_base 34800
```
fixed the whole thing!

Thank you! 

Now it's time to fix the auto rotation. I hope this one will be more straight forward.

Tnx again.

---

### Post by Favux on 2011-09-06
Outstanding!  Good job, and nice work hanging in there.  :)

See Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)

---

