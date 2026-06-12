---
title: "Added 500GB SATA with SATA card, now system won't boot"
date: 2008-12-27
forum: Hardware
---

### Post by bp1509 on 2008-12-27
d

---

### Post by bp1509 on 2008-12-27
d

---

### Post by caljohnsmith on 2008-12-27
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and hopefully what your problem might be.

---

### Post by bp1509 on 2008-12-28
d

---

### Post by igknighted on 2008-12-28
The problem is likely that the new drive was identified by Grub as (hd0).  Previously, (hd0) was your current drive.  Try running the script again when booted to the liveCD, with the sata drive and card plugged in.

---

### Post by caljohnsmith on 2008-12-28
So it looks like you have Grub correctly installed to your 40 GB Ubuntu drive, so if you are getting a Grub error on start up with the SATA drive connected, I think you might simply need to make sure the 40 GB drive is still first in the BIOS boot order. Let me know how that goes.

---

### Post by igknighted on 2008-12-28
> **caljohnsmith said:**
> So it looks like you have Grub correctly installed to your 40 GB Ubuntu drive, so if you are getting a Grub error on start up with the SATA drive connected, I think you might simply need to make sure the 40 GB drive is still first in the BIOS boot order. Let me know how that goes.

It's not the bios order, because grub does start.  That wouldn't happen if the bios order was wrong.  However, grub does number hard drives on its own, different than bios or the linux kernel.  Since the drive strings in the grub menu don't specify the HD, it assumes the first one, and hence it fails.

---

### Post by caljohnsmith on 2008-12-28
> **igknighted said:**
> It's not the bios order, because grub does start.  That wouldn't happen if the bios order was wrong.  However, grub does number hard drives on its own, different than bios or the linux kernel.  Since the drive strings in the grub menu don't specify the HD, it assumes the first one, and hence it fails.
In my experience, that's not true. Grub sees the order of drives on start up the same as the BIOS boot order, so that's how Grub numbers the devices; Grub does not order the drives different than BIOS. And in my experience, yes, it could be a BIOS boot order problem, because I've seen the case where if a new HDD is added, and if that HDD is set first in the BIOS boot order or (hd0), and if that HDD does not have a boot loader in the MBR, the BIOS will skip over that drive and try to boot the next drive in the boot order (hd1) which could be the Grub HDD. But Grub will not boot because it is looking for its stage1.5 file on (hd0), not on (hd1), because the (hd0) value is hard-coded into the stage1 file when Grub was installed to that drive in order for Grub to boot when it is first in the BIOS boot order. That might be the scenario that bp1509 is experiencing, because I doubt his new HDD has a boot loader in the MBR at this point. Also, any problems with Grub's menu.lst are irrelevant if you get a Grub stage1.5 error like bp1509 is getting, because that means Grub doesn't even get as far as booting the stage2 file and trying to load the menu.lst.

---

### Post by markbuntu on 2008-12-28
The SATA PCI card is reordering your drives so that the first SATA card is seen as hd(0). It is important to realize that grub sees all drives as hd(x). Some of those cards have their own bios which boots after the main bios and sets those drives as sd(0) etc.

What you can try is to remap the drives in the /boot/grub/device.map like this

(hd0) /dev/hda
(hd1) /dev/sda

since the kernel will be able to distinguish between a IDE drive (/dev/hdx and and SATA drive /dev/sdx.

---

### Post by igknighted on 2008-12-28
> **markbuntu said:**
> The SATA PCI card is reordering your drives so that the first SATA card is seen as hd(0). It is important to realize that grub sees all drives as hd(x). Some of those cards have their own bios which boots after the main bios and sets those drives as sd(0) etc.

What you can try is to remap the drives in the /boot/grub/device.map like this

(hd0) /dev/hda
(hd1) /dev/sda

since the kernel will be able to distinguish between a IDE drive (/dev/hdx and and SATA drive /dev/sdx.

Modern linux kernels see all hard drives as /dev/sdx.

That aside, the above is a great suggestion.  Boot the liveCD, then run the command 'sudo fdisk -l' to show what the hard drives are recognized as.  Then map them as mentioned above, but use the devices as shown in the previous step.

---

### Post by caljohnsmith on 2008-12-28
> **igknighted said:**
> Modern linux kernels see all hard drives as /dev/sdx.

That aside, the above is a great suggestion.  Boot the liveCD, then run the command 'sudo fdisk -l' to show what the hard drives are recognized as.  Then map them as mentioned above, but use the devices as shown in the previous step.
That unfortunately won't work, although I wish it were that easy; the device.map is only used on start up if you have references to /dev/sdX or /dev/hdX in your menu.lst, so that Grub knows how those devices correspond to the BIOS boot drives (hdX). Changing the device.map file will not change how Grub sees the order of drives on start up; that is determined solely by the BIOS boot order.

---

### Post by bp1509 on 2008-12-29
d

---

### Post by markbuntu on 2008-12-29
The SATA card is pci so the bios just sees the pci and assigns it a semi-random IRQ. Then the bios on the card presents the drives to the os. It may the IRQ assignment that is changing the order of the drives, that could explain the random nature of the problem. Low IRQ, sata drive gets seen first, high irq, it gets seen second and every time you reboot it can change. You can try assigning a high fixed irq to the card in the bios and see if that fixes it.

---

### Post by bp1509 on 2008-12-29
d

---

