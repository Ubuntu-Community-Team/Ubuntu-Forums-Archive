---
title: "Can't Mount Hard drive"
date: 2009-02-10
forum: Hardware
---

### Post by wlraider70 on 2009-02-10
I have a HD from an old driecttv DVR.
SO I'm assuming that the formatting is causing the issue.
I can see the disk in under computer, when i click on it it says can't mount file.

I don't care about the files that are on the disk, though it would be cool to see them if possible. 

IS there a way to format without mounting?

---

### Post by taurus on 2009-02-10
The drive should not be mounted if you want to format it.

However, what is the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by wlraider70 on 2009-02-10
Disk /dev/sdb: 40 GB, 30923740273bytes
255 heads, 63 sectors, 485 cylinders
Disk Identifier 0x00000000
Disk /dev/sdb Doesn't contain a valid partition table

---

### Post by Sk8man on 2009-02-10
hmm looks like u will have to format it to use it.

---

### Post by wlraider70 on 2009-02-10
ok, how do I do that?

---

### Post by martinbaselier on 2009-02-10
sudo gparted is the easiest way to create a partition and format it.
choose /dev/sdb after starting gparted.

---

### Post by Sk8man on 2009-02-10
ok, um usaully i just put in the ubuntu cd then go to gparted and then format the drive (make sure u dont nuke your ubuntu install, just make sure u format the right drive, ) but u can install gparted strait on your install and go from their,

---

### Post by martinbaselier on 2009-02-10
you only need to run gparted from the cd if you want to resize your root partition,since you can't unmount it you're currently running your system  from it, so using it from inside your install is actually safer because you can't accidently remove you rootpartition. 
 Gparted is installed standard on ubuntu if I remember correctly.

---

### Post by Sk8man on 2009-02-10
funy funy, it is removed when ubuntu is installed (well at least in xubuntu it is!), you'll have to reinstall it through add\remove,

---

### Post by kdixon on 2009-02-10
hey i had your problem before where i couldn't mount my harddrive. the problem was when i was using it in windows i didn't shut down my computer properly (theres some technical reasons why this wont allow you to mount it properly in ubuntu, but i dont know them). i fixed this by booting up in windows(i have 2 harddrives, 1 dedicated to ubuntu and one to windows) and then shutting down properly. i dont i know how well this applies to your situation but maybe it will kick up some ideas.

---

### Post by martinbaselier on 2009-02-10
@sk8man: then I didn't remember correctly. It's been some time since I installed it.
@kdixon: When unmounting a device, remaining data is written (flushed) and the filesystem updated. I presume windows will be able to correct errors on it's native filesystem better than linux can, since it has all the information on how it uses it. 
Since I allready gave commandline instructions:
sudo apt-get install gparted
will install gparted.
then run sudo gparted

---

### Post by wlraider70 on 2009-02-11
ok, it did it. 
I had to add gparted.
run it from termiinal
add a partition

How do I mark this as solved?

---

