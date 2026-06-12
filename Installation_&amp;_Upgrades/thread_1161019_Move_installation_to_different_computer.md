---
title: "Move installation to different computer"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by randyklein99 on 2009-05-16
I have been playing/experimenting with Ubuntu on an extra laptop I have.  My main laptop is still XP pro.  I am ready to convert that laptop to Ubuntu Jaunty.  I really like how I have my current installation set up and don't really want to go through everything again.  

I know this is almost impossible to do in Windows, but is there a way to simply move/clone my current installation to an entirely different PC?

---

### Post by edgeeffect on 2009-06-24
I've done this loads of times before using SuSE, Slackware, & Debian. Just by copying all the files over and tweaking the odd hostname, network address, and stuff.

But with Ubuntu, I just can't get it to start up. I don't know what's going wrong.

---

### Post by coffeecat on 2009-06-24
> **edgeeffect said:**
> But with Ubuntu, I just can't get it to start up. I don't know what's going wrong.

You need to edit /boot/grub/menu.lst and /etc/fstab. Ubuntu uses UUIDs wherever possible in both those files. Because you've moved the installation from one hard drive to another, **all** the UUIDs (for swap, / and whatever else you might have) will have changed.

Either edit those files to use /dev/sda1 type references or run 'sudo blkid' from a live CD to get the new UUIDs and substitute these UUIDs into the two files. If you go for the former option be aware that in menu.lst, instead of a root line, you have something like this:

```
uuid        blahblahblah
```You'll need to change that to

```
root    (hd0,1)
```... or whatever the appropriate (hdx,y) number is.

---

### Post by merlinus on 2009-06-24
This may work, but because the hardware is different and usually detected and set up upon installing, certain things may no longer work.  Examples might be video in addition to the uuids changing, as others have stated.

Ubuntu keeps configurations and such for apps in /home/user in hidden directories that begin with a dot (.).  You can certainly back those up and copy them over to the new install.

---

### Post by cariboo on 2009-06-24
I would suggest taking the hard drive from your spare laptop and inserting it in the new one and see what happens. If everything works without to many problems, use [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html") to create a clone of your install and install it on your new laptop.

---

### Post by edgeeffect on 2009-06-24
> **coffeecat said:**
> You need to edit /boot/grub/menu.lst and /etc/fstab. Ubuntu uses UUIDs wherever possible in both those files. Because you've moved the installation from one hard drive to another, **all** the UUIDs (for swap, / and whatever else you might have) will have changed.

Either edit those files to use /dev/sda1 type references or run 'sudo blkid' from a live CD to get the new UUIDs and substitute these UUIDs into the two files. If you go for the former option be aware that in menu.lst, instead of a root line, you have something like this:

```
uuid        blahblahblah
```You'll need to change that to

```
root    (hd0,1)
```... or whatever the appropriate (hdx,y) number is.

Yeah... I've done that but it still inundates me with errors on boot-up

---

