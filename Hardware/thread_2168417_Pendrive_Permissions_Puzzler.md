---
title: "Pendrive Permissions Puzzler"
date: 2013-08-17
forum: Hardware
---

### Post by fredbird67 on 2013-08-17
OK, I'm trying to create my own lightweight Ubuntu-based distro.  I've installed Ubuntu Mini ISO 12.04 and have added in the software I want in the finished product.  But I'm not doing much else on here (customizing the desktop, etc.) until I get this whole USB pendrive permissions mess sorted out.  Here's what's happening:

In Xfce, whenever I insert my flash drive into the computer, I can see the icon for the drive on the desktop -- but it's grayed out and refuses to mount.  I've tried adding in quite a few things from the repositories that sound like they should allow me to automatically mount any USB drive -- but NONE of them have given me any joy.

For some funny reason, when I installed LightDM as the login manager, for some reason, it also pulled in Unity, which I do NOT plan to keep, as I'm trying to keep the finished product fairly lightweight.  Even though I don't really care for Unity, I thought I'd try logging in in Unity and plugging it in while logged in there, and it was there that I discovered part of the problem.  In Unity, when I looked down the side panel in Nautilus, one of the folder shortcuts in there was "usb0".  I clicked that and was able to access the contents of my flash drive -- but I couldn't create any folders or documents or edit anything in there -- but at least this was a start, although I'm obviously not content to let it be like that.

Logging out of Unity and back in in an Xfce session, I found that, in Thunar, I can go to /media/sbc1 (sometimes it may be something else in the /media folder).  However, the folder icon for the my flash drive by the name I gave it (FM32GBDRIVE) has an X on it, indicating that it can only be viewed by root, and THAT is the issue at hand here.

While I could fix this for my own individual drive, keep in mind here that this is going to ultimately be a Linux distro, and as such, I need the ability for this to automatically mount as /media/(drivename) with no headaches or hacking involved.

Any suggestions?

Thanx in advance,
Fred in St. Louis

---

### Post by tgalati4 on 2013-08-17
Each desktop environment has a different framework for handling USB and external drives in general.  You need to mount the drive, make a notification pop-up, pick a somewhat descriptive name for the drive, then make it show up in a file manager.  Because you have mixed xfce and Unity, there may be conflicts.

As much as I hate to say it, I would start from scratch and only install the packages that you want to use so that you don't have conflicting USB drive frameworks.

I don't know if there is a definitive guide, but my meager searching found these two links:

[http://askubuntu.com/questions/52413/method-to-create-a-live-usb-disk-with-persistence-which-actually-works](http://askubuntu.com/questions/52413/method-to-create-a-live-usb-disk-with-persistence-which-actually-works)

[http://askubuntu.com/questions/172570/how-to-create-a-livecd-livedvd-liveusb](http://askubuntu.com/questions/172570/how-to-create-a-livecd-livedvd-liveusb)

---

### Post by fredbird67 on 2013-08-17
I don't have time to do this right now, but after much thought, since LightDM also pulled in Unity, I'm gonna test your theory either tomorrow night or Monday morning and try instead installing another login manager first, and THEN, once the USBs are mounting to my satisfaction, try replacing whatever login manager I initially chose with LightDM.  It's crazy that I have to get that on there in such a roundabout way, but I'll give it a try.

I had originally thought about LXDM, except doesn't that automatically pull in Openbox and LXDE?  If so, even though it's TOO minimalistic for my tastes, I think I'm gonna try initially going with SLIM...

---

### Post by fredbird67 on 2013-08-19
Tgalati4, I just tried your suggestion, and...no dice. ](*,)

---

### Post by fredbird67 on 2013-08-29
I finally found something that works, y'all.  First of all, I don't know specifically what combination of files allowed me to get the USBs to work.  But I did notice that, when you get toward the end of the installation of the Ubuntu Mini CD, there's a list of what all you can install.  One of those that I tried was "Lubuntu Minimal Installation", which seemed to work pretty well...that is, until I removed everything pertaining to LXDE and Openbox and was left with a system that wouldn't boot. ](*,)  In other words, I fixed one problem but wound up with another.

But then I got to thinking, "I wonder if there's a list online somewhere of the packages that make up the Lubuntu Minimal Installation, and if I can install those but leave out the parts pertaining specifically to LXDE and Openbox".  Well, I found such a list and took down every package included in that that's NOT specifically for LXDE or Openbox, and then added everything I wanted from Xfce on top of that as well as other programs that will be pre-installed in said distro...and VOILA! \\:D/  I now have the base for an Xfce system where I can mount and unmount flash drives with no hassle AND that boots up without a hitch.

---

