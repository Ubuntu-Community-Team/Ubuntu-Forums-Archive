---
title: "Disk problems after install of 9.04"
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by az10sbum on 2009-09-26
I installed 9.04 on a Compaq Presario F500.  It is a dual processor 64 bit Athalon, and I did a 64 bit install.

It is a dual boot system with Windows XP, and everything seemed to go well during the install, but I started getting disk errors on the partition after I rebooted.  I get an UNEXPECTED INCONSISTENCY error on my partition.

The first thought is that disk is going bad, however the computer was in active use and there were no known problems with the disk before I installed, and it passes the "check disk for defects" that is available on the run live CD every time.


Any suggestions on what to do next would be greatly appreciated

Dave

---

### Post by az10sbum on 2009-09-27
Is this the correct forum to post this kind of question?

---

### Post by raymondh on 2009-09-28
> **az10sbum said:**
> I installed 9.04 on a Compaq Presario F500.  It is a dual processor 64 bit Athalon, and I did a 64 bit install.

It is a dual boot system with Windows XP, and everything seemed to go well during the install, but I started getting disk errors on the partition after I rebooted.  I get an UNEXPECTED INCONSISTENCY error on my partition.

The first thought is that disk is going bad, however the computer was in active use and there were no known problems with the disk before I installed, and it passes the "check disk for defects" that is available on the run live CD every time.


Any suggestions on what to do next would be greatly appreciated

Dave

Access terminal and post results of

```
sudo fdisk -l
```

Also, why not run a fsck check?  I suggest you do this from a liveCD (I prefer using a liveCD of gparted) as it automatically unmounts the partition.  Just rt-click to highlight the Ubuntu partition and select CHECK.

If you want to use the Ubuntu liveCD to run fsck .... boot into it and access a terminal.  If your file format is ext3, the command is

```
sudo e2fsck -C0 -p -f -v /dev/[COLOR="Red"]hdXY[/COLOR]
```

where [COLOR="Red"]hdXY[/COLOR] is your ext3 ubuntu partition.

If you have BAD BLOCKS, this is the command (_only if you have bad blocks_)

```
sudo e2fsck -c -c -k -v /dev/[COLOR="Red"]hdXY[/COLOR]
```

To verify the above commands, you may (from terminal) run

```
man e2fsck
```

and it will open up the manual for fsck for your reading/research.

Regards,

---

