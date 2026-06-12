---
title: "Graphire4 Wacom Tablet in Ubuntu 9.04"
date: 2009-09-07
forum: Hardware
---

### Post by Rogue Yun on 2009-09-07
Hello all, new guy here.  So I might need some step by step instructions.

I'm trying to get a Graphire4 on Ubuntu Jaunty to work.

Though the light comes on when I plug it in I can't seem to use the pen to move the cursor on the screen.

I've tried a bunch of things, but if you were to ask me what I tried I couldn't explain it back to you.

Any ideas?

Thanks in advance!

Craig

---

### Post by Favux on 2009-09-07
Hi Rogue Yun,

Not sure what's going on, you should be at least getting the stylus in Jaunty.

I'm assuming your Graphire4 is a usb tablet?  Sometimes the wacom.ko (the usb kernel driver/module) doesn't "kick" in on some systems.  You should see wacom stuff if you enter in a terminal:
```
dmesg | grep [Ww]acom
```

If not a fix is to add "wacom" (without the quotes) to the end of the 'modules' file in "/etc/".  In other words:
```
gksudo gedit /etc/modules
```
add "wacom" and reboot.  Now dmesg should show wacom stuff and your stylus should be active.

You might want to take a look at post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)  Just make sure both 0.8.2-2 linuxwacom Jaunty packages are installed in Synaptic Package Manager.

Hope this helps.

---

### Post by Rogue Yun on 2009-09-15
Hallo Favux,

It is indeed a usb tablet, my friend still has my mouse to it so I can't check that.

So this is what I got...

```
craig@craig-laptop:~$ dmesg | grep [Ww]acom
[13197.052554] input: Wacom Graphire4 4x5 as /devices/pci0000:00/0000:00:1d.2/usb7/7-1/7-1:1.0/input/input9
[13197.118145] usbcore: registered new interface driver wacom
[13197.118153] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```

So there appears to be wacom stuff I guess.  Any ideas on what I should do?

Thanks in Advance!

---

### Post by Favux on 2009-09-15
Hi Rogue Yun,

Well the dmesg output shows that a usb connection (through wacom.ko) is established with your tablet.  The stylus should be working.

So check in Synaptic Package Manager that both xserver-xorg-input-wacom & wacom-tools are installed.  If not tell it to install them and reboot.  If they are there tell it to reinstall them and reboot.  It kind of looks like your wacom.rules in udev are't there and this should fix that.  This is assuming you didn't try to install linuxwacom some other way.

---

### Post by Rogue Yun on 2009-09-15
Thanks for the quick reply,

So, I did as you asked, found that they were already installed.  I reinstalled and rebooted.

Still no luck.

Checked for the wacom.rules and only found "40-xserver-xorg-input-wacom.rules" in the directory /lib64/udev/rules.d

Thanks for your help, do you have any other ideas?  I'm wondering if my stylus (if that is what the pen is called) died on me.

---

### Post by Favux on 2009-09-15
Hi Rogue Yun,

That could be.  The stylus tip could be broken.  Do you have a windows partition or another computer you could test it on?  Or maybe see if your Wacom mouse works?

---

### Post by Rogue Yun on 2009-09-15
I think we've come to a knowledge of the problem.

I dusted off my old windows partition and it didn't work in there either.

I guess I'll have to get a new stylus.

Thank you so much Favux, I had forgotten about checking it out on my windows partition (which, when you are trying to get away from windows, might be a good thing).

Now... How do I show that my problem was solved?

---

### Post by Favux on 2009-09-15
Hi Rogue Yun,

You're welcome.

Sorry about the broken stylus.

It's in Thread tools above your first post.

---

