---
title: "DELL Precision 5820 tower and NVMe M.2 front-panel SSD issues"
date: 2018-01-06
forum: Hardware
---

### Post by DerPC on 2018-01-06
Hi all,

This post is to summarize my findings on the issues I've had with my new DELL Precision 5820 tower.

This machine came with a NVMe M.2 1TB Samsung SSD and a single 2TB harddrive for backups. It was delivered with Ubuntu 16.04, but like a true besserwisser, that was seen as "old" so we jumped in and set/reset everything in the BIOS to what we assumed it should be ( SATA ACPI, no fancy schmancy stuff, everything enabled about the CPU and so forth). And then we installed KUbuntu 17.10.

And boy did that blow up in our faces.

After a long process with DELL Pro support on the line, I managed to (in my own messy way) bork an installation I had already made to the hard drive (that worked unlike the SSD where we were able to install to it but never boot from it). So I kind of went into random monkey mode (if I push ALL the buttons, I must be able to push the right sequence at some time). And I did. Turning on Intel RAID and Intel SSD Volume Management ( two separate screens in the BIOS) as well as completely disabling legacy boot, have secure boot off (needed for the CPU microcode updates), I was able to install KUbuntu on the SSD _AND_ boot from it.

tl;dr - Even if you have only ONE SSD, you MUST turn on RAID and Volume Management in EFI mode.

DELL have documented this in their knowledge base, but it's worth documenting this here as well since nobody should have to waste their time like I did.

And yes - it IS counter-intuitive to turn on RAID when you don't RAID...

Hope y'all have a better start on your 5820s than I did (thoroughly enjoying the machine now though! :) )

---

### Post by oldfred on 2018-01-06
You are the first one I have seen that could install with RAID on.
Generally install works, but grub does not install to RAID unless using the Server version.

Also many Dell with NVMe drives needed UEFI updates & SSD firmware updates.

[https://www.dell.com/support/article/us/en/19/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/19/sln301754/how-to-install-ubuntu-and-windows-8-or-10-as-a-dual-boot-on-your-dell-pc?lang=en)
 Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

### Post by DerPC on 2018-01-06
I went through the solution with DELL Pro Support and they were as surprised as I was. Generally I would NEVER enable hardware RAID or hardware volume management unless I had >=2 drives of the same type/size to raid. Highly counter-intuitive, but alas, the only way it will work with Linux.

---

