---
title: "Ubuntu on Asus EEE 901 Win XP?"
date: 2008-11-14
forum: Hardware
---

### Post by Zlatan on 2008-11-14
Is it worth to pay 150EUR/180USD for Asus EEE 901 Win XP edition- to remove Windows and use it with Ubuntu?
Would battery life and wireless be OK?

Thank you

---

### Post by silkstone on 2008-11-15
Unless you really need Windows, it's better to go for the Linux version which has a larger SSD.

However, Xandros is not very good for a variety of reasons, but you can install Ubuntu-eee (based on Hardy) quite easily and everything works including wireless. This version comes with the Array kernel configured for the eee PC.

I can recommend that method - I'm typing this on a 901 running Ubuntu-eee and I'm very pleased with it. If you wait a couple of weeks there will be a new version of eeebuntu - another Ubuntu variant tailored to the eee PC - but this one will be based on Intrepid. Since I'm familiar with Hardy (I run it on three other machines) I prefer it to Intrepid which still seems to have a few bugs. ;)

---

### Post by Zlatan on 2008-11-18
> **silkstone said:**
> Unless you really need Windows, it's better to go for the Linux version which has a larger SSD.

However, Xandros is not very good for a variety of reasons, but you can install Ubuntu-eee (based on Hardy) quite easily and everything works including wireless. This version comes with the Array kernel configured for the eee PC.

I can recommend that method - I'm typing this on a 901 running Ubuntu-eee and I'm very pleased with it. If you wait a couple of weeks there will be a new version of eeebuntu - another Ubuntu variant tailored to the eee PC - but this one will be based on Intrepid. Since I'm familiar with Hardy (I run it on three other machines) I prefer it to Intrepid which still seems to have a few bugs. ;)

OK, salesguy was wrong,sales price was for 900 Xandros machine:) nd now am an owner of it. I was trying to boot Ubuntu from USB on it, but there was"Missing operating system" error. It was Ubuntu Intrepid Ibex on USB burned with software in System>Administration.
What would be your recommendation?

---

### Post by Tommy on 2008-11-23
> **Zlatan said:**
> I was trying to boot Ubuntu from USB on it, but there was"Missing operating system" error. It was Ubuntu Intrepid Ibex on USB burned with software in System>Administration.
What would be your recommendation?

I just bought an eee PC 900 and downloaded and followed the directions at [http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/) 

The utility they recommend (unetbootin) is really funky BUT I erased the flash drive using Ubuntu's Partition Editor, formatted it as FAT32, then was able to successfully install the eee version of Ubuntu. Very impressive. The Xandros that came with my eee was very disappointing.

---

### Post by Zlatan on 2008-11-27
> **Tommy said:**
> I just bought an eee PC 900 and downloaded and followed the directions at [http://www.ubuntu-eee.com/](http://www.ubuntu-eee.com/) 

The utility they recommend (unetbootin) is really funky BUT I erased the flash drive using Ubuntu's Partition Editor, formatted it as FAT32, then was able to successfully install the eee version of Ubuntu. Very impressive. The Xandros that came with my eee was very disappointing.

Does not System>Administration>Create a USB startup disk in Intrepid do the same? Anyway, my 900 does not recognize it's Ubuntu on flash drive...
And BTW- aren't there problems with LAN, Wifi, webcam in Ubuntu-EEE?
Thank you

---

### Post by snowpine on 2008-11-28
Hi there,I have an eee 900ha. I've had much better luck with unetbootin than with the Intrepid usb creator, which still seems a little buggy. I would recommend ubuntu eee 8.04.1 if you're looking for a stable and easy to install OS that supports all of the eee's features out of the box. That being said, I have since "graduated" to Crunchbang on the eee: [http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/](http://crunchbanglinux.org/forums/topic/11/crunchbang-on-the-eee-pc/)

---

### Post by Tommy on 2008-11-29
> **Zlatan said:**
> Does not System>Administration>Create a USB startup disk in Intrepid do the same? Anyway, my 900 does not recognize it's Ubuntu on flash drive...
And BTW- aren't there problems with LAN, Wifi, webcam in Ubuntu-EEE?
Thank you

I'm not running Intrepid on my main system -- sticking with Hardy for now -- so I can't say. I installed the ubuntu-eee Hardy version on my eee, NOT the stock version as you described.

HOWEVER I CAN say that the ubuntu-eee packaged version includes support for LAN and WiFi (my eee PC 900 doesn't have a webcam so I can't comment on that), but everything works as advertised. It's a very easy way to give an alternative distro a try, INCLUDING being able to boot from a USB stick OR SD card, very much like you can boot Ubuntu from a CD, and you can install or run it "live" without installing. [It's NOT stock Ubuntu because they use the array.org kernel and some other customizations to make it work on the eee with no additional configuration.]

Alternatively you COULD start with the standard release of Ubuntu and go through all the steps to make all the parts work. I'm sure that would be educational...

P.S.: The next release of ubuntu-eee will be renamed because it's not an Ubuntu-sanctioned distro AND they are going to add support for other brands of netbooks. I believe the current thinking is it will be called Ion.

---

### Post by Tommy on 2008-11-29
I just re-read your posting and had a further thought...

> **Zlatan said:**
> Anyway, my 900 does not recognize it's Ubuntu on flash drive...


The unetbootin utility not only copies the .iso file to the flash drive or SD card, but it also sets the proper flags so the medium appears bootable to the computer. I'm sure if you knew the tricks you could do that manually. Even with unetbootin I found that the first attempt failed, and I started again "from scratch" using the Partition Editor to delete the partitions and create a brand-new empty fat32 partition on the SD card. I ran unetbootin again with the ubuntu-eee .iso file. THEN the computer was able to boot from the SD card.

I inserted the SD card in the eee PC and I turned it on, then pressed the Esc key as soon as the eee startup screen appeared, and chose the bootable SD card (which erroneously claims to be a USB device) from a menu. At this moment I can't remember if I also had changed the OS Install setting in the BIOS while I was installing... I definitely did when I reinstalled the stock ASUS image from a cobbled-together USB DVD drive...

There are lots of little tricks to know... if this is new to you, you should look for a "HowTo" for whichever OS you're trying to install. 

P.S.: As you can tell I've tried several things on this little machine... I bought it as a holiday gift... BUT I may return it because I think this particular unit may have a hardware defect that drains the battery.

---

