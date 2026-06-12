---
title: "dual boot"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by nandyboy on 2009-10-30
Friends.......Previously I had installed Oracle Enterprise Linux on my system, now I have installed Ubuntu(s) . My problem is Iam unable to boot into Enterprise Linux. This option is not being displayed while booting system. Then to get back to Enterprise Linux, I did an upgrade using the media. But then I didnt get Ubuntu. So I installed Ubuntu again. Yeah I knew Ubuuntu was already there. So this  time as well, Iam unable to get Enterprise Linux in the boot options. But I have two Ubuntu options getting displayed. 

Can anyone help me out of this so that I can have both the OS displayed at the boot menu and also only a single copy of Ubuntu exists. 
Please help me...Iam new to Ubuntu. I have searched a lot and tried many options but couldnt solve it. Iam afraid, if I unknowingly corrupt my MBR. 

Thanx in advance
Nandyboy

---

### Post by Herman on 2009-10-30
Have you installed the latest Ubuntu? (Ubuntu 9.10 Karmic Koala)?
You forgot to say what version of Ubuntu you have, and the advice you need will be different if you have an older Ubuntu.

I will assume you mean you installed Ubuntu Karmic Koala, which has just been officially released a few hours ago.

I think I would try running 'sudo grub-mkconfig' first to see if the OS prober will detect your Enterprise Linux or not.
Don't worry, because 'sudo grub-mkconfig' doesn't really do anything, it will just give you some output on your screen to show you what kind of grub.cfg file it can make for you.
```
sudo grub-mkconfig
```If you're happy with what you see, and the output from the above command indicates that OS Prober is able to detect your Enterprise Linux and that will be added to your new grub.cfg, you can run,
```
sudo grub-mkconfig -o /boot/grub/grub.cfg 
```With the -o option, grub-mkconfig will actually go ahead and write the changes to your grub.cfg so that the Enterprise Linux entry(s) will be added to your GRUB Menu and that should solve your problem.

---

### Post by Herman on 2009-10-30
If OS Prober fails to detect your Enterprise Linux, then it could be that Enterprise Linux's file system needs a file system check.
You should be able to easily run a file system check on your Enterprise Linux operating system using GParted in your Ubuntu Karmic Koala Desktop Live/Install CD.

[LIST=1]
[*]Boot your Live CD, open GParted (aka 'Gnome Partition Editor'), and right-click on the partition you want checked. In most versions of Ubuntu it is 'System-->'Administration'-->'Partition Editor'.
[*]Select 'check' from the right-click menu. If 'check' is greyed out you might need to select 'unmount first, then click 'check'.
[*]Click the 'Apply'  check mark button up on the toolbar.
[*]Click the 'Apply' button in the confirmation pop-up window
[*]Watch the reciprocating bar for a few minutes, a very large file system may take a while
[*]Click on the 'Details' triangle to expand the window
[*]Click on the triangle in front of 'Check and repair filesystem (ext3_ on ....)' for details
[*]Be sure to fully expand all details and read what has been done. If it's the Ext3 file system, GParted will have calibrated your file system and run e2fsck -f -y -v on it for you, and has run resize2fs for you to make sure your file system is the right size to fill your partition.
[/LIST]

---

### Post by nandyboy on 2009-10-30
Herman !!! Thanx a ton for your reply....Let me tell you the good news.....My problem is resolved now....What I did was mounted the device where Enterprise Linux was installed in the Ubuntu .....Then I copied the contents of menu.lst (from Enterprise) and pasted it in the Ubuntu's menu.lst. and rebooted.....BINGO....there was the option for Enterprise listed and also was able to boot into Enterprise Linux....:D

Sorry for not mentioning the Ubuntu version, I am on 8.04 Hardy...it seems the grub-mkconfig runs in the latest version. It didnt run here. Anyways...Thanx for your reply

Wait...I wanted to remove the duplicate Ubuntu OS residing in the system...How to proceed, shall I just format the partition in Enterprise?? And one more thing, I have two swap partitions...while Enterprise was booting, noticed an error relating to swap....shall I remove one of the swap partitions as well,since both Linuxs can use the same swap partition..isnt it ??

-Nand

---

### Post by Herman on 2009-10-30
Yes, you should be able to just format the partition containing the superfluous Ubuntu installation, or delete it and resize a different partition to fill the free space. I'm not at all familiar with Enterprise Linux, it seems to be a type of Red Hat. I'm used to using GParted for that type of work in Ubuntu, I'm not sure what partition editor you might use in Enterprise Linux. Just try to make sure you don't delete the wrong partition though, needless to say.

You can delete one of your swap areas too, you can tell which one to keep by running 'sudo blkid' for a list of file system UUID numbers.
Then you can run 'cat /etc/fstab' to check which one is the swap area your operating systems is using. If you delete the one that's not registered in your /etc/fstab you'll probably be able to resize some other partition to use that freed space too.

Your Linux systems will use whatever swap area(s) is/are listed in the OSes /etc/fstab file.
Linux operating systems can share the same swap area unless you're going to 'hibernate'. If you might 'hibernate' an operating system instead of shutting it completely down, you need one swap area per OS, and at least one and a half times the size of your RAM I'm told. Otherwise, two or more Linux OSes can take turns using the same swap area without any problems at all.

---

### Post by nandyboy on 2009-10-30
Hi Herman , Yeah , tomorrow I will be resizing/deleting the partition having duplicate Ubuntu. Also thank you for the suggestion on swap space. I will remove one.....

Its a very nice forum.....Will keep coming here ....:D

-Nandyboy

---

