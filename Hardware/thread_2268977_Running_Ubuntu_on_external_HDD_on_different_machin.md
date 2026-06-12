---
title: "Running Ubuntu on external HDD on different machines (BIOS or UEFI)"
date: 2015-03-12
forum: Hardware
---

### Post by alkalined on 2015-03-12
I have Ubuntu 14.04 (64 bit) installed on an external HDD, which I use on 3 different laptops (all of them more than 3 years old) without any issues.
I now got a Yoga 2 though and it wouldn't even recognize it as a boot device. After some reading and research, it sounds like the problem is the fact that the new laptops are now using this UEFI thing, instead of a regular BIOS (which purpose is apparently to make people's lives harder :)).

I found some guide on converting the ubuntu install to UEFI compatible [https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode]("https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_or_Legacy_mode")
but as far as I understand, doing this would make it no longer working on my other older laptops.

So, basically, now I'm looking for a way to make this work on any machine, be it BIOS or UEFI based.
Is this even possible at all?

---

### Post by Hulk_Joshua on 2015-03-13
set Secure Boot to "off" into BIOS and disable Fast Startup

---

### Post by oldfred on 2015-03-13
The easiest choice is to just boot it in BIOS/CSM/Legacy mode if at all allowed with that computer. 

You would have to convert install to UEFI and then install a BIOS boot loader also.
For UEFI drive must be gpt partitioned and if an older install, you probably used MBR(msdos).  And converting will erase data.

One user did create a flash drive for both, but has had issues. I think parts of grub or boot get out of sync and then cause those issues.

       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

