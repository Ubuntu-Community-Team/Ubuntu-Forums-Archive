---
title: "Update Manager Error - Linux-2.6.24-19-generic"
date: 2008-07-27
forum: General Help
---

### Post by TheMuffinMan616 on 2008-07-27
Okay so I have spent the better part of the last two days studying and configuring bootloaders, partitions, VM's, Ubuntu, and the works. Being a diehard windows user, this wasn't the easiest of tasks. I think I have finally got it all taken care of. I am running off a Wubi install on my external and with a stroke of luck got my bluetooth keyboard/mouse to work. (im still afraid to turn my computer off) but now I only have one problem...

Ubuntu continues to remind me that I have some updates that need to be taken care of. When I go to update there is always an error with this one package. When I try to install the "linux-image-2.6.24-19-generic" an error comes up saying

"E: /var/cache/apt/archives/linux-image-2.6.24-19-generic_2.6.24-19.36_i386.deb: unable to make backup link of `./boot/vmlinuz-2.6.24-19-generic' before installing new version"

I have been scouring these forums to no avail and am hoping that I can get some help with this...

Thanks so much any help is greatly appreciated
-TheMuffinMan

---

### Post by hishamzz on 2008-07-27
Same boat as you are in buddy. Check this link :-

> [http://www.linuxquestions.org/questions/linux-software-2/not-able-to-update-ubuntu-656091/](http://www.linuxquestions.org/questions/linux-software-2/not-able-to-update-ubuntu-656091/)

They assume that the problem might be with there not being enough space on /boot. But they have not given a very definite solution as to how this could be overcome other than having Ubuntu on a different partition.

Anybody else here who could assist please?

Zz

---

### Post by ago on 2008-07-29
Is your installation on vfat? Can you check your free space?

---

### Post by IkeaKev on 2008-07-29
I have the same issue.
I'm only 3 Linux days old :)

Using the Wubi homepage, I installed Ubuntu 8.04 on my D: drive which was freshly formatted as fat32.
I've still got XP on my C: drive.  Maybe be worth pointing out that it's physically a single 40gb drive with a logical partition half way through. I chose the option to use 15gb for installation and let Wubi do the rest.

---

### Post by ago on 2008-07-29
If you are on fat32 disable the kernel upgrade for the time being

---

### Post by ofirtirosh on 2008-09-09
I have the same problem, also installed with wubi but when you check the file system fron within ubuntu it says that it's ext3.
Is there a way to install that package without creating a backup link??:confused:

---

