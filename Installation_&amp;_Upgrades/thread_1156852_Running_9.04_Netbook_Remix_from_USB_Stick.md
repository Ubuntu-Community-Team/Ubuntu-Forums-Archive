---
title: "Running 9.04 Netbook Remix from USB Stick"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by forumwurm on 2009-05-12
I have made a bootable stick according to this manual:

[https://help.ubuntu.com/community/Installation/FromImgFiles#Windows](https://help.ubuntu.com/community/Installation/FromImgFiles#Windows)

the gui didn't worked for me but it was easy with the command line tool.

Now I can start from the usb stick and i can install from the stick, but...

is it possible to work from the usb stick. so how can I install updates and additional software to the stick?

thanks for your help.

---

### Post by forumwurm on 2009-05-28
no ideas?

---

### Post by nickmcg on 2009-05-30
I'm looking to do something similar with the standard 9.04.

I used the usb startup creator, and, although it boots, every time I'm asked for language, and I boot into the live CD (equivalent)

---

### Post by forumwurm on 2009-06-14
nobody a solution for that

thx

---

### Post by dandnsmith on 2009-06-15
It's possible - I've done it.
There are a few points to note:
1. the img file for the remix, when installed by the recommended method(s), will occupy the whole of the usb stick.
2. if you try to install it to a partition on the stick, or recover unused space, you may have a bit of trouble (I did).
3. [pen drive linux](http://www.pendrivelinux.com/) has methods for a 'persistent install' to usb stick - but they only work for iso files.

What I did was to create the usb stick for the remix,
create a persistent install stick, analysing the method used,
duplicate the setup on a usb stick, paying attention to the way the syslinux boot is controlled, and putting on a casper-rw module.

It worked for a while, but then either the usb-stick had problems or the rw space was filled (but, according to me, it was less than half full).

You have to realise that, unless you do a proper, full install to usb stick, you will be limited to size and scope of 'updates', and they won't be updating in the true sense.

---

