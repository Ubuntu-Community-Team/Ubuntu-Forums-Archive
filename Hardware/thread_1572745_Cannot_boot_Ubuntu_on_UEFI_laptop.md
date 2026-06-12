---
title: "Cannot boot Ubuntu on UEFI laptop"
date: 2010-09-11
forum: Hardware
---

### Post by Sebazzz91 on 2010-09-11
Hi,

I have some problems getting Ubuntu to boot on an UEFI laptop.

My laptop, a XXODD 860tnu (a Clevo barebone) is fitted with an UEFI firmware in the form of Phoenix SecureCore. I have currently Windows 7 professional 64-bit installed on a GPT partitioned disk. I have currently partitioned it this way:
500 GB GPT harddisk:
100MB EFI System Partition (the Windows Boot Manager is located here)
100MB Microsoft Reserved
350GB Windows 7 (NTFS)
20GB ext4 for Ubuntu
100GB Data (NTFS)

I want to have an dual boot installation with Ubuntu. I downloaded the Ubuntu 10.10 (yes, the beta) image and burned it on an optical disk and booted. First I get Grub with the option of installing Ubuntu or checking the disk for errors. Of course, I select the first option. I get an error about 'paging' and get the boot menu then again the error about paging and after an keystroke Ubuntu 10.10 live boots. I'm able to install with no problems, but after a reboot I'm not able to boot Ubuntu because the Windows 7 bootloader is still present as the primary bootloader, and Grub is nowhere to be seen. 

I've tried to install grub-efi-amd64 but that doesn't work either, same story. I also tried EasyBCD and Wubi but both options give me an error similar to this one:
[IMG]http://tweakers.net/ext/f/AjJrtYRkAV4UIZgDp5Go8uvp/full.jpg[/IMG]

So EasyBCD or Wubi is not an option. 

So my question is: How can I boot Ubuntu, or install GRUB which will also let me boot Ubuntu?

The specifications of my computer:
XXODD 860tnu (no, this is not a mac computer)
UEFI firmware (Phoenix SecureCore)
Windows 7 64-bit
GPT-partitioned harddisk

Thanks in advance.

---

### Post by srs5694 on 2010-09-11
A Google for "Ubuntu on UEFI" turned up several pages that might help, including:


[list]
[*][https://wiki.ubuntu.com/EFIBootLoaders](https://wiki.ubuntu.com/EFIBootLoaders) -- The "Booting from EFI" section seems particularly important.
[*][https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091304.html](https://lists.ubuntu.com/archives/ubuntu-users/2006-August/091304.html)
[*][https://bugs.launchpad.net/ubuntu/+source/casper/+bug/635439](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/635439)
[*][https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-uefi-support](https://blueprints.launchpad.net/ubuntu/+spec/foundations-m-uefi-support)
[*][http://osdir.com/ml/help-grub-gnu/2010-02/msg00009.html](http://osdir.com/ml/help-grub-gnu/2010-02/msg00009.html)
[/list]


Try Googling it for more results; these are only the results from the first page that seemed most relevant. "Linux on UEFI" is also likely to produce relevant results, although there may be Ubuntu-specific issues, too.

---

### Post by Sebazzz91 on 2010-09-11
I've figured out how to do it. When the Windows Boot Manager appears, I press the key for 'Cancel' (in my case ESC). Then the EFI reverts to legacy boot mode and invokes the bootsector on the harddisk. Then Ubuntu boots perfectly. It's not perfect, but it does the job. I also don't know how reliable this method is and how easy it breaks.

Any suggestions how to do it the right way are still appreciated :)

> **srs5694 said:**
> A Google for "Ubuntu on UEFI" turned up several pages that might help, including

Try Googling it for more results; these are only the results from the first page that seemed most relevant. "Linux on UEFI" is also likely to produce relevant results, although there may be Ubuntu-specific issues, too.
I already tried searching for this subject, with other terms. That didn't help me, so that's why I created this thread. The search results don't explain why it happens nor do they explain how to fix it the right way. Anyway, thanks for your reply.

---

