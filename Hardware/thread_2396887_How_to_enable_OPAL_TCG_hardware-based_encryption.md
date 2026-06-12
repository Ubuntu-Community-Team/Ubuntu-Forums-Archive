---
title: "How to enable OPAL TCG hardware-based encryption?"
date: 2018-07-22
forum: Hardware
---

### Post by thomas3032 on 2018-07-22
I have a Samsung 960 EVO M.2 NVMe hard disk (1 TB) which replaces the manufacturer's M.2 SATA SSD drive in a Dell Latitude 5580. To use the disk's hardware encryption feature, I could have set a simple Class-0 password (as I did for many years using the ATA-password for SSDs). However, Dell's BIOS only allows to set passwords only for M.2 SATA SSDs but not for NVMe drives:

[https://www.dell.com/support/article/de/de/dedhs1/sln305225/no-bios-option-to-set-a-hard-drive-password-on-m2-ssd?lang=en](https://www.dell.com/support/article/de/de/dedhs1/sln305225/no-bios-option-to-set-a-hard-drive-password-on-m2-ssd?lang=en)

Dell seems not to be willing to update their BIOS to support Class-0 passwords, so I'm looking for other options to enable hardware-based encryption. I am fully aware that I could use software-based encryption (e.g. LUKS) but I really want to have hardware-based encryption for some reasons (especially usability, performance, power consumption, SSD specifics).

The other option to enable hardware-based encryption would be to use OPAL TCG, which the 960 EVO supports as well. Does anybody know how I can safely set up OPAL TCG to have hardware-based encryption for ubuntu 18.04? How do OPAL TCG patches in Kernel 4.13+ come into play here?

Best regards
Thomas

---

### Post by thomas3032 on 2018-09-22
I now tried it out to use TCG OPAL for the Samsung Evo 960. And finally, it worked ;-)

My setup is the Dell Latitude 5580 with recent BIOS version, booting in BIOS mode. The OS is ubuntu 18.04 with recent updates installed. I only have a swap partition (for hibernating encryptedly) and a btrfs partition.

I just followed the steps described at [https://github.com/Drive-Trust-Alliance/sedutil/wiki/Encrypting-your-drive](https://github.com/Drive-Trust-Alliance/sedutil/wiki/Encrypting-your-drive)

The Version of the sedutil-cli rescue system was 1.15.1

The only thing which I noticed not to work is the S3 sleep mode because ubuntu does not unlock the drive when resuming. To mitigate this issue, I now use hibernate (even when closing the lid). To use hibernate via the swap partition, I had to extend the swap partition's size and set the resume parameter in /etc/defaults/grub

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash resume=UUID=28eded29-f9e6-44b5-9e54-XXXXXXXXXXXX"

The UUID of the swap partition can be determined with blkid command.

Also noticable:

- After the Pre-Boot-Authentication has unlocked the drive, the laptop returns to the Dell logo and during that time I can also put in a USB stick and boot from there while the drive is already unlocked.
- When putting the PBA image on the drive and setting the password, all the data persists on the drive. The data does not change (although it is wise to have a recent backup at hands).

---

