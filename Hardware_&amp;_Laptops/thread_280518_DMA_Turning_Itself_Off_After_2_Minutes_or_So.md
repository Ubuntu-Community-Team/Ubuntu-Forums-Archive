---
title: "DMA Turning Itself Off After 2 Minutes or So"
date: 2006-10-19
forum: Hardware &amp; Laptops
---

### Post by RankHypocrisy on 2006-10-19
I recently installed Dapper Server on an old Athlon Thunderbird 900Mhz box to use as a file server and Torrentflux box.  Everything went quite smoothly, and I got everything up and running with very little trouble.  As I was tweaking my setup, however, I noticed a problem.

I have 2 hard drives in the system:  a 40gb Maxtor on /dev/hda, and a 160gb Western Digital on /dev/hdc.  DMA is enabled in the bios, and it is enabled in the kernel.  After I boot the machine up, hdc has DMA automatically enabled.

Here is my issue -- DMA is not automatically enabled for hda at boot.  Furthermore, I cannot enable it on hda permanently.  When I type
```
sudo hdparm /dev/hda
```
it shows that DMA is off.  When I type 
```
sudo hdparm -d1 /dev/hda
```
it shows that it has enabled DMA.  When I then type
```
sudo hdparm /dev/hda
``` again, it shows that DMA is still enabled.

When I again type
```
sudo hdparm /dev/hda
```
it shows that DMA is still enabled.

But here is where it gets weird.  One of the next 2 times that I type
```
sudo hdparm /dev/hda
```

it will show that DMA is now off.  I can turn it back on, and it will (after less than 2 minutes) turn itself back off.  This is absolutely 100% repeatable and reproducible, and very, very odd.

Here is what I've tried so far --
1. Changed out the IDE cable.
2. Upgraded the kernel
3. Messed around with hdparm.conf so that DMA runs at boot.
4. Messed with the HD jumper settings (making sure it was Master and not Cable Select).

So far, no luck.  Does anyone have any ideas?  I'm about to give up and install another distro, but I would really like to stick with Ubuntu.

Thanks in advance.

---

### Post by RankHypocrisy on 2006-10-20
No one has any ideas?

---

### Post by ixus_123 on 2006-11-02
Still no joy for me after upgrading to Efty.

I'm linking to my thread so if anyone finds a solution ifn one it might be easier for people searching to find

[http://ubuntuforums.org/showthread.php?t=281046]("http://ubuntuforums.org/showthread.php?t=281046")

---

### Post by extole on 2008-03-30
In Gutsy I'm getting the exact same behavior. I'll post again when/if I figure it out.

---

### Post by extole on 2008-03-30
Well, I got mine working. I cracked open my case and changed the ide connection I was using from the one on the end of the cable to the one in the middle. Seemed to fix it.

Peace out -
extole

---

### Post by ixus_123 on 2008-07-03
Just revisiting this, mine was also a hardware error.

A water reservoir had leaked onto my DVD-ROM. not much water but it must have rotted something giving the very odd DMA errors

No more water near electricals.  I'm just glad that didn't start a fire or something

---

