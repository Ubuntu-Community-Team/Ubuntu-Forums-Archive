---
title: "USB devices stop working"
date: 2007-02-27
forum: Hardware &amp; Laptops
---

### Post by McBraindk on 2007-02-27
Hi, I've just installed Ubuntu on my Toshiba Laptop.

All is working well, and Im absolutely flabbergasted by its usefullness.

So far paradise awaits.. But!

My USB devices seem to stop working approx. 10 mins after they have been plugged in.

The devices in question is a Logitech MX1000 mouse, a Logitch Cordless Pro Keyboard and my Brother printer.

I've tried following the guide to Logitech mice, but it seems gedit wont let me save?

I sincerely hope someone can help me with this issue (usb) because so far Ubuntu rocks.

Oh, and  by the way. In The ways of the almighty Linux  I am a complete beginner. So please respond in the most explainatory manner you can. 

Thank You

---

### Post by ziggykg on 2007-02-27
You mentioned that gedit doesn't let you save a file you were editing.  Try opening it using 'sudo' command (from a terminal window), like this:

```
sudo gedit /path/to/file
```

where '/path/to/file' is the full path to the file you want to edit.

---

### Post by dustman on 2007-02-27
I also have the same problem...my USB devices stop working. I have installed Ubuntu 6.10, and this problem is from this version of Ubuntu, because I had Ubuntu Dapper Drake, and my mouse worked fine there...:(

---

### Post by mvaranda on 2007-04-14
My Toshiba was working fine with 6.06 but USB started freezing after upgrading to 6.10.

The fix that worked for my machine was the following:

sudo gedit /boot/grub/menu.lst

change boot option (red):

kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash [COLOR="Red"]noapic irqpoll pci=routeirq[/COLOR]

I hope it helps.
Take care

---

### Post by dustman on 2007-04-16
Yeah, forgot to post here :D...I solved my problem about one month ago...and I added exactly those options in the boot menu, and it worked fine :)


Cheers!

Radu

---

### Post by laakkus on 2007-04-19
worked 4 me too!

although i used:

```
kernel  /boot/vmlinuz-2.6.17-11-generic root=/dev/hda3 ro quiet splash noapic pci=routeirq
```

---

### Post by dustman on 2007-04-19
I think the problem is solved by using just "noapic" option. Haven't tried it only with this option, but if it works, I'm not in the mood to make experiments :D

---

