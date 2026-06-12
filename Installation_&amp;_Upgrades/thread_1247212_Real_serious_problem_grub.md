---
title: "Real serious problem grub"
date: 2009-08-22
forum: Installation &amp; Upgrades
---

### Post by antel on 2009-08-22
Ok I have xp on this computer. I installed netbook remix but the program launcher kept disappearing, my friend said he didn't want it and just install regular ubuntu. I ubinstalled the netbook remix and removed files that contained the name wubi, ubuntu, etc etc. After that I restarted but the grub menu was still there. Btw it isn't the normal windows or ubuntu menu. It shows every single partition. Anyway, when I installed ubuntu and restarted, the netbook remix was still an option and when I clicked on xp, it took me to the regular ubuntu. I uninstalled ubuntu from netbook remix but the xp option still takes me to ubuntu and says it is missing. MŸ friend doesn't have his xp cd. I realllyyýyy need helpp

---

### Post by eagle416 on 2009-08-22
What exactly are you trying to accomplish? Dual booting WinXP and Normal Ubuntu?

Boot into ubuntu, and fix grub from the terminal. I can't exactly remember how, google around. If I think of it I'll post it.

---

### Post by VMC on 2009-08-22
run the livecd and output "sudo fdisk -l" also output the installed Ubuntu /boot/menu.lst file. So you need XP to run ,correct?

---

### Post by antel on 2009-08-22
Yes I want xp to work. At this point he doesn't care about ubuntu. Just wants to delete netbook remix completely and boot windows.

---

### Post by antel on 2009-08-22
it isnt working. it cannot be found. i just want to get into windows so i can successfully and completely delete all the ubuntu installations.

---

### Post by eagle416 on 2009-08-22
Okay. I had this problem about 4 days ago.

The critical thing to do is get windows running. You can make a grub disk (google SUPER GRUB DISK), or reinstall ubuntu to restore grub. Do whatever you have to do to get access to windows on your computer.

As soon as you hit ENTER on the windows option to get it to start, press F8 over and over until you get the boot options screen. It should ask for booting normally, safe mode, safe mode with terminal etc.... There should be a button you hit (it'll tell you) to get to the OS choice menu. There, you should find two or more options, one being WINDOWS XP and one of the others being WINXP RECOVERY CONSOLE.

Try to get to the recovery console. If you can't find anything about a recovery console, [http://www.neowin.net/forum/lofiversion/index.php/t378188.html]("http://www.neowin.net/forum/lofiversion/index.php/t378188.html")

be advised that winnt32.exe might not be in i386, it might just be in /WINDOWS.

The important thing is to get to a recovery console.

Then:

```
C:>fdisk /mbr
C:>fixmbr

```

Now your computer will automatically go into windows, and you've gotten rid of GRUB.

Go in there with a live cd to remove all Ubuntu partitions.

---

