---
title: "NVMe SSD with old i7"
date: 2017-12-04
forum: Hardware
---

### Post by allcoms on 2017-12-04
I have an old i7 950 (3Ghz) desktop based around an ASUS Sabretooth X58 mobo that I feel would still be quite a usable machine if I could get some faster storage working in it than the current spinning disk its using.

The board features 2x SATA3 ports but they're Marvell. I tried a SAMSUNG 850 SATA3 SSD with it and it topped out at 400MB/s read when it should be getting 500+ MB/s plus. Whilst this SSD works fine under Windows 10, running off the SSD is very unstable under Ubuntu 17.10 when using the (Intel) SATA2 ports or the Marvel ports. Ubuntu runs fine off a regular HD . I tried disabling NCQ for the SSD under Ubuntu 17.10 which made things a bit more stable but not enough to prevent frequent freezes.

My questions:

* Has anyone here tried the 250GB SAMSUNG 960 EVO M.2 NVMe SSD with a Supermicro AOC-SLG3-2M2 PCIe NVMe adapter under 17.10? Are these two compatible?

* Should this combination of SSD and M.2 adapter work on such an old CPU/mobo? I think this board dates back to about 2010 and so it only has PCIe v2.0 slots whilst that SSD and adapter are sold as PCIe gen 3.0 devices. PCIe is supposed to be backward compat and I realise I may not be able to harness the full speed of the device on such an old mobo/CPU but as long as it brings better performance than using a mechanical drive and it is reliable then I think it would be a worthwhile investment.

I've pretty much given up on getting a SATA SSD to work reliably with this machine but if anyone has a similar computer currently running with a modern SATA SSD then I would be interested in hearing what kernel/SATA options you had to use to avoid freezes.

Thanks

---

### Post by gordintoronto on 2017-12-04
I'm running Xubuntu 17.04 on a GA-MA770T-UD3P motherboard from 2009, with a 250 GB Samsung SSD 750. The motherboard has ACPI issues, but after solving that, the system is rock solid.

I used sudo to edit /etc/default/grub, adding "acpi=off" to the line which contained "quiet splash". Then I ran: sudo update-grub

---

### Post by allcoms on 2017-12-26
Thanks for your reply gordintoronto!

As I said in my post, I had totally given up on using the onboard SATA, knowing that even if I did get it working reliably it still wouldn't be full speed. I now have my NVMe drive and so I can reply to myself.

Yes, it is possible to use NVMe devices sold as/for PCIe 3.0 with a mobo that only supports PCIe 2.0. I am using a 250GB Samsung 960 EVO M.2 drive with a StarTech x4 PCIe to M.2 adapter and it works great. hdparm says I get about 1400 MB/s read speed. That isn't using the drive to its full potential but it sure beats 400 MB/s (via the unreliable onboard SATA3) at best

HOWEVER

Linux didn't support NVMe until 2012 so if you have a mobo that predates 2012 (most BIOS-based mobos) then it probably won't support booting directly off NVMe. That was the case for me as I have a BIOS mobo from 2010 so I had to create a syslinux bootable USB drive. I have read GRUB can have issues booting off NVMe and syslinux is much easier to configure than GRUB too.

Here is a guide to creating a syslinux drive:

[https://agentoss.wordpress.com/2011/02/28/how-to-create-a-bootable-linux-usb-drive-using-extlinux/](https://agentoss.wordpress.com/2011/02/28/how-to-create-a-bootable-linux-usb-drive-using-extlinux/)

A few things to note if you follow that guide:

The author uses quite an old version of syslinux/extlinux but I would recommend using the latest testing or stable version. I used the latest testing version of syslinux - 6.04-pre1.

When you get to installing the MBR, it is located within the bios/mbr subdir of the syslinux source tarball and the extlinux script to run to install extlinux is under the bios/extlinux dir.

You will need to copy both the Ubuntu kernel and initrd.img onto the USB (or SATA) syslinux drive. My extlinux.conf APPEND line looks like:

> APPEND rw root=/dev/nvme0n1p1 initrd=initrd.img

Next time I install Arch I'll be using syslinux instead of GRUB.

---

