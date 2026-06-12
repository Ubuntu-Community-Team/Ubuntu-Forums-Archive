---
title: "EFI grubx64.efi file and boot times."
date: 2012-06-16
forum: Hardware
---

### Post by wnelson on 2012-06-16
First I installed the normal lubuntu 12.04 then upgraded to various kernels ending with 3.5.0-030500rc2-generic. Then I tried the following:

1. Booting from the hard drive instead of the efi boot option for ubuntu.

#efibootmgr -v
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0003,0006,0005,0009
Boot0000  Setup	
Boot0001  Boot Menu	
Boot0002  Diagnostic Splash	
Boot0003* ubuntu	HD(1,22,9897,a926a351-323a-4bc3-b5c4-e943800db10f)File(\EFI\ubuntu\grubx64.efi)
Boot0004* ATA SSD:	030a2500d23878bc820f604d8316c068ee79d25b91af625956449f41a7b91f4f892ab0f603
Boot0005* ATA HDD: WDC WD3200BPVT-24ZEST0                  	ACPI(a0341d0,0)PCI(11,0)ATAPI(0,0,0)
Boot0006* ATAPI CD: TSSTcorp CDDVDW TS-L633F                	ACPI(a0341d0,0)PCI(11,0)ATAPI(1,0,0)
Boot0007* USB HDD:	030a2400d23878bc820f604d8316c068ee79d25b33e821aaaf33bc4789bd419f88c50803
Boot0009* Network Boot: Realtek PXE B02 D00	BIOS(6,0,5265616c74656b20505845204230322044303000)

I noticed that the boot time was drasticlly improved and wifi was activated, without using rfkill.

I then decided to check the file size of /boot/efi/EFI/ubuntu/grubx64.efi 116736 and then ran the following and :

#apt-get install --reinstall grub-efi-amd64-bin, grub-efi-amd64

I noticed that the size was larger 117760. My boot time were fast enough that I booted without splash option in my grub setup and the boot time was amazing. I don't have bootchart install but I can say that boot times have gone from at least ~30 seconds to about ~15 seconds. 

I still have issues with wifi not being active when selecting the efi ubuntu menu selection.

Could you please try reinstalling grub-efi-amd64-bin, grub-efi-amd64 and see if you get the same results? I guess that the update process does not modify the /boot/efi/EFI/ubuntu/grubx64.efi file.

walt

---

