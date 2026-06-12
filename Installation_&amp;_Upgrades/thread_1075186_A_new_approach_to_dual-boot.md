---
title: "A new approach to dual-boot"
date: 2009-02-20
forum: Installation &amp; Upgrades
---

### Post by GaretJax on 2009-02-20
... unfortunately it didn't work :(

I know there are probably too many posts on dual-booting, but I took a direction that I hadn't seen before and I thought I'd share what not to do.

I bought a Dell Mini 9 with Ubuntu 8.04 (hardy) pre-installed. I installed XP SP3 in a small partition at the end of the hard drive for things like watching streaming Netflix and other small things.  I want grub to be my primary boot loader but XP keeps hijacking it.

Here is what I did that didn't work. Dell Mini came pre-installed with Ubuntu. I booted off a flash drive with Gnome Parted and made a two NTFS partitions at the end of the disk.

Here is a picture of how my hard drive is now divided:
part0: Dell Utility
part1: Ubuntu (boot)
part2: NTFS drive to share data between OS's
part3: NTFS, XP SP3

I then moved the boot flag over to part3. Rebooted and installed XP on part3. After XP was installed I then went back into Gnome Parted and gave the boot flag back to part1 (Ubuntu) and modified Ubuntu's boot menu and added XP.

I was initially very happy because I tested this by booting into both XP and Ubuntu several times. Each time I booted into XP and rebooted, I was always brought back to the grub boot loader which is located on part1. It seemed that XP was going to play nice :D (yeah right!)

It turns out that XP will sometimes move the boot flag to its own partition after installing upates or making administrative changes to XP. Each time this happens I have to reboot into Gnome Parted to move the boot flag back to Ubuntu. Frustrating. 

Most all the help I've seen tells me that I should install XP first then install Ubuntu but there is no way I am going to redo any installs.

So what is the easiest way to correct my situation? I know there is lots of documentation on how to dual-boot but I am not even sure what the recommended scenario is here.

Which partition should grub be on? How do I move it there? How can I be sure that XP won't hijack it anymore?

*** n00b alert ***
I pretty much know how to do anything in Windows but in Ubuntu I will essentially need (I hate to say it) some hand-holding.

Thanks in advance.

---

### Post by caljohnsmith on 2009-02-20
It sounds to me like you are using the Windows MBR (Master Boot Record) to boot the Grub which must be installed to the boot sector of your Ubuntu partition. I would recommend installing Grub to the MBR, that way it won't matter which partition gets the boot flag. Try running these commands from your Ubuntu install:
```
sudo grub
grub> find /boot/grub/stage1
```
The command above should return your main Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,2), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
That should install Grub to the MBR, and then you won't have to worry about which partition gets the boot flag. How about giving that a shot and let me know how it goes.

---

### Post by GaretJax on 2009-02-20
Here, I will post my results from the terminal.

> grub> 

grub> find /boot/grub/stage1
 (hd0,1)

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.


It looks like whatever it did, it did it well.  So now, exactly what did it do, if you do not mind me asking?

---

### Post by caljohnsmith on 2009-02-20
Those commands you ran install Grub to the MBR (Master Boot Record) of your HDD so that when the HDD drive boots, you will for sure get Grub. Did you trying rebooting after running the Grub commands? Can you boot Ubuntu and Windows OK?

---

### Post by GaretJax on 2009-02-20
Yes I'm able to boot between both operating systems using grub.  As far how permanent this is, time will tell but I'll also take your word for it.

Now if we were to look at my hard drive picture again, could you tell me what has changed?

part0: Dell Utility
part1: Ubuntu
part2: XP SP3

When I boot my computer and the MBR is read, which partition is passed the baton to load grub?  In other words which partition is grub installed on? 

I would like to know this because if one day I delete my XP partition, does all the grub functionality go with it?

---

### Post by caljohnsmith on 2009-02-20
> **GaretJax said:**
> 
part0: Dell Utility
part1: Ubuntu
part2: XP SP3

When I boot my computer and the MBR is read, which partition is passed the baton to load grub?  In other words which partition is grub installed on? 

I would like to know this because if one day I delete my XP partition, does all the grub functionality go with it?
Grub in the MBR points to the Ubuntu partition for its boot files, so which partition has the boot flag is fortunately irrelevant now. But to answer your question, it is your Ubuntu partition that has Grub installed in it, or more specifically it has Grub's boot files. If you delete your XP partition, then you won't lose Grub on start up so long as the Ubuntu partition number doesn't change. If the Ubuntu partition number changes, you would need to reinstall Grub to the MBR again and have it point to the new partition for its boot files. You can do that with the commands in post #2, because using the Grub "find" command will find the Ubuntu partition for you; or more specifically, that "find" command finds which partition has Grub's boot files. If you have any more questions, let me know, but otherwise cheers and enjoy your dual-boot setup. :)

---

### Post by GaretJax on 2009-02-20
I can sleep soundly tonight :).  Thanks for all your help caljohnsmith.

---

