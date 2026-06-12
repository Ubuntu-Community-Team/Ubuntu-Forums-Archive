---
title: "Unable to mount 64GB micro SDXC card (Ubuntu 18.04)"
date: 2020-06-02
forum: Hardware
---

### Post by keijo-kukka on 2020-06-02
Hi guys, I'm a bit of a rookie with Linux and Ubuntu and I have problem with micro SD card.

I have Dell Latitude E5450 ([this]("https://www.dell.com/support/home/en-us/product-support/product/latitude-e5450-laptop/overview")) which has an integrated SD card reader and Ubuntu 18.04 installed. I've recently purchased Kingston 64 GB Canvas Select Plus UHS-I Speed Class 1 micro SDXC card (with regular size SD adapter) and I have verified that the card is working by trying it out in my other laptop witch has Linux Mint installed and also in Windows 10. However, I can't get my E5450 Ubuntu to mount the card.

I've tried formatting the card with different file systems (EXT3, EXT4, exFAT), but it just won't get mounted and visble in 'Files' application. When I insert the card, Ubuntu plays out small 'click' which seems to indicate that it at least recognizes the card when it's inserted. My Ubuntu Dell also mounts other micro SD cards with 32 GB or less memory. I'm using Ubuntu's preinstalled drivers and Dell doesn't seem to provide any drivers to 18.04. I have an app called 'Timeshift' installed for backups and it seems recognize the card, but it just displays that it has no recognizable filesystem even though I've tried to format the card with various file systems.

Is there anything I can do? Does this sound like a driver problem? And if so, can it be fixed with some 3rd party drivers? Thanks!

---

### Post by CelticWarrior on 2020-06-02
The likely conclusion is the reader is old(ish) and doesn't support SDXC.

---

### Post by keijo-kukka on 2020-06-02
Ok, thanks for the quick answer. It's a bit strange though, because this laptop is five years old, but my other laptop with Linux Mint (Acer Packard Bell Easynote) is over ten years old and it still recognizes the 64 GB card fine.

---

### Post by TheFu on 2020-06-02
in 18.04 exFAT support is an addon.  Have you loaded those tools?  20.04 has exFAT support included.

Some hardware just isn't compatible. There's little that can be done.  Wish there was a 100% certain way to know in advance what works and what doesn't.  

After you insert the card, wait 5 seconds then look at the end of the boot messages.  Use 'dmesg' to see that.  Anything there like this:
```
[1513874.490069] sd 4:0:0:0: Attached scsi generic sg2 type 0
[1513874.763272] sd 4:0:0:0: [sdc] 15949824 512-byte logical blocks: (8.17 GB/7.61 GiB)
[1513874.765512] sd 4:0:0:0: [sdc] Write Protect is off
[1513874.765515] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[1513874.767477] sd 4:0:0:0: [sdc] Write cache: disabled, read cache: disabled, doesn't support DPO or FUA
[1513874.773612]  sdc: sdc1
[1513874.778903] sd 4:0:0:0: [sdc] Attached SCSI removable disk

```
/dev/sdc1 is a partition that can be mounted.  if nothing shows up, i'm thinking a motherboard Bios update?  Maybe?

---

### Post by keijo-kukka on 2020-06-03
Yes, I have exFAT support installed in my Ubuntu 18.04 as well.

Command 'dmesg' seems to show only UFW rules? I can't see anything related to partitions?

I might have to check for BIOS/UEFI updates as well, thanks for your help. I really appreciate it!

---

### Post by TheFu on 2020-06-03
If dmesg doesn't show anything, I haven't any clue. Sorry.  For other types of devices, that can mean the driver isn't available, but storage stuff sorta just works OR never works in my experience.

One more idea.  What is the kernel version on the machine that works and on the machine that doesn't work?

---

