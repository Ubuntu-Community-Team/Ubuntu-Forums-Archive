---
title: "&quot;Error 22: No Such Partition&quot; Despite Fix Attempts"
date: 2008-07-13
forum: General Help
---

### Post by rootless on 2008-07-13
[SIZE="5"]The Short Version:[/SIZE]

I deleted a Ubuntu partition on one hard drive and attempted to boot into my Ubuntu partition on my other hard drive. Now, despite many attempts to fix it, I am still getting "Error 22: No Such Partition."

I would be VERY grateful if anyone could offer me any help with this problem I am having. I have spent hours tinkering on my own, and trying solutions I've found in google, to no avail. This is the first time I haven't been able to find a solution already posted on this forum!
[SIZE="5"]
The Origin Of The Problem:[/SIZE]

It all started earlier today. I had one master hard drive partitioned into /dev/sda2 (broken windows partition) and /dev/sda3 (small Ubuntu partition, flagged as boot) with /dev/sda4 as swap.

I had a second hard drive, wired as slave, running a large Ubuntu partition on /dev/sdb1 and swap on /dev/sdb2

This is a stupid, confusing system, I know. My partitions were configured this way because I had recently added the slave hard drive to expand my disk space.

Anyway, I decided to fix this confusing system. I flagged the new, large partition (/dev/sdb1) as boot. I then deleted the small Ubuntu partition (/dev/sda3) along with it's swap (/dev/sda4). 

Oops. I attempted to boot up from the partition selection menu into /dev/sdb1, and instead got "Error 22: no such partition"

No problem, I thought. Ubuntu isn't finding the boot partition because the other hard drive was still wired to boot as master. I wired the new hard drive as master, and the old one as slave. I took out the hard drive jumpers, assuming that my motherboard would recognize which was master and which was slave based on the way they are wired. Oops.

I booted up again, and got a nasty message, saying that my HD was bad, and that I should remove and replace it. I couldn't get past that menu. Uh oh. I was convinced I just fried my new hard drive, but when I put the jumpers back in their original places, the computer booted up again.

It would only boot into the partition selection menu again, so, I was back at square one, but still somewhat relieved that my brand new HD was still functional. I booted with my Live CD and checked the contents of my HDs. Everything was as it should be, except they still refused to boot!

[SIZE="5"]Solutions I've tried that have failed:[/SIZE]

At this point I got ontu Ubuntuforums, and read many threads. 

Amongst others, I read [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=378322](http://ubuntuforums.org/showthread.php?t=378322)[/COLOR]

and [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)[/COLOR]

and [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=376858](http://ubuntuforums.org/showthread.php?t=376858)[/COLOR]



I did a sudo fdisk -l and got:

```
Disk /dev/sda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7fec625

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *         785       22607   175293247+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00027618

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       53626   430750813+  83  Linux
/dev/sdb2           53627       53723      779152+  82  Linux swap / Solaris
```

Then, I checked fstab and got a strange result:

```

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb2 swap swap defaults 0 0
```

I have no idea what this means.

I tried a 

```
sudo grub
root (hd1,2)
setup (hd1)
```

But I am not sure if I tried to install grub in the correct place. I didn't even think this was necessary, but I figured I'd try it out.

In desperation, I also tried hitting b at the partition selection screen and plugging in various numbers instead of (hd0,1).

In conclusion, I have searched Ubuntu Forums thoroughly, and I am totally out of ideas. You guys have been there for me, and I've used Ubuntuforums to solve every other problem I have come up against. Surely someone will be able to help me with this.

Does anyone have any ideas?

---

### Post by Sef on 2008-07-13
Have you tried [Super GRUB Disk]("http://www.supergrubdisk.org/")?

---

### Post by rootless on 2008-07-13
I just burned it. I'll try this and get back to you.

Thanks.

---

### Post by logos34 on 2008-07-13
> **rootless said:**
> 
I**t would only boot into the partition selection menu again**, so, I was back at square one, but still somewhat relieved that my brand new HD was still functional. I booted with my Live CD and checked the contents of my HDs. Everything was as it should be, except they still refused to boot!


If SGD doesn't fix it:


sdb1 is either

root (hd0,0)

or

root (hd1,0)

On the grub menu screen press 'e' on the ubuntu selection to edit, 'e' again on 'root' line and try either of the above.  Pres 'b' to boot.  If it gets you into ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

change 'groot' and 'root' lines to match

---

### Post by rootless on 2008-07-13
LOL, hey, I was just tooling around in grub and I tried booting from (hd1,0), and I got it to boot into my desktop!

I'm not sure what I did differently this time. Hah.

Ah, it's like the thing has come back from the dead. Staring at those black screens was getting depressing.

Still though, this is only a temporary fix. I still have to go back and change it to boot from (hd1,0) every time I boot.

Any Ideas?

---

### Post by rootless on 2008-07-13
Logos, you read my mind.

As usual, Ubuntuforums never fails me.

You guys are brilliant. Thank you. Ubuntuforums should be a TV show or something.

:grin:

I'll run that command in terminal and then tell you how it goes.

---

### Post by rootless on 2008-07-13
Just to clarify...

So you're saying that I should change all references to root (X,X) and groot (X,X) to root (1,0) and groot (1,0)?

Just wanna make sure- menu.lst looks complicated and it looks like I could cause major damage in here. Lol.

---

### Post by rootless on 2008-07-13
That did it!

:guitar:

Thanks again!

---

### Post by logos34 on 2008-07-13
Glad it's fixed.  Mark thread as solved. (>thread tools)

Enjoy your ubuntu!

---

