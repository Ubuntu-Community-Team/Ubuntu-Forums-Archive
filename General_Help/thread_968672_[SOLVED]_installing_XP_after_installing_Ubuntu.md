---
title: "[SOLVED] installing XP after installing Ubuntu"
date: 2008-11-02
forum: General Help
---

### Post by garystam on 2008-11-02
Is it possible to add Windows XP to your computer after installing the latest version of Ubuntu - this Linux release an entire and only partition on the hard drive. I just need to use XP for a couple of work programs that are not supported by Linux. Help!

---

### Post by iris-n on 2008-11-02
Yes, it is possible. Just shrink your ubuntu partition, and install XP on the available space. That will render your ubuntu unbootable, but you just need to reinstall grub, easily done with the [[COLOR="DarkOrange"]_super grub disk_[/COLOR]]("http://www.supergrubdisk.org/").

However, if you just need to run office programs (aka, not games), you'd be better off installing xp in a virtual machine. That's what I do, for one.

I use virtualbox:
```
sudo apt-get install virtualbox-ose
```

---

### Post by garystam on 2008-11-03
Thank you. Being a linux newbie, can you tell me where to go to find info on finding partition, repartitioning and how to do it on Linux?? Also, how do I use the code you sent me. :confused:Sorry, but I guess we all have to start somewhere, and any help you would provide, would be so appreciated.

---

### Post by iris-n on 2008-11-03
My bad, I should have provided you with more links. But as you haven't decided which way to install windows, I will explain both.

As to partitioning, the problem is that most guides deal with tweaking your windows partition to fit ubuntu in it, not the contrary. There's [_[COLOR="DarkOrange"]this guide[/COLOR]_]("http://www.psychocats.net/ubuntu/partitioning") on planing partitions, from which you may abstract the necessary info. The whole site is worth a check out, it's the one I first used, anyway. 

As to the program to edit the partitions, you will find it under System-> Administration->Partition Editor. You will have to run it from the live cd, as it is impossible to edit a mounted partition.

The code I gave you is the one to install VirtualBox, the virtual machine I talked about. You run it from the terminal, Applications->Accesories->Terminal, one of the most powerful environments of linux. But, if you're not pleased with the text interface, you can always install from Applications->Add or Remove Programs. You will find VirtualBox easily there. Just be sure to mark 'show all available applications'.

Hope I've helped. Any further doubts, feel free to ask.

Iris

---

### Post by cj2003 on 2008-11-03
Supporting response #2, you can try this guide:

[Booting Windows Xp as Guest inside Ubuntu Hardy both in same harddrive]("http://ubuntu-news.net/modules/news/article.php?storyid=5136")

---

### Post by garystam on 2008-11-03
I pasted your link into the package manager, and it worked fine and installed very easily. Thanks! I don't find Partition Manager under Administration, in fact there is no listing for it. Would that change by using the Live CD?

---

### Post by zoomy942 on 2008-11-03
> **garystam said:**
> I pasted your link into the package manager, and it worked fine and installed very easily. Thanks! I don't find Partition Manager under Administration, in fact there is no listing for it. Would that change by using the Live CD?


yup.  the partition manager is on the Live CD.

Also, i used this to dual boot...

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm]("http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm")

---

### Post by Monotoko on 2008-11-03
Yes it would, the LiveCD has the partition manager on it, whereas the installation doesnt (you can get it, its called GParted, but i would advise using the live CD, as none of your partitions are mounted then) 

i myself have done the same thing (installed windows with linux) a few weeks ago, it is a pretty simple process

1: Insert Live CD and boot into Ubuntu from it

2: Go to Partition manager
(System -> Administartion -> partition manager)

3: Shrink your current partition so that you have some unallocated space (enough to put windows on)

4:Shutdown and take your LiveCD out (keep it somewhere safe, cos youl need it in a bit!)

5: Boot from your windows CD, when it gets to the part where it asks you where to install, choose the unallocated space

6: you might as well go get some coffee (or another beverage of your choice) if youv done an installation before, you know it takes a while

-skip 8 hours-

Right, Windows is installed, next step:

7: Oh noez! Windows boots straight away, what do we do?
Well dont panic, your ubuntu partition is still there, just put
your LiveCD in again, and boot from it like you did before

8: Put the following code inside the terminal
```

sudo grub
find /boot/grub/stage1
[COLOR="Red"]root (hd0,1)[/COLOR]
setup (hd0)
quit
```

The bit thats coloured in red, may vary, use the location given from
```
find /boot/grub/stage
```
instead of the one up there

9: Damn, windows has gone again -.- but dont fear, its still there, at least you have access to ubuntu again

Boot into ubuntu normally (without the CD) and use in the terminal:
```

sudo gedit /boot/grub/menu.lst

```
and put your windows entry in there

you now have access to both :D

---

### Post by mickcalcara on 2008-11-03
I am thinking of adding a second hard drive to my current Linux machine. This second hard drive will contain Windows XP. Many of these how to documents talk about installing both Windows and Linux on the same hard drive. Does separate physical drives work just as well? thanks

---

### Post by garystam on 2008-11-04
If I use Virtual Box within XP, I assume that I can run Quicken programs, Microsoft office and backup my documents, etc.?? Can you backup to a USB drive, or external hard drive? I know this is more of a windows question, but would be interested to know experiences with it. Thanks.

---

### Post by iris-n on 2008-11-04
mickcalcara, it does. i had that setup at home, a computer with two hds that was running XP, I installed Ubuntu on the slave hd, and it detects and boots XP just fine. Depending on how you install the hd, the MBR may or not be erased, but **Monotoko**'s advice will work just the same. You just may have a little more trouble finding your XP install.

garystam, running xp inside a virtual machine is just like running xp by itself, except for poorer performance. you can access the cd drive and whatever hd's you have. as for usb support, it's a hurdle, kindy of messy to install. for sharing files with the host, i use shared folders, as provided by their guest additions (explained very well in their user manual).

---

### Post by garystam on 2008-11-04
> **iris-n said:**
> Yes, it is possible. Just shrink your ubuntu partition, and install XP on the available space. That will render your ubuntu unbootable, but you just need to reinstall grub, easily done with the [[COLOR="DarkOrange"]_super grub disk_[/COLOR]]("http://www.supergrubdisk.org/").

However, if you just need to run office programs (aka, not games), you'd be better off installing xp in a virtual machine. That's what I do, for one.

I use virtualbox:
```
sudo apt-get install virtualbox-ose
```
Installed XP in Virtual Box and it works great!! Thanks again.

---

