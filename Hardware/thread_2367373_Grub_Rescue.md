---
title: "Grub Rescue"
date: 2017-07-29
forum: Hardware
---

### Post by ramalair on 2017-07-29
Hello everyone; old Ubuntu user here. Nice to be back on the forums. After a three year hiatus using MacOS I've returned to Ubuntu and like most of us, I'm a linux evangelist again! My friend has an old laptop and I recommended he install a linux distribution on it to improve it's functionality.

He installed elementary (boo!) and it seemed to work alright but he then wanted to try ubuntu, instead. He booted a USB stick and began an ubuntu installation. At some point something went wrong, though.

Now, when he boots the laptop, it goes straight to grub rescue:

```
error: no such partion.
Entering rescue mode
grub rescue>
```

I did some research for other people with similar problems and thus executed this script. Here's the response:

```
grub rescue> ls
(hd0) (hd0, msdos5)
grub rescue> set prefix=(hd0)/boot/grub
grub rescue> set root=(hd0)
grub rescue> insmod normal
error: unknown file system
grub rescue> insmod (hd0)/boot/grub/normal.mod
error: unknown filesystem
grub rescue>
grub rescue>
```

I've never worked with grub before but I'm pretty used to using terminal for executing commands or locating files on the system. I'm very much out of my programming comfort zone here and would like some help.

We have another bootable USB stick (booted with the freshest ubuntu distribution from my laptop and formatted correctly) but when I enter into his sytem to get it to boot from the USB it goes straight to grub regardless.

Aside from throwing it out the window, any ideas for how to fix this? :D

---

### Post by ramalair on 2017-07-29
I've tried to set the prefix and root on the other system (hd0,msdos5) but the script is the same.

---

### Post by ajgreeny on 2017-07-29
Go to 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
and also 
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) 
for a lot of useful information.

To allow us to see more about the problem installtion go to **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the **pastebin** link you get which will show us a lot more about your friend's system and should give us some clues about what went wrong with the installation.

---

### Post by lisa85 on 2017-08-05
After numerous attempts to fix this issue, I unplugged all USB devices  from my laptop, shut down my laptop and then everything booted  perfectly.  Apparently my 32GB thumb drive was the culprit.

---

