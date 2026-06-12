---
title: "Installing a backend? (parallel port scanner)"
date: 2006-11-04
forum: Hardware &amp; Laptops
---

### Post by Ryupower on 2006-11-04
Hi, I have a Plustek OpticPro 9630 scanner, I found out that I needed a special backend for this ( old parallel port )scanner. I downloaded it, opened up the package, and went like WOAH!! :eek: 
There were soooo many files in that thing!!! My question is: how do you install the module/backend? I couldn't find much useful information in the ( many ) files.

Anyone here able to tell me how to install a driver/module for a (parallel port) scanner? 
What's the file type I need and what do I need to do with it? 

I searched around the internet and couldn't find much. :(

---

### Post by edemark on 2006-11-09
in theory plustek backends come with sane already. You might try the following: edit the following file /etc/sane.d/dll.conf
there is line commented out with # called plustek_pp. So you have to remove # and then save the file. 
I hope it will work out for you

---

### Post by Ryupower on 2006-11-13
> **edemark said:**
> in theory plustek backends come with sane already. You might try the following: edit the following file /etc/sane.d/dll.conf
there is line commented out with # called plustek_pp. So you have to remove # and then save the file. 
I hope it will work out for you


Thank you very much! :)

---

### Post by thompa on 2007-02-02
HI there,

I have a similar problem... trying to make a Plustek 9630 work with Ubuntu.. but the fix didn't work for me. I tried to edit the file but it was protected and so I logged in as root and was able to do it there (removing the # infront of Plustek_pp).

Did you do anything else to get your scanner working?

Allan

---

### Post by Lazy_Warrior on 2007-02-02
Hi I'm trying to install a OpticPro 4830P (Yes it's a old scanner)
I've uncommented the plustek_pp, but xsane keeps getting my webcam as source, and I can't seem to change that.

Furthermore, in the plustek_pp.conf there is alink to the device:
[direct]
device parport0

I can't see any entry in /dev for parport0, is there something I'm missing?  (Yes I've connected the scanner, and put in the power cord :p )

Can I make XSane use another device than my webcam?
I've tried with
>xsane parport0
>xsane /dev/parport0

I hope someone can help me, and I think it might be related to the problem mentioned above.
Thanx in advance.
/Kristoffer

---

### Post by KaiO on 2007-02-03
Dunno if this is relevant, but:
I had trouble scanning with my multi function HP. Printing was ok, but scanner was "not found".
Found out through the forums that I had to have the /dev/parport0 node or the scanner was lost.
You can try:
sudo mknod -m 666 /dev/parport0 c 99 0
and see if the scanner is found.

Also see this thread for additional info:
[http://www.ubuntuforums.org/showthread.php?t=316233](http://www.ubuntuforums.org/showthread.php?t=316233)

---

### Post by Lazy_Warrior on 2007-02-03
Hey
Thank you for your tip. I found some extra information regarding adding the parport0 at
[http://www.murrayc.com/blog/permalink/2005/12/24/wheres-my-parport0/]("http://www.murrayc.com/blog/permalink/2005/12/24/wheres-my-parport0/")
> parport0 is created by the kernel-module ppdev.

“modprobe ppdev” should load it
if not you need to configure your kernel to use it and recompile.

then you do:

“mknod /dev/parport0 c 99 0 -m 666&#8243;
to create the devicenode if it’s not created on the fly avter the modprobe (if you have udev)

Not I have the parport, but xsane won't use it. How do I tell xsane to use the parallel port, and how can I tell that the scanner actually is found?

xsane /dev/parport0 gives an error - Could not open device '/dev/parport0' - Illegal arbument (it's translated from Danish, so the words may be a bit different from the actual text)

/Kristoffer

---

### Post by KaiO on 2007-02-03
What happens if you create the node
sudo mknod -m 666 /dev/parport0 c 99 0
and then run xsane without arguments? 
(no* /dev/parport0* )

---

### Post by Lazy_Warrior on 2007-02-05
xsane sais that "No device available" (translated from Danish, so the actual words may be a bit different).

I'm having no idea what might be wrong. The parrallel port is found (when loading the kernel module) but sane finds nothing. There should be a driver for the scanner in sane.

Is there a way to see whether the parallel port is working as it should? Just to check eerything step by step.

/Kristoffer

---

