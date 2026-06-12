---
title: "Old Wacom serial tablet is not recognized in karmic"
date: 2009-12-17
forum: Hardware
---

### Post by Barbidoux on 2009-12-17
This discuss follow domething begun in thread 176

Resume :

> I use a Wacom UD1212 (yeah, a good old serial model).

It take to me 2 or 3 Ubuntu version to understand how to add it in xorg.conf (and I was ashamed when I saw how simple it was when you know). So it worked fine until Jaunty (meaning it didn't work anymore after Jaunty's installation).

I tried to modify Jaunty's xorg.conf, but the best I had was a pen with 2 seconds delay in the same time that I losed the nvidia graphic card. So an unusable tablett with an unusable sreen was too much for me.

3 days ago, I just upgrade to Karmic with the secret hope that the plug&play would do it. Well, nice try, but **** ! That doesn't work.

I red almost all this thread and tried different things, but it is difficult to select what is for Jaunty or Karmic (alpha, beta or final release), USB or serial. I understand that Karmic doesn't use xorg.conf anymore. I tried this way and it just slow down Gnome without any move from stylus or pointer.

Everything containing "Wacom" is installed and the wacom driver seems to be "ubuntu 1.0.8.4.1" (I understand that it is the 8.4.1 version, so seems good to me).

xinput -list know nothing about "wacom" unless it is called "Virtual core pointer"
lsmod show that the wacom driver is loaded
xsetwacom list give nothing

I don't know where to begin.

Hello Favux, are you there

I joined the files you asked in thread 176
Seems that I have now something in lshal

I hope (and I think so) that there is no link with the modifications you give me and tha fact that I had to fsck this PC since 2 hours. It was very long to make it work again !

---

### Post by Favux on 2009-12-17
re:  Wacom ArtZII (UD1212-R) serial tablet; pnp identifier = PNP0501 ?

