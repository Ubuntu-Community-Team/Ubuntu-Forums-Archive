---
title: "is it possible to install Ubuntu on USB and run it  in Windows GUI"
date: 2008-11-04
forum: General Help
---

### Post by waheedrafiq on 2008-11-04
I want to be alble to learn Linux more so i want to install Ubuntu on USB pen drive and run it  in Windows GUI 

is this possible ?

---

### Post by scouser73 on 2008-11-04
Here is the info you need for Linux on a USB stick; [http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

---

### Post by waheedrafiq on 2008-11-04
many thanks for your reply I have prior posting this tread visited this site via google search and I can't find my answer .

the site link to this page [http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/](http://www.pendrivelinux.com/2008/11/01/ubuntu-810-install-using-the-built-in-usb-installer/)

this is what i want to know " you have login to windows , inserted your usb drive , and up comes a windows that contains Linuxs " you can work witin this windows as if you where running linux os from hard drive. I don't want to close my windows OS and then boot directly from the USB drive thats not what I want to acheive. , what i am looking at is more  vmware but on a USB pen drive. "


i hope the above makes sense

---

### Post by prshah on 2008-11-04
> **waheedrafiq said:**
> I want to be alble to <..> install Ubuntu on USB pen drive and run it  in Windows GUI 

Most virtualisation software do not have the option to boot from USB directly. 

However, you can mount your ISO image of the live CD in (for example) VMWare and enjoy playing around with Ubuntu in Windows (Hardware permitting).

If you are looking for a "portable" usb version of VMware that you can carry around with you and use from any Windows system, you can create a VMWare "player" file, but you will need to install the (free?) VMWare player on every Windows system you want to use the image on.

---

### Post by fatphilthethird on 2008-11-04
You can run linux off a usb drive from within windows by using QEMU, [http://bellard.org/qemu/](http://bellard.org/qemu/)

Try this tutorial [http://www.pendrivelinux.com/2007/11/30/qemu-persistent-knoppix/](http://www.pendrivelinux.com/2007/11/30/qemu-persistent-knoppix/) which I think does what you're after.

I've tried getting Xubuntu running under QEMU following this tutorial, but couldn't get it to work: [http://ubuntuforums.org/showthread.php?t=344444](http://ubuntuforums.org/showthread.php?t=344444)

Fat

---

### Post by waheedrafiq on 2008-11-04
Billions of thank you fella's  I think you have pretty much answer my queries 

go linux , go linux :)

---

