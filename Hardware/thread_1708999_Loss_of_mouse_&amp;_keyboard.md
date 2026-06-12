---
title: "Loss of mouse &amp; keyboard"
date: 2011-03-17
forum: Hardware
---

### Post by Mahngiel on 2011-03-17
*I've searched the boards well enough that I haven't found anything regarding this.  There have been posts about the inputs coming in and out, and mostly for laptops.*

I use Ubuntu 10.10, Studio Edition daily.  Most of my windows required work was done in a Vbox until I decided just to dual boot.  Naturally, the installation of Win7 wiped Grub and i had to reinstall it via LiveCD.  No problem.

However, once I log into buntu, I have no input devices.  My eth0 is working fine, but nothing else.  I have full keyboard and mouse use all the way into logging in.

Since I have no mouse/keyboard, I can't pull any error logs or messages.  I have tried un/replugging the devices in during my session, as well as all USB ports unplugged at restart and letting grub auto load my boot selection.

Suppose I could use the LiveCD to check the error logs, and while I do that, does anybody have any ideas to best this situation?

Thanks.

Things I've found:
lsusb
```

Bus 006 Device 005: ID 046d:c227 Logitech, Inc. G15 Refresh Keyboard
Bus 006 Device 004: ID 046d:c226 Logitech, Inc. G15 Refresh Keyboard
Bus 006 Device 003: ID 046d:c044 Logitech, Inc. LX3 Optical Mouse

```var/log/messages
```

Mar 17 14:44:31 studio kernel: [    1.952098] serio: i8042 KBD port at 0x60,0x64 irq 1
Mar 17 14:44:31 studio kernel: [    1.952154] mice: PS/2 mouse device common for all mice
...
Mar 17 14:50:58 studio kernel: [   31.796021] usb 2-1: new high speed USB device using ehci_hcd and address 3
Mar 17 14:51:28 studio kernel: [   62.340018] usb 2-1: new high speed USB device using ehci_hcd and address 4
Mar 17 14:51:39 studio kernel: [   72.860018] usb 2-1: new high speed USB device using ehci_hcd and address 5
```
the message log is showing me that the kernel knws the device is there, and what it is. So why do they keyboard and mouse not work?

---

### Post by dabl on 2011-03-17
If you can choose "Recovery Mode" from the boot menu, choose "Drop to Root Prompt" from the recovery menu, and if it takes you to the CLI and you have keyboard functionality, then that would indicate that the problem is entirely in the X settings.

So, do a shutdown/restart and this time, from the recovery menu, choose "Fix X".

Then shutdown/restart and try logging in to the greeter.

---

### Post by Mahngiel on 2011-03-18
Thanks for the reply dabl.  

I went into recovery mode, as you suggested.  As it opened up I had complete USB input failure.  It took a few seconds of desperately trying to use the keyboard to realize it wasn't working.  A few moments later, messages began popping up, which you can see in the attachment.   I used my phone to record the event so I could post back with the output.  Here is dialog (minus redundancies) that came up over 1:40 seconds:

```

usb 2-1: device descriptor read/64, error -110
usb 2-1: device not accepting address 4, error -110
usb 2-1: device not accepting address 5, error -110
hub z-0:1.0 unable to enumerate USB device on port 1
usb 5-1: device descriptor read/64, error -110
usb 5-1: device not accepting address 4, error -110
usb 5-1: device not accepting address 5, error -110
hub 5-0:1.0 unable to enumerate USB device on port 1

```

After the last "unable to enumerate", my keyboard lit up.  There was no entry for fix x, but there was failsafe X.  I chose to fix broken packages, and my system hung for 5 minutes trying to detect the battery. (This is a desktop).  Hard reboot ensued.

Back to livecd, i pulled the xorg.conf regarding the inputs:
```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
```

Any idea where to go from here?

---

### Post by dabl on 2011-03-18
I'm not enough of a USB engineer to know exactly what is wrong.  Clearly, the USB hardware is not playing nice.

Do you have access to another USB keyboard, that you could try?  Are you using a USB KVM switch, perchance?  If so, try plugging the keyboard directly into the computer's USB connector -- same for the mouse.

That's all I've got.

---

### Post by Mahngiel on 2011-03-18
Well, crazy update to divulge.  Following up on a tip off launchpad that others have had over the generations of *buntu related to mostly printers, I got my input functionality back.  I unplugged my SD card reader from the motherboard.  What a weird series of events, and I do not know how this was a sudden conflict.  Not sure if this should be a solved thread or not, either.

---

### Post by dabl on 2011-03-18
> **Mahngiel said:**
> 

 Not sure if this should be a solved thread or not, either.

Well, I guess that depends on your view of what constitutes "solved", eh?  :popcorn:

---

### Post by Mahngiel on 2011-03-18
Ha! Mayhaps it's a time for "Halp! My SD card reader ****s up my USB input devices  !!11!1".

---

