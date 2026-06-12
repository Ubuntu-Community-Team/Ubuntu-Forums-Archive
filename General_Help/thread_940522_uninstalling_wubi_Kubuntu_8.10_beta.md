---
title: "uninstalling wubi Kubuntu 8.10 beta"
date: 2008-10-07
forum: General Help
---

### Post by coolguy2000 on 2008-10-07
Hi All,

I installed kubuntu 8.10 and i again uninstalled it.

Now there is a problem in my disk space usage

D:\ - before installing 16 GB 
D:\ - **after installing 26 GB **
D:\ -** after uninstall it is still 26 GB.**

How do I recover my disk space in this case.

Since it is in beta I wanted to use 8.04.1 for few days.

Thanks,
sur

---

### Post by lisati on 2008-10-07
1) How did you install Kubuntu? Was it from a CD or some other method (e.g. within a "virtual machine")?
2) Is "D:\" a partition you had set aside for checking out Kubuntu?

---

### Post by coolguy2000 on 2008-10-07
1. I installed from my existing windows XP using Wubi 8.10
2. I choosed D: partition from Wubi and set 10 GB for installing kubuntu kde 4 in my windows drive.

---

### Post by 3rag0n on 2008-10-07
> **coolguy2000 said:**
> 1. I installed from my existing windows XP using Wubi 8.10
2. I choosed D: partition from Wubi and set 10 GB for installing kubuntu kde 4 in my windows drive.

I have tried wubi once...
If you check your D:\ drive, perhaps you will see a folder "ubuntu" ( or "kubuntu", maybe). There will be one (or more) junk files of the sum total size 10 GB. 
What wubi does is this :

When you allocated 10 GB for kubuntu, wubi created a junk file containing random data of size 10 GB inside your D drive. This is wubi's way of creating a virtual filesystem or partition. Whenever you save your files and settings in kubuntu, all changes are saved in this virtual filesystem ( or partition).

This means that, even if your kubuntu is just a fresh install,
the size of the junk file will be 10 GB.

And even if you install a lot of softwares and stuff and save many files in your kubuntu, the size of that file will STILL remain 10 GB.

The traditional way of uninstalling kubuntu is by going to the Add/Remove Programs menu in windows. If i am right in assuming you did this, then hopefully **when you boot your PC, there will be no OS choices menu.**

NOW DO THE FOLLOWING ONLY IF THE ABOVE BOLD STATEMENT IS TRUE. Somehow the uninstaller has failed to remove the 10 GB virtual partition. Do this: locate the 10 GB file in your D drive and... well... shift+delete it !
You'll get your normal D drive size back.:lolflag:

---

### Post by lisati on 2008-10-07
I've never actually used Wubi, so I'll have to pass on the reins to someone else who might be in a better position to evaluate if that might have some bearing on the situation.

---

### Post by coolguy2000 on 2008-10-07
Hi All,

After uninstalling the file was moved to 

D:\found.000 a hidden folder.

I used [WinDirStat]("http://windirstat.info/") to find the correct the problem.

now the problem is recovered  :)

---

### Post by 3rag0n on 2008-10-07
> **coolguy2000 said:**
> Hi All,

After uninstalling the file was moved to 

D:\found.000 a hidden folder.

I used [WinDirStat]("http://windirstat.info/") to find the correct the problem.

now the problem is recovered  :)

:lolflag:

---

### Post by ago on 2008-10-07
> **coolguy2000 said:**
> Hi All,

After uninstalling the file was moved to 

D:\found.000 a hidden folder.

I used [WinDirStat]("http://windirstat.info/") to find the correct the problem.

now the problem is recovered  :)

Either the ubuntu folder is left around, which would be a bug and I'd like to know about it, or you have a found.000 hidden file, which is an ntfs issue and not much I can do about. The hidden file can be deleted normally though, you need to make sure you can see hidden files in windows explorer settings though.

---

### Post by 3rag0n on 2008-10-07
> **ago said:**
> Either the ubuntu folder is left around, which would be a bug and I'd like to know about it, or you have a found.000 hidden file, which is an ntfs issue and not much I can do about. The hidden file can be deleted normally though, you need to make sure you can see hidden files in windows explorer settings though.

Windows is like a naughty kid.
Windows loves to make copies of your files and hide them.:)

---

