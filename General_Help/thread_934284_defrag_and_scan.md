---
title: "defrag and scan"
date: 2008-09-30
forum: General Help
---

### Post by karmyster on 2008-09-30
Are there Ubuntu equivalents of the defragment and scan disk operations? If so, please let me know what they are and how to use them. 

Thanks
***[COLOR="Navy"]K[/COLOR]***

---

### Post by leg on 2008-09-30
No the file systems work differently and you don't need to defrag them. You won't have those kind of problems until your hard drive is getting very full. Then there is something you can use to defrag it but you probably won't gain that much when the disk is pretty full.

---

### Post by russlar on 2008-09-30
for scanning disks for errors, there's *fsck*. Note that it only works on unmounted filesystems, and often runs at bootup.

---

### Post by snova on 2008-09-30
You don't need to defragment a Linux filesystem most of the time, but in the rare case where you have something to gain from it, there are tools to do that.

As for scandisk, the replacement is called "fsck" (FileSystem ChecK), and it runs every time you boot up. Every 20 or 30 boots it runs a thorough check that takes a few minutes, and that's it.

So you don't have to do anything at all.

---

### Post by Crafty Kisses on 2008-09-30
You don't really have to defrag in Linux, the file system is organized and stored more efficiently than a Windows box. If you really want to then I can
suggest you go to something like Google and search "Linux defrag" or something and grab a utility, they do exist, but unnecessary.

There is an option to "clean" though, just run this command in Terminal:
```
sudo apt-get clean
```

---

### Post by Ryadt on 2008-09-30
This will explain why linux doesn't need defragmenting: [http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by Spaceman9 on 2008-09-30
Linux works differently then windows. With windows it saves files where ever it finds space working out from the hub of the hard drive. That's what makes the disk become dfragmented as you save or delete files. With Linux it saves files in one contiguous space on the drives disk so there's no defragmentation with Linux. 

Also with Linux it checks all your partitions every time you boot up your distro. If it finds anything wrong it will take care of it for you then. Neat uh.

---

### Post by karmyster on 2008-10-04
Thanks for the info ppl, one less thing for me to worry about!!

***[COLOR="Navy"]K[/COLOR]***

---

