---
title: "Tricky mouse problem"
date: 2007-12-27
forum: Hardware &amp; Laptops
---

### Post by BreathEasy on 2007-12-27
I have a Logitech MX510, which is one of those multi-button mice. Now, to get all the buttons to work properly, I had to edit my xorg.conf file and in the InputDevice section, I changed the lines

Driver          "mouse"
Option          "Device"        "/dev/input/mice"

to

Driver          "evdev"
Option          "Device"        "/dev/input/event3"

The mouse buttons work fine now, but the problem is that my keyboard has a scroll wheel on the left side, and after making the change, it no longer does anything anymore. Seems like the /dev/input/mice device monitored the actions of the scroll wheel, but by changing the InputDevice to event3 (ie. specifically the Logitech mouse), the actions are now ignored. I can always go back to using /dev/input/mice and both devices will work together, but then the extra buttons on the mouse will not function correctly anymore.

Is it possible to add an entry for the scroll wheel on the keyboard somehow, so both will work? I've tried various things, but nothing seems to work.

---

### Post by kidders on 2007-12-28
Hi there,

What you want to do *is* possible, but it can be a little tricky to walk someone through. Hopefully we'll get there!

/dev/input/mice and similar are sort of "catch-all" pointing device interfaces, which means all your mice (or mouse-like things) can be accessed through it. As you've noticed, the down-side is the generic, limited functionality you get from that approach. The event interface, on the other hand, is much more sophisticated, so you can get access to all sorts of device-specific functionality, but you have to deal with each device in isolation ... which I suppose is pretty obvious, in a way ... and is the reason your keyboard won't work properly.

Anyhow, from what you've posted, it looks like /dev/input/event3 points to your MX510. In your shoes, my first step would be to try to identify the event interface to your keyboard's "mouse" as well. In theory, you can then add an additional "InputDevice" section to your xorg.conf, hit CTRL+ALT+Backspace, and you're done.

In practice, there are two things that're going to make your life a little more complicated...[LIST]
[*]A tendency (which you may already have noticed) for /dev/input/event* to arbitrarily re-order themselves, combined with some long-standing quirks in the way Xorg handles these devices.
[*]The fact that your keyboard is part mouse, part keyboard may make it hard to keep track of which event interface is which.[/LIST]Anyhow, enough rambling. I'd suggest something like this...

**I - Try to figure out which event interface is which**

Take a look at the output of something like...```
find /dev/input/event* -exec udevinfo -a -n {} \; | less
```It should produce lots and lots of output like the following...```
  looking at device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/hci0/acl000A9540B1C1/input/input9/event7':
    KERNEL=="event7"
    SUBSYSTEM=="input"
    DRIVER==""
    ATTR{dev}=="13:71"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/hci0/acl000A9540B1C1/input/input9':
    KERNELS=="input9"
    SUBSYSTEMS=="input"
    DRIVERS==""
    ATTRS{modalias}=="input:b0005v05ACp0209e0110-e0,1,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,8C,8E,96,98,9E,9F,A1,A3,A4,A5,A6,AD,B0,B1,B2,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,raml0,1,2,3,4,sfw"
    ATTRS{uniq}=="00:0A:95:40:B1:C1"
    ATTRS{phys}=="00:10:60:D2:11:1D"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/hci0/acl000A9540B1C1/input':
    KERNELS=="input"
    SUBSYSTEMS==""
    DRIVERS==""

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/hci0/acl000A9540B1C1':
    KERNELS=="acl000A9540B1C1"
    SUBSYSTEMS=="bluetooth"
    DRIVERS==""
    ATTRS{address}=="00:0A:95:40:B1:C1"
    ATTRS{type}=="ACL"
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0/hci0':
    KERNELS=="hci0"
    SUBSYSTEMS=="bluetooth"
    DRIVERS==""
    ATTRS{sniff_min_interval}=="80"
    ATTRS{sniff_max_interval}=="800"
    ATTRS{idle_timeout}=="0"
    ATTRS{inquiry_cache}==""
    ATTRS{hci_revision}=="1958"
    ATTRS{hci_version}=="3"
    ATTRS{manufacturer}=="10"
    ATTRS{address}=="00:10:60:D2:11:1D"
    ATTRS{type}=="USB"
    ATTRS{uevent}==""

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3/2-3:1.0':
    KERNELS=="2-3:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="hci_usb"
    ATTRS{modalias}=="usb:v0A12p0001d1958dcE0dsc01dp01icE0isc01ip01"
    ATTRS{bInterfaceProtocol}=="01"
    ATTRS{bInterfaceSubClass}=="01"
    ATTRS{bInterfaceClass}=="e0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bInterfaceNumber}=="00"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2/2-3':
    KERNELS=="2-3"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="0"
    ATTRS{version}==" 2.00"
    ATTRS{devnum}=="4"
    ATTRS{busnum}=="2"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="01"
    ATTRS{bDeviceSubClass}=="01"
    ATTRS{bDeviceClass}=="e0"
    ATTRS{bcdDevice}=="1958"
    ATTRS{idProduct}=="0001"
    ATTRS{idVendor}=="0a12"
    ATTRS{bMaxPower}==" 90mA"
    ATTRS{bmAttributes}=="80"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 2"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:131"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{serial}=="0000:00:0b.0"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{manufacturer}=="Linux 2.6.23-gentoo-r2-kidders ohci_hcd"
    ATTRS{quirks}=="0x0"
    ATTRS{maxchild}=="8"
    ATTRS{version}==" 1.10"
    ATTRS{devnum}=="1"
    ATTRS{busnum}=="2"
    ATTRS{speed}=="12"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bcdDevice}=="0206"
    ATTRS{idProduct}=="0000"
    ATTRS{idVendor}=="0000"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{configuration}==""
    ATTRS{dev}=="189:128"

  looking at parent device '/devices/pci0000:00/0000:00:0b.0':
    KERNELS=="0000:00:0b.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{msi_bus}==""
    ATTRS{broken_parity_status}=="0"
    ATTRS{numa_node}=="-1"
    ATTRS{modalias}=="pci:v000010DEd0000026Dsv00001458sd00005004bc0Csc03i10"
    ATTRS{local_cpus}=="3"
    ATTRS{irq}=="23"
    ATTRS{class}=="0x0c0310"
    ATTRS{subsystem_device}=="0x5004"
    ATTRS{subsystem_vendor}=="0x1458"
    ATTRS{device}=="0x026d"
    ATTRS{vendor}=="0x10de"

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""
    ATTRS{uevent}==""
```This example (from my machine) is the udev device chain for my keyboard, which essentially goes [FONT=Courier New]input device -> bluetooth interface -> USB dongle -> USB hub[/FONT], right back to the PCI interface my USB controller is connected to. The udevinfo utility reveals a great deal of information (manufacturer codes for all your hardware, device capabilities, etc.), so you *should* be able to figure out which /dev/input/event[X] points to your keyboard's integrated pointing device.

