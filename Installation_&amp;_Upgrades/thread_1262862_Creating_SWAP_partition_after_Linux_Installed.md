---
title: "Creating SWAP partition after Linux Installed"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by churro on 2009-09-10
I didn't create a swap partition when I first installed linux, if I re-size a not really used up partition "not the partion i installed linux"  and format it as a swap partition.

Will my linux os auto-detect the swap partion and use it? Or do I have to enter some commands in terminal?

I'm a newbie, Help me out.

Using Jaunty

---

### Post by dstew on 2009-09-10
I don't think linux will auto-detect a new swap partiton, but it is easy to inform it of the change.

Once you have an installed system, you will need to create a new partition, and alter your /etc/fstab file to make it use the partition at boot time. You can make a partition with any partition editor. I like gparted, and use the gparted live CD. I don't think you need to format the partition. If you can, designate it as "use for swap", but if you can't, don't worry about it.

Once you create the partition, you can inform your system to use it this way. Say you created /dev/sda3 to use as swap. Try these commands:```
sudo mkswap /dev/sda3
sudo swapon /dev/sda3
```That makes the partition active as swap space on your running system.

To make it use the new partition as swap space on reboot, edit your /etc/fstab file. To use gedit in the graphical user space, get a command line with alt-F2. Then enter the command```
gksudo gedit /etc/fstab
```Add to the file this line:```
/dev/sda3  none swap  sw  0 0
```Save the file, close the editor and reboot. Once you have used some programs, check to see if swap is being used with the **free** command. [Here]("https://help.ubuntu.com/community/SwapFaq") is a nice reference about swap.

---

### Post by churro on 2009-09-10
thanks a lot for your help dstew :KS

I will try this when I get home from work

---