Continued from the "Re: Wacom tablets in Ubuntu guide/howto" thread:  [http://ubuntuforums.org/showthread.php?t=967147&page=42](http://ubuntuforums.org/showthread.php?t=967147&page=42)

Hi Barbidoux,

> I hope (and I think so) that there is no link with the modifications you give me and tha fact that I had to fsck this PC since 2 hours. It was very long to make it work again !

I hope not either!!!  That concerns me.  But it does look like I guessed right.  Your lshal went from:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
```
to:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'cursor', 'pad'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'pad'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'pad'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
```
Which looks correct!  So I hope the .fdi had nothing to do with your problem.  I don't think we would be seeing this if we were trying to configure the wrong device (I hope).  I would feel better if the first section looked more like this:
```
udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'PnP Device (FUJ02e5)'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_FUJ02e5'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:05'  (string)
  pnp.id = 'FUJ02e5'  (string)
  pnp.serial.irq = 4  (0x4)  (int)
  pnp.serial.port = '0x220'  (string)
```
But I'm guessing the differences are due to your tablet being made before newer plug and play specifications.

I would reboot a few times and rerun fsck and then Updgrade Manager before I did anything else.

I modified the .fdi again but left the name the same because you were the only one who had downloaded it.  So please install the new .fdi, be careful it has the same name.  It should get rid of the spurious pad we are seeing.  Then a new lshal with it.  And at this point we should also look at your Xorg.0.log.  That's in "/var/log".  It could potentially give us useful information.


We know your tablet is on ttyS0 from the last time you had it working and apparently from your lshal.

Since the eraser is being recognized I assume the stylus is too.  No reaction to stylus on the tablet?  (We'll worry about the mouse later.)

It could be we need a different baud rate or irq.  In a terminal try:
```
dmesg | grep ttyS
```
We are hoping for output that looks something like:
```
serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
So we have the right information to configure with.

---

### Post by Barbidoux on 2009-12-18
Hello

I just replace the .fdi and reboot.

Here is the result of dmesg :
> [    0.827378] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.827771] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A


I joined the 2 files you asked for.

---

### Post by Favux on 2009-12-18
Hi Barbidoux,

Sorry, my fault.  :(  I forgot to remind you to change the match line in the serial-tablet&tablet-pc_test2_10-wacom.fdi to:
```
      <match key="@info.parent:pnp.id" contains_outof="PNP0501;WACf;FUJ02e5;FUJ02e7">
```
So I need you to do that and then after a reboot please repeat and post the dmesg and lshal commands and a new copy of your Xorg.0.log.

---

### Post by Barbidoux on 2009-12-19
Good moring

Dmesg give me the same answer :
> [    0.827123] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.827518] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A

You'll find attached xorg.0.log, lshal and full dmesg

A little doubt at this time : the file to modify is

/usr/share/hal/fdi/policy/20thirdparty/10-linuxwacom.fdi

or another one called 

serial-tablet&tablet-pc_test2_10-wacom.fdi ?

Hope I didn't make a mistake !

---

### Post by Favux on 2009-12-19
Hi Barbidoux,

Oops!  I see the problem now.

You are suppose to rename serial-tablet&tablet-pc_test2_10-wacom.fdi to 10-linuxwacom.fdi.  Or at least copy the contents into  a blank 10-linuxwacom.fdi.  It's called 10-wacom.fdi in Jaunty and 10-linuxwacom.fdi in Karmic.

If you now have something called serial-tablet&tablet-pc_test2_10-wacom.fdi, or similar, in "/usr/share/hal/fdi/policy/20thirdparty/" you need to remove it.  The .fdi's have to start with a number.  There should only be one wacom.fdi.

Then again lshal and Xorg.0.log.  Do you understand my instructions now?

---

### Post by Barbidoux on 2009-12-19
No, there is no mistake :
As your file in post #176 open directly in Firefox on my PC, I just cut and pasted the content in the file I had in /usr/share/hal/fdi/policy/20thirdparty. This file's name is 10-linuxwacom.fdi. I had doubt when I saw the name of your file, but I think I made the right thing.

I join the ls of ls this directory so you can see what's in. To be sure, I removed the "10-linuxwacom.fdi~" after this ls.
I join the actual "10-linuxwacom.fdi" so you can see if it's correct after all these modificaiton.

---

### Post by Favux on 2009-12-19
Hi Barbidoux,

Ahhh!  You were right, it was the .fdi I needed to see.  You've added PNP0501 to the wrong line.  A natural mistake.  Remove it from the line it is on along with the extra semi-colon ( ; ) and place it on the first line:
```
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="WACf;FUJ02e5;FUJ02e7">
```
to:
```
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="serial">
      <match key="@info.parent:pnp.id" contains_outof="PNP0501;WACf;FUJ02e5;FUJ02e7">
```
And we should be good to go!

---

### Post by Barbidoux on 2009-12-19
Well, now I have an understanding problem : 

The .fdi I sent in my precedent post looks exactly like you ask me to modify it !!??

There's something I can't catch.

Here is this line I just cut and pasted from gedit (and it's the same as the one in the precedent post) :

<match key="@info.parent:pnp.id" contains_outof="PNP0501;WACf;FUJ02e5;FUJ02e7">

EDIT : hum well, without the smiley...

---

### Post by Favux on 2009-12-19
Hi Barbidoux,

The contents of this "Barbidoux_test1_10-linuxwacom.fdi.txt" are what we want in your 10-linuxwacom.fdi.  The forum won't let you upload a .fdi hence ".fdi.txt".  And the "Barbidoux_test1_" is a label so we can keep them straight.

---

### Post by Barbidoux on 2009-12-19
Well, I finally find my mistake.

I didn't see that there was 2 lines with same beginning.
I think I made a search with the editor at least one time. Was there allways 2 of these lines ?)

So here are the files after the last modifications

Just to know : for testing, I just move the pen and the puck and the mouse's pointer should move. Am I right ?

---

### Post by Favux on 2009-12-19
Hi Barbidoux,

Good, we are finally on the same page.
> Was there allways 2 of these lines ?
No, the serial-graphics-tablet_test1 .fdi only had one.
> for testing, I just move the pen and the puck and the mouse's pointer should move. Am I right ?
Yes, we can also try xxd if we need to.

The lshal now looks good:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'cursor'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
```
The dmesg shows:
```
[    0.472844] isapnp: Scanning for PnP cards...
[    0.501758] Switched to high resolution mode on CPU 1
[    0.504099] Switched to high resolution mode on CPU 0
[    0.825846] isapnp: No Plug & Play device found
[    0.827017] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.827115] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.827510] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
and
```
[   23.867893] usbcore: registered new interface driver wacom
[   23.867898] wacom: v1.51:USB Wacom Graphire and Wacom Intuos tablet driver
```
which I suppose is from the wacom.ko, which is the Wacom usb kernel driver/module.

Unfortunately Xorg.0.log shows a problem:
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) stylus: always reports core events
(**) stylus device is /dev/ttyS0
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom unable to read ISDV4 * data after 3 tries at (19200)
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device stylus cursor
(**) stylus cursor: always reports core events
(**) stylus cursor device is /dev/ttyS0
(**) stylus cursor is in relative mode
(**) stylus cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus cursor: serial speed 9600
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom unable to read ISDV4 * data after 3 tries at (19200)
(EE) Couldn't init device "stylus cursor"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
(II) config/hal: Adding input device eraser
(**) eraser: always reports core events
(**) eraser device is /dev/ttyS0
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom unable to read ISDV4 * data after 3 tries at (19200)
(EE) Couldn't init device "eraser"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
```
Maybe the relevant line is:
```
Wacom unable to read ISDV4 * data after 3 tries at (19200)
```
So it could be a baud rate problem or a problem with the ISDV4 protocol?  I wish we knew which protocol the ArtIIZ uses.

There are three main serial baud rates used according to the code in wacserial.c (in the linuxwacom 0.8.4-1 source code tar):  38400, 19200, and 9600.  Also 4800, 2400, and 1200 are mentioned for "testing" which may actually be what an older serial tablet like yours needs.  I guess we can just try them.  Let's start with 38400 since it is already in the .fdi.

I don't know if we should look at lshal and Xorg.0.log after each though.

---

### Post by Favux on 2009-12-19
Oh, and I see I should mention a code snippet from the wacserial.c I mentioned earlier:
```
	static SERIALSUBTYPE xDigitizerII[] =
	{
		WACOM_SUBTYPE("UD-0608-R", "Wacom DigitizerII 6x8",   1),
		WACOM_SUBTYPE("UD-1212-R", "Wacom DigitizerII 12x12", 2),
		WACOM_SUBTYPE("UD-1218-R", "Wacom DigitizerII 12x18", 3),
		WACOM_SUBTYPE("UD-1825-R", "Wacom DigitizerII 18x25", 4),
		{ NULL }
	};
```
As you can see your tablet seems to be in there.  So hopefully we just need to figure out how to complete setting it up.

---

### Post by Barbidoux on 2009-12-21
Hello

Some news : I think it's a "Windowsache" : you tell the driver what to do, and it does just what _he_ wants ! It always try at 19200 !!!

I don't know if it is right, but I think I had to configure the serial port at 9600 to make it work (but that's a lot of time and as I'm IT manager, it's hard to remember all serial ports I had to modify in the 12 or 14 last years). But I'm not even sure it was for Linux configuration...

---

### Post by Barbidoux on 2009-12-21
As I thought, I made the test replacing 38400 with 9600 in the .fdi file.

Well It always try at 19200...

Keep in mind that my Karmic is an update of Jaunty. I tried some things in Jaunty to make this tablet work. I don't remember modifying serial ports parameters, but perhaps some things I tried made it when I didn't watch (a script or something else).

Seems that we are not far...

---

### Post by Favux on 2009-12-21
Hi Barbidoux,

Did you accidently post the same thing on post #15 as #14?

Anyway there is code that seems to select the baud rate for the tablet which may be what we are running into.  But if it is suppose to be at 19200 why isn't the linuxwacom driver attaching in Xorg.0.log?

If you look in /usr/share/hal/fdi/policy/10osvendor/10-tabletPCs.fdi you'll see some other configuration options, like:
```
	<merge key="input.device.set" type="string">/dev/ttyS0</merge>
or
	<merge key="pnp.serial.baud_base" type="int">38400</merge>
or
    <!-- add addon if need special ttySx settings -->
    <match key="input.device.set" exists="true">
      <append key="info.callouts.add" type="strlist">hal-system-setserial</append>	
    </match>
```
So there are options.  And we can always fall back on xorg.conf.

It sounds like you are getting the hang of using the .fdi and already tried a different baud rate.  I was going to construct another match for your tablet to test baud rates etc. on.

Let me know what you want to do.

---

### Post by Barbidoux on 2009-12-21
Well, I tried with 9600 as you could see, but it doesn't care what I put in the .fdi file.

So, I don't know how to ask gently to the driver "Just try at 9600" if the number we put don't do it.

Any idea ?

---

### Post by Favux on 2009-12-21
We might as well try the rest, it won't take that long, including 19200!  Then we can rethink.  I agree with you, we are probably close.  It's probably something simple.

---

### Post by Barbidoux on 2009-12-21
I'm not sure to understand : what can we do if the modifications we make don't bother the system a little bit ?

We put 38400, it says "Cannot connect at 19200"
We put 9600, it says "Cannot connect at 19200"
We could put anything, if it doesn't care a little bit, it can take a long time before it works.

Is there another place for this kind of parameters ?

EDIT
I'm not sure I undestood everything in your post #16.
Should I add some of these config lines in my .fdi file ?
And if yes, where exactly ? I already made mistakes in modifying this file (wrong place), I would like to be sure what to do.

---

### Post by Favux on 2009-12-21
Hi Barbidoux,

No it did take 38400 as you can see:
```
 LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) stylus: always reports core events
(**) stylus device is /dev/ttyS0
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) /dev/ttyS0: Tablet PC buttons are on 
(**) Option "BaudRate" "38400"
(**) stylus: serial speed 38400
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
Wacom unable to read ISDV4 * data after 3 tries at (19200)
(EE) Couldn't init device "stylus"
(II) UnloadModule: "wacom"
(EE) config/hal: NewInputDeviceRequest failed (1)
```
I don't know if the 19200 on the error line is real or spurious.  The question I have is if we need to change one of the "Option" lines.  For example is:
```
Option "Parity" "None"
```
correct?  Or is:
```
Option "DataBits" "8"
```
right.  Can we alter them like?:
```
          <merge key="input.x11_options.DataBits" type="string">9</merge>
```
I've attached a .fdi with an ArtZII section you can experiment in.

That's what I mean we need to rethink.  It shouldn't be this hard.  So anyway you could try the other baud rates if you want.

---

### Post by Barbidoux on 2009-12-21
Here are the test results

Hope it help going forward.

What's bugging me is that I feel that there's only a little thing wrong, but the question is to know what it is.

---

### Post by Barbidoux on 2009-12-21
Well, as I am on holidays, I made several tests.

As I remember that old modem didn't like software flow control, I tried to configure the serial port as hardware flow control, but I didn't find the keyword to do that.

I join all the tests with the results.

Perhaps will you be more inspired than me !:confused:

Does it still try to detect an USB tablet that it can't find and then unload the wacom driver for this reason ?

---

### Post by Favux on 2009-12-21
Hi Barbidoux,

> What's bugging me is that I feel that there's only a little thing wrong, but the question is to know what it is. 
Exactly.  That's what is bothering me.
> As I remember that old modem didn't like software flow control
Good, that's the kind of thing we need to know about and look into.
```
Does it still try to detect an USB tablet that it can't find and then unload the wacom driver for this reason ? 
```
I've seen that error message before with serial tablets and have never quite figured out what it means.  I don't know if it is real or just a generic error message that makes it look like it has something to do with usb.

OK, I'll look at what you've got.

---

### Post by Favux on 2009-12-21
I was looking at a [new post]("http://sourceforge.net/mailarchive/forum.php?thread_name=200912200933.16931.san.vu-ngoc%40laposte.net&forum_name=linuxwacom-discuss") on linuxwacom-discuss where Daniel Neville is having trouble with his Wacom ArtZ II (UD-1212) in Hardy (8.04).  His wacdump messages make me wonder if even 9600 is too fast.

When the ArtZ came out (1994?) weren't modems transitioning from 2400 to 4800?  I don't know if that pertains to internal serial stuff but maybe we should investigate the lower baud rates like 4800?

---

### Post by Barbidoux on 2009-12-21
You mean just put 4800 or 2400 at the good place in the .fdi file ?

---

### Post by Favux on 2009-12-21
Right, try:
```
        <!-- ArtIIZ serial tablet operate at baud rate? -->
        <match key="@info.parent:pnp.id" contains_outof="PNP0501">
          <merge key="input.x11_options.BaudRate" type="string">4800</merge>
```
etc.

---

### Post by Barbidoux on 2009-12-21
Nice try but no !

Seems to me that it should work at 9600 or even more. We are talking about 90th, not 80th ! The IBM PC came in 1981. In 95 with Windows 95, the modem were 28'800 or 33'600.

---

### Post by Favux on 2009-12-21
Given the Xorg.0.log you are clearly right!  OK, I think we've exhausted baud rate so lets let it go back to using the default and try something else.

Looking at the LWP [HOWTO]("http://linuxwacom.sourceforge.net/index.php/howto/inputdev"), it says:
>                Option "ForceDevice" "ISDV4"
                   tells the  driver to  dialog  with the  tablet  the  serial
                   Tablet PC way.  It is a special  Wacom IV protocol,  called
                   ISDV4  protocol. This option is mandatory for serial Tablet 
                   PCs only.

Oviously not a lot of information.  But maybe we should try removing or commenting out the line:
```
	<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>
```
and see what happens.

---

### Post by Barbidoux on 2009-12-21
Well, you touch it. And now, I remember that I had to delete a line for tablet PC in the xorg.conf. I can't remember something called ISDV4, but I think it was that.

So now, I have something working better than the best I could do in Jaunty : the nvidia driver work fine and I have some move on the tablet, but the tablet seems to be slow slow.
It seems that the pointer is attached to the pen with a spring : funny at the beginning, but rapidly frustrating.

I tried to speed up the baud rate, but it is the same or even worth.

Any idea ?

---

### Post by Favux on 2009-12-21
Hi Barbidoux,

Outstanding!!!  We've got it working!  Sort of anyway.

OK, you forgot to remove the 4800 baudrate:
```
II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) stylus: always reports core events
(**) stylus device is /dev/ttyS0
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "4800"
(EE) stylus: Illegal speed value (must be 9600 or 19200 or 38400).(**) stylus: serial speed 4800
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom tablet model : UD-1212-R00 V1.2-0
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Serial UD tablet speed=9600 (38400) maxX=15240 maxY=15240 maxZ=255 resX=1270 resY=1270  tilt=disabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
(II) config/hal: Adding input device stylus cursor
(**) stylus cursor: always reports core events
(**) stylus cursor device is /dev/ttyS0
(**) stylus cursor is in relative mode
(**) WACOM: suppress value is 2
(**) stylus cursor: threshold = 15
(**) stylus cursor: max x set to 15240 by xorg.conf
(**) stylus cursor: max y set to 15240 by xorg.conf
(**) stylus cursor: max z = 255
(**) Option "BaudRate" "9600"
(**) stylus cursor: serial speed 9600
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)
(==) Wacom device "stylus cursor" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
(II) config/hal: Adding input device eraser
(**) eraser: always reports core events
(**) eraser device is /dev/ttyS0
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) eraser: threshold = 15
(**) eraser: max x set to 15240 by xorg.conf
(**) eraser: max y set to 15240 by xorg.conf
(**) eraser: max z = 255
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
```
But the rest shows the linuxwacom driver is attaching!

I added a part to exclude ISD4 for the ArtZ and commented out the baud rate but left it in so you can still play with it.  If commenting out 4800 doesn't do it we can look at:
```
Option "Suppress" "number"
```
and
```
Option "Speed" "Rspeed"
```

---

### Post by Barbidoux on 2009-12-21
I made these changes and put the results attached.

xsetwacom list give :

stylus           stylus    
eraser           eraser   

Seems strange to me : 2x stylus + 2x eraser

I have only 1 stylus, no eraser and a puck. Is it a clue ?

EDIT

I just saw that the puck work very funny : 
- I go to right one time, the pointer go to right
- After that I go to left one time, the pointer go to right
- At this time, for the third move, the pointer go to left even if I go to right and so on !

This mean that if I continue doing right left right left with the puck, the pointer do the inverse move. Very funny to see but a little bit less if you want to work with it !

And now, I will sleep a little bit and see if I have a good idea during the night.

Good night and thanks for your help

---

### Post by janjan7777 on 2009-12-21
Dear all, first thanks a lot for your work.
I tested the latest fdi, and the behaviour I see with the puck is not inverted, but it is a strong delay. As like there are always a number of events waiting in a delay line/queue and are released only when the queue is filled up from the other side...
Regards,
Jan

---

### Post by Favux on 2009-12-21
Hi janjan7777,

Welcome to Ubuntu forums!

Thanks for joining in!  Good to have confirmation the .fdi is working.
> I tested the latest fdi, and the behaviour I see with the puck is not inverted, but it is a strong delay. As like there are always a number of events waiting in a delay line/queue and are released only when the queue is filled up from the other side...
Interesting.  So it may indeed be Surpress or Rspeed if we are lucky.

But how is the stylus behaving?  That's what I'm kind of focused on.

I think the eraser was introduced later so you do not have an eraser on the back of your stylus either, correct?


Hi Barbidoux,

It's looking very good.  Dmesg shows:
```
[    0.827026] Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
[    0.827125] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.827519] 00:08: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
```
lshal:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'cursor'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'eraser'  (string)
```
And Xorg.0.log:
```
(II) config/hal: Adding input device stylus
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
	compiled for 1.6.4, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 4.0
(II) Wacom driver level: 47-0.8.4-1 $
(**) stylus: always reports core events
(**) stylus device is /dev/ttyS0
(**) stylus is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(**) Option "Device" "/dev/ttyS0"
(**) Option "StopBits" "1"
(**) Option "DataBits" "8"
(**) Option "Parity" "None"
(**) Option "Vmin" "1"
(**) Option "Vtime" "10"
(**) Option "FlowControl" "Xoff"
usbDetect: can not ioctl version
(==) Wacom tablet model : UD-1212-R00 V1.2-0
(==) Wacom using pressure threshold of 15 for button 1
(==) Wacom Serial UD tablet speed=9600 (38400) maxX=15240 maxY=15240 maxZ=255 resX=1270 resY=1270  tilt=disabled
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
(II) config/hal: Adding input device stylus cursor
(**) stylus cursor: always reports core events
(**) stylus cursor device is /dev/ttyS0
(**) stylus cursor is in relative mode
(**) WACOM: suppress value is 2
(**) stylus cursor: threshold = 15
(**) stylus cursor: max x set to 15240 by xorg.conf
(**) stylus cursor: max y set to 15240 by xorg.conf
(**) stylus cursor: max z = 255
(**) Option "BaudRate" "9600"
(**) stylus cursor: serial speed 9600
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)
(==) Wacom device "stylus cursor" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
(II) config/hal: Adding input device eraser
(**) eraser: always reports core events
(**) eraser device is /dev/ttyS0
(**) eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) eraser: threshold = 15
(**) eraser: max x set to 15240 by xorg.conf
(**) eraser: max y set to 15240 by xorg.conf
(**) eraser: max z = 255
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
```
So it appears the baud rate is 9600.  And it even identifies the tablet.
> Seems strange to me : 2x stylus + 2x eraser
Don't worry about that, that is normal.  Have you tried calibrating the stylus in wacomcpl?

I don't know why your cursor isn't showing up because janjan7777's is with the same .fdi.  Try rebooting and see if you see it.

Right now lshal is saying it doesn't exist:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
```
When a sub-device (subdev) ends in an extension like '_0', that is HAL's way of saying the sub-device doesn't exist.  So although it's in the Xorg.0.log it's (probably) spurious.  Try "xinput --list" and see if it is in there.  But notice HAL thinks you have an eraser.

