---
title: "install ubuntu on HP 2133 without external CD/DVD ?"
date: 2008-07-19
forum: Hardware
---

### Post by foobard on 2008-07-19
hi there

I want to buy an HP 2133 and install Ubuntu on it. But I don't have an external CD/DVD.

Is there any way to use the CD/DVD in a different laptop to do the install?

---

### Post by overdrank on 2008-07-19
> **foobard said:**
> hi there

I want to buy an HP 2133 and install Ubuntu on it. But I don't have an external CD/DVD.

Is there any way to use the CD/DVD in a different laptop to do the install?

Hi and welcome, you may look here
[https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD](https://help.ubuntu.com/community/Installation#Installation%20without%20a%20CD)

---

### Post by dave_t_uk on 2008-08-09
YES!

It is possible, I just did it this morning.  I booted and installed ubuntu-8.04.1-desktop-i386.iso using a 2GB SD flash memory card.  I did not have to buy an external drive.

To set up the flash card, I followed the instructions here:
[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

Then to walk through the install, I followed:
[https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

However, one requirement for booting the ubuntu installer is to add the xforcevesa parameter at the boot option.  Unfortunately, the linux pendrive technique outputs a bootable stick that inconveniently prevents you from adding any command line options.  However, it's easy to fix this.  Once you've created the bootable flash card, open it up in windows explorer, and edit the file 'syslinux.cfg' (on the root of the drive) in a text editor.

Near the bottom, you'll see the the line

```
ALLOWOPTIONS 0
```
Change this to
```
ALLOWOPTIONS 1
```
this will allow you to press tab at the boot screen on the 2133, and type in the parameter xforcevesa.

The install walk through is almost identical to that described in [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133), but the first few steps are slightly different, with it running from a flash card.

The rest of the setup worked flawlessly, the only thing that didn't work first time was the alsa drivers, which gave me a compile error when I tried the latest ones (alsa-driver-1.0.17), but worked fine with the previous version (alsa-driver-1.0.17rc3).

Posting this info to give my bit back for today, having learned so much from this forum and associated wikis.  Many thanks!

Dave

---

### Post by catdriver97 on 2008-08-09
> **dave_t_uk said:**
> YES!

It is possible, I just did it this morning.  I booted and installed ubuntu-8.04.1-desktop-i386.iso using a 2GB SD flash memory card.  I did not have to buy an external drive.



Thanks for posting a clearly written solution to this very common problem!  Do you mind if I add it to the wiki?  

Not everybody has an external CD/DVD drive, and I probably wouldn't have bought one for my mini-note if this tutorial had been around.

Thanks for contributing back to the Ubuntu Mini-Note community!

Erik

---

### Post by earlycj5 on 2008-08-11
> **dave_t_uk said:**
> YES!

The rest of the setup worked flawlessly, the only thing that didn't work first time was the alsa drivers, which gave me a compile error when I tried the latest ones (alsa-driver-1.0.17), but worked fine with the previous version (alsa-driver-1.0.17rc3).

Posting this info to give my bit back for today, having learned so much from this forum and associated wikis.  Many thanks!

Dave

I made note of the same thing with the ALSA drivers some time ago, I'm glad it's not just me.

---

### Post by roystondh on 2008-09-05
Many Thanks Dave_t_uk and the others posting here

I last night managed to get ubuntu 8.02 up and running on my HP2133

Only one thing to comment in the instructions is that it mentioned potential issues with the wireless connectivity when using the UK KX872AA version of hardware and I am pleased to report that I had none and was able to use the "standard" install procedure outlined in the document.

Once again thanks - nice to be using something that has a GREAT community behind it !!!


Royston dh

---

### Post by GA400 on 2008-10-15
:)By following the advice here I was able to install Ubuntu onto my 2133 from SD card.  Ubuntu is so much better than Vista.  Vista was locking up nonstop.  I nearly threw this thing through the window or spiked it into the floor with Vista.  Ubuntu is smooooottthh.  I enjoyed getting back on the command line and running the commands, and partitioning the drive.  Kinda scary at first but it was much easier than I thought.  Last time I played with Linux was about 6 years ago. It has come a long way.

Thanks Everyone!

Rich

---

### Post by thoregil on 2008-11-11
Fixed it :)=

---

### Post by PSY0NIC on 2008-11-15
One stop shop for USB install.  Downloads the ISO's and everything for you... And works.  Don't forget xforcevesa when you boot off the thumbdrive.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

---

### Post by briggsy on 2008-11-15
Just installed Ubuntu 8.10 from SD Card successfully using the instructions on [https://wiki.ubuntu.com/LaptopTestingTeam/HP2133](https://wiki.ubuntu.com/LaptopTestingTeam/HP2133)

Sadly, 8.10 doesn't support the Wireless card in the HP 2133 out of the box - this may only apply to the UK version of the 2133. Will see if anyone has fixed this.

---

### Post by windowsseven on 2008-12-16
go 2 [http://www.ubuntu2133.blogspot.com/]("http://www.ubuntu2133.blogspot.com/")

guides etc for hp 2133

---

### Post by windowsseven on 2008-12-16
Will be updated this week, be updated

---

### Post by windowsseven on 2008-12-16
Guide here!

[http://ubuntu2133.blogspot.com/2008/12/ubuntu-intrepid-ibex-810-install.html]("http://ubuntu2133.blogspot.com/2008/12/ubuntu-intrepid-ibex-810-install.html")

Very easy

---

