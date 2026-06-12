---
title: "PS/2-&gt;USB Adesso Cirque Touchpad works, straight USB does not"
date: 2011-07-13
forum: Hardware
---

### Post by robertbub on 2011-07-13
I'm having an odd problem.

When I plug in my PS2 Cirque Touchpad into a USB converter into my laptop, everything works.  But, if I plug in my Adesso Cirque Touchpad USB directly into laptop, it does not work -- the cursor does not move nor do the button click.

The laptop's touchpad (a synaptics-based one) continues to work fine in both cases.

The mouse seems to be recognized just fine:> $ xinput list|grep -i touchpad
â   â³ Cirque Corporation 9925 AG Touchpad      id=11   [slave  pointer  (2)]
â   â³ SynPS/2 Synaptics TouchPad               id=14   [slave  pointer  (2)]For both the PS/2 version and the USB version, "xinput list-props" reveals that the device is considered to be an "evdev".  It also shows up in gpointing-device-settings.

One unusual thing is that I notice this in the syslog:> Jul 13 07:07:07 kernel: [ 1201.052491] usb 2-1.2: reset full speed USB device using ehci_hcd and address 6several times a second.

Is there any way to get this USB-based touchpad working?

I'm running Lucid Lynx.  FWIW, this also seems to affect the Linux Mint Debian Edition.

---

### Post by robertbub on 2011-07-14
Two things.[LIST=1]
[*]**Windows**.  It turns out that this external touchpad works fine in Windows (Win7).
[*]**Model**.  It looks like there are two models of USB versions of this touchpad.  More below.
[/LIST]There are 2 models of this Glidepoint touchpad: 160U and 160UB.  I managed to get my hands on the 160U version (an older version) and it works fine, including the side scrolling (scrollwheel simulation).  The 160UB apparently doesn't work at all.

By the way, the touchpad is identified differently:> â   â³ Cirque Corporation USB GlidePoint        id=11   [slave  pointer  (2)]

I speculate that there is a bug in latest kernels (my Ubuntu is running 2.6.32 and my Linux Mint is running 2.6.39) that cannot handle the high-speed 3.0 USB interface.  I hope this is fixed in future versions so other people will have access to this alternative mouse/assistive technology for accessibility.

---

### Post by dmrparthenon on 2011-10-10
Linux supports usb 3.0 since 2.6.31. Perhaps it is buggy, but other issues should be ruled out first.

I have the same issue as you: I'm using a cirque easycat 160 ub usb touchpad. It appears to be recognized (e.g. in xinput -list), but does absolutely nothing. I also get the same continual usb reset messages in my dmesg. 

Does anyone know how to tell if the correct drivers are loaded into the kernel?

I'm on Natty Narwhal.

---

### Post by dmrparthenon on 2011-10-10
By the way, why is this marked SOLVED?

---

### Post by t_at_cirque on 2011-12-22
Robertbub & Dmrparthenon,
I am a representative of Cirque and have sent you both private messages to further explore the issue you are experiencing.  

If you have questions for me directly, please respond via PM when you have a moment.

---