Check the connections (if the Lens Cursor Wacom mouse is wired to the tablet?).  Can you test it in Windows or on another computer and make sure it isn't a hardware problem.

---

### Post by janjan7777 on 2009-12-21
No, I have an eraser. Tablet is a serial UD-1212-R with stylus and puck, the stylus including the eraser. My observations are the following:
Eraser: works perfectly
Stylus: Slow, but fast when tip is pressed down
Puck: Slow, but fast when button is pressed down

EDIT: I had the same behaviour in 8.04 (I guess), then things were working fine in 9.04, and the problems returned after today's update to 9.10...

---

### Post by Favux on 2009-12-21
Hi janjan7777,

So my research was right:
> It came out for the Mac(?) in 1994. The Wacom ArtZII (UD1212-R). Some of them were huge and I think it's the model they first introduced the eraser on.
Maybe there was an option for a stylus without it which is why Barbidoux doesn't have one?

Let's try Rspeed then.  I changed it to 1.1 from the default 1.0:
>                Option "Speed" "Rspeed"
                   sets the cursor's  relative  movement speed to Rspeed.  The
                   default value is 1.0.  A Rspeed greater than 1.0 will speed
                   up the cursor's  relative movement.  A Rspeed less than 1.0 
                   but greater  than 0 will slow  down the  cursor's  relative 
                   movement. A Rspeed too close to 0 is not recommanded.


If that isn't any good try varying it.  Or is it fine for you when the button is pressed down?

---

### Post by Barbidoux on 2009-12-22
Well, thanks to Janjan7777, I didn't notice that the stylus has a normal behavior when pressed down. The puck work better to with a button pressed, but the precision is worse thant the stylus.

So, we have exactly the same behavior. And I agree to say that it is probably a delay in sending the information so that it wait something before sending the last moves on the tablet. Is there a buffer or something that could wait to be full before sending ?

I'm not sure to understand what is the Rspeed : I never use a so big tablet to do relative movements. It should be fixed. Am I right ? 

I'll try and see wht the matter.

EDIT

I just tried with Rspeed at 1.1, 0.1 or 2 and it change nothing.

The puck behave very strange : some moves give something on the screen but when I just let it in upright corner and then in downleft, the pointer stay where it is. Seems that it work like a mouse . It should be fixed.

More funny : when trying the pen after the puck (just touch the tablet), the pointer do the last puck move. It always need an event to execute some instructions.

---

### Post by Favux on 2009-12-22
Hi Barbidoux,

Good, that sounds better than it did.  You have the Wacom mouse working now.  Before you get too far try wacomcpl if you haven't already.  See "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").

Do you mean absolute vs relative on the movement?  It was looking from the Xorg.0.log that while absolute is default for the stylus, relative is default for the cursor.

---

### Post by Favux on 2009-12-22
Hi Barbidoux,

See if wacomcpl lets you adjust the stylus and cursor "feel" more to your liking.  Also see if it allows you to change the cursor from relative to absolute mode:
>                Option "Mode" "Relative"|"Absolute"
                   sets the  mode of the device.  The default value for stylus
                   and  eraser is Absolute;  cursor is  Relative;  pad mode is
                   decided  according to its core  option due to its nature of
                   not moving system cursor:  Relative if it is a core device;
                   Absolute, otherwise.

If it doesn't we could use an xsetwacom command to add it to wacomcpl's .xinitrc or try to add it to the .fdi.

---

### Post by Barbidoux on 2009-12-22
> You have the Wacom mouse working now.Well, I wouldn't say that : the pointer move when moving the puck, but it is hard to catch a screen button since the link between the pointer and the puck seems to be made by a spring.

Moves are correct  only when a button is down or when the pen is "pushed".

In wacomcpl, I don't have the puck (only stylus and eraser) and there is nothing about relative or absolute.

And I red some posts (in french and not resolved)  describing the same chewy behavior with that kind of tablet

---

### Post by janjan7777 on 2009-12-22
Hi, I just want to confirm the results that *Barbidoux* got.
There is also a bug report at [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997), but I am also using 9.10/32bit and, different from them, still have the problems reported.

---

### Post by Favux on 2009-12-22
Hi janjan7777 and Barbidoux,

Lol!  I knew about the bug report.  I talked X-Kent into posting on that one and another one.

Could you please post your lshal?  Barbidoux says he doesn't have an eraser on his stylus but his lshal shows there is one but no Wacom mouse.  And he doesn't see the mouse on "xinput --list".  But his mouse kind of responds, so there must be some driver somewhere running it!  I can't think what, other than linuxwacom, it could be.

And to both of you.  Do any of the settings in wacomcpl help the stylus become more responsive?

Ping's awfully busy right now but maybe we could ask him for help?

---

### Post by janjan7777 on 2009-12-22
Here is my (trimmed) lshal:
```

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.callouts.add = {'hal-setup-wacom'} (string list)
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Rspeed = '1.1'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'cursor'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'eraser'  (string)

```

and my xinput --list:
```

"Virtual core pointer"  id=0    [XPointer]                                                          
        Num_buttons is 32                                                                           
        Num_axes is 2                                                                               
        Mode is Relative                                                                            
        Motion_buffer is 256                                                                        
        Axis 0 :                                                                                    
                Min_value is -1                                                                     
                Max_value is -1                                                                     
                Resolution is 0                                                                     
        Axis 1 :                                                                                    
                Min_value is -1                                                                     
                Max_value is -1                                                                     
                Resolution is 0                                                                     
"Virtual core keyboard" id=1    [XKeyboard]                                                         
        Num_keys is 248                                                                             
        Min_keycode is 8                                                                            
        Max_keycode is 255                                                                          
"Power Button"  id=4    [XExtensionKeyboard]                                                        
        Type is KEYBOARD                                                                            
        Num_keys is 248                                                                             
        Min_keycode is 8                                                                            
        Max_keycode is 255                                                                          
"AT Translated Set 2 keyboard"  id=5    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Video Bus"     id=6    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Sleep Button"  id=7    [XExtensionKeyboard]
        Type is KEYBOARD
        Num_keys is 248
        Min_keycode is 8
        Max_keycode is 255
"Macintosh mouse button emulation"      id=10   [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"DualPoint Stick"       id=2    [XExtensionPointer]
        Type is MOUSE
        Num_buttons is 5
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
        Axis 1 :
                Min_value is -1
                Max_value is -1
                Resolution is 1
"AlpsPS/2 ALPS DualPoint TouchPad"      id=3    [XExtensionPointer]
        Type is TOUCHPAD
        Num_buttons is 12
        Num_axes is 2
        Mode is Relative
        Motion_buffer is 256
        Axis 0 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1
        Axis 1 :
                Min_value is 0
                Max_value is 767
                Resolution is 1

```

xorg.conf is almost empty. I use the nvidia driver, version 185. Yesterday I played around with xsetwacom, but no changes noticed...

---

### Post by Favux on 2009-12-22
Thanks janjan7777,

OK, now we are getting somewhere.  Your lshal looks the same as Barbidoux's and seems to be saying there is no cursor.  Or actually is it saying there is no?:
```
info.product = 'stylus cursor'  (string)

```
What's a 'stylus cursor'?  Did you see that before with xorg.conf or other .fdi's?

The "xinput --list" shows nothing.  You should be seeing stylus and eraser.  The contains_not filter on the Wacom names "parser" will be taking out the cursor/stylus cursor because HAL is saying it isn't there.  Does "xsetwacom list" show stylus and eraser?  Do you see them in wacomcpl?

So we need to take a look at your Xorg.0.log in /var/log/.

---

### Post by janjan7777 on 2009-12-22
Dear Favux,

no, I didn't see that "stylus cursor" before, but I have no experience with fdis.

xsetwacom list gives me
```

stylus stylus
eraser eraser

```my Xorg.0.log:

