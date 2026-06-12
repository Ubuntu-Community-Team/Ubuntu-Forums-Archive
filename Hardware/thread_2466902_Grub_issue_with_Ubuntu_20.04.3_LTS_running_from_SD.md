---
title: "Grub issue with Ubuntu 20.04.3 LTS running from SD card on Surface Pro 6"
date: 2021-09-09
forum: Hardware
---

### Post by etienne-jannin on 2021-09-09
Hi all,

I am trying to install and run Ubuntu 20.04.3 LTS from SD card on my Surface Pro 6.
I started Ubuntu from the USB drive and after inserting the SD card, I created the required partitions (EFI, Swap, root, and a FAT32 partition to share with Windows).

For reference, [here]("https://blog.hackdesk.com/running-ubuntu-on-micro-sd-card-on-surface-pro-4-dfe9e38e17e1") is the guide I followed.

Now here comes my problem.
After installing properly Ubuntu and restarting (and choosing "ubuntu" to boot first in the UEFI boot configuration menu), Grub takes me to the grub command line instead of either starting Ubuntu from the SD card or offering a menu.
On the grub command line, if I type "ls" I get the following:

grub> ls
(proc) (hd0) (hd0,gpt4) (hd0,gpt3) (hd0,gpt2) (hd0,gpt1)

I would expect to see a lot more in there (and at least hd1), which I think is why grub is unable to start Ubuntu.

On the EFI partition on my SD card, I have the following:

[FONT=Arial]root@ubuntu:/media# mount /dev/sdb1 microsdefi
root@ubuntu:/media# cd ./microsdefi/EFI/ubuntu[/FONT]
[FONT=Arial]root@ubuntu:/media/microsdefi/EFI/ubuntu# cat grub.cfg
search.fs_uuid d8a9d550-b63c-467c-8d29-7ecd43d50a2e root **hd1**,gpt3
set prefix=($root)'/boot/grub'
configfile $prefix/grub.cfg[/FONT]

My understanding is that hd0 is the SSD and hd1 the SD card, so grub at this point is not seeing the SD card nor the USB drive.

If I configure the UEFI boot configuration to start from the USB drive and I force grub into the command line (by pressing escape), I now get this:

grub> ls
(proc) (hd0) (hd0,msdos1) (hd1) (hd1,gpt4) (hd1,gpt3) (hd1,gpt2) (hd1,gpt1) (hd2) (hd2,gpt4) (hd2,gpt3) (hd2,gpt2) (hd2,gpt1)

I assume that hd0 is the SSD, hd1 the USB drive, and hd2 the SD card (or hd1 the SD card and hd2 the USB drive, not sure).

Has anybody seen this issue before? Do you have any idea why grub is unable to find the SD card and the USB drive when starting from the SD card?

Thanks for your help!

Etienne

---

