---
title: "URGENT : Problems installing ubuntu on itanium HP"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by wachaca on 2008-12-23
Hello,
Problem: Trying to install ubuntu 8.10 on a server which has redhat.
CD is not recognized as bootable so my only option is to intervene in elilo.

The server is an HP RX1620 Itanium server (IA64), which loads Redhat using
EFI and elilo.

uname -a spits out:
Linux 2.6.9-67.EL #1 SMP ia64 GNU/Linux

I do have the Ubuntu 8.10 CD placed in the CD drive but the server does not
recognize it as bootable.

part 1: trying to boot/load from CD
I have been reading many manuals including these ones
[https://help.ubuntu.com/8.10/installation-guide/ia64/ch05s01.html](https://help.ubuntu.com/8.10/installation-guide/ia64/ch05s01.html)
[http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/itanium-install-guide/s1-ia64-intro-efi-shell.html](http://www.redhat.com/docs/manuals/linux/RHL-7.2-Manual/itanium-install-guide/s1-ia64-intro-efi-shell.html)

In the Ubuntu case; I tried to boot from the Boot Maintenance Menu but when
I select the CD drive it spits out "Load failed [Not Found]."

when I go into EFI Shell, and type MAP I do not see the CRDROM as a bootable
system partition, but rather a block device.
So I try to mount it using the command
mount blk1 fs2
then I type fs2:
finally type elilo
But that gives me not found error message.

This is what I get when I type ver.

 fs1:\> ver
EFI Specification Revision : 1.10
EFI Vendor                 : HP
EFI Revision               : 14.62

SAL Specification Revision      3.01   SAL_A Revision    = 2.00
  SAL_B Revision    = 2.15

PAL_A Revision        7.31 PAL_B Revision        2.10
PAL_B Revision        5.69

Shell> bcfg boot dump -v
The boot option list is:
01. HD(Part1,SigF07E3A08-8C84-46ED-A9D7-279CB4A5A50F)/EFI\redhat\elilo.efi
"Red Hat Enterprise Linux AS"
02. Acpi(HWP0002,100)/Pci(2|0)/Mac(0011855F4F32) "Core LAN Gb A"
03. Acpi(HWP0002,100)/Pci(2|1)/Mac(0011855F4F33) "Core LAN Gb B"
04. VenHw(D65A6B8C-71E5-4DF0-A909-F0D2992B5AA9) "EFI Shell [Built-in]"
05. Acpi(HWP0002,0)/Pci(2|0)/Ata(Primary,Master) "Internal Bootable DVD"
Part 2: trying to use Elilo to load ISO image.

I downloaded the kernel files from
[http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-amd64/current/images/hd-media/](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/installer-amd64/current/images/hd-media/)
I then placed these files and the Intrepid ISO file in the same directory
/boot/efi/efi/redhat/
I modified elilo.conf to add the new kernels.
However, this is where I am stuck because I do not have installed elilo to generate a new elilo.efi file.
So just how do I do this?

Then I rebooted the server and hit tab just when elilo was about to boot
into redhat and was surprised to find that the options that I added in
lilo.conf appeared without me regenerating the elilo.efi file.

however when I select the option that I added into the lilo.conf file I get
an error:
elilo.c(line 77):Cannot find a loader for vmlinuz
Load failed [Load Error]. Press any key to continue..

---

### Post by Coder543 on 2008-12-23
I have no idea. I'm sorry, your post is so big idk if you said it, you are using the ubuntu server install disc right? Also, the bios is set to use cds as bootable above hard drives?

---

### Post by wachaca on 2008-12-23
> **Coder543 said:**
> I have no idea. I'm sorry, your post is so big idk if you said it, you are using the ubuntu server install disc right? Also, the bios is set to use cds as bootable above hard drives?
Thanks for your help.
The problem is that the CD drive does not recognize the CD as bootable.
Hence I cannot boot from the CD.

---