```

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux bla 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686                                                                                                  
Kernel command line: root=UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx ro quiet splash                 
Build Date: 14 November 2009  05:48:26PM                                                            
xorg-server 2:1.6.4-2ubuntu4.1 (buildd@)                                                            
        Before reporting problems, check http://wiki.x.org                                          
        to make sure that you have the latest version.                                              
Markers: (--) probed, (**) from config file, (==) default setting,                                  
        (++) from command line, (!!) notice, (II) informational,                                    
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.                               
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Dec 22 22:29:14 2009                                
(==) Using config file: "/etc/X11/xorg.conf"                                                        
(==) No Layout section.  Using the first Screen section.                                            
(**) |-->Screen "Default Screen" (0)                                                                
(**) |   |-->Monitor "<default monitor>"                                                            
(==) No device specified for screen "Default Screen".                                               
        Using the first device section listed.                                                      
(**) |   |-->Device "Default Device"                                                                
(==) No monitor specified for screen "Default Screen".                                              
        Using a default monitor configuration.                                                      
(==) Automatically adding devices                                                                   
(==) Automatically enabling devices                                                                 
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.                                  
        Entry deleted from font path.                                                               
(==) FontPath set to:                                                                               
        /usr/share/fonts/X11/misc,                                                                  
        /usr/share/fonts/X11/100dpi/:unscaled,                                                      
        /usr/share/fonts/X11/75dpi/:unscaled,                                                       
        /usr/share/fonts/X11/Type1,                                                                 
        /usr/share/fonts/X11/100dpi,                                                                
        /usr/share/fonts/X11/75dpi,                                                                 
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,                                           
        built-ins                                                                                   
(==) ModulePath set to "/usr/lib/xorg/modules"                                                      
(II) Cannot locate a core pointer device.                                                           
(II) Cannot locate a core keyboard device.                                                          
(II) The server relies on HAL to provide the list of input devices.                                 
        If no devices become available, reconfigure HAL or disable AllowEmptyInput.                 
(II) Loader magic: 0x3bc0                                                                           
(II) Module ABI versions:                                                                           
        X.Org ANSI C Emulation: 0.4                                                                 
        X.Org Video Driver: 5.0                                                                     
        X.Org XInput driver : 4.0                                                                   
        X.Org Server Extension : 2.0                                                                
(II) Loader running on linux                                                                        
(++) using VT number 7                                                                              

(--) PCI:*(0:1:0:0) 10de:0141:107d:597b nVidia Corporation NV43 [GeForce 6600] rev 162, Mem @ 0xd0000000/67108864, 0xc0000000/268435456, 0xd4000000/16777216, BIOS @ 0x????????/131072                  
(II) Open ACPI successful (/var/run/acpid.socket)                                                   
(II) System resource ranges:                                                                        
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [17] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [19] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
(II) "extmod" will be loaded by default.                                                            
(II) "dbe" will be loaded by default.                                                               
(II) "glx" will be loaded. This was enabled by default and also specified in the config file.       
(II) "record" will be loaded by default.                                                            
(II) "dri" will be loaded by default.                                                               
(II) "dri2" will be loaded by default.                                                              
(II) LoadModule: "glx"                                                                              
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so                                            
(II) Module glx: vendor="NVIDIA Corporation"                                                        
        compiled for 4.0.2, module version = 1.0.0                                                  
        Module class: X.Org Server Extension                                                        
(II) NVIDIA GLX Module  185.18.36  Fri Aug 14 17:50:12 PDT 2009                                     
(II) Loading extension GLX                                                                          
(II) LoadModule: "extmod"                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so                                         
(II) Module extmod: vendor="X.Org Foundation"                                                       
        compiled for 1.6.4, module version = 1.0.0                                                  
        Module class: X.Org Server Extension                                                        
        ABI class: X.Org Server Extension, version 2.0                                              
(II) Loading extension MIT-SCREEN-SAVER                                                             
(II) Loading extension XFree86-VidModeExtension                                                     
(II) Loading extension XFree86-DGA                                                                  
(II) Loading extension DPMS                                                                         
(II) Loading extension XVideo                                                                       
(II) Loading extension XVideo-MotionCompensation                                                    
(II) Loading extension X-Resource                                                                   
(II) LoadModule: "dbe"                                                                              
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so                                            
(II) Module dbe: vendor="X.Org Foundation"                                                          
        compiled for 1.6.4, module version = 1.0.0                                                  
        Module class: X.Org Server Extension                                                        
        ABI class: X.Org Server Extension, version 2.0                                              
(II) Loading extension DOUBLE-BUFFER                                                                
(II) LoadModule: "record"                                                                           
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so                                         
(II) Module record: vendor="X.Org Foundation"                                                       
        compiled for 1.6.4, module version = 1.13.0                                                 
        Module class: X.Org Server Extension                                                        
        ABI class: X.Org Server Extension, version 2.0                                              
(II) Loading extension RECORD                                                                       
(II) LoadModule: "dri"                                                                              
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so                                            
(II) Module dri: vendor="X.Org Foundation"                                                          
        compiled for 1.6.4, module version = 1.0.0                                                  
        ABI class: X.Org Server Extension, version 2.0                                              
(II) Loading extension XFree86-DRI                                                                  
(II) LoadModule: "dri2"                                                                             
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so                                           
(II) Module dri2: vendor="X.Org Foundation"                                                         
        compiled for 1.6.4, module version = 1.1.0                                                  
        ABI class: X.Org Server Extension, version 2.0                                              
(II) Loading extension DRI2                                                                         
(II) LoadModule: "nvidia"                                                                           
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so                                           
(II) Module nvidia: vendor="NVIDIA Corporation"                                                     
        compiled for 4.0.2, module version = 1.0.0                                                  
        Module class: X.Org Video Driver                                                            
(II) NVIDIA dlloader X Driver  185.18.36  Fri Aug 14 17:24:40 PDT 2009                              
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs                                            
(II) Primary Device is: PCI 01@00:00:0                                                              
(II) Loading sub module "fb"                                                                        
(II) LoadModule: "fb"                                                                               
(II) Loading /usr/lib/xorg/modules//libfb.so                                                        
(II) Module fb: vendor="X.Org Foundation"                                                           
        compiled for 1.6.4, module version = 1.0.0                                                  
        ABI class: X.Org ANSI C Emulation, version 0.4                                              
(II) Loading sub module "wfb"                                                                       
(II) LoadModule: "wfb"                                                                              
(II) Loading /usr/lib/xorg/modules//libwfb.so                                                       
(II) Module wfb: vendor="X.Org Foundation"                                                          
        compiled for 1.6.4, module version = 1.0.0                                                  
        ABI class: X.Org ANSI C Emulation, version 0.4                                              
(II) Loading sub module "ramdac"                                                                    
(II) LoadModule: "ramdac"                                                                           
(II) Module "ramdac" already built-in                                                               
(II) resource ranges after probing:                                                                 
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [17] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [19] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
(II) NVIDIA(0): Creating default Display subsection in Screen section                               
        "Default Screen" for depth/fbbpp 24/32                                                      
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32                                                   
(==) NVIDIA(0): RGB weight 888                                                                      
(==) NVIDIA(0): Default visual is TrueColor                                                         
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)                                              
(**) NVIDIA(0): Option "NoLogo" "True"                                                              
(**) NVIDIA(0): Enabling RENDER acceleration                                                        
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is                       
(II) NVIDIA(0):     enabled.                                                                        
(II) NVIDIA(0): NVIDIA GPU GeForce 6600 (NV43) at PCI:1:0:0 (GPU-0)                                 
(--) NVIDIA(0): Memory: 262144 kBytes                                                               
(--) NVIDIA(0): VideoBIOS: 05.43.02.69.68                                                           
(II) NVIDIA(0): Detected PCI Express Link width: 16X                                                
(--) NVIDIA(0): Interlaced video modes are supported on this GPU                                    
(--) NVIDIA(0): Connected display device(s) on GeForce 6600 at PCI:1:0:0:                           
(--) NVIDIA(0):     Maxdata (RogenTech) (CRT-0)                                                     
(--) NVIDIA(0): Maxdata (RogenTech) (CRT-0): 400.0 MHz maximum pixel clock                          
(II) NVIDIA(0): Assigned Display Device: CRT-0                                                      
(==) NVIDIA(0):                                                                                     
(==) NVIDIA(0): No modes were requested; the default mode "nvidia-auto-select"                      
(==) NVIDIA(0):     will be used as the requested mode.                                             
(==) NVIDIA(0):                                                                                     
(II) NVIDIA(0): Validated modes:                                                                    
(II) NVIDIA(0):     "nvidia-auto-select"                                                            
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024                                    
(--) NVIDIA(0): DPI set to (101, 108); computed from "UseEdidDpi" X config                          
(--) NVIDIA(0):     option                                                                          
(==) NVIDIA(0): Enabling 32-bit ARGB GLX visuals.                                                   
(--) Depth 24 pixmap format is 32 bpp                                                               
(II) do I need RAC?  No, I don't.                                                                   
(II) resource ranges after preInit:                                                                 
        [0] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [4] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [5] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [6] -1  0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [7] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [8] -1  0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [9] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [10] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [11] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [12] -1 0       0xffffffff - 0xffffffff (0x1) MX[b]                                         
        [13] -1 0       0x000f0000 - 0x000fffff (0x10000) MX[b]                                     
        [14] -1 0       0x000c0000 - 0x000effff (0x30000) MX[b]                                     
        [15] -1 0       0x00000000 - 0x0009ffff (0xa0000) MX[b]                                     
        [16] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [17] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [18] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [19] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [20] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [21] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
        [22] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[b]                                         
        [23] -1 0       0x00000000 - 0x00000000 (0x1) IX[b]                                         
(II) NVIDIA(0): Initialized GPU GART.                                                               
(II) NVIDIA(0): Setting mode "nvidia-auto-select"                                                   
(II) Loading extension NV-GLX                                                                       
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized                                     
(==) NVIDIA(0): Disabling shared memory pixmaps                                                     
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture                                       
(==) NVIDIA(0): Backing store disabled                                                              
(==) NVIDIA(0): Silken mouse enabled                                                                
(II) NVIDIA(0): DPMS enabled                                                                        
(II) Loading extension NV-CONTROL                                                                   
(II) Loading extension XINERAMA                                                                     
(==) RandR enabled                                                                                  
(II) Initializing built-in extension Generic Event Extension                                        
(II) Initializing built-in extension SHAPE                                                          
(II) Initializing built-in extension MIT-SHM                                                        
(II) Initializing built-in extension XInputExtension                                                
(II) Initializing built-in extension XTEST                                                          
(II) Initializing built-in extension BIG-REQUESTS                                                   
(II) Initializing built-in extension SYNC                                                           
(II) Initializing built-in extension XKEYBOARD                                                      
(II) Initializing built-in extension XC-MISC                                                        
(II) Initializing built-in extension SECURITY                                                       
(II) Initializing built-in extension XINERAMA                                                       
(II) Initializing built-in extension XFIXES                                                         
(II) Initializing built-in extension RENDER                                                         
(II) Initializing built-in extension RANDR                                                          
(II) Initializing built-in extension COMPOSITE                                                      
(II) Initializing built-in extension DAMAGE                                                         
(II) Initializing extension GLX                                                                     
(II) config/hal: Adding input device stylus                                                         
(II) LoadModule: "wacom"                                                                            
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so                                              
(II) Module wacom: vendor="X.Org Foundation"                                                        
        compiled for 1.6.4, module version = 1.0.0                                                  
        Module class: X.Org XInput Driver                                                           
        ABI class: X.Org XInput driver, version 4.0                                                 
(II) Wacom driver level: 47-0.8.4-1 $                                                               
(**) stylus: always reports core events                                                             
(**) stylus device is /dev/ttyS0                                                                    
(**) stylus is in absolute mode                                                                     
(**) WACOM: suppress value is 2                                                                     
(**) Option "BaudRate" "9600"                                                                       
(**) stylus: serial speed 9600                                                                      
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)                             
(**) Option "Device" "/dev/ttyS0"                                                                   
(**) Option "StopBits" "1"                                                                          
(**) Option "DataBits" "8"                                                                          
(**) Option "Parity" "None"                                                                         
(**) Option "Vmin" "1"                                                                              
(**) Option "Vtime" "10"                                                                            
(**) Option "FlowControl" "Xoff"                                                                    
usbDetect: can not ioctl version                                                                    
(==) Wacom tablet model : UD-1212-R00 V1.4-4                                                        
(==) Wacom using pressure threshold of 15 for button 1                                              
(==) Wacom Serial UD tablet speed=9600 (38400) maxX=15240 maxY=15240 maxZ=255 resX=1270 resY=1270  tilt=disabled                                                                                        
(==) Wacom device "stylus" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270  
(II) config/hal: Adding input device AT Translated Set 2 keyboard                                   
(II) LoadModule: "evdev"                                                                            
(II) Loading /usr/lib/xorg/modules/input//evdev_drv.so                                              
(II) Module evdev: vendor="X.Org Foundation"                                                        
        compiled for 1.6.4, module version = 2.2.5                                                  
        Module class: X.Org XInput Driver                                                           
        ABI class: X.Org XInput driver, version 4.0                                                 
(**) AT Translated Set 2 keyboard: always reports core events                                       
(**) AT Translated Set 2 keyboard: Device: "/dev/input/event3"                                      
(II) AT Translated Set 2 keyboard: Found keys                                                       
(II) AT Translated Set 2 keyboard: Configuring as keyboard                                          
(II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD)           
(**) Option "xkb_rules" "evdev"                                                                     
(**) Option "xkb_model" "pc105"                                                                     
(**) Option "xkb_layout" "de"                                                                       
(**) Option "xkb_variant" "nodeadkeys"                                                              
(II) config/hal: Adding input device stylus cursor                                                  
(**) stylus cursor: always reports core events                                                      
(**) stylus cursor device is /dev/ttyS0                                                             
(**) stylus cursor is in relative mode                                                              
(**) WACOM: suppress value is 2                                                                     
(**) stylus cursor: threshold = 15                                                                  
(**) stylus cursor: max x set to 15240 by xorg.conf                                                 
(**) stylus cursor: max y set to 15240 by xorg.conf                                                 
(**) stylus cursor: max z = 255                                                                     
(**) Option "BaudRate" "9600"                                                                       
(**) stylus cursor: serial speed 9600                                                               
(II) XINPUT: Adding extended input device "stylus cursor" (type: Wacom Cursor)                      
(==) Wacom device "stylus cursor" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270                                                                                               
(II) config/hal: Adding input device eraser                                                         
(**) eraser: always reports core events                                                             
(**) eraser device is /dev/ttyS0                                                                    
(**) eraser is in absolute mode                                                                     
(**) WACOM: suppress value is 2                                                                     
(**) eraser: threshold = 15                                                                         
(**) eraser: max x set to 15240 by xorg.conf                                                        
(**) eraser: max y set to 15240 by xorg.conf
(**) eraser: max z = 255
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(==) Wacom device "eraser" top X=0 top Y=0 bottom X=15240 bottom Y=15240 resol X=1270 resol Y=1270
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event0"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/hal: Adding input device Power Button
(**) Power Button: always reports core events
(**) Power Button: Device: "/dev/input/event1"
(II) Power Button: Found keys
(II) Power Button: Configuring as keyboard
(II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD)
(**) Option "xkb_rules" "evdev"
(**) Option "xkb_model" "pc105"
(**) Option "xkb_layout" "de"
(**) Option "xkb_variant" "nodeadkeys"
(II) config/hal: Adding input device ImExPS/2 Generic Explorer Mouse
(**) ImExPS/2 Generic Explorer Mouse: always reports core events
(**) ImExPS/2 Generic Explorer Mouse: Device: "/dev/input/event4"
(II) ImExPS/2 Generic Explorer Mouse: Found 9 mouse buttons
(II) ImExPS/2 Generic Explorer Mouse: Found x and y relative axes
(II) ImExPS/2 Generic Explorer Mouse: Found scroll wheel(s)
(II) ImExPS/2 Generic Explorer Mouse: Configuring as mouse
(**) ImExPS/2 Generic Explorer Mouse: YAxisMapping: buttons 4 and 5
(**) ImExPS/2 Generic Explorer Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "ImExPS/2 Generic Explorer Mouse" (type: MOUSE)
(**) ImExPS/2 Generic Explorer Mouse: (accel) keeping acceleration scheme 1
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter chain progression: 2.00
(**) ImExPS/2 Generic Explorer Mouse: (accel) filter stage 0: 20.00 ms
(**) ImExPS/2 Generic Explorer Mouse: (accel) set acceleration profile 0
(II) ImExPS/2 Generic Explorer Mouse: initialized for relative axes.
(II) config/hal: Adding input device Macintosh mouse button emulation
(**) Macintosh mouse button emulation: always reports core events
(**) Macintosh mouse button emulation: Device: "/dev/input/event2"
(II) Macintosh mouse button emulation: Found 3 mouse buttons
(II) Macintosh mouse button emulation: Found x and y relative axes
(II) Macintosh mouse button emulation: Configuring as mouse
(**) Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
(**) Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
(II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE)
(**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
(**) Macintosh mouse button emulation: (accel) filter chain progression: 2.00
(**) Macintosh mouse button emulation: (accel) filter stage 0: 20.00 ms
(**) Macintosh mouse button emulation: (accel) set acceleration profile 0
(II) Macintosh mouse button emulation: initialized for relative axes.

```wacomcpl shows stylus and eraser.

