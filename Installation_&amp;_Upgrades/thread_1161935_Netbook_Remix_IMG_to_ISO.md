---
title: "Netbook Remix IMG to ISO ??"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by gnothi on 2009-05-17
I'll endure whatever your contemptuous flames, because I really just wish a solution. Please, detail how to go from IMG file to bootable DVD.

In experimentation, I've installed UNR onto a VM in VirtualBox, which runs sluggish on a 1.8GHz PC. I also installed UNR from standard Jaunty repositories, only to find that it's a kludge that doesn't properly implement a complete and native UNR (compared to the VM install). I've also tried utilities like *ccd2iso*, *Kiso*, and Windows *Image Master* to convert the IMG file to ISO, to no avail.

**PLEASE: Can I install UNR onto a PC that's too old to boot from a USB drive, but can boot DVD?**

Has Canonical made it impossible to convert the UNR 9.04 **IMG** file to a standard **ISO** file for burn and boot from DVD?

?

---

### Post by snowpine on 2009-05-17
Running the following terminal command in an existing Ubuntu Jaunty install will give you exactly the same system as installing UNR from scratch:

> sudo apt-get install ubuntu-netbook-remix

If UNR seems "sluggish" in your tests, that's because it is. It is an extra layer on top of Ubuntu Gnome, which is arguably one of the "heaviest" linux distros in existence. I would not recommend Ubuntu UNR for older hardware. If your computer is too old to boot from USB, it is definitely too old for Ubuntu UNR! If you want to post your system specs, I would be happy to recommend a distro for you.

---

### Post by gnothi on 2009-05-18
> **snowpine said:**
> Running the following terminal command in an existing Ubuntu Jaunty install will give you exactly the same system as installing UNR from scratch:
> sudo apt-get install ubuntu-netbook-remix

I've tried that. The result is **not** a complete and native UNR, even on a clean install of Jaunty. Close, but not quite.

UNR is sluggish on a virtual machine in [_VirtualBox_](http://www.virtualbox.org/). UNR should be more responsive running natively on my PC.

So, there's no way to convert the IMG to ISO for boot from DVD?

:(

---

### Post by Textureglitch on 2009-06-01
> **gnothi said:**
> Please, detail how to go from IMG file to bootable DVD.


On windows you can use the freeware program [ImgBurn]("http://www.imgburn.com/"). That'll pretty much burn every image format known to man onto an optical disc.

---

### Post by Sav on 2009-08-05
Use nrg2iso

---

### Post by Qagak on 2009-08-13
Have you tried taking a look at [https://answers.launchpad.net/ubuntu/+question/69754](https://answers.launchpad.net/ubuntu/+question/69754) ? 

Maybe this will help?

---

### Post by GeorgePRPE on 2009-09-09
VirtualBox has a clean solution:
 
VBoxManage convertfromraw <filename.img> <outputfile.vdi>

Now you can add the vdi file as a slave disk to your VM, then reboot and make it to boot from the slave disk. Ready to install!

---

### Post by PANGERAN on 2010-01-13
Here are the steps.

1. Run the command to create a bootable VDI image (without quotes):
“VBoxManage convertfromraw ubuntu-netbook-remix-i386.img ubuntu-netbook-remix-i386-live.vdi”
2. Run the command to create a new empty VDI image where to install the image with 8GB space:
“VBoxManage createhd -filename ubuntu-netbook-remix-i386.vdi -size 8000&#8243;
Note: you can use -register option at the end of this command or register this VDI file from the VirtualBox later.
3. Create a new VM using the ubuntu-netbook-remix-i386-live.vdi (use the existing vdi option)
4. Attach the ubuntu-netbook-remix-i386.vdi as a Primary Slave
5. Start the VM (boot)
6. Install
note: Install will automatically install into the Primary Slave drive.
7. Shutdown the VM
8. Remove the ubuntu-netbook-remix-i386-live.vdi from the VM setting, and make the ubuntu-netbook-remix-i386.vdi as the Primary Master.
9. Restart the VM

source: 
[http://platonic.techfiz.info/2009/04/24/tip-to-convert-img-to-iso-try-on-ubuntu-netbook-image/](http://platonic.techfiz.info/2009/04/24/tip-to-convert-img-to-iso-try-on-ubuntu-netbook-image/)

[http://platonic.techfiz.info/2009/04/26/ubuntu-netbook-on-virtualbox/](http://platonic.techfiz.info/2009/04/26/ubuntu-netbook-on-virtualbox/)

---

### Post by Cheesemill on 2010-01-13
You could always just download the .iso :)

---