**II - Try to get Xorg talking to it**

It's quite possible that adding your new "InputDevice" section will (a) have no effect whatsoever, (b) make your mouse/keyboard situation worse, or (c) break X altogether. It may take you a few attempts to get it right, so make sure you have a terminal-based text editor that you like installed, in case you need to tweak or undo changes to xorg.conf.

**III - Make your configuration more robust**

At this point, your input devices may be *working* ... but perhaps not quite the way you'd like them to. For instance, your keyboard's scroll wheel might be backwards, or X might be mistaking it for a pair of mouse buttons. If you've managed to get your MX510 to behave itself already, configuring the button mappings & so on should be a piece of cake for you though.

The next tweak has to do with what happens when you reboot, disconnect & reconnect your input devices, plug them into different USB ports, and so on. You may find that what used to be called /dev/input/event3 suddenly moves to, say, /dev/input/event7 for no reason. In theory, this shouldn't make the slightest difference, but in practice it can sometimes create problems, because of several odd glitches in the way Xorg manages input devices. If your keyboard or mouse stop working when you power off, swap USB ports & boot up again, I would suggest forcing udev to assign fixed /dev node names to them.

Anyhow, hopefully something in here is of some help.

---

### Post by BreathEasy on 2008-01-02
Wow; sorry for not responding sooner, but I didn't expect much of a response to the question, but I see you're a Gentoo user so I'm not surprised at the detailed response you gave. :)

Anyways, I'll do some investigating, but at least I've got something to go on. Thanks!

---

### Post by BreathEasy on 2008-01-02
OK, this is my progress so far.

I've deduced that my scroll wheel is linked to /dev/input/event2. From this, I added the following to xorg.conf:

```
Section "InputDevice"
	Identifier	"Keyboard Mouse"
Option "SendCoreEvents" "true"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event2"
EndSection

```
If I include the "CorePointer" option, it doesn't work or in certain cases, blocks out the main mouse. If I leave out the  "SendCoreEvents" option, it still doesn't register and in fact, blocks the multimedia keys on the keyboard from working at all.

I then had to add a **Inputdevice     "Keyboard Mouse"** line under the ServerLayout area, which I forgot to do previously which probably explains the failures before. Now the scroll wheel works, but I've noticed something unusual about the multimedia keys - before, I could press the Browser, Email, volume control and other keys and launch different things, which still works here (btw, I had to rebind all the multimedia key shortcuts for some reason, they had new event registers), but now, an event only seems to get triggered when I RELEASE the button. Before doing all this, I could press the mute button and the system would be muted immediately upon pressing. Now, I can hold it down as much as I like, but it will only mute once it detects a release. It's nothing that serious, but I'd like to know what's happened and how I can reverse this behavior if possible.

---