Thanks alot for your help!

EDIT:
I tried to browse the source code for the kernel drivers, but from cursory browsing I didn't really see the difference between eraser and stylus. Could it be the "tilt" information which is only transmitted for the stylus?

---

### Post by Favux on 2009-12-22
Hi janjan7777,

When xsetwacom list shows stylus and eraser does xinput --list also show them?

Xorg.0.log seems OK, but I wonder why evdev pops up between stylus and cursor & eraser.  Linuxwacom slow to recognize them?

Tilt may be one of the differences but I thought Rspeed applied just to the mouse/cursor.  If it applies to stylus also then maybe I put it in the wrong place on the .fdi and that's why we aren't seeing any changes with it.

Does the stylus and especially eraser work in Gimp or wherever?  I'm beginning to wonder if the problem is hal-setup-wacom doesn't work right with the ArtZII.  Could the Wacom mouse be a separate device with them and so can't be added/appended as a sub-device?

I'm going to attach a .fdi that just has the stylus.  See how that works.

Edit:  Could you please describe the mouse.  Is it physically connected to the tablet with a serial cable?  Or is it a free device like the stylus and works when on the tablet?

---

### Post by janjan7777 on 2009-12-22
Dear Favux,
with the new file, only the stylus works, but still exhibiting the same behaviour (slow, fast if pressed). Tested also in Gimp.

> **Favux said:**
> 
When xsetwacom list shows stylus and eraser does xinput --list also show them?

Old fdi: no, the files above are from the same run
New fdi: yes, it is visible now! :)

xinput --list
```

"stylus"        id=3    [XExtensionKeyboard]                                               
        Type is Wacom Stylus                                                               
        Num_keys is 248                                                                    
        Min_keycode is 8                                                                   
        Max_keycode is 255                                                                 
        Num_buttons is 32                                                                  
        Num_axes is 6                                                                      
        Mode is Absolute                                                                   
        Motion_buffer is 256                                                               
        Axis 0 :                                                                           
                Min_value is 0                                                             
                Max_value is 15240                                                         
                Resolution is 1270                                                         
        Axis 1 :                                                                           
                Min_value is 0                                                             
                Max_value is 15240                                                         
                Resolution is 1270
        Axis 2 :
                Min_value is 0
                Max_value is 255
                Resolution is 1
        Axis 3 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 4 :
                Min_value is -64
                Max_value is 63
                Resolution is 1
        Axis 5 :
                Min_value is 0
                Max_value is 1023
                Resolution is 1

```xsetwacom list:
```

stylus stylus

```lshal (trimmed):
```

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  info.capabilities = {'serial', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:07/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)

```> **Favux said:**
> 
Does the stylus and especially eraser work in Gimp or wherever?  I'm beginning to wonder if the problem is hal-setup-wacom doesn't work right with the ArtZII.  Could the Wacom mouse be a separate device with them and so can't be added/appended as a sub-device?


Stylus and eraser worked (with the old fdi) in Gimp in the same way as in the other programs (stylus: slow, fast when pressed; eraser: works perfectly). With the new file, the eraser, as expected, does not work.

> **Favux said:**
> 
Edit:  Could you please describe the mouse.  Is it physically connected to the tablet with a serial cable?  Or is it a free device like the stylus and works when on the tablet?

It is free (wireless), four buttons, and a crosshair with a wire loop around.

Thanks,
Jan

---

### Post by janjan7777 on 2009-12-22
Another observation: wacdump on a virtual terminal (outside of X11) does not exhibit this strange behaviour, as far as I can see it. The position numbers there are always plausible.

---

### Post by Favux on 2009-12-22
Hi janjan7777,

Good, stylus is in xinput with the new .fdi.  Now substitute 'cursor' for 'stylus' in the two lines that have 'stylus'.  Let's see how the cursor behaves.  Also need the xinput and lshal again.  Xorg.0.log with both wouldn't hurt.

> Another observation: wacdump on a virtual terminal (outside of X11) does not exhibit this strange behaviour, as far as I can see it. The position numbers there are always plausible.
That's sounding like a code problem in linuxwacom rather than anything else.  Can we pinpoint the change?  

Barbidoux says Jaunty and Karmic.  So that would be 0.8.1-4 (Hardy) OK and bad with 0.8.2-2 (Jaunty).  And I think others say the same thing.

But you were bad in Hardy, OK in Jaunty, and bad in Karmic?

---

### Post by Barbidoux on 2009-12-23
Hello

I tried your limited .fdi.

Everything the same as Janjan : pen work chewy except while "clicking" (push or index button) and no response from puck.

If you need other tests, please tell me. As Janjan made them and seems to experiment the same behavior, I'm not sure we need to make them twice, but if you need confirmation, please tell me.

---

### Post by Favux on 2009-12-23
Hi,

OK.  That's right, only the stylus was in that .fdi.  I'm trying to rule out any "interference" by making only one device active at a time.  That way we can eliminate a problem with hal-setup-wacom, etc.

The fact that the behavior didn't change with only stylus enabled is important information.  We are eliminating variables.

The .fdi attached to this post only enables the Wacom mouse (cursor).  See if it makes any difference to how the cursor behaves.

If it is the same then it would seem it is a problem with the serial signal, although janjan7777 is saying it looks clean to him with wacdump.  Or a problem with the code (starting to seem likely).  Or maybe we are should be using some other "protocol"?

One thing you both could do is look at the outputs of xidump and xinput with both of the simple .fdi's and see if you see anything of interest.  For xidump use:
```
xidump stylus
```
and
```
xidump cursor
```
To see xinput options just enter xinput in a terminal.  It will show you options, for example:
```
xinput test stylus
```
ctrl-z to exit either of them.

---

### Post by janjan7777 on 2009-12-23
Dear Favux,
in response to post #48:
Only puck works, stylus and eraser not. Behaviour is still the same (slow with delay, fast if button pressed). lshal etc attached in zip.

EDIT:
With the "cursor" fdi, xidump stylus gives
```

Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'stylus'
Error (2): WacomConfigOpenDevice: No such device
Get: Failed to open device 'stylus'
Unable to find input device 'stylus'

```xidump cursors shows also the delay line behaviour, e.g., the numbers change sign (relative mode) only after some further motion. Using the stylus after a puck motion shows this "flushing a buffer" effect, e.g., missing events from the puck are processed, but then no response as expected.

As far as I remember, behaviour was bad in 8.04 or 8.10 (not sure, probably 8.10), then was better in Jaunty, and is now bad again in Karmic. But I may be mistaken, didn't use it a lot in Jaunty.

---

### Post by Favux on 2009-12-23
Hi,

Alright.  We now know there isn't any interference between stylus and cursor or with hal-setup-wacom.  But we also now have to seperate .fdi's, one for stylus and one for cursor to experiment with.

Since you have to press down hard with the stylus (is pressing the button on the cursor the equivalent?) maybe there is something wrong with the Threshold?

