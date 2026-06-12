---
title: "Toshiba Portege Freezes and fans turn on high"
date: 2011-08-17
forum: Hardware
---

### Post by KsKnightmare on 2011-08-17
I'm currently running Ubuntu 11.04 64bit on a Toshiba Portege r835-p56x and occasionally when i go to shut down it will freeze and the fans will turn on high. recently it just randomly does this, the fans will get real loud then it will freeze all of a sudden. i have made no edits to the kernel or anything. 
anyone know whats going on?

---

### Post by ccurry21 on 2011-08-19
This has been happening to quite a few systems with Toshiba Portege r835-p56x with Ubuntu 11.04 64 bit . It seems to be a kernel issue: [http://ubuntuforums.org/showthread.php?t=1760568](http://ubuntuforums.org/showthread.php?t=1760568)

What kernel version are you using? ```
uname -r 
``` Shows that I am using 2.6.39-0-generic, and while I still have occasional sudden freezes where the fan turns starts turning full blast, this issue is nowhere near as frequent as it used to be. It used to happen once at day or more, but now it's maybe once a week with me.

---

### Post by KsKnightmare on 2011-08-22
ive got this kernel right now, 2.6.38-11-generic

---

### Post by ccurry21 on 2011-08-23
One thing you might want to try is to upgrade your kernel.

First, find the kernel you want to upgrade to (I upgraded to linux-image-2.6.39-0-generic, which has resulted in fewer crashes, for example):

```
apt-cache search linux-image
```Then install the kernel you choose, substituting the appropriate version numbers of that kernel for the x's:

```
sudo apt-get install linux-image-x.x.x-xx
```Then reboot your machine so the new kernel is loaded. 

I doubt this will fix the problem, but again, in my case it severely reduced it's frequency. I'm interested to know what the result is for you.

---

### Post by KsKnightmare on 2011-08-24
ok im downloading and installing 2.6.38-11 right now. so i'll let you know how it runs in a day or two.
thanks for your help!

---

### Post by KsKnightmare on 2011-08-24
ok so i installed x.x.xx-11 and i think its booting into the virtual, recovery mode or something. as soon as i start up my laptop it just hangs at the purple splash screen but i'm never able to log in, i have to hold power then i get the boot menu and i have to go to previous versions and then boot into generic. how do i set this as default? or set -10 kernel to default?

---

### Post by ccurry21 on 2011-08-25
Did mean to say you installed kernel  2.6.38-11-generic? Because you said in an earlier comment that that's the one you had before. If so, you ought to have installed something newer.

One thing you can do is use to change the bootloader settings is a graphical editor like Startup Manager if you have it, or
```
 sudo apt-get install startupmanager
```
(if you don't have it), and there's an option to set the "Default operating system." 

Or you can try to manually edit the grub configuration file (if you're using the default the boot loader):
```
/etc/default/grub
```
The line where you can change the default boot option is:
```
GRUB_DEFAULT=0
```
Replace "0" with whatever menu selection you would like to boot by default (with the first one being 0), then run ```
sudo update-grub
```

---

### Post by KsKnightmare on 2011-08-25
well I did something wrong and my computer would automatically boot into memtest and wouldnt go into the grub menu, so i couldnt do anything. but i reinstalled the os, no freeze problems yet, ill keep you posted

---

### Post by clkndk on 2012-02-13
Perhaps my reply on this older post might be interesting (still no solution though)

[http://ubuntuforums.org/showthread.php?p=11685212#post11685212](http://ubuntuforums.org/showthread.php?p=11685212#post11685212)

---

