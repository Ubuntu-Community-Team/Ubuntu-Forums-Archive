---
title: "bad sound generate from my hdd"
date: 2007-04-25
forum: Hardware &amp; Laptops
---

### Post by siya_kh1983 on 2007-04-25
hi. when I wanna install or add or upgrade application in my notebook , my hdd make a bad sound like the head of my hdd hit the disk, or look like a mechanical water drop down... Is it harmful for my hdd...
by the way, I used windows xp sp2 and there isn't any sound like this from my hard, I know the writing sound is what look like, and this sound is too different.
thanx

---

### Post by Metacarpal on 2007-04-25
It's possible that your hard drive may be going bad.  I highly recommend backing up your data (any documents or files that you can't easily re-install) to some kind of external media - a CD, a USB thumb drive, external hdd - heck, sometimes I just zip things up and email them to myself.

You should do this right away, just in case the drive goes down.

It's highly unlikely that Ubuntu is causing the strange noises you're hearing.  You'd probably be hearing them now if you'd stuck with XP.

After you back up your data, you should run fsck on the drive to see if it can repair the problem.  You shouldn't try to run this from your desktop, though.  I'm sure there's an easy, direct way to get this done, but I don't know it - so here's a slightly ugly way of going about it:

First, you'll need to know what your main drive is called.  Open a terminal (Applications menu > accessories > terminal) and type (or copy-paste) this:

```
cat /etc/fstab | grep " / " -B 1
```

This should get you two lines of output.  For instance, on my computer, that returns:
```
# /dev/sda1
UUID=cf258456-1035-4ab2-b445-fd8f5ed68bf2 /               ext3    defaults,errors=remount-ro 0       1
```
The first line (after the #) is the name of your hard drive (or the primary partition).  Now we're going to tell your computer to check the drive for errors on every boot.  (Don't worry, we'll put it back later.)

In the terminal:
```
sudo tune2fs -c 1 /dev/**sda1**
```
(replace sda1 with whatever your drive was called in the previous output.)

Then reboot.  This will cause fsck (file system check) to run the next time you reboot.  It will find, report, and (hopefully) fix any errors that appear on your drive.  After that, you can run set the system back to checking on every 30 boots (or however often you like):

```
sudo tune2fs -c **30** /dev/**sda1**
```
(replace sda1 with whatever your drive was called in the previous output.)

If you don't want to do all that, you could just reboot the computer over and over 'til fsck runs on its own.:lolflag: 

Best of luck to you!!!

---

### Post by siya_kh1983 on 2007-04-28
some one told me that my hdd head when wanna park, it take this sound...
I don't think that there is any error or bad sector...
do you ever hear this sound???

---

### Post by Metacarpal on 2007-04-28
Well, I don't know exactly what sound your drive is making.  I mean, I've heard hard drives make a lot of sounds... some are normal, some are really bad.  If your drive is making a noise it didn't make before, or it's louder or making noise more often, better to back up and test the drive than risk losing all your data.

---

### Post by siya_kh1983 on 2007-04-29
ok. thanx so much for your help

---

### Post by tungvm87 on 2008-03-15
i am using lenovo 410y, and while computer was running ubuntu 7.10, my hard disk was making noise too, i don't know why because that don't happen in window vista and Win xp sp2.
i hope yous could help me resolve this problem. Thanks

---

### Post by Tuxoid on 2008-03-15
my hard drive in my LG notebook I thought was deceased. If others are having such problems, I may have some in that it could be much more normal. Although it has marked several bad sectors on my drive and complains about logical blocks at startup. I backed everything up and formatted my ext3 partition and I have been booting using a custom liveCD for at least three weeks. I basically can't use anything, can't install anything (unless I'd like to temporarily install it into the the RAM :( )

I have taken my hard drive out of my machine and I don't know if I should try get it working or get it tested unless this is just abnormal drive operation.

---

