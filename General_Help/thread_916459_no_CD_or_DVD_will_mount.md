---
title: "no CD or DVD will mount"
date: 2008-09-10
forum: General Help
---

### Post by grashdur on 2008-09-10
I've installed Hardy Heron on my Gateway (desktop) computer (using wubi). I cannot get any CDs or DVDs to mount at all (as of today, trying it with various disks), although some CDs have worked earlier, occasionally. 

This computer is dual-boot, and the same CD/DVD drive runs perfectly in Windows XP. In Ubuntu, when I put a disk in the drive, the disk starts spinning and the light turns on, and then after a little while the light turns off again and nothing else happens. No mounted-disk icon on the desktop, no CD/DVD drive showing up in Places > Computer, nothing appearing in the /media folder. 

This is an internal drive, and it's the original one that came with the computer. In Windows I looked up the drive's properties, and found it identified as an &#8220;HL-DT-ST DVD-RW GWA-4165B&#8221; -- I haven't found anything relevant online about it, at least that I can make any sense of. 

I've looked at books, and all over this forum, but no luck. 

I looked at my kernel boot message (which I just found out how to do) and saw no mention of any cd, dvd, or hdd. 

I originally had the very same problem with the CD/DVD drive not working with Feisty Fawn on my Sony Vaio laptop &#8211; but now with Gutsy Gibbon installed, the drive runs perfectly. 

So is this just a problem of no such driver being available for Linux? Is there any hope of getting this to work?

---

### Post by Crafty Kisses on 2008-09-10
Have you tried manually mounting it?
```
sudo mount /dev/scd0 /media/cdrom0
```

---

### Post by grashdur on 2008-09-10
Thanks for the suggestion. I tried it just now, and got this response:

mount: mount point /media/cdrom0 does not exist

I had a CD in the drive while doing this. I then tried typing 

sudo mount /dev/scd0 /media

and got the response:

mount: special device /dev/scd0 does not exist

---

### Post by grashdur on 2008-09-12
This time, the CD/DVD drive is working again. 

Does anybody know whether my use of Wubi to install Ubuntu could have anything to do with this drive's intermittent availability? I've looked all around and so far I haven't found any information that would suggest this. But I also haven't found anything else that might be causing it.

---

### Post by grashdur on 2008-09-20
I have a workaround: It seems that the DVD/CD drive is now working properly *on every other bootup.* So if I need the drive and it's not working, I'll just reboot. Then I'll just wait for the problem to be solved on future versions of Ubuntu.

---

### Post by grashdur on 2008-09-25
As mentioned, my DVD/CD drive was available on every other bootup, which was more or less acceptable for now -- but now it's *really* stopped working: I was trying to back up some of my files to DVD, and when I tried to do the second disk I got some sort of "unhandled error" and then on each subsequent attempt I was asked to instead insert a "supported" disk into the drive. I kept trying with the same blank DVD and then with another one, but it just wouldn't write. 

Since then, every time I boot up, I have *no* DVD or CD drive showing up at all under Places > Computer. :(

What in the world is going on? I really would like to skip the extra work of copying data over to my Windows side and then rebooting into Windows in order to write to DVDs. Do I have some sort of faulty driver? Why would it work *every other time*, and now not at all?  :confused:

---

