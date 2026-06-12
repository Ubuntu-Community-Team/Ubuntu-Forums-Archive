---
title: "syba sata to ide dongle"
date: 2007-01-26
forum: Hardware &amp; Laptops
---

### Post by jdmux on 2007-01-26
Has anyone gotten the syba sata to ide dongle to work?
Part number appears to be SD-ADSAIDE-S1
Here is the newegg link
[http://www.newegg.com/Product/Product.asp?Item=N82E16822998001](http://www.newegg.com/Product/Product.asp?Item=N82E16822998001)

I connected it to one of the sata controllers on the mobo of
my Dell Dimension E521 and had no luck. I see now that I should try with
setting the drive to master. Let's see.

---

### Post by jdmux on 2007-01-27
Well, it works with one of my 3 drives. Now I have to try and figure out why
it doesn't work with the two. There is one for which it would be awful if the data
was lost on.

Why does Ubuntu take so long to boot when there is new hardware, or after
an unsuccessful boot with new hardware?

Can I "hot plug" an ide drive? The machine won't boot with the drive attached,
so after I boot it, can I expect that plugging in the drive will have a chance of
the drive being detected?

---

### Post by jdmux on 2007-01-27
Well, this appears to be diverging from the thread title, but I'll keep going anyhow.

I'm at the moment limited to having only 2 sata cables. So I've tried the following
two variations (again, I'm trying to boot with a drive attached via the sata to ide dongle
and get a look-see at what's on that PATA drive):

1) have drive with OS in sata0, take the sata1 controller which normally goes
to the CD and attach it to the syba sata to ide dongle.  In this case both drives
pass the bios hard drive test. However, when I attempt to boot, instead of going
to the grub menu, I just get a blinking underscore in the top left of the screen.

2) put sata1 back to the CD, move sata0 to the drive I'm trying to mount, and load
a 6.10 cd in the CD. I try to boot ubuntu from the CD, and after some time I get the
error:
Buffer I/O error on device sr0.

Can anyone shed any light on this?

Tomorrow I'll grab some more sata cables so I don't have to mess around with
that, but I'm really interested in learning if that hard disk is shot or not. I really
hope not.

Thanks.
jgw

---

### Post by jdmux on 2007-01-27
For one of the drives (the one with the important info on it!) setting
the jumper to chip select instead of master worked! I'm also booting
a gentoo livecd and mounting the separate drives to do data copy,
but I'm not sure that that is crucial. I'll reboot and see if ubuntu comes
up with the drive when it's in chip select.

---

### Post by jdmux on 2007-01-27
The chip select was the key for the remaining two drives. The fact
that I was booted through a gentoo livecd didn't make a difference.

Unfortunately my IDE DVD-RW didn't work with the dongle, so
I'll have to buy a new one.

Look for my add on ebay for 3 IDE drives and a DVD-RW! :D

---