Both the stylus and cursor in Xorg.0.log show:
```
(==) Wacom using pressure threshold of 15 for button 1
```
Xinput shows:
```
	Axis 2 :
		Min_value is 0
		Max_value is 255
		Resolution is 1
```
Where Axis 2 is almost for sure the pressure levels.  And that checks out:
```
               Option "Threshold" "number"
                   sets  the  pressure  threshold  used to generate a button 1
                   events of stylus. The default is MaxPressure*3/50.


```
So:  255 * 3 / 50 = 15.3  which agrees with the 15 in Xorg.0.log.

But you have to press hard.  Do you still have any literature saying how many pressure levels the ArtZII has?

Anyway let's check if something is wrong, and it must be because you have to press so hard.  Let's trying lowering the Threshold to 10 and see if that makes a difference:
```
	<merge key="input.x11_options.Threshold" type="string">10</merge>
```
And you can also check it with the "cursor" .fdi.

---

### Post by janjan7777 on 2009-12-25
Hi Favux,
as far as I remember, pressure resolution was about 255 steps, but I cannot check at the moment (I'll be back home on 28th or so). I bought the device use, so I do not have the documentation. At least resolution was fine enough to give me nice smooth gray levels in gimp. I'll try the new fdi as soon as I get back. Thanks a lot so far!
Jan

---

### Post by Barbidoux on 2009-12-28
Hello

Just tried your last .fdi.

I didn't see a difference : move are good when "clicked" and very chewy in other case.

I'm not sure I caught everything in your last posts.

---

### Post by Favux on 2009-12-28
Hi Barbidoux & janjan7777,

Ok, so Threshold isn't the answer.  You may have been on the right track with hardware vs software flow control.

With the stylus test2 .fdi below we'll check to see if what is needed is special ttyS0 settings by doing an info.callout to hal-system-setserial.

Right now I'm off looking at serial_core.ko & 8250_pnp.ko, kernel modules/drivers which are part of the serial chain.  I would appreciate the output of your:
```
lsmod
```

I have found a good Serial wiki:  [http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html)  which seems to hold some clues.

---

### Post by Barbidoux on 2009-12-28
Hello

Here are the results.

I don't think this is a serial port problem since it works fine when clicked (communication is fine).
I "smell" a problem in priority in the system and the driver : when clicked, the priority goes up, when not, the event is put in lower priority. When clicked, what is in the pipe is sent ...

Well, I don't know, that's only feelings.

EDIT : During the night, I thought to this problem. It could be a buffering problem : when pushed, there are pressure information continuously, making a lot of data comparing to just move signal. And a lot of data mean a lot more flush of the buffer. After thinking to that, I retried the pen and I think that even when clicked, the precision is worse than what it was in older ubuntu version. It's workable, but not as good as it could be.

---

### Post by Favux on 2009-12-29
Hi Barbidoux,

That sounds very likely.  Since in Xorg.0.log we know there is no software flow control 'Option "FlowControl" "Xoff"', what if the problem is that linuxwacom isn't setting hardware flow control?  That would overflow the UART/fifo's wouldn't it?  That would lose whole contiguous chunks of data.  So let's try setting it ourselves by entering in a terminal:
```
stty -F /dev/ttyS0 crtscts
```
'crtscts' stands for a Control setting to use the RTS and CTS pins of the serial port for hardware flow control.  See "man Stty" in a terminal.

I don't know if we can change it on the fly like this with linuxwacom or if we need to run it before linuxwacom initializes.

And did you try turning software flow control on?

---

### Post by gad241 on 2010-01-03
Hello Gents..been following along with this thread trying to produce results with my serial tablet. Gimp doesn't see the tablet. I'm using the following:

Ubuntu 9.04 64-bit
Tablet is a Wacom PenPartner CT-0405-R
Stylus has eraser built-in.

Here is the output of lshal:```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device', 'hal-setup-wacom', 'hal-setup-wacom'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control', 'input', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'eraser', 'cursor'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_4'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_4'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_3'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_3'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_2'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_2'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'
  info.capabilities = {'input'} (string list)udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device', 'hal-setup-wacom', 'hal-setup-wacom'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control', 'input', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'eraser', 'cursor'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_4'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_4'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_3'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_3'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_2'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_2'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device', 'hal-setup-wacom', 'hal-setup-wacom'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control', 'input', 'input'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = 'stylus'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'stylus'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
  wacom.types = {'eraser', 'eraser', 'cursor'} (string list)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_4'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_4'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_3'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_3'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_2'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_2'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus cursor'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_1'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'cursor'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'stylus eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev_0'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'
  info.capabilities = {'input'} (string list)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  info.product = 'eraser'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0_subdev'  (string)
  input.device = '/dev/ttyS0'  (string)
  input.x11_driver = 'wacom'  (string)
  input.x11_options.ForceDevice = 'ISDV4'  (string)
  input.x11_options.Type = 'eraser'  (string)
```

Can provide section from Xorg.0.log if needed.

---

### Post by janjan7777 on 2010-01-03
Hi,
sorry that I'm a bit late in replying, family and so, you now.

The stty command does not change the bad behaviour. Neither does "stty -ixon -F /dev/ttyS0" or xoff.

What I still find odd is that the eraser did not show this problem. There must be a fundamental difference in the treatment of the eraser and the other tools...

---

### Post by Favux on 2010-01-09
Hi janjan7777,

I think the eraser finding is interesting.  It's telling us something, if we could figure it out.


Hi gad241,

Welcome to the thread!  Your lshal looks weird.  Like you have multiple wacom.fdi's or have duplicate sections in the same .fdi.  Please check that.  Do you remember which ttyS your PenPartner CT-0405-R was on?  I gather you don't see a serial pnp identifier for it in lshal, correct?


OK.  Lets try different match lines in the .fdi.  So this is a new .fdi, substitute it for the old one.  And gad241 if you don't have a PnP identifier and your tablet sets up on ttyS0 you can use it too.  Otherwise change the ttyS to the number your tablet uses, e.g. ttyS1.

We've learned that we can setup on the pnp_PNP0501.ko as a proxy for the pnp identifier the ArtZII is lacking.  Which brings up a question again:  Did the ArtZII or PenPartner ever identify for anyone as plug and play?  If so does anyone remember the number?  Do you have literature describing them as Plug & Play?

If it and the PenPartner are pre-plug and play let's try match lines based on the HAL specification for "legacy" devices.  I'm wondering if going through the plug and play module is "blocking" our attempts to configure like "stty -F /dev/ttyS0 crtscts" and the other ones we've tried.  This is based on the observation that when the stylus of a serial tablet pc doesn't work it's after a reboot and PnP lines shows up in Xorg.0.log.  If the stylus works after restarting X no PnP entries show up in the Xorg.0.log.

I hope I have the match lines correct and they work.  I'm not convinced the ArtZII has a pad even if there are buttons on the tablet.  I think the pad appeared with usb tablets.

I also have an xorg.conf ready if the consensus is to give up on a .fdi.  I may either add more to this post and/or start a new thread.

---

### Post by JAKEOTR on 2010-01-09
Hello...Favux thanks for your response..i had a separate thread going [http://ubuntuforums.org/showthread.php?t=1373560](http://ubuntuforums.org/showthread.php?t=1373560). Favux asked me to post here. My original post:

>>I have a serial ud-0608-r Digitizer II and could not get it to plug and play with 9.10. I finally got it to work using the guides for 8.10 (xorg config). But the last niggling problem is my cursor is very slow. It lags behind terribly. The stylus and the eraser work just fine, but the mouse function does not. I am able to use wacomcpl, and have tried different settings...I have tried speed settings in xorg and no luck there. Any have any ideas? Thanks>>

I have been messing with it this morning and found that my stylus and eraser both work fine (all art functions in Gimp)...the eraser works as the cursor fine, its just the stylus end that doesnt work as the cursor. Its slow and a little jumpy/squirrely. I may also be confused as what the "cursor" is. I do not have a separate mouse for the tablet. I am referring to moving the pen across the face of the tablet without touching it thus moving the cursor, touching down for mouse clicks. I dont have the issue with having to press down hard.

I tried commenting out my cursor section in xorg and the pen still works (with the same problem) so maybe I dont need it. Please ask me any questions as I'm not sure i've set this up correctly. I have renamed my .fdi file so I'm not using it at this time. I have a wacom tablet with 18 fuction/macro buttons across the top and a pen with an eraser and a two button rocker switch.

Here is my xorg file:
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice   "stylus"  "SendCoreEvents"
    InputDevice   "eraser"  "SendCoreEvents"
#    InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only

EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
  #  Option         "Device" "/dev/psaux"
    Option         "Device" "/dev/input/mice"
    Option         "Emulate3Buttons" "yes" #no
    Option         "ZAxisMapping" "4 5"
    Option         "CorePointer"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
#  Option        "Type"          "cursor"
#  Option      "Mode"          "Relative" 
#  Option      "Speed"         "10.0" 
#  Option 	"Speed" 	"Rspeed" 
#EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by Favux on 2010-01-09
Hi JAKEOTR,

Just to be sure, even though you're using a xorg.conf, you are in Karmic (9.10), correct?

Right,   cursor = Wacom mouse  in linuxwacom "speak".  So if you don't have one commenting it out is correct.  The cursor is not the little arrow on the screen.

OK, I don't think the macro buttons work through pad, which I think is usb only, but I'm not 100% sure.

So basically same problem stylus lags but eraser is OK.  Interestingly your stylus is working in "hover" mode (no pressing down hard).

What was the last version of Ubuntu that things worked right on?

---

### Post by Favux on 2010-01-09
Hi JAKEOTR,

Just to be sure, even though you're using a xorg.conf, you are in Karmic (9.10), correct?

Right   cursor = Wacom mouse  in linuxwacom "speak".  So if you don't have one commenting it out is correct.  The cursor is not the little arrow on the screen.

OK, I don't think the macro buttons work through pad, which I think is usb only, but I'm not 100% sure.

So basically same problem stylus lags but eraser is OK.  Interestingly your stylus is working in "hover" mode (no pressing down hard).

What was the last version of Ubuntu that things worked right on?

Also do you have more than one monitor?

---

### Post by gad241 on 2010-01-09
Hi Favux,

Actually I do have multiple .fdis. I have the 10-linuxwacom.fdi located in /usr/share/hal/fdi/policy/20thirdparty. The other one is custom_wacom.fdi located in /etc/hal/fdi/policy. The latter was built using this thread: [https://help.ubuntu.com/community/Wacom.fdi](https://help.ubuntu.com/community/Wacom.fdi). Looking at your attached file, it appears that I shouldn't have created the custom wacom fdi. Yes, the Wacom PenPartner is attached to ttyS0 and PNP0501 isn't a valid uid eh?

---

### Post by Favux on 2010-01-09
Hi gad241,

Right only one .fdi.  Actually theoretically you can use two or a .fdi and xorg.conf, but practically not a good idea.

Nope, well valid just not for the tablet.  But it worked.  ;)  The (a) PenPartner is in the wacom.rules symlink table:
```
ATTRS{idVendor}=="056a", ATTRS{idProduct}=="0000", SYMLINK+="input/tablet-penpartner"
```
Let's check your lshal and make sure there isn't an identifier for your PenPartner:
```
lshal>gad241_lshal.txt
```
Was there a serial and a usb version?

---

### Post by JAKEOTR on 2010-01-10
Favux...I am using 9.10, only 1 monitor, tablet buttons I don't care about... this is the first time I've hooked up the tablet in years(last time was Windows NT). So my problem is the pen works on the stylus end fine when I touch it to the tablet, but lags when I hover. The eraser end works hovering and touching. Wonder if it could be the pen itself? Also do you think my pad would work automagically, if I reinstalled 9.10 with the tablet connected?

---

### Post by gad241 on 2010-01-10
Favux,

I removed the custom_wacom.fdi from /etc/hal/../policy directory and copy/paste your txt file over what was in 10-wacom.fdi. Rebooted. Attached is lshal. Xorg log does not show the tablet being recognized. At one point Xorg saw the tablet using one of your post but I can't remember what I did to make that happen. On a side note, can you recommend a reading source on configuring devices using HAL? I have the HAL specs but I'm not sure where I should be using match key, merge key, etc.

---

### Post by gad241 on 2010-01-10
Ok...some reason the txt file didn't go through. I cut out the non-relevant entries.

---

### Post by Favux on 2010-01-10
Hi everyone,

Has anyone tried the new .fdi yet?  Does it get your tablet working?


I'm attaching a generic xorg.conf based on Nvidia video.  If you have different video I can help you with that.  In Karmic with Intel and ATI video you may not have any video sections, if so use the:
```
Identifier	"X.org Configured"
```
in "ServerLayout" instead of:
```
	Identifier	"Default Layout"
	Screen		"Default Screen"
```
Comment out what you don't have like eraser or cursor (Wacom mouse), don't forget the corresponding line in "ServerLayout".  Some of you have two stylus buttons, I left the second one commented out.

Don't forget to back up your current working xorg.conf and be prepared to restore it at the command line.  The xorg.conf is touchy in Karmic so X breakage is likely.


Hi JAKEOTR,

It could be the stylus tip is broken but really the lag problem sounds similar to what everyone else is seeing and the problems serial users have been seeing with Karmic.  They're transitioning from HAL to DeviceKit in Karmic on the way to udev-extras, and that might be one of the possible causes of the stylus pointer arrow lag.
> Also do you think my pad would work automagically, if I reinstalled 9.10 with the tablet connected? 
I doubt it.


Hi gad241,

There's an upload size limit on files so compress the lshal.txt by right clicking on it and use Create Archive.  Then Manage Attachments will let you upload it.

Since it looks like you did try the "legacy" .fdi I'm eager to see what your lshal shows.

I spent a long time looking for a "HAL for Dummies" with no luck.  Basically the spec. is the best I have.  A couple of sources give some examples that might help:
[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)
[http://wiki.archlinux.org/index.php/HAL](http://wiki.archlinux.org/index.php/HAL)

---

### Post by gad241 on 2010-01-10
HAL for Dummies...that's funny but with Linux is what I need. Ok..zipped up my lshal will try to attach for the third time.

---

### Post by Favux on 2010-01-10
Hi gad241,

You and me both.

Alright it looks like the first match line worked.
```
<match key="platform.id" contains="serial">
```
Added to the two pnp_PNP0501 sections:
```
udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'
  info.linux.driver = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'pnp'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pnp'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08'  (string)
  pnp.description = '16550A-compatible COM port'  (string)
  pnp.id = 'PNP0501'  (string)

udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'
  access_control.file = '/dev/ttyS0'  (string)
  access_control.type = 'modem'  (string)
  info.callouts.add = {'hal-acl-tool --add-device'} (string list)
  info.callouts.remove = {'hal-acl-tool --remove-device'} (string list)
  info.capabilities = {'serial', 'access_control'} (string list)
  info.category = 'serial'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  info.product = '16550A-compatible COM port'  (string)
  info.subsystem = 'tty'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pnp_PNP0501_serial_platform_0'  (string)
  linux.device_file = '/dev/ttyS0'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'tty'  (string)
  linux.sysfs_path = '/sys/devices/pnp0/00:08/tty/ttyS0'  (string)
  serial.device = '/dev/ttyS0'  (string)
  serial.originating_device = '/org/freedesktop/Hal/devices/pnp_PNP0501'  (string)
  serial.port = 0  (0x0)  (int)
  serial.type = 'platform'  (string)
```
is a new one:
```
udi = '/org/freedesktop/Hal/devices/platform_serial8250'
  info.linux.driver = 'serial8250'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = 'Platform Device (serial8250)'  (string)
  info.subsystem = 'platform'  (string)
  info.udi = '/org/freedesktop/Hal/devices/platform_serial8250'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'platform'  (string)
  linux.sysfs_path = '/sys/devices/platform/serial8250'  (string)
  platform.id = 'serial8250'  (string)
```
So the second match line:
```
<match key="serial.device" contains="/dev/ttyS0">
```
isn't right.

Hmmm.

Change it to?:
```
<match key="serial.port" contains="0">
```

---

### Post by gad241 on 2010-01-11
Hey Favux...I'll try that when I get back to the house. I'm going to have to back to one of your previous threads and see if I can get back to the stage where Xorg recognized something on the COM port. I did load the Windows drivers on XP for the tablet to see if I could gleam some product hex keys. All I got was some 4 digit numbers and PNP0501.

---

### Post by gad241 on 2010-01-11
Favux..got Xorg to recognize the tablet at least some what using your serial-tablet&tablet-pc_test2_10-wacom.fdi.txt. Xorg shows the system is having issues with ISDV4 and then the wacom driver is unloaded. I have attached a new lshal.txt and abbreviated Xorg log for your viewing.

---

### Post by dvalphen on 2010-01-11
Hi,

I have a Wacom Intuos serial. Got it working after following your above posts, in particular adding the PNP0501 entry to the line       
  <match key="@info.parent:pnp.id" contains_outof="PNP0501;WACf;FUJ02e5;FUJ02e7">
and commenting out the line
<!--<merge key="input.x11_options.ForceDevice" type="string">ISDV4</merge>-->

This is based off the generic .fdi file.

The mouse action is also exhibiting the super slow responses, and the pen/erasor working ok.

I've attached Xorg and lshall logs in case they may be of use.

This is a clean install of Karmic x64 using the built in kernel driver, haven't tried building the latest from source - heres hoping I dont have to!

---

### Post by gad241 on 2010-01-11
Hey dvalphen...good call on commenting out ISDV4. I now have movement from the stylus but like you I'm seeing lag. Getting close now and with Favux help we may get this thing licked.

---

### Post by gad241 on 2010-01-11
Just a quick update. The stylus has some lag but the eraser function seems to be tracking correctly. I also commented out the sections concerning the touch functions since I don't think the PenPartner has that feature but I'm seeing some flickering with my display. Didn't notice this before commenting out the touch section. Might have to put it back in if the display keeps acting up. Also I think Gimp kills the tablet during configuration of the external input. Will have to double check that.

---

### Post by gad241 on 2010-01-11
Another quick update. Had a game lock up which required a hard shutdown. Booted back up. Display now seems to be acting correctly. Fired up Gimp and the stylus still lagging behind position on pad but the eraser is still working correctly (it acts as another pointer). Still some tweaking required.

---

### Post by gad241 on 2010-01-12
Another update. I commented out the entry concerning the cursor and it appears that the stylus is tracking a lot better.

---

### Post by Favux on 2010-01-13
Hi dvalphen,

Welcome to the thread!

Is it an Intous3?  Does it have a pad?  Your lshal shows a stylus and eraser and says you don't have a Wacom mouse (cursor).  Is that correct?.  You seem to be saying you have one.  Interestingly it tries to set up stylus, eraser, and cursor on ttyS1 first unlike with the ArtZII's and PenPartner.  In the Xorg.0.log the stylus and eraser on ttyS1 are rejected by linuxwacom because it can't read the input.  Also the Xorg.0.log shows the linuxwacom driver recognizes the tablet and calls it "Wacom tablet model : GD-0912-R00,V1.2-7" whereas the ArtZII and PenPartner aren't identified.

It is very helpful to see another serial tablet setting up on PNP0501 so thank you!  I do not see a PnP identifier for your tablet either.  What would be very useful is if you could set up your Intuos with a xorg.conf.  That way if we confirm the cursor lag is still present we know it's not due to  PNP0501.

With the stylus and eraser working correctly for you then maybe setting up on PNP0501 is a "valid" method and we have a .fdi for serial Wacom tablets without PnP identifiers!  Also, can you tell me what version of Ubuntu was the last one that the tablet worked correctly on?


Hi gad241,

> got Xorg to recognize the tablet at least some what using your serial-tablet&tablet-pc_test2_10-wacom.fdi.txt.
Using PNP0501 as an identifier?
> I commented out the entry concerning the cursor and it appears that the stylus is tracking a lot better. 
Now that's interesting, your PenPartner CT-0405-R doesn't have a Wacom mouse (has stylus with eraser).  The lshal shows it knows there is no cursor, so how would that make a difference?

And same thing about xorg.conf with you.  If behavior doesn't change then we know it isn't the .fdi's fault.

---

### Post by gad241 on 2010-01-13
Hey Favux. Yes, it work with PNP0501..:D! I attached my .fdi file for your viewing. As far as the cursor is concern, I thought maybe the stylus and cursor may have been acting against each other. It was a SWAG on my part. I also tried to re-order the match key, merge and append entries. NO..NO...X didn't like that and promptly messed up gdm. Lessons learned there. The tablet works with Gimp now and the stylus is still not dead on with movement but is a lot better than it was and I can live with it. Thanks for all your help. If there is something else you might want me to try, let me know and I'll give it a go.

---

### Post by Favux on 2010-01-14
Hi gad241,

Great, progress!  Did you calibrate your tablet/stylus with wacomcpl?

OK, so using the serial-tablet&tablet-pc_test2_10-wacom.fdi.txt from [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") and adding PNP0501 to the identifiers has almost got things working for your PenPartner CT-0405-R.  After you commented out all the devices you don't have in the .fdi (including the Wacom names "parser").

What we need is one or two other serial tablets that don't have a PnP identifier and aren't identified by linuxwacom in Xorg.0.log to confirm that that works for them too.

---

### Post by gad241 on 2010-01-14
Yes, I commented out the entries that I don't believe the tablet supports. Haven't tried to calibrate the tablet with wacomcpl. Got to figure out how that works. I'll reply later once I tried that with the results. Thanks again for all your help.

---

### Post by janjan7777 on 2010-01-14
(quote shortened)
> **Favux said:**
> Hi everyone,
Has anyone tried the new .fdi yet?  Does it get your tablet working?
...
I'm attaching a generic xorg.conf based on Nvidia video.[U]
...[/U]

Dear Favux,
respoding to your Post #69:
tried the new fdi and the xorg.conf, but still slow. Should I attach the Xorg.0.log etc?
Thanks,
Jan

---

### Post by Favux on 2010-01-14
Hi gad241,

Sure, you're welcome.  Post #176 has a link to setting up wacomcpl or I can give you a direct one.


Hi janjan7777,

OK, not what we'd like but good to hear from you again.  Yes I'd like to see the Xorg.0.logs.  If you can put labels on the one with the ArtZII_test1_10-linuxwacom.fdi and the other with the xorg.conf that would help.

---

### Post by gad241 on 2010-01-16
Hey Favux..yeah if you can give the direct link to wacomcpl that would be helpful...thanks.

---

### Post by Favux on 2010-01-16
Hi gad241,

Sure it's "Section 3: Calibrating your Tablet" in this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Wacomcpl is the Wacom Control Panel, you just type it (wacomcpl) in a terminal and the gui pops up, as long as wacom-tools is installed.

---

### Post by dvalphen on 2010-01-20
Ive got the original Intuos (bought around 2000) with mouse and pen/erasor. GD-0912 is the model, so the driver is identifying it correctly. I think I last used the tablet on feisty or gutsy, where all i needed to do was add some wacom lines to the xorg.conf file. 

Worth pointing out that none of the devices worked before I added the PNP0501 entry to the .fdi file, the only indication that it was even connected was from wacdump if I specified the correct serial port (/dev/ttyS0)

with the .fdi config, I now get stylus and erasor showing up in wacomcpl

---

### Post by Favux on 2010-01-20
Hi dvalphen,

OK, you guys have just about convinced me that using PNP0501 is the way to go.  At least until we find it interfering with some other serial device.

Is the stylus working correctly for you?  At this point I'm leaning more to it being a problem with the linuxwacom drivers.  It's too bad we don't have anyone using a serial tablet all along with each release so we can pin down in which version of linuxwacom things went wrong.  That would make figuring it out a lot "easier".

---

### Post by p0rg1 on 2010-01-20
> **Favux said:**
> Hi dvalphen,

OK, you guys have just about convinced me that using PNP0501 is the way to go.  At least until we find it interfering with some other serial device.

Is the stylus working correctly for you?  At this point I'm leaning more to it being a problem with the linuxwacom drivers.  It's too bad we don't have anyone using a serial tablet all along with each release so we can pin down in which version of linuxwacom things went wrong.  That would make figuring it out a lot "easier".

I used my serial Intuos GD-0405-R in Ubuntu 8.10 and I'm fairly certain that I had it working in Ubuntu 9.04 if that is any help. This was when using the drivers from the repo. I just started looking into getting it to work in Ubuntu 9.10, so I found the posts above very interesting.

---

### Post by janjan7777 on 2010-01-26
Dear Favux,
in response to #83/#84, here are the files for an almost empty xorg.log and the fdi from 15.1.2010 (fdi and xorg.conf attached). With this configuration, the tablet is not working at all:

---

### Post by janjan7777 on 2010-01-26
...and here the version with populated xorg.conf, behaviour still the same.

Thanks and best regards,
Jan

---

### Post by janjan7777 on 2010-01-26
Seems that also Windows users are experiencing this problem, see e.g., [http://blog.lesc.se/2009/10/fixing-lagdelay-problem-for-wacom.html](http://blog.lesc.se/2009/10/fixing-lagdelay-problem-for-wacom.html)

---

### Post by Favux on 2010-01-28
Hi Jan,

Thanks for checking that out.  So for the .fdi I guess the easy way out is PNP0501 to get a 'platform' match.

Since you're using xorg.conf I assume you have setserial installed and a serial line in serial.conf in /etc/.  What does it look like?

Can you tell me what the output of:
```
setserial -g /dev/ttyS*
```
and:
```
sudo stty -F /dev/ttyS0
```
looks like?

I'm interested in testing some changes to the serial.conf line among them  'spd_normal', 'skip_test', and esp. 'low_latency'.  That's because the default '^low_latency' is "optimized for efficient CPU processing of serial characters at the cost of paying an average of 5-10ms of latency before the characters are processed".  I'm wondering if that might be the lag, or part of it anyway.  While 'low_latency' doesn't have the latency but is more CPU intensive.

What do you think?  Are you interested in looking into that?

---

### Post by janjan7777 on 2010-01-29
Dear Favux,
I didn't have setserial installed.
Now I installed it, without rebooting, and it said
```

$ setserial -g /dev/ttyS*
/dev/ttyS0, UART: 16550A, Port: 0x03f8, IRQ: 4
/dev/ttyS1, UART: unknown, Port: 0x02f8, IRQ: 3
/dev/ttyS2, UART: unknown, Port: 0x03e8, IRQ: 4
/dev/ttyS3, UART: unknown, Port: 0x02e8, IRQ: 3

```and 

```

sudo stty -F /dev/ttyS0
speed 9600 baud; line = 0;
min = 1; time = 10;
-brkint -icrnl ixoff -imaxbel
-opost
-isig -icanon -iexten -echo

```There is no /etc/serial.conf

No change after a reboot.

---

### Post by Favux on 2010-01-29
Hi janjan7777,

Oh, OK.  Good information there.

So then try adding this line:
```
/dev/ttyS0 port 0x03f8 irq 4 autoconfig
```
to serial.conf.  To create the file and edit it use:
```
gksudo gedit /etc/serial.conf
```
Then try rebooting.

---

### Post by janjan7777 on 2010-01-29
OK, tried that. Still bad tablet behaviour.

```

$ sudo stty -F /dev/ttyS0
speed 9600 baud; line = 0;
min = 1; time = 10;
-brkint -icrnl ixoff -imaxbel
-opost
-isig -icanon -iexten -echo

```

---

### Post by Favux on 2010-01-29
Hi jan,

Just can't make it easy for us, can they?

OK, try adding 'uart 16550A' like:
```
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 autoconfig
```
and reboot and see if it makes a difference.  And then also see if removing 'autoconfig' makes a difference.  I don't know for sure if doing that means we have to add anything else in like a 'baud_base'.

Then try adding the other options I mentioned above one at a time so it ends up looking like:
```
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 spd_normal skip_test low_latency
```
I hope we get lucky.

---

### Post by janjan7777 on 2010-01-29
No luck, unfortunately :(
Tried all of the above except for baud_base. stty output is unchanged.
I tried baud_base from a virtual console (with setserial and all the other parameters), then there was no reaction from the tablet any more.

---

### Post by Favux on 2010-01-29
Hi jan,

Thank you very much for looking into that!

With baud_base you'd have to specify what it is, something like:
```
/dev/ttyS0 uart 16550A port 0x03f8 irq 4 baud_base 115200 spd_normal skip_test low_latency
```
It's possible fooling around with the parameters might work if you found just the right ones.  For example is it possible that we want another UART other than 16550A, etc.

This is all from (in a terminal):
```
man setserial
```
and
```
man stty
```


**[SIZE="4"]So what have we learned?[/SIZE]**
I think we've looked at just about everything now and we are back to the original bug report:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/365997)
For the reporter the change happened going from Intrepid to Jaunty.  That would be linuxwacom 0.8.1-4 to 0.8.2-2.  But from what ninevoltz is saying it's more a problem with linuxwacom not being made totally compatible with the new Xserver.  The change happening between Xserver 1.5.2 (Intrepid) and 1.6.2 (Jaunty).

I've tried looking at the diff's for those versions and the others in between and up to 0.8.4-4.  Nothing leapt out at me as a change (obvious error like a dropped line etc.) in serial stuff.  But I could have easily missed something.  I especially concentrated on 1.0.8.3-2  because it was the first version to support Xserver 1.6.  The Ubuntu version of linuxwacom 0.8.2-2 was specially patched to support Xserver 1.6 and HAL.  That may be why I'm not seeing the problem.  If new code is needed in linuxwacom to support old serial tablets on Xservers above 1.5.2 I'd be clueless.

We know they took the module 8250_pnp.ko directly into the kernel in Intrepid so that may or may not have anything to do with it.

And serial tablets got worse with Karmic (Xserver 1.6.4).

So while we haven't ruled out a problem with Ubuntu and serial devices or a bug in linuxwacom it does seem to lean to being a linuxwacom problem in that **linuxwacom doesn't totally support old serial devices with Xservers 1.6 or higher** (or possibly 1.5.2 and higher).

I don't know if this will be fixed in Lucid where they are moving the Xserver part of linuxwacom to Xorg's xf86-input-wacom, the X11 input driver for X Servers 1.7 and later (X11R7.5).

**[SIZE="4"]Conclusion[/SIZE]**
Time may be running out since Lucid is due in 3 months.  You folks should get together and post on the bug report.  I'd also search launchpad and post on similar bug reports or start a new one.

I'd also post on [linuxwacom-discuss]("https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss") and also post a bug report on the bug tracker:  [http://sourceforge.net/projects/linuxwacom/](http://sourceforge.net/projects/linuxwacom/)  For example this bug report should sound familiar:  [http://sourceforge.net/tracker/?func=detail&aid=2934383&group_id=69596&atid=525124](http://sourceforge.net/tracker/?func=detail&aid=2934383&group_id=69596&atid=525124)  You could join in on that one.

Since there are new dev.s working on the merger/synching of Xserver part, which is what serial tablets use, this is a real chance to get some attention and get it fixed.

**[SIZE="4"]Edit (1-31-10)[/SIZE]**:  It looks like the plan is for linuxwacom 0.8.5-10 to be put out in about a week and then 0.8.6 (the next Production version) in about a week after that.  So **[SIZE="3"]our window is narrowing to get this fixed[/SIZE]**.  I added a comment to Wolfgang's LWP bug report at SourceForge.  It would help if some more of you added comments too.

---

### Post by Favux on 2010-01-30
**[SIZE="4"]Additional Information:[/SIZE]**
To see what I am talking about with the 8250_pnp.ko see this patch for the new version of 8250_pnp.c proposed to deal with Xserver 1.7
> From: Matthew Garrett <mjg@redhat.com>
Date: Thu, 7 Jan 2010 16:30:08 -0800
Subject: [PATCH 2/2] 8250_pnp: Use wildcard for serial Wacom tablets

 Wacom claims that the WACF namespace will always be devoted to
 serial Wacom tablets. Remove the existing entries and add a
 wildcard to avoid having to update the kernel every time they
 add a new device.

Signed-off-by: Matthew Garrett <mjg@redhat.com>
Tested-by: Ping Cheng <pingc@wacom.com>
Signed-off-by: Ping Cheng <pingc@wacom.com>
---
 drivers/serial/8250_pnp.c |   10 +---------
 1 files changed, 1 insertions(+), 9 deletions(-)

diff --git a/drivers/serial/8250_pnp.c b/drivers/serial/8250_pnp.c
index b5496a1..cbe17c8 100644
- Hide quoted text -
--- a/drivers/serial/8250_pnp.c
+++ b/drivers/serial/8250_pnp.c
@@ -328,15 +328,7 @@ static const struct pnp_device_id pnp_dev_table[] = {
      /* U.S. Robotics 56K Voice INT PnP*/
      {       "USR9190",              0       },
      /* Wacom tablets */
-       {       "WACF004",              0       },
-       {       "WACF005",              0       },
-       {       "WACF006",              0       },
-       {       "WACF007",              0       },
-       {       "WACF008",              0       },
-       {       "WACF009",              0       },
-       {       "WACF00A",              0       },
-       {       "WACF00B",              0       },
-       {       "WACF00C",              0       },
+       {       "WACFXXX",              0 },
      /* Compaq touchscreen */
      {       "FPI2002",              0 },
      /* Fujitsu Stylistic touchscreens */
So you see there could be a problem if your serial device was left off or an error garbled it.  Of course if your tablet doesn't have/use a PNP identifier this wouldn't matter.  Then it probably is dealt with the linuxwacom driver which I think applies to most of the older serial tablets we've been looking at.

---

