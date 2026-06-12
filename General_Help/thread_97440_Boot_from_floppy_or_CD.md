---
title: "Boot from floppy or CD"
date: 2005-12-01
forum: General Help
---

### Post by moctile on 2005-12-01
I'd like to install Ubuntu on a 40 GB external USB hard disk drive so that I can carry it around with me from machine to machine. At work, at home, at my girlfriend's house, all my apps, configurations, projects will be the same. However, booting from a USB device is sketchy and doesn't even work on all computers. So I'd like to set up a floppy disk and/or CD that I can use to boot the machine. The point is to have the system on a portable external drive, but at the same time to be able to boot reliably.

The problem is, I have no idea how to do this. I'm hoping someone can suggest a way to go about it, or even just the names of some commands/files/utilities I could research. I've found that you can download various kinds of bootable floppy images, but once it started booting, how would you get it to use the USB drive as the root of the operating system?

I would be grateful for any help with this.

Thanks,

E

---

### Post by odin on 2005-12-01
I'm not sure about this but have you tried a live cd and then try to acces the usb?

I've never used a live cd in my life but what I understood about it you should be able to do it in that way.

---

### Post by akiro.yamamoto on 2005-12-01
While I was searching for an answer to your problem I came across this : [http://www6.tomshardware.com/howto/20051110/taking_linux_on_the_road_with_ubantu-01.html](http://www6.tomshardware.com/howto/20051110/taking_linux_on_the_road_with_ubantu-01.html)
It seems to be a review of the H2 with Ubuntu installed onto a USB drive... :smile:

---

### Post by akiro.yamamoto on 2005-12-01
But I actually think that using a live-cd and saving your files to the USB drive would be easier and faster....

---

### Post by moctile on 2005-12-01
Thanks for the suggestions. I considered using a live CD and storing my project files to the USB drive. However, to do work I have to run several servers which are designed to be able to write to /var and store configurations on /etc. There are probably workarounds, but there are so many reasons I need to be able to write to various parts of the system that after a while it would just get ridiculous. I'd be spending all my time messing around with workarounds. I'm sure live CDs are great for somethings, but for software development I doubt that they would make a good platform.

---

### Post by moctile on 2005-12-01
I saw that article on Tom's Hardware Guide too. Problem is that device to too small. I need to get it working on a real hard drive.

---

### Post by tarkus on 2005-12-01
You could install GRUB on a floppy disk and ask it to boot from the external hard drive (assuming that it can see USB hard drives)

---

### Post by Bachstelze on 2005-12-01
Boot from a Live CD, mount your USB drive, and use the chroot command.

---

### Post by moctile on 2005-12-01
Installing Grub -- that sounds promising. I'll try to find out if grub can see USB devices. If so, that may do it.

Using chroot -- excellent suggestion. If I were just editing text files in vi that would probably work. I'm not extremely familiar with chroot, but from what I understand it wouldn't work for what I'm doing. I'm running too many different servers and graphical tools.

E

---

### Post by Bachstelze on 2005-12-01
No, no, I think chroot is for you. What it does is changing the root folder. For example, if you have your system on /media/usb, run "chroot /media/usb" and now when you open nautilus and go to root, it will be the root of your USB drive. I have used it many times, I can tell you that it works perfectly.

---

### Post by moctile on 2005-12-01
OK, I'll try the chroot method.

---

