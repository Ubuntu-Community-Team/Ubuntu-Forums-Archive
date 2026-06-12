---
title: "HP 510 laptop touchpad not working."
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by LPomfrey on 2007-02-27
The touchpad on my HP 510 laptop is refusing to work. The Synaptics touchpad input device lines in xorg.conf are there so I'm assuming it's being detected, however it's not working at all (no cursor movement and clicking isn't doing anything.)

I've tried disabling ACPI and APCI on boot (which managed to disable the wireless but not get the touchpad working), have tried using Ubuntu 6.06 and 6.10 (Live CDs), and have tried commenting out the "wacom" tablet entries in xorg.conf, all to no avail.

Does anyone know how to get this working? :confused:

---

### Post by trashmatic on 2007-03-16
Sorry to come to your post so late, hope you still read this.

Your best bet, by far, is to just install and update Feisty.  It's not a stable release yet, but the very latest kernel and packages make everything work out of the box.  At least, it seems that way to me.

This laptop with 6.10, however, was painful.  There are instructions at hp500.xf.cz for getting the touchpad to work.  It is possible that you could still run 6.10 and just pull the kernel image from Feisty, but I'm not sure how exactly to do it.

---

### Post by DiThi on 2007-03-28
It doesn't work on feisty!

What I should do to help make it work before feisty release?

It also don't autodetect the resolution automatically, and I can't set it manually. It's 1280x800 while it sets 1024x768 at best :(

HP 510 is so unsupported... I can't find any information about this touchpad

---

### Post by DiThi on 2007-03-28
Hey, I followed that page [http://hp500.xf.cz/](http://hp500.xf.cz/) and I got the correct resolution. I compiled the kernel and I got the touchpad working! buuut, wifi doesn't work!

This should be fixed before feisty final release!

For those who want the touch pad in HP 5xx but not wifi, here's the kernel I compiled:

[http://pixelements.es/files/linux-image-2.6.20.3-ubuntu1_hp500.1.0_i386.deb](http://pixelements.es/files/linux-image-2.6.20.3-ubuntu1_hp500.1.0_i386.deb)

It's still uploading while I'm writing this, will be complete in 1:55 hrs. I don't know why, but it's 218.7mb big!

---

### Post by dobrichkia on 2007-03-30
I by HP 510 notebook. Install ubuntu linux. 
After install:
echo mem > /sys/power/state
laptop go to suspend, all ok
but where push button Power, laptop broken (freeze), don't wont resume.
Pls help, i one month reads forums, but :(.

---

### Post by alpr on 2007-04-20
> **trashmatic said:**
> Sorry to come to your post so late, hope you still read this.

Your best bet, by far, is to just install and update Feisty.  It's not a stable release yet, but the very latest kernel and packages make everything work out of the box.  At least, it seems that way to me.

This laptop with 6.10, however, was painful.  There are instructions at hp500.xf.cz for getting the touchpad to work.  It is possible that you could still run 6.10 and just pull the kernel image from Feisty, but I'm not sure how exactly to do it.

hey mates,
I am at the same issue at the moment. After Feisty Fawn has been lately released and I knew the problems with this notebook on edgy i thought "hey let's give it a try, maybe it works now with the new version" yea... but it unfortunately didn't. neither the screen resolution was adjustable nor the touchpad worked. i followed the steps shown at [www.hp500xf.cz](www.hp500xf.cz) and was able to make at least the monitor work properly. but there was no chance to configure the kernel, because of changes in it which came with feisty.

what shall i do next?

would be grateful for any kind of help!

---

### Post by Vargster on 2007-06-06
The lastest kernel upgrade dated June 3rd seems to have fixed this  problem in Fiesty.

---

### Post by Nonno Bassotto on 2007-06-13
To have the correct resolution I just had to install

xserver-xorg-video-intel

and it recognized the correct resolution without further tweaking (just had to restart X). Don't know about the touchpad: I used Feisty live cd, so I couldn't try the new kernel (i'd have to restart and then I'd lose the changes). As soon as I install it, I will give you feedback.

The wireless was working out of the box (but not the network-manager applet).

---

### Post by sanju123 on 2008-07-17
Go to Synaptic pointing device
Right click on icon
on "tap to click"

It may help you

cheers

Santju

---

