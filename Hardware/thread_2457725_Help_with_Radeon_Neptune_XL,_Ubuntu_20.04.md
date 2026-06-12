---
title: "Help with Radeon Neptune XL, Ubuntu 20.04"
date: 2021-02-07
forum: Hardware
---

### Post by frazeebd on 2021-02-07
Hello!  I am *brand *new to Ubuntu and linux.  I have loaded Ubuntu 20.04 onto an old Dell Alienware laptop I had sitting around.

This pc has hybrid graphics with an integrated GPU and a separate PCI Radeon card.  It is older, probably 3-4 years I think.

I'm trying some games on Steam, but they only launch with the integrated graphics.  If I try forcing the issue with DRI_PRIME=1 it gives a horrible pink and white speckled screen and just freezes up.  This occurs on multiple games.  Those same games work fine if I let them launch with the integrated GPU.

I'm not really sure what to do at this point.  Here are some basic things I got from the terminal on the matter: 

[https://paste.ubuntu.com/p/YcwgMFf2gY/](https://paste.ubuntu.com/p/YcwgMFf2gY/)

You can see that the open source radeon driver is selected, which... sounds right from what I know?  Not really sure, again I'm super new to Ubuntu.  In either case right now it seems like I cannot get that amd card to work with anything, even though it seems to be set up correctly.  I'm not sure perhaps if this is a particular version of the radeon card that just isn't supported?  Neptune XL is not on the wiki page for the open source radeon driver but then again those lists aren't always exhaustive.

I'm guessing at this point it is a lack of support for this particular card, but before I give up I may as well see what folks here think.  Thanks for reading!

---

### Post by Yellow Pasque on 2021-02-09
The Radeon 8970M/Neptune (which is basically a rebadge of 7970M) is part of the "Southern Islands" group of AMD GPU's. It is officially supported ( [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/) ). It's not guaranteed to be a bug free experience though.

If it was me, I would try using the newer amdgpu kernel module.  Boot with "radeon.si_support=0 amdgpu.si_support=1" kernel parameters.

---

### Post by frazeebd on 2021-02-11
> **Yellow Pasque said:**
> The Radeon 8970M/Neptune (which is basically a rebadge of 7970M) is part of the "Southern Islands" group of AMD GPU's. It is officially supported ( [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/) ). It's not guaranteed to be a bug free experience though.

If it was me, I would try using the newer amdgpu kernel module.  Boot with "radeon.si_support=0 amdgpu.si_support=1" kernel parameters.

Thank you so much for taking the time to reply!

I did a bunch of research on this since I am new to Linux.  I was able to update the grub file with the line above for si support.  I also ran a sudo update-grub and rebooted the machine.  The console does show that the amdgpu driver is now running.

Unfortunately, the problem persists.

Even if I try to just launch steam itself with dedicated graphics card, it fails to even properly launch the steam console.  Instead of the steam splash window, I just get a rectangular box in the middle of the screen that appears white with pink polka dots all over it.  The application freezes up at that point.  This is essentially the same result as when I tried to load a program with DRI_PRIME=1.

I also tried with the .cik support which as I understand is another version from a similar generation... that did the same thing.  I reverted to the amdgpu.si anyway, but it doesn't actually work regardless.

Everything works fine on the integrated graphics, there just isn't much horsepower.... but it indicates the problem is specific to the amd.  It may be a bad card or something, who knows.

If there are any other tricks anyone can think of I'd love to try it!

---

### Post by genukie on 2021-04-14
got it vrunning with radeon si and cik = 1 the gpu falls into category of picaired

---

