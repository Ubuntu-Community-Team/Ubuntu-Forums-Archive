---
title: "Hardware hell ending up with an error in /etc/fstab"
date: 2006-12-20
forum: Hardware &amp; Laptops
---

### Post by finferflu on 2006-12-20
Hi all,
I've been having a very troublesome time with my friend's laptop. He's got an IBM Thinkpad A21m, Kubuntu Edgy installed.

I was trying to make the Netgear wireless card (WG111 v2) work, but it didn't want to know anything about it. In fact, after installing the proper drivers, I ran **sudo modprobe ndsiwrapper**, but I got an error:

```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
```

So, I went back on the forums looking for an answer, and I found, together with other ones, the possibility of installing an older version of ndiswrapper-utils. I tried other solutions first, without succes, so I was about to go for it. But, in the while time, I got some updates to do, I started Adept, and it stopped at 92%, while the hard disk was making strange noises (in regular intervals, it was like a loop), and I want to point out that this is a new hard disk that I had bought because the machine wouldn't start, the reason being connected always with the same noises. 

So the whole system froze, and I had to switch it off manually. When it was on again, I tried uninstalling ndiswrapper-utils, but I got the obvious error saying that dpkg had been interrupted, and I had to run **dpkg --configure -a**. Fine. I ran it, and nearly at the end, strange noises again, and nothing more going on. This time the system did not freeze, fortunately. 

So I thought it would have been wise to run **fsck**, but running it I get the following error:

```
WARNING: bad format on line 5 of /etc/fstab
```

This is the fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1
UUID=8ed4c1cf-0b53-4326-93dd-50f10fda63a1 /               ext3    defaults,errors=remount-ro 0       0
# /dev/hda5
UUID=2d34a710-de9d-408c-a9aa-d88ca064c6c7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

So I feel stuck here, not knowing what else I could possibly do.

Thanks for reading all this, and for your time!

---

### Post by po0f on 2006-12-20
finferflu,

Line 5 should be
```
[FONT="Courier New"]#/dev/hda1[/FONT]
```
not
```
[FONT="Courier New"]/dev/hda1[/FONT]
```

[EDIT]

And if you want to use the floppy, change:
```
[FONT="Courier New"]/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/FONT]
```
to:
```
[FONT="Courier New"]/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/FONT]
```
or if you don't care:
```
[FONT="Courier New"]#/dev/           /media/floppy0  auto    rw,user,noauto  0       0[/FONT]
```

---

### Post by finferflu on 2006-12-20
Thanks! I don't get that error anymore. 

Could you please point me out which flags would be more appropriate for my case to use with fsck, since the simple command fsck doesn't do anything?

Thanks a lot!

---

### Post by finferflu on 2006-12-26
Well, I'm still waiting for an answer, an my friend's laptop is still stuck, without the ability of using apt...

---

### Post by po0f on 2006-12-26
finferflu,

Change it to this:
```
[FONT="Courier New"]/dev/hda1
UUID=8ed4c1cf-0b53-4326-93dd-50f10fda63a1 /     ext3    defaults,errors=remount-ro 0   1[/FONT]
```
The '1' let's fsck know that if two drives need to be checked, check all the drives marked with 1 first, then the 2s.  For a desktop system, the root filesystem should be labeled 1 and all other partitions 2.

---

### Post by finferflu on 2006-12-26
So you mean that in that way I should be able to run fsck without flags?

Thanks!

---

### Post by finferflu on 2006-12-28
Ok, it looks like the problem is solved for now, I just let the hardisk click and make noises freely for about 20 min, running apt, and it worked. Now I can install stuff again! :D

---

