---
title: "LiveUSB Installation"
date: 2009-10-07
forum: Installation &amp; Upgrades
---

### Post by mcgodx on 2009-10-07
Hey all,

I just purchased an HP DV2Z somewhat recently, and it does not have  CD-ROM drive.  Because of that, I was looking in to some Windows Live USB tools that I can use in order to make a bootable image for Ubuntu (since I do not currently have a Ubuntu distribution available to me).  Every time I try to create it (using different tools) it gives me the following error:

```
[   0.424001] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[   2.416039] ata1: softreset failed (device not ready)
modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

modprobe: FATAL: Could not load /lib/modules/2.6.28-11-generic/modules.dep: No such file or directory

Loading, please wait...

BusyBox v1.10.2 (Buntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Using the prompt that follows, I have determined that the file is indeed there.  Anyone know what the deal is?  I have tried 9.04, 9.10, and Linux Mint 7.

If anyone has a solution I would greatly appreciate it!

---

### Post by skatinjj on 2009-10-07
what programs are you using?

---

### Post by mcgodx on 2009-10-07
> **skatinjj said:**
> what programs are you using?

The latest test was using Linux Mint 7 using the technique here:
[http://www.pendrivelinux.com/usb-linux-mint-7-flash-drive-creation-windows/](http://www.pendrivelinux.com/usb-linux-mint-7-flash-drive-creation-windows/)

I have also tried USBuntu as well as another one, but I cannot find it now...

Fedora boots fine, although some drivers do not seem to be readily available too easily.  I can go that route, although I would prefer the ease of Ubuntu.

---

### Post by skatinjj on 2009-10-07
you can try [this]("http://unetbootin.sourceforge.net/").

I just downloaded and am getting ready to try it out.

---

### Post by mcgodx on 2009-10-07
> **skatinjj said:**
> you can try [this]("http://unetbootin.sourceforge.net/").

I just downloaded and am getting ready to try it out.

Yeah that was the other one I tried.  I tried to get the thing to work in Compatibility Mode, the boot process skips past those modprobe errors, however after a while it gets to the following line:

```
[   6.132207] eth0: RTL8102e at 0xf7cdc000, 00:21:cc:3b:f2:29, XID 24c00000 IRQ 2300
```

It then dumps me into that "BusyBox" shell after waiting a long while.

I still see the two errors about not being able to locate /lib/modules/2.6.28-11-generic/modules.dep, however that is a while up the list from where it stops at.

---

### Post by skatinjj on 2009-10-07
When the errors appear, switch consoles (ctrl+alt+F2) then

```
mount /dev/sdx (x may be a or b most likely in your case) /dev/cdrom
```

then go back to the first console (ctrl+alt+F1) and see if it continues to boot.

This is just an idea I am throwing out since I did not get the error when I tried just now.

---

### Post by mcgodx on 2009-10-07
> **skatinjj said:**
> When the errors appear, switch consoles (ctrl+alt+F2) then

```
mount /dev/sdx (x may be a or b most likely in your case) /dev/cdrom
```

then go back to the first console (ctrl+alt+F1) and see if it continues to boot.

This is just an idea I am throwing out since I did not get the error when I tried just now.

I gave that a shot, but the prompt won't come up in the extra consoles.

---

### Post by skatinjj on 2009-10-07
If a menu comes up where you can edit boot options, you try to edit the line so that it points to the usb drive.

This is my last suggestion for right now, sorry I can't be of more help.

---

### Post by mcgodx on 2009-10-07
> **skatinjj said:**
> If a menu comes up where you can edit boot options, you try to edit the line so that it points to the usb drive.

This is my last suggestion for right now, sorry I can't be of more help.

It seems like it the lines are right in the GRUB menu, but I am not 100% sure, I am not too familiar with how live images work...

If anyone can help me out I'd be appreciative.  Otherwise I may end up just going with Fedora.

---

### Post by mcgodx on 2009-10-09
Well I tried it out, Fedora had a bunch of problems with my computer, maybe I need to wait a while before I can expect a good experience.  However, I was able to create a Ubuntu VM and I used that to create a Live USB disk, and it worked just fine, so somehow the Windows clients were broken.  The only thing I can think of is that I was using Windows 7.

---