### Post by BreathEasy on 2008-01-02
Well that was enlightening. :)

Given the mouse and the keyboard's scroll wheel were both being controlled by "evdev" instead of whatever it was before, I decided to go all in and link up the keyboard as well:

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Option		"CoreKeyboard"
	Driver		"evdev"
	Option		"Device"	"/dev/input/event1"
EndSection
```

I still get the events upon release deal, BUT... the keyboard shortcuts program now shows things like XF86Mail instead of 0xac for example, which seems nice. Plus, before, I had a few extra multimedia keys which weren't being detected by the keyboard shortcuts app, but now they are, so I have even greater functionality now. Yay for evdev, whatever the heck it is. :)

EDIT: Well that's annoying. The super key (or "start" key in my case) is not responding. Not like I need it much, but it does mean things like the Shift Switcher Compiz Plugin aren't responding anymore. Weird thing, xev shows it reponding just fine. Damn Linux. :(

EDIT x2: I managed to get the Super keys to become detected again by going into the Keyboard menu option in Gnome, Layout Options, Alt/Win key behavior and enabling "Super is mapped to the Win-keys (default)." Was originally selected on the Default option, but obviously not when the keyboard changed over. Linux is ready for the desktop yo! :)

---

### Post by kidders on 2008-01-02
> **BreathEasy said:**
> I'm not surprised at the detailed response you gave.Lol... (I think!)

You've certainly been busy since I last checked in! It's important to read about xorg.conf before fiddling ... it saves all that annoying guesswork. At any rate, it sounds like you've gotten everything working. :-) In my opinion, Linux's input device management is far too flexible for its own good hehe.

Anyhow, once you're done tinkering with keyboard layouts, button mappings & so on, I would suggest putting your config files away in a safe place, so you never have to go through all this again. The same xorg/xmodmap/etc. configurations should work just fine on almost any other Linux distro you may use in the future, provided you keep the same hardware.

The other suggestion I would make is to consider adding a custom config file to /etc/udev/rules.d. Since you've explicitly addressed things like /dev/input/event1 in your xorg.conf, the configuration will be prone to failure, because the device numbers (event1, event2, ...) are essentially random. For example, I've manually glued my keyboard & mouse to /dev/input/event7, /dev/input/event8 & /dev/input/event9, making my xorg.conf immune to incidental changes in device detection order due to kernel updates, switching USB ports, changes to my BIOS configuration, and so on.

The alternative is to replace the explicit /dev paths with other identification information (vendor name, product description, etc.) ... but that end of Xorg is a little flaky, so I wouldn't be too enthusiastic about recommending it. Instead, you might like to take a quick look at [http://www.google.ie/search?q=udev+rules](http://www.google.ie/search?q=udev+rules). Just remember to create your own ruleset ... don't modify one of Ubuntu's.

**Edit:** Oh... You were wondering about evdev. It's just a driver. When you write [FONT=Courier New]Driver "kbd"[/FONT] or [FONT=Courier New]Driver "evdev"[/FONT] into an InputDevice section, you're selecting the device driver that'll be used to talk to your hardware, and what other configuration options you can/must use in that section. The difference is that drivers like "mouse" are very, *very* old, and don't try to accommodate features that aren't common to all input devices. Evdev is far more flexible, and is the only reasonable choice for anything more than your average $5 mouse.

---

### Post by BreathEasy on 2008-01-03
OK, I've come to the end of this current saga, lol.

Thing is, I have no problem keeping the main mouse and keyboard scroller bound to events in /dev/input, because they don't seem to change after many reboots. However, trying to run the keyboard using evdev causes massive problems, because it has a habit of not sticking to event1 like it should. You reboot, and it's moved to event2 and shifted everything else up by one - you fix it, reboot, and it's back to using event1. Or, you reboot, it's not using event1, you reboot without changing anything, it's still not using event1. Seems like once you touch it, it decides to change itself.

I experimented with the udev rules, but honestly, I couldn't justify the extra work involved. For one thing the rule didn't work after a reboot because the KERNELS value I used changed from 1-1 to 2-1. The only **tangible** thing I gain by running the keyboard off of evdev is two extra multimedia keys, but they're not dramatically important. I've also noticed that by using evdev, the keyboard has a significantly reduced delay before key repeating, and despite increasing the delay as far as I can go, it's still not comfortable. Ultimately it's more trouble than it's worth, so I've gone back to using the standard "kbd" and keep using events for the mouse and scroller, which appear extremely stable for now. If I use kbd, the keyboard remains as event1, keeping everything else in line.

Thanks majorly for your help once again. :popcorn:

EDIT: Only now do I discover the power of xmodmap. Coupled with xev I can now use the remaining multimedia keys that couldn't be set in Compiz. Using evdev for the keyboard would now be pointless.

---

### Post by kidders on 2008-01-03
Yep... I use "kbd" for my keyboard as well. Glad you sorted things out. :-)

---

