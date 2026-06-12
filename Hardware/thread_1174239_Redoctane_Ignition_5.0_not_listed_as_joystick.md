---
title: "Redoctane Ignition 5.0 not listed as joystick"
date: 2009-05-30
forum: Hardware
---

### Post by ar1stotle on 2009-05-30
I know this has to do with DDR, but it could just be a general technical question, so bear with me.

OK, I just got a new DDR pad from redoctane (ignition 5.0). I play StepMania on my linux machine (which currently runs Ubuntu, but I also tried it on the Mint LiveCD to see if it made a difference, which it didn't). Basically, for my old DDR pads, I had a Super JoyBox 3 to convert the playstation 2 plug to USB, which worked fine, but it doesn't work with the new one. The new one, however, has its own USB plug. Thing is, when I plug it in, it's not recognized as a joystick input device like my other one was. Here's the system log for when I plug in both devices:

> May 30 21:07:28 mint kernel: [  930.188086] usb 4-1: new full speed USB device using uhci_hcd and address 4
May 30 21:07:29 mint kernel: [  930.376582] usb 4-1: configuration #1 chosen from 1 choice
May 30 21:07:29 mint kernel: [  930.385139] hub 4-1:1.0: USB hub found
May 30 21:07:29 mint kernel: [  930.387185] hub 4-1:1.0: 3 ports detected
May 30 21:07:29 mint kernel: [  930.678293] usb 4-1.1: new full speed USB device using uhci_hcd and address 5
May 30 21:07:29 mint kernel: [  930.794506] usb 4-1.1: configuration #1 chosen from 1 choice
May 30 21:07:29 mint kernel: [  930.801317] input: RedOctane USB Pad as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.1/4-1.1:1.0/input/input12
May 30 21:07:29 mint kernel: [  930.830836] input,hiddev96,hidraw1: USB HID v1.11 Joystick [RedOctane USB Pad] on usb-0000:00:1d.0-1.1
May 30 21:10:12 mint kernel: [ 1094.096210] usb 4-1: USB disconnect, address 4
May 30 21:10:12 mint kernel: [ 1094.096222] usb 4-1.1: USB disconnect, address 5
May 30 21:10:21 mint kernel: [ 1102.516168] usb 4-1: new low speed USB device using uhci_hcd and address 6
May 30 21:10:21 mint kernel: [ 1102.783504] usb 4-1: configuration #1 chosen from 1 choice
May 30 21:10:31 mint kernel: [ 1112.857296] usbhid: timeout initializing reports
May 30 21:10:31 mint kernel: [ 1112.859589] input: WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1:1.0/input/input13
May 30 21:10:31 mint kernel: [ 1112.884233] input,hidraw1: USB HID v1.00 Joystick [WiseGroup.,Ltd TigerGame PS/PS2 Game Controller Adapter] on usb-0000:00:1d.0-1

While I've done a bit of messing around with Linux distros, I don't know how to do some of the more technical things. It seems like it's able to recognize the RedOctane DDR Pad but it doesn't list it as an input device in /dev/input. The SuperJoybox 3 gets listed as js0. Any pros out there who can help me get this working? 
TIA!

---

### Post by ar1stotle on 2009-05-31
Or is there any way to make it load the same driver that it loads with the Super Joybox adapter? I just want it to be a valid input with all the keys mapped.

---

### Post by ar1stotle on 2009-06-02
No suggestions?

---

### Post by ar1stotle on 2009-06-14
Bringing this back 1 more time in case someone new is looking...

---

### Post by sfp-a7x on 2009-07-03
I recently bought an Ignition 5.0 and I'm having the same issue as you.  I think I made a bit of progress...

Note the following line in your dmesg output:  ```
May 30 21:07:29 mint kernel: [ 930.801317] input: RedOctane USB Pad as /devices/pci0000:00/0000:00:1d.0/usb4/4-1/4-1.1/4-1.1:1.0/input/input12
```  I believe that in your case, /dev/input/event12 corresponds to your dance pad.  Install the joystick package and run 'sudo evtest /dev/input/event12'.  When you step on the pad you'll see events.

Unfortunately, the next time you reboot or unplug/replug the pad, you might get a different eventXX device file.

This is as far as I've gotten.  If I run 'sudo jstest /dev/input/eventXX', I get the following:  ```
Driver version is 0.8.0.
Joystick (Unknown) has 2 axes and 2 buttons.
Testing ... (interrupt to exit)

jstest: error reading: Invalid argument
```

If I figure out a solution I'll post again.

---

### Post by sfp-a7x on 2009-07-04
It looks like the RedOctane Ignition 5.0 uses the same USB vendor ID and device ID as the Sony PS3 controller (054c:0268).  Unfortunately, it looks like the PS3 controller has a flaw so the generic HID driver doesn't support it -- there's a special driver for it instead (sony_hid).  I noticed that this special driver is automatically loaded when I plug in the dance pad.  I wonder if the special driver is incompatible with the Ignition 5.0?

Perhaps tomorrow I'll try recompiling the kernel after ripping out the special driver and restoring generic support.

---

### Post by sfp-a7x on 2009-07-04
No luck.  :(  Removing the hid_sony module and restoring generic support for this USB device made no difference.  I know that it's using the generic HID driver because there is no hid_sony module loaded and my dmesg output shows "generic-usb" where it used to say "sony":
```
[  696.515643] input: RedOctane USB Pad as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.0/input/input13
[  696.515703] generic-usb 0003:054C:0268.0007: input,hidraw4: USB HID v1.11 Joystick [RedOctane USB Pad] on usb-0000:00:1d.0-1.1/input0
```

I'm running kernel 2.6.31-1.14 from Karmic.

---

### Post by sfp-a7x on 2009-07-04
Partial success!

If I symlink /dev/input/js0 to the eventXX file (cd /dev/input && ln -s eventXX js0) then StepMania works.  jstest still doesn't work, however.  Also, I think that technically the eventXX files don't refer to joystick devices -- those have minor number 0-15.

So, I don't really understand what's going on, but I'm glad it works.

Now to figure out how to make udev automatically create js0 when I plug in the pad...

---

### Post by sfp-a7x on 2009-07-05
I learned a lot more about what is going on.  Apparently the joydev module by default will only load for input devices that report absolute axes events for a least one of the following axes: X axis, throttle axis, or wheel axis.  The RedOctane Ignition 5.0 dance pad does not report any axes events, so the joydev module is not loaded and it doesn't pay any attention to the device.

Here's how I learned this (remember that I'm running 2.6.31-1.14 from Karmic, so the following may be different if you're running a different kernel):  If you look at the output of "modinfo joydev" you'll see these lines:```
alias:          input:b*v*p*e*-e*3,*k*r*a*6,*m*l*s*f*w*
alias:          input:b*v*p*e*-e*3,*k*r*a*8,*m*l*s*f*w*
alias:          input:b*v*p*e*-e*3,*k*r*a*0,*m*l*s*f*w*
```  These lines tell depmod what aliases to put in /lib/modules/`uname -r`/modules.alias.  These aliases tell the kernel while module should be loaded when a device is detected.  See [http://wiki.archlinux.org/index.php/ModaliasPrimer](http://wiki.archlinux.org/index.php/ModaliasPrimer) for more information.

By looking at the kernel's input subsystem source code (drivers/input/input.c and include/linux/input.h), I discovered that the "e*3," part of the alias lines mean that it handles devices that report absolute axes events.  The  "a*0,", "a*6,", and "a*8," parts mean that it handles devices that have an X axis, a throttle axis, or a wheel axis (respectively).  This works for everything that fits the traditional definition of "joystick", and then some.

To see what the RedOctane pad reports, take a look at the output of the dmesg command after plugging in the pad.  You'll see a line like this:  ```
[31108.757023] input: RedOctane USB Pad as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.0/input/input17
```  That last part is a path in sysfs -- you can type "cd /sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.0/input/input17" to see some files that provide information about the device.  In there there's a file called modalias.  If you type "cat '/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.1/6-1.1:1.0/input/input17/modalias'" you'll see the following:```
input:b0003v054Cp0268e0111-e0,1,4,k120,121,122,123,124,125,126,127,128,129,ram4,lsfw
```  We can break the meaning of this string down:
[LIST=1]
[*]b0003:  bus type, 0x3=USB?
[*]v054C:  vendor ID 054C, which is Sony (the manufacturer of the chip in the dance pad's controller)
[*]p0268:  product ID 0268, Sony's ID for the controller chip in the dance pad
[*]e0111:  version, possibly the version of the HID spec the device follows (v1.11)?
[*]e0,1,4,:  this device reports 0x0=EV_SYN (synchronization), 0x1=EV_KEY (key/button), and 0x4=EV_MSC (miscellaneous) events, respectively (note that 0x3=EV_ABS is not present)
[*]k120,121,122,123,124,125,126,127,128,129,: this device reports key/button events for the following buttons:  0x120=BTN_TRIGGER, 0x121=BTN_THUMB, 0x122=BTN_THUMB2, 0x123=BTN_TOP, 0x124=BTN_TOP2, 0x125=BTN_PINKIE, 0x126=BTN_BASE, 0x127=BTN_BASE2, 0x128=BTN_BASE3, 0x129=BTN_BASE4 (respectively)
[*]ram4,lsfw:  other stuff that's not really relevant
[/LIST]

So the dance pad does not resemble what the joydev module expects, which is why no js0 device is created.  I think that the next step is to ask the kernel developers to expand joydev's definition of a joystick.  Unfortunately, I'm not sure how they'd do this -- the dance pad only reports key/button events, which makes it look an awful lot like a keyboard.  Maybe that's the answer -- treat it like a keyboard rather than a joystick.

---

### Post by sfp-a7x on 2009-07-05
I've created an ugly, hackish udev rule to make the RedOctane dance pad work for StepMania.

/etc/udev/rules.d/59-redoctane-ignition-5.0.rules:```
# hack to get the RedOctane Ignition 5.0 working in StepMania
# put this in /etc/udev/rules.d/59-redoctane-ignition-5.0.rules

ACTION!="add|change", GOTO="redoctane_ignition_5.0_end"
SUBSYSTEM!="input", GOTO="redoctane_ignition_5.0_end"
KERNEL=="input[0-9]*", GOTO="redoctane_ignition_5.0_end"

# if it's the dance pad:
#   * set ID_CLASS to "joystick" so that symlinks are created in
#     /dev/input/by-id and dev/input/by-path
#   * create a js0 link to appease StepMania
#   * set the permissions to read-only by everyone
ATTRS{modalias}=="input:b0003v054Cp0268e0111-e0,1,4,k120,121,122,123,124,125,126,127,128,129,ram4,lsfw", ENV{ID_CLASS}="joystick", SYMLINK+="input/js0", MODE="0444"

LABEL="redoctane_ignition_5.0_end"
```

This rule says that if an input device with the exact characteristics of the Ignition pad (no more, no less) is discovered, do the following:
[LIST]
[*]set the ID_CLASS variable to "joystick" (which causes symlinks to be created in /dev/input/by-id and /dev/input/by-path by rules in /lib/udev/rules.d/60-persistent-input.rules)
[*]create a symlink called /dev/input/js0 that points to the event device
[*]set the permissions of the event device so that everyone can read it
[/LIST]

Note that this is a hack.  The /dev/input/js0 file symlink should be replaced by a "real" joystick device created by the joydev device.

I hope this helps!

---

### Post by tanonev on 2009-07-10
Hi,

I tried following these instructions (adding in the rules.d hack), but I must have missed a step somewhere.

dmesg mentions the following about my pad:
```
[  746.405323] input: RedOctane USB Pad as /devices/pci0000:00/0000:00:1d.2/usb3/3-1/3-1.1/3-1.1:1.0/input/input12
[  746.420168] input,hidraw0: USB HID v1.11 Joystick [RedOctane USB Pad] on usb-0000:00:1d.2-1.1

```evtest on the appropriate event does reveal that the pad is responding, but it also contains a lot of the following messages:
```
Event: time 1247278440.418993, -------------- Report Sync ------------
Event: time 1247278440.420997, -------------- Report Sync ------------
Event: time 1247278440.422994, -------------- Report Sync ------------
Event: time 1247278440.424994, -------------- Report Sync ------------
Event: time 1247278440.426990, -------------- Report Sync ------------
Event: time 1247278440.428993, -------------- Report Sync ------------
Event: time 1247278440.431005, -------------- Report Sync ------------
Event: time 1247278440.432984, -------------- Report Sync ------------
Event: time 1247278440.434982, -------------- Report Sync ------------
Event: time 1247278440.436979, -------------- Report Sync ------------
Event: time 1247278440.438979, -------------- Report Sync ------------
Event: time 1247278440.440990, -------------- Report Sync ------------
Event: time 1247278440.442997, -------------- Report Sync ------------
Event: time 1247278440.444994, -------------- Report Sync ------------
Event: time 1247278440.447007, -------------- Report Sync ------------
Event: time 1247278440.448989, -------------- Report Sync ------------

```jstest returns the exact same input as mentioned in this thread.

StepMania DOES notice that there's a joystick, but on startup, it says the following:
```

Opened /dev/input/js0
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
/////////////////////////////////////////
WARNING: Unexpected packet (size -1 != 8) from joystick 2; disabled
/////////////////////////////////////////

```I don't believe I have any generic HID driver installed (nor have I figured out how to do so); am I suffering from driver problems that are causing my pad to spam additional bad input?  (I've tried this with a couple pads, and the pads work fine on a PS2 and on a friend's Mac, so I don't think it's the pad itself doing the misfiring.)

Thanks in advance :)

---

### Post by sfp-a7x on 2009-07-11
> **tanonev said:**
> evtest on the appropriate event does reveal that the pad is responding, but it also contains a lot of the following messages:
```
Event: time 1247278440.418993, -------------- Report Sync ------------
```I also see those messages after I step on or off the pad.  I think they're harmless.

> StepMania DOES notice that there's a joystick, but on startup, it says the following:
```

Opened /dev/input/js0
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX
/////////////////////////////////////////
WARNING: Unexpected packet (size -1 != 8) from joystick 2; disabled
/////////////////////////////////////////

```I find it odd that it says "from joystick 2".  Do you have other joystick-like devices in your system?  Perhaps a second non-Ignition 5.0 pad?  If so, that's probably the problem -- the ugly /etc/udev/rules.d hack may not be playing nice with your other joystick(s).

I should note that I'm running StepMania 3.9 -- if you're running a different version that could explain it.

> I don't believe I have any generic HID driver installed (nor have I figured out how to do so); am I suffering from driver problems that are causing my pad to spam additional bad input?  (I've tried this with a couple pads, and the pads work fine on a PS2 and on a friend's Mac, so I don't think it's the pad itself doing the misfiring.)

Both the generic HID driver and the special Sony PlayStation 3 controller driver are part of the Linux kernel, so you definitely have them installed.  Type 'lsmod | grep hid' in a terminal after plugging in the pad and you'll see usbhid (the standard HID driver) and hid_sony (the special Sony PlayStation 3 controller driver).  I doubt you're having any driver problems beyond the known problem of joydev not recognizing the Ignition 5.0 as a joystick.

---

### Post by tanonev on 2009-07-11
Thanks for the quick response :)

> **sfp-a7x said:**
> I also see those messages after I step on or off the pad.  I think they're harmless.

Those messages come up before I even touch the pad; as you can see from the timestamps, they fire some 500 times a second.  Does that happen on yours as well?

> I find it odd that it says "from joystick 2".  Do you have other joystick-like devices in your system?  Perhaps a second non-Ignition 5.0 pad?  If so, that's probably the problem -- the ugly /etc/udev/rules.d hack may not be playing nice with your other joystick(s).

The Ignition 5.0 pad was the only external device connected to my computer during testing.

> I should note that I'm running StepMania 3.9 -- if you're running a different version that could explain it.

Ahh, good to know...I'm running StepMania 4, so that might react differently.  I'm still suspicious about the evtest though, so I'd appreciate confirmation on whether I should really be seeing nothing but Report Sync messages.

> Both the generic HID driver and the special Sony PlayStation 3 controller driver are part of the Linux kernel, so you definitely have them installed.  Type 'lsmod | grep hid' in a terminal after plugging in the pad and you'll see usbhid (the standard HID driver) and hid_sony (the special Sony PlayStation 3 controller driver).  I doubt you're having any driver problems beyond the known problem of joydev not recognizing the Ignition 5.0 as a joystick.

I have usbhid but not hid_sony.  Do I need to install hid_sony?

---

### Post by sfp-a7x on 2009-07-11
> **tanonev said:**
> Those messages come up before I even touch the pad; as you can see from the timestamps, they fire some 500 times a second.  Does that happen on yours as well?
No, that doesn't happen to me.  Very interesting.

What kernel do you have installed (type 'uname -a' at a terminal to find out)?  My machine is a Jaunty machine, but I'm running the kernel from Karmic (2.6.31-2.16 generic) in order to work around an unrelated bug.  It could be that something changed in the drivers between the kernel you're using and the kernel I'm using.

> The Ignition 5.0 pad was the only external device connected to my computer during testing.
There goes my theory.  Try the following:  Reboot the computer without the pad plugged in.  Once it's up, get to a command prompt and see if there are any /dev/input/jsXX devices (type 'ls -l /dev/input/js*') or /dev/jsXX devices ('ls -l /dev/js*').  My guess is there won't be, but I wanted to make sure that your version of the joydev device driver isn't doing something different than mine.

> I have usbhid but not hid_sony.  Do I need to install hid_sony?
No, if you're running Jaunty it's already installed.  (If you type 'modinfo hid_sony' it will show you some basic information about the module.)

The hid_sony driver is new as of Jaunty, so if you don't have the hid_sony driver then I'm guessing you're running Intrepid or older.  If this is correct, you may want to try upgrading to Jaunty.

If you are running Jaunty, my guess is that your Ignition 5.0 has different internal hardware than my Ignition 5.0, which means the hid_sony device wouldn't be automatically loaded and wouldn't apply to you.  Type 'lsusb' in a terminal window and see if you have lines that look like these:```
Bus 006 Device 005: ID 054c:0268 Sony Corp. Batoh Device
Bus 006 Device 004: ID 22ba:0109 Technology Innovation Holdings, Ltd
```The bus and device numbers will probably be different, but the ID numbers should be the same.

---

### Post by tanonev on 2009-07-11
The pad is indeed the only js device; there are no js devices whatsoever on reboot, and all js devices go away after I unplug the pad.

I'm running Hardy, kernel version 2.6.24-24.  I have a clean install of Jaunty on another partition, but that install is incredibly wonky (and I can't get StepMania to work without falling back on software rendering, which is something of a dealbreaker).  I may try a reinstall of Jaunty, but I'm not too optimistic about it...

Is it possible to get hid_sony without upgrading to Jaunty?

---

### Post by sfp-a7x on 2009-07-11
> **tanonev said:**
> I'm running Hardy, kernel version 2.6.24-24.  I have a clean install of Jaunty on another partition, but that install is incredibly wonky (and I can't get StepMania to work without falling back on software rendering, which is something of a dealbreaker).  I may try a reinstall of Jaunty, but I'm not too optimistic about it...
Even though StepMania doesn't work as it should, boot into your Jaunty partition and try out the pad in evtest (don't forget the /etc/udev/rules.d hack).  If it behaves any better, try firing up StepMania and see if the pad works.  It would be nice to rule out the driver differences between Hardy and Jaunty.  If the pad works in Jaunty, then I guess the next step is to figure out how to fix Jaunty's wonkiness.

> Is it possible to get hid_sony without upgrading to Jaunty?
No.  hid_sony used to be integrated into the usbhid driver -- they separated it out for convenience (and possibly to fix some bugs).  So technically you already have the hid_sony driver, just an older version and integrated inside usbhid.

---

### Post by rsay on 2009-09-23
sfp-a7x,

Thanks for this post. I was able to use your hack to get my cobalt flux dance pad(Control box V5.0) working under Jaunty with StepMania 3.9. My device had a slightly different modalias:

```
input:b0003v054Cp0268e0111-e0,1,4,k120,121,122,123,124,125,126,127,128,129,12A,ram4,lsfw
```

(Note the extra ",12A" toward the end.) Otherwise, I used your code exactly.

---

### Post by rsay on 2009-09-27
As an update, I get the same error with Stepmania 4 on Jaunty and Karmic

```
WARNING: Unexpected packet (size -1 != 8) from joystick 2; disabled
```

I was able to get my dance pad working with stepmania 4 using the jkeys program to remap the dancepad buttons to keyboard letters. It did cause me to have a sound bug which was solved by running stepmania with pasuspender.

```
pasuspender ./stepmania
```

---

### Post by rsay on 2009-09-30
I now have my Cobalt Flux dancepad working in Stepmania 3.9,  Stepmania 4.0 and openitg beta2 on ubuntu64 jaunty and ubuntu karmic. Based on the great info in this thread and some other reading, I developed a different kind of workaround. (I don't think this is necessarily better, but it works for the newer stepmania versions.)

```
sudo rm 59-redoctane-ignition-5.0.rules
sudo apt-get install btnx
sudo btnx-config
```
You can immediately close btnx-config. It was just opened to create some blank configuration files.

Unplug your pad if it is plugged in
```
lsusb
```
Look and see what usb devices are already on your computer. Then, plug in the dancepad
```
lsusb
```
Look for the new device, it should be easy to pick out. Mine looked like this:
```
Bus 002 Device 007: ID 054c:0268 Sony Corp. Batoh Device
```

Find the new device. You need the numbers after ID: **054c:0268**
```

sudo gedit /etc/btnx/btnx_config_Default
```
fill in the vendor_id **054c** and product_id **0268** on the appropriate lines. (It doesn't matter if you use the leading 0x or not. 0x054c=054c) You can leave the other lines at their defaults.

This was my initial /etc/btnx/btnx_config_Default:
```

Mouse
vendor_id = 054c
product_id = 0268
revoco_mode = 0
revoco_btn = 3
revoco_up_scroll = 5
revoco_down_scroll = 5
EndMouse
```
Save the file, then restart btnx-config
```
sudo btnx-config
```
Now you can detect buttons and assign keys just like in the [[COLOR="DarkRed"]btnx manual[/COLOR]]("http://www.ollisalonen.com/btnx/man/btnx-manual.html#detecting-buttons")

After the buttons are all detected, go to the buttons tab and assign a key to each button.
I used Up, Down, Right, Left, Left_Bracket, Right_Bracket, ESC and ENTER so that my dancepad would also work as a mythtv controller. I didn't define the start or reset buttons because I don't use them. 
Click on "restart btnx" and close btnx-config. You should be in business.

```
cd ~/Stepmania-CVS
pasuspender ./stepmania
```

Configure the keys as usual under options.

---

### Post by ar1stotle on 2010-10-10
Just wanted to say thanks to all those who replied. I just thought of looking it up again because my old ddr pads finally gave out completely. I can vouch that the btnx solution works great. Thanks!

---

