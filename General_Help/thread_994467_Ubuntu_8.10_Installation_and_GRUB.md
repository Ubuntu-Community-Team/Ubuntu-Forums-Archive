---
title: "Ubuntu 8.10 Installation and GRUB"
date: 2008-11-26
forum: General Help
---

### Post by polysleep on 2008-11-26
Hello all any help would be grand.

I have 3 HDD 1st is an IDE with Windows XP installed, 2nd IDE with Ubuntu Installed, 3rd Sata as my "file server" basically a place I store all my things I don't want to loose if the system crashed.

Ok, I'll try to make this short. All was working fine until a problem with Wine and running a windows game. System locked up etc... The GRUB was working fine no issues until this happened.

Tried to load into Win XP error NTLDR was missing. After some searching and trials, I decided to just reinstall win xp.

It reinstalled on same drive but drive letter switched to d: and the "server drive" switched to c:

I went ahead and reinstalled Ubnuntu on the 2nd IDE drive and set the GRUB for the main drive, which turns out to have been the "server drive".

So now I'm really messed up. I reinstalled windows again because the GRUB issue came back up with NTLDR missing. 

Now I have win xp back on c: ok great.... but now when I try to access the "server drive" it shows as it hasn't been formatted and do I want to format it now?

I never told the install to touch the "server drive".

Went into bios and disabled each drive and tried to boot to each drive individually. The IDE with win xp boots fine, the 2nd IDE won't boot at all, and the sata drive "server drive" shows black screen with the word GRUB and that's it.

Now for the question.... how in the world do I fix this mess? I cannot stress the severity of not loosing anything on the sata drive or it's my hide with the wife.

Thanks in advance....

---

### Post by phidia on 2008-11-26
I would boot with a live cd and mount each drive to see what's there before going further. 

To fix this I think you need to enter fdisk -l in a linux terminal and then make sure you understand how grub numbers your drives and partitions. After that restore grub. See the grub  restore guide [here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by logos34 on 2008-11-26
+1 Phidia's suggestion.

It appears grub is on the mbr of the sata disk but the drive numbers are all screwed up at boot, so stage1/1.5 can't find /boot/grub/menu.lst.  You might want to disconnect the other drives before reintalling grub from the live cd, just to make certain it goes on the ubuntu drive.  (just unplugging the power cable is enough).

You can remove grub from the server disk by using the 'uninstall' option in Super Grub Disk (see link my sig).  Easier is to use the dd command:

> sudo dd if=/dev/zero of=/dev/**sdc** bs=446 count=1replace 'sdc' with whatever your server disk is designated.  Be careful with the command.

---

### Post by sedawk on 2008-11-26
Check this thread:
[http://ubuntuforums.org/showthread.php?t=987306&highlight=testdisk](http://ubuntuforums.org/showthread.php?t=987306&highlight=testdisk)

Looks like you put a grub boot block to the sata drive, also
clearing partition table. This can be fixed as no data
inside the partitions is lost.

May be this can help too:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

When you have a Live-CD you can also try other things like
backing up a compressed image of the whole sata drive to an external
usb drive or similar before touching the sata drive ...

---

### Post by polysleep on 2008-11-27
Ok so I followed the first suggestion and from a what i'm thinking is a live-cd. which allows you to try ubuntu on the system before installing it. I ran the fdisk -l and the response is:

cannot open /dev/sda
cannot open /dev/sdb
cannot open /dev/sdc

Now i'm guessing here but this doesn't look good does it?

---

### Post by caljohnsmith on 2008-11-27
Polysleep, how about trying:
```
sudo fdisk -l
```
In other words, you have to run fdisk as root in order for it to work. :) Also, please identify the Windows/Ubuntu partitions that fdisk lists. Since you mentioned that you can set your BIOS to boot whichever drive you choose, how about booting the Ubuntu drive on start up, but use the following instructions to install Grub to the MBR of the Ubuntu drive so it is bootable:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd1,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Then reboot, set your BIOS to boot the Ubuntu drive, and you should at least get a Grub menu on start up if all goes well. Let me know if you get that far or if you run into problems.

---

### Post by polysleep on 2008-11-27
Ok I got everything sorted. I used the win xp install disk to run repair and did a bootfix. That fixed the windows problem, then i did the same thing to the "server drive" and it is working now. 

thanks so much to you guys for help.

---

