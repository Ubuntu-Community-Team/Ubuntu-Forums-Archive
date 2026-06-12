---
title: "grub error 17"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by tons-of-funs on 2009-10-14
my friend is installing ubuntu 9.04 64 bit on his asus x83v, after he "installed" it, ubuntu did not tell him to restart his computer after, i knew something was not right, his disk are in the right order, he tried to install ubuntu studios and that told him that he didnt have a cd drive....well then wtf was he booting from? anyways he is on ubuntu 9.04 live session, please please some one help. if i am unclear please ask as many questions as you need

---

### Post by tommcd on 2009-10-14
> **tons-of-funs said:**
> my friend is installing ubuntu 9.04 64 bit on his asus x83v, after he "installed" it, ubuntu did not tell him to restart his computer after, i knew something was not right, his disk are in the right order...
What do you mean by "his disk are in the right order"? Please list how many hard drives are in the computer and what partition you installed Ubuntu on. From the live CD open a terminal: applications > accessories > terminal, and post the output of:
```
sudo fdisk -l
```
This will list your drives and partitions. Tell us what partition Ubuntu was installed to, and what happened when the installer installed grub.
 Are you getting grub error 17 when you boot as in the title of your thread? Here is brief explanation of grub error 17:
[http://members.iinet.net.au/~herman546/p15.html#17](http://members.iinet.net.au/~herman546/p15.html#17)
It is possible that the installation did not finished or got screwed up somehow. If grub is the only problem then you can try reinstalling grub from the Ubuntu live CD:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

---

### Post by tons-of-funs on 2009-10-14
what i meant by the disc were in the right order was, i read a different solution and it said that one of the possibilities of getting grub error 17 was discs not being in the right order, and i did type that code in and it didnt say they were out of order, i will look again for you, thank you for your speedy reply
there is only one hard drive

---

### Post by tommcd on 2009-10-14
Having only 1 hard drive makes troubleshooting this a bit easier. So try reinstalling grub from the live CD as per the link in my last post, then try to boot Ubuntu from the hard drive. If that doesn't work the post the exact errors you get when you try to reinstall grub and when you try to boot from Ubuntu on the hard drive.

---

### Post by tons-of-funs on 2009-10-14
my friend used an external g-parted disc to re-format the hard drive, he is installing ubuntu studio and so far *fingers crossed* it seems to be working

---

### Post by sirjables on 2009-10-14
Hello, everyone.  I am the friend that tons is talking about.

Everything seems to be working fine.  I had to reformat with GParted, but it seems to be going smoothly now.  Thanks for the help.

EDIT:  Actually, the installer of Ubuntu 9.04 seems to be stuck at 94% during the installation of the GRUB boot loader.

---

### Post by tommcd on 2009-10-14
> **sirjables said:**
> 
EDIT:  Actually, the installer of Ubuntu 9.04 seems to be stuck at 94% during the installation of the GRUB boot loader.
So did the install complete? Are you able to boot Ubuntu?
If not, then boot from the live CD. First, just to rule out a bad CD as the source of your problems, run the option from the main menu of the live CD that says: **check disc for defects**. This will take a minute or 2 to run. If it passes with no errors, then the CD is good.
Next, see if you can reinstall grub from the live CD as per the link I gave earlier. 
It seems odd that grub would have so much trouble installing on a computer with just 1 hard drive. Make sure you have no other storage devices connected to the computer during the install (i.e., no flash drive, memory card, or external hard drive). 
You can also try installing grub from a Super Grub Disc if all else fails:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
The super grub disc can also be used to boot into Ubuntu on the hard drive. This will allow you to check if Ubuntu installed ok, and the only problem is grub.
Actually the Ubuntu live CD has the option to boot from the hard drive on the main menu:
[http://www.psychocats.net/ubuntu/images/installingjaunty02.png](http://www.psychocats.net/ubuntu/images/installingjaunty02.png)
If you still can't get grub installed, and still can't boot Ubuntu, try booting from the live CD and choose the option to boot from the first hard drive. This will (hopefully) verify that Ubuntu installed ok, and the only problem is grub.
There may be something else wrong with the install besides grub.

And welcome to the Ubuntu forums!

---

### Post by tons-of-funs on 2009-10-14
i have already tested the disc for errors and it is fine, there is just some unknown conflict with grub, what i dont understand is why would ubuntu studio work fine but not ubuntu :confused:
all well i think he is doing g-parted again and gonna just install ubuntu studio with a theme for regular ubuntu

---

