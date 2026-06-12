---
title: "Replacing HDD"
date: 2016-09-13
forum: Hardware
---

### Post by SageOfSmeg on 2016-09-13
I would like to replace my hard disk containing both /home and /var and upgrade to a larger HDD.
The / directory is on a separate disk, so that’s okay as it is.
 
Unfortunately, it’s an old machine with only two connectors (power and IDE) for two physical drives, so I am asking for the simplest/easiest approach for swapping out the one disk? 
I assume it would be a matter of perhaps booting using a Live CD and manually editing the fstab after the hardware change.

Any help appreciated, thanks.

Lubuntu 12.04
Very old desktop PC
Pentium II
750MB RAM

---

### Post by sudodus on 2016-09-13
It is very simple to copy only the home directory. And yes, you should do all of it when booted from CD/DVD/USB.

You can actually just copy the the directory tree with rsync or cp (and suitable options). After that you have to fix the UUID reference in /etc/fstab or if you prefer, the change the UUID of the new drive to that of the old drive. This latter method can cause problems, if you connect both drives at the same time. If you change the file system (for example from ext3 to ext4), you must take care of that in /etc/fstab too.

Another method would be to clone (the content of) the old drive to the new and larger drive. You can do that with Clonezilla. The method is straight-forward, and you will have two drives with the same UUIDs (and the same potential problem as above, if you intend to use both drives at the same time, otherwise there is no problem).

Edit:

But there is another issue: Lubuntu 12.04 had no long time support, and it has passed end of life. Please consider trying a newer version, which is supported. Part of Lubuntu 12.04, the engine under the hood in common with Ubuntu 12.04 LTS, is supported until April 2017, but the desktop packages are not supported, and there may be security holes.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by SageOfSmeg on 2016-09-14
> **sudodus said:**
> Lubuntu 12.04 had no long time support, and it has passed end of life. 

Yes, I agree that it is a potential security issue.

Sadly despite trying alternatives I have been unable to install anything else successfully. It's a very old machine, circa 1999, originally with Windows98. 
Lubuntu 12.04 was the only distro I could get to install and run up to the desktop. 
Antix or Trisquel are the only other aternatives I know that MIGHT work, but installing anything on this hardware can take several hours even with command-line mode. I would rather not spend time experimenting, hence just wanting to increase storage capacity.
So for the time being I will stick with Lubuntu 12.04, which seems to work fine for my needs as I only use it to monitor my home network and also a PostgreSQl database.

---

### Post by Bucky Ball on 2016-09-14
[Or this]("https://help.ubuntu.com/community/Installation/MinimalCD"). You will need to take a learning curve but worth installing the kernel and just lxde (the desktop environment used by Lubuntu) and see if that runs. If so, add things until it doesn't then take a step backwards. :)

Incidentally, Lubuntu does have long-term support now, although it's for three years, not five, so 16.04 LTS is supported until 2019. Yes, your current install is well out of date and yes it is and will become more vulnerable security-wise. Advise you do something. Could be your days in the Ubuntu fold on that machine are at an end, though ...

---

### Post by sudodus on 2016-09-14
You can speed up the installation, if you use other methods, for example connect the hard disk drive to another (and faster) computer and install a newer version of Lubuntu. I have tested the current version, 16.04.1 LTS in old computers (but not quite that old yet).

There is enough RAM, and the Ubuntu flavours are portable, if you do avoid installing any proprietary driver (for graphics).

You can try the mini.iso as suggested by Bucky Ball, or get an installed system directly via this method:

[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](https://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300)

or this method: [OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

These two methods have the advantage, that they are fast and easy to use in old computers, and after installation you should be very restrictive to install program packages. Install only what you really need, and there will be more space and horsepower for the tasks you want to run.

-o-

But if you still want Lubuntu 12.04, we cannot stop you. It should be safe, if you avoid 'looking outside your home network's firewall'.

And the maybe cloning with ***Clonezilla*** is an alternative: Boot into a Clonezilla CD/DVD/USB drive and clone the whole drive.

After that you boot into a live linux system with a graphical desktop environment, for example Lubuntu, and run ***gparted*** to expand the partition to use the whole new drive, [GrowIt.pdf](http://phillw.net/isos/linux-tools/uefi-n-bios/GrowIt.pdf)

---

### Post by SageOfSmeg on 2016-09-19
Thanks to everyone who responded.

I have decided to replace the old 4GB HDD with an 80GB drive, which should be more than adequate for my needs. With that in mind, perhaps it may offer me more options to upgrade from Lubuntu 12.04 to more recent releases.

However, I am still restricted by the old hardware (Pentium II 350 MHz, Non-PAE, 750MB RAM, USB 1, PC100 "PC-Chips Motherboard M726", CD-ROM but no DVD drive).

So as a follow-up question - would the latest Lubuntu/Ubuntu releases support such old hardware (from my research, 14.04 with forced PAE might work)?

---

### Post by sudodus on 2016-09-19
I am rather sure that Pentium II is capable of PAE. If there is a limit, it would be in the motherboard.

If it works with a ***modern version of Ubuntu***, fine. (I think the CPU works without the boot option forcepae.)

If it does not work, you can try ***Debian***, which still provides a non-pae kernel. Don't use the default desktop environment, but try for example LXDE, or even simpler, only a window manager, for example Fluxbox or Openbox.

---

### Post by SageOfSmeg on 2016-09-28
I have successfully installed Lubuntu 14.04 on a new 80GB HDD. It runs very slowly but so far appears to be working okay.

---

### Post by sudodus on 2016-09-28
Congratulations :-)

If you feel that this problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

-o-

If you have another problem, it is better to start a new thread with a good title to describe the problem.

---

