---
title: "Hard Drive worked fine before, now will not mount"
date: 2008-08-25
forum: Hardware
---

### Post by FoxTheCave on 2008-08-25
Hi, my 700gb FreeAgent External HardDrive worked perfectly a few days ago. Today however, I took it to a friends to get some movies off of him. He uses Windows Vista - now however, the hard drive will not mount on my Ubuntu Operating System. When I plug it in it simply says:

[[IMG]http://img137.imageshack.us/img137/6619/cannotmountam7.th.png[/IMG]](http://img137.imageshack.us/my.php?image=cannotmountam7.png)

Anyway, I tried both of the suggestions for Linux users there and neither worked. I typed that into the command line letter for letter, and it simply told me that 'only root could mount' (what does this mean?) and that for the second one, the directory didn't exist.

Can someone please help me? This thing cost me a hundred sterling!

Many, many thanks in advance!

Edit: Someone else told me that I have to plug it into a Windows machine and safely remove the hardware, so this is solved.

---

### Post by eggdeng on 2008-08-25
> 'only root could mount' (what does this mean?)
You need to prefix ```
sudo
``` to the command.

---

### Post by FoxTheCave on 2008-08-25
Okay, I did that but now Terminal just spat this all out to me, none of which I understand. Can someone translate or direct me further?

[[IMG]http://img528.imageshack.us/img528/3238/mountingprintscreenty0.th.png[/IMG]](http://img528.imageshack.us/my.php?image=mountingprintscreenty0.png)

---

### Post by FoxTheCave on 2008-08-25
Anyone?

---

### Post by eggdeng on 2008-08-26
You have a typo in the command, the console is very picky about white spaces.
I have come across a fix (suggested by halfling85 on [http://ge.ubuntuforums.com/showthread.php?t=836409]("http://ge.ubuntuforums.com/showthread.php?t=836409")) which may be easier and quicker. First, just make sure the device is identified as /dev/sdb1 using
```
sudo fdisk -l
```
Copy and paste to avoid typos.
Now run
```
sudo apt-get install ntfsprogs
``` which will install a program which includes a repair utility. Run the utility (assuming the drive is sdb1)
```
sudo ntfsfix /dev/sdb1
```
With luck, this will repair and mount the drive.
Back to the original problem, as far as I can work out, the command should read
```
sudo mount -t ntfs-3g /dev/sdb1 /media/FreeAgent Drive -o rw force
```
but, hopefully, you won't need it.

---

### Post by FoxTheCave on 2008-08-26
Thank you, thank you, thank you, thank you, you are my hero!

It worked!

---

