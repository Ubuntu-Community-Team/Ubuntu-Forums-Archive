---
title: "USB Hard Drive Installation Problems - Ubuntu 8.10"
date: 2008-12-02
forum: Installation &amp; Upgrades
---

### Post by mdszepher on 2008-12-02
I have a 160GB Western Digital USB Hard Drive, and have tried multiple times to make it a bootable installation I can take anywhere.  The "Create a USB Startup disk" tool will not even identify my USB Hard Drive, and other ways I have read on installing Ubuntu only lead me to a Error 17 from GRUB.

My goal is to have a Ubuntu installation on my USB Hard Drive that allows me ot save my work, instead of booting from a Live CD as I am doing now.  What can I do to make this work?  I have a 64 bit disk of 8.04 if there is anything I can do from that, as the computers I will be using this on are all 64 bit CPUs.

---

### Post by inobe on 2008-12-02
hi, is this the article you are looking for ?

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by mdszepher on 2008-12-02
Not sure - I'd check GRUB on the USB Drive, but I only see a Lost and Found in one partition, and "ldlinux.sys" on the other.

---

### Post by inobe on 2008-12-02
another way that is much easier would be virtualization, vmware maybe ?

this would allow ubuntu to run on windows within vmware !

it will not affect windows in any way...

---

### Post by mdszepher on 2008-12-02
I've used VMware and Virtual PC before, but they require me to be logged in, or have the program already installed.  In the situation I am in, I will need to have the OS installed directly on the USB disk without virtualization.

---

### Post by inobe on 2008-12-02
yes, you can at least use the external drive as the vm drive, the only exception' the space vmware would take up on c: !

you could also boot of a thumb drive ?

that's basically all i have for ideas' i tend to avoid situations that require hit or miss scenarios and only wish to offer better solutions, i hope some of may suggestion may prove useful.

good luck

---

### Post by caljohnsmith on 2008-12-02
Have you tried installing Ubuntu to the USB drive with the normal Ubuntu installer, but when you get to last stage of the installation process, click on the "advanced" button to specify where Grub gets installed? If so, try that, and specify to have Grub installed to /dev/sdb or whichever is your USB drive. Once the installation is done, set your BIOS to boot the USB drive, and you should at least get the Grub menu on start up if all goes well. If you get a Grub error 17 when booting Ubuntu from the menu, that is usually really easy to solve. How about seeing if you can get that far first and we can work from there if you want.

---

### Post by mdszepher on 2008-12-02
I may be that far already.  I installed Ubuntu using [this method]("http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/"), and I only see the GRUB error 17 when I boot from the USB drive.

---

### Post by caljohnsmith on 2008-12-02
> **mdszepher said:**
> I may be that far already.  I installed Ubuntu using [this method]("http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/"), and I only see the GRUB error 17 when I boot from the USB drive.
That's actually a different method than what I was talking about. Have you tried booting your Live CD, choose the "try Ubuntu without making changes" type option, and then when you boot to the Ubuntu desktop, double-click the Installer icon on the desktop? That's what I was referring to. How about trying that and let me know how it goes.

---

### Post by mdszepher on 2008-12-02
Will do.

I'll have to do it with my 8.04 64 bit disk, shouldn't make much of a difference, should it?

---

