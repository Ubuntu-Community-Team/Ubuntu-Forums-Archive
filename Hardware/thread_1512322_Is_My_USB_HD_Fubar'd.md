---
title: "Is My USB HD Fubar'd?"
date: 2010-06-18
forum: Hardware
---

### Post by ve4cib on 2010-06-18
I have a 120GB Western Digital USB HD formatted to a single FAT-32 partition that's been working very well for a few years, and has suddenly stopped working.

Nautilus does not detect the drive when I plug it in, gparted does not list /dev/sdb when I refresh the list of devices, and I get the following errors in dmesg:

```
$ dmesg
[  975.205106] usb 2-1: new full speed USB device using ohci_hcd and address 11
[  975.396108] usb 2-1: device descriptor read/64, error -62
[  975.689531] usb 2-1: device descriptor read/64, error -62
[  975.968147] usb 2-1: new full speed USB device using ohci_hcd and address 12
[  976.172175] usb 2-1: device descriptor read/64, error -62
[  976.445102] usb 2-1: device descriptor read/64, error -62
[  976.728715] usb 2-1: new full speed USB device using ohci_hcd and address 13
[  977.137038] usb 2-1: device not accepting address 13, error -62
[  977.325047] usb 2-1: new full speed USB device using ohci_hcd and address 14
[  977.747395] usb 2-1: device not accepting address 14, error -62
[  977.747418] hub 2-0:1.0: unable to enumerate USB device on port 1

```

This all started when I picked up my laptop, not realizing the drive was still connected & mounted (but not actively reading/writing).  The USB cable pulled out of the drive, and it landed on the desk after a fall of some six inches.

Is the HD itself recoverable, or should I just open it up, smash the platters, and throw it away?  I've never run into a problem with a USB HD like this before; I've had to reformat the drive, but I can't even do that.

I also tried plugging the device into a WinXP box, thinking that maybe since it's a Windows format it might have better luck.  Windows reported the USB device as "defective, and should be replaced."

I have several gigs of backups on the drive, so I'd like to recover the data if at all possible.  Does anyone have any suggestions on how to proceed?  Any and all help is greatly appreciated!

---

### Post by wilee-nilee on 2010-06-18
If you look at dcstar's posts they suggested a code to erase a specific file on a computer that had been dropped and the HD was not working. I suspect the HD is not borked it's just how much do you want whats on it and how long will you wait or work on trying to find a answer. I wish I could be of more help.

---

### Post by ve4cib on 2010-06-18
> **wilee-nilee said:**
> If you look at dcstar's posts they suggested a code to erase a specific file on a computer that had been dropped and the HD was not working. I suspect the HD is not borked it's just how much do you want whats on it and how long will you wait or work on trying to find a answer. I wish I could be of more help.

Do you have any links to the relevant posts?

This file that might have been dropped, it's on the HD, right?  Because I've tried the drive in three different computers now (the original 9.04 box that caused the problem, the XP machine, and a fresh 10.04 machine) and they all fail to detect the HD as anything other than a broken USB device.

---

### Post by wilee-nilee on 2010-06-18
> **ve4cib said:**
> Do you have any links to the relevant posts?

This file that might have been dropped, it's on the HD, right?  Because I've tried the drive in three different computers now (the original 9.04 box that caused the problem, the XP machine, and a fresh 10.04 machine) and they all fail to detect the HD as anything other than a broken USB device.

I didn't save the link as it was a unusual method that I would be hesitant, being that I didn't really understand, why this worked, and it was on the actual computer rather then a external. It was within the last 48 hours though that I saw this fix. I like the fractal avatar.

---

### Post by ve4cib on 2010-06-18
Ah, okay.  It definitely looks to be a problem with the drive itself, not with the computer.  I'll maybe see if I can crack the case open and make sure the USB connector pins didn't break in the fall.  Thanks for the idea anyway though.

And I'm glad you like the avatar.  I had to write  a program to generate julia and mandelbrot sets for a course I took in university (advanced analysis and design of algorithms).  The picture is the result of that program.

---

### Post by wilee-nilee on 2010-06-18
> **ve4cib said:**
> Ah, okay.  It definitely looks to be a problem with the drive itself, not with the computer.  I'll maybe see if I can crack the case open and make sure the USB connector pins didn't break in the fall.  Thanks for the idea anyway though.

And I'm glad you like the avatar.  I had to write  a program to generate julia and mandelbrot sets for a course I took in university (advanced analysis and design of algorithms).  The picture is the result of that program.

There are fractal programs in synaptic that are pretty cool. That is a good feat though in being able to write you own, I only know some basic commands to run a computer, no language or script abilities.

---

