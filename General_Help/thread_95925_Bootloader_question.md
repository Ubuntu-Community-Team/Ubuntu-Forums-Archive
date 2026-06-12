---
title: "Bootloader question"
date: 2005-11-27
forum: General Help
---

### Post by guice on 2005-11-27
So, I've installed Kubuntu on a secondary system which is going to be my primary Kubuntu system, for now, until the world get a got more Linux friendly (noteably games and NVIDIA's lack of SLI. ;)).

Anyway, I've had Kubuntu install on my primary system and I want to drop it. I know I can just wipe partition it's on and resize my drives to kill everything out, but my question is there anything I need to do about the boot loader?

Grubb is installed to switch between the OS's and if I remove linux, grubb will be gone as well; how will the system handle that? Do I need to edit the boot.ini? Or will things just fall into place correctly?

I want to make sure before I wipe the Linux partitions and get farked with inability to boot.

---

### Post by incubus on 2005-11-27
I assume that you intend to switch back to windows. If you want the native boot loader, you can boot windows CD, go to rescue mode, and run "fixmbr", if I remember correctly (it's been a long time, fortunately!).

Now, you may keep GRUB depending on how you partitioned your disk. If you created a dedicated partition just for it (usually a small one in the beginning of the disk), you can just edit the file "menu.lst" and set GRUB to load windows automagically without a waiting time. The file is very self-explicative.

Whatever you do, backup important data. You never know. :) Hope this helps.

PS: Having some linux Live CD in case of problem is also very good, since you can install GRUB again if everything fails.

---

### Post by guice on 2005-11-27
Your assumptions are 100% correct. Maybe I'll do the menu.lst thing, though. I don't mind just leaving Kubuntu on this system (I have more than enough drive space) but always been annoyed that I had to watch for GRUB in order to get Windows up.

Thanks!

---

### Post by aysiu on 2005-11-27
Just change *default 0* to be *default 4* in your /boot/grub/menu.lst

This assumes, of course, that Windows is your fifth entry (default 4 is really default 5-1=4).

---

### Post by guice on 2005-11-27
Not 5th, still need to remove default 64bit (have k8 loaded). However, I fully understand the differences between zero based and non-zero based numbering.

---

