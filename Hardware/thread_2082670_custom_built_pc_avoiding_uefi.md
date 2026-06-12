---
title: "custom built pc: avoiding uefi"
date: 2012-11-10
forum: Hardware
---

### Post by mzrk7 on 2012-11-10
Hello everyone, I would like to share with you some doubts I have. I would like to build myself a new computer, still, I am actually having some issues with uefi machines, and the whole story about secure boot still looks quite bad to me. I can't find new motherboards with bios, so, do you think is a really bad idea to look for old motherboards so that I can stick with bios? I perfectly know that one day uefi will probably be the standard interface, but some suggestions would be very helpful.
Thank you very much!

---

### Post by mzrk7 on 2012-11-11
anyone?

---

### Post by gordintoronto on 2012-11-11
There are no current motherboards (except maybe in Microsoft's RT tablet) which require secure boot. My suggestion would be to go with current technology.

If you get hard drive bigger than 2 GB, that will probably be a bigger hassle than UEFI.

---

### Post by oldfred on 2012-11-12
I have not seen a UEFI system that does not boot from BIOS mode. So if you install Ubuntu in BIOS mode it and with grub in the MBR it will boot. Some have settings in UEFI/BIOS and others look for efi partition and if not found look for MBR before erroring out. 

How you boot install media CD or flash drive is how it will install. So if you boot CD in UEFI mode it installs in UEFI mode. If you boot CD in BIOS mode which may be called BIOS, AHCI, legacy or something, it will then install in BIOS mode.

You can still use gpt partitioning with BIOS mode. With UEFI you need an efi partition. With BIOS you need a bios_grub partition. I often suggest both as it is hard to go back and create the efi partition at the beginning of the drive, just do not set boot flag on it so it is not really seen as an efi partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32  (for UEFI boot or future use for UEFI)
    1 MB bios_grub  no format (for BIOS boot)
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

---

### Post by mzrk7 on 2012-11-12
Thank you! But what about secure boot?

---

### Post by Cheesemill on 2012-11-12
> **mzrk7 said:**
> Thank you! But what about secure boot?
I believe you can disable it in the BIOS settings.

---

### Post by oldfred on 2012-11-12
Secure boot is only required to be enabled on systems with Windows 8 pre-installed and the same requirements says there must be a way to turn it off. (Unless it is Windows RT which is not really Windows).

---

### Post by mzrk7 on 2012-11-12
What I mean is that I wouldn't like to have it at all. I don't even know if I'll install Windows.

---

### Post by oldfred on 2012-11-12
Then do not use it. It is part of the specification for UEFI, so it may be there, but like many things does not have to be turned on.

---

### Post by grahammechanical on 2012-11-12
This might re-assure you:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

> if Secure Boot is not enabled, the second-stage bootloader is booted without applying any checks. If Secure Boot is enabled, the signature is checked on the second stage before passing control, as expected.
The second-stage bootloader is GRUB 2. 

> If the kernel is unsigned and the system has Secure Boot turned on, the Ubuntu grub will fall back to calling ExitBootServices() first, and then booting the kernel. This way, users still have the freedom to boot their own kernels on Secure Boot-enabled hardware, possibly with a slightly degraded boot experience, while the firmware remains protected from untrusted code.

Regards.

---

### Post by mzrk7 on 2012-11-12
Thank you all for your advices! Things are a little bit clearer now :D

---

### Post by Dlambert on 2012-11-12
> **mzrk7 said:**
> Thank you all for your advices! Things are a little bit clearer now :D

And don't worry, I have secure boot. And whether it's on or off, Ubuntu still works. :)

---

