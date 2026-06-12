---
title: "install to clean HDD with no cd/floppy/usb"
date: 2009-02-06
forum: Installation &amp; Upgrades
---

### Post by slam888 on 2009-02-06
I want to install ubunto onto my old laptop but i havent got a cd drive or floppy and it doesnt boot from usb. It a clean HDD on it due to windows fail to boot up.
Is there a way install ubuntu using the internal HDD. 
I am able to remove the HDD and have got a usb enclosure for it.
thank for any help

---

### Post by Tim Sharitt on 2009-02-07
There are methods of booting both the Live CD and the alternate CD from the hard drive. I don't really know what to suggest, since I don't know what type of system your working from, but you can see some of the options at [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation).

Post back if you need help deciding on a way to go, or need help getting there once you have decided and I'll try to help out the best I can.

---

### Post by slam888 on 2009-02-08
I looked through the website. but cant find what i need.
the site only tell u about booting from usb or floppy drive which i dont have or have xp on the HDD which i dont have.
i got a cleaned out HDD which i need to install a boot and ubuntu. but i dont know how :S

---

### Post by boof1988 on 2009-02-08
I used to use [Unetbootin](http://unetbootin.sourceforge.net/) for this kind of thing.  But I can't seem to download/install it now.

Here are a couple of resources that might be useful for you.  I haven't used them (since I would use Unetbootin instead) but they may be helpful  for you.

[http://ubuntuforums.org/showthread.php?t=457318](http://ubuntuforums.org/showthread.php?t=457318)
[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Here's another installation guide that might be of use:
[https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive](https://help.ubuntu.com/community/Installation/FromImageLoadedOnHardDrive)

---

### Post by lha on 2009-02-08
You'll need to install Grub (or some other boot loader) to your hard drive and put installation files on it. Then you just have to put the hard drive back into your laptop and start the installer.

I'd create a partition, say sda1, that is going to be used as a swap partition when installation is completed. However, instead of formatting sda1 as swap, I'd make it ext3 and put a boot loader and the installation files on it. At this point, the hd can put back into the laptop and installation can be started. For example, create sda2 to which Ubuntu will be installed. At this point, do not create a swap partition. When the installation is completed, you can format sda1 as swap and add it to fstab.

For more details, see the following pages: [https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick") Even though this page is for installing from USB, I believe you can use these instruction in your case as well. You'll might need to do the partition trickery described above. Alternatively, see [https://help.ubuntu.com/community/Installation/FromCForUSBStick]("https://help.ubuntu.com/community/Installation/FromCForUSBStick"), [http://www.freesoftwaremagazine.com/articles/grub_intro/]("http://www.freesoftwaremagazine.com/articles/grub_intro/"), and [http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html") for detailed instructions on how to follow the procedures I delineated.

---

### Post by slam888 on 2009-02-08
I tried using Unetbootin and used the option usb drive to install onto the HD. i put it all back into the laptop then got a error saying "Remove Disc/media"

how can i install grub onto the HD without having any OS on it.

---

### Post by lha on 2009-02-08
> **slam888 said:**
> how can i install grub onto the HD without having any OS on it.

Please look at the third link in my previous post. Of course, you will need another computer with Linux (or a Linux LiveCD) to do this.

---

### Post by slam888 on 2009-02-08
> **lha said:**
> Please look at the third link in my previous post. Of course, you will need another computer with Linux (or a Linux LiveCD) to do this.

thanks sorry didnt look through all the links.
well a lot of work tonite to see if it works.
got to unscrew my whole laptop again.

---

### Post by lha on 2009-02-08
When you're able to get into grub on your laptop, you can follow the [InstallationFromLinux]("https://help.ubuntu.com/community/Installation/FromLinux") guide.

---

