---
title: "Advice with partitioning new installation of ubuntu and XP"
date: 2009-05-19
forum: Installation &amp; Upgrades
---

### Post by fung on 2009-05-19
I'm planning on doing a clean wipe of my OS partitions and completely reorganize everything. I have 1 1TB, 2 500GB drives not in raid and I want both ubuntu and winXP on here as well. (can't live without my games!!). The 1TB I'm planning to use as just a data drive.

The big question sticking in my mind is should I have both of them sitting on the same physical 500gb drive? or should I split them over both 500s? Are there advantages/disadvantages to doing one or the other?

---

### Post by c0nfusedami on 2009-05-19
I would say that unless you plan on doing some sort of crazy downloading like hundreds of movies or something that you should just keep it simple and set 1 500GB hard drive to linux and the other to XP. If you really need storage space set 1 500GB hard drive for both your os's.

---

### Post by fung on 2009-05-19
Well are there any "logistical" issues with putting them on separate drives or the same drive?

---

### Post by atomizer on 2009-05-19
I think it is best to split to 2 drives.
I had to tinker with resizing and moving partitions (with the chance of dataloss) just because my C: was full and my /home was not (all on the same drive).
And maybe you can put your windows-swap on your linux-drive and vicaverca for a very small boost

---

### Post by c0nfusedami on 2009-05-19
The only issue that I can foresee in putting them on the same drive is if you didn't make the partition large enough for the os's then you could run into space issues with a large amount of applications but you really don't have a space issue. you should be able to access the same partitions from both os's

---

### Post by Sef on 2009-05-19
Check out the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").

---

### Post by KidKappa on 2009-05-19
I am looking to do the same, dual boot win7 and ubuntu, if i put both os's on a single drive and use a larger drive for data, what file system should that larger drive be? ntfs, ext3?  i'd rather not use fat32 cuz I have files larger than 4gb.

---

### Post by dreamer565 on 2009-05-19
> **Sef said:**
> Check out the [Illustrated Dual Boot]("http://users.bigpond.net.au/hermanzone/").
@Sef - thanks for the link.  the graphical steps for installing and partitioning my drive is just what i was looking for.  could have really helped if i'd found it before running the install and a) first time hosing my mbr on my xp drive b) 2nd try going with defaults which didn't resize anything and gave me no room to save settings.  I was trying to follow a couple other guides on creating a dual xp and ubuntu machine, and this one fills in some things that were missing.

very helpful!> [http://mywebsite.bigpond.net.au/dfelderh/p24.html](http://mywebsite.bigpond.net.au/dfelderh/p24.html)

---

