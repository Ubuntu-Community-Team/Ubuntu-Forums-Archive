---
title: "Lucid installs on Medion Akoya E1222 freeze randomly."
date: 2010-09-28
forum: Hardware
---

### Post by casbahdk on 2010-09-28
I have been asked by a friend to install Linux on his Medion Akoya E1222. Interestingly, all versions of Ubuntu based distros freeze randomly on the laptop when booting from a live CD. Sometimes when the install process is installing grub, other times during partitioning, etc. I have tried passing an acpi=off boot argument, but that doesn't seem to help. I think the Akoya is what is called a Pine Trail netbook.

Does anyone have any ideas about this issue?

---

### Post by casbahdk on 2010-10-15
My problem seems to be related to this posting about USB installs:
[https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat]("https://wiki.ubuntu.com/Lubuntu/ReleaseNotes/MaverickMeerkat") it isn't just Lubuntu, however. As my friend's Medion Akoya E1222 is a netbook, I have been using an external USB CD/DVD drive to boot from an Ubuntu distro live CD, to install. My experience seems to be the same as if trying to install from a USB pen drive. The question is how do I get a version of Ubuntu installed without a USB pen drive or an external CD/DVD drive? Is there a work around to this problem? Anyone?

---

### Post by casbahdk on 2010-10-16
I installed Debian on the Okaya, with an extra primary partition as per these instructions:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Then I booted from the Lubuntu 10.10 live CD, copied the contents of a USB pen drive setup as a Lubuntu 10.10 live install to /dev/sda3 under /temp/installer (as per the above url) and edited the GRUB menu.lst file:

```
title		installer
root		(hd0,2)
kernel		/tmp/installer/casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd		/tmp/installer/casper/initrd.lz
```

Unfortunately, I can't figure out how to update GRUB (I think Debian still uses legacy GRUB) from the Lubuntu live CD. Can anyone help me?

---

### Post by edward1978 on 2010-10-16
> **casbahdk said:**
> I installed Debian on the Okaya, with an extra primary partition as per these instructions:

[https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Then I booted from the Lubuntu 10.10 live CD, copied the contents of a USB pen drive setup as a Lubuntu 10.10 live install to /dev/sda3 under /temp/installer (as per the above url) and edited the GRUB menu.lst file:

```
title        installer
root        (hd0,2)
kernel        /tmp/installer/casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd        /tmp/installer/casper/initrd.lz
```Unfortunately, I can't figure out how to update GRUB (I think Debian still uses legacy GRUB) from the Lubuntu live CD. Can anyone help me?

su update-grub

---

