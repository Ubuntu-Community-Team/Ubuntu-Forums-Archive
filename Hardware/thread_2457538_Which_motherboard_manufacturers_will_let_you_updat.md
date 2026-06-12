---
title: "Which motherboard manufacturers will let you update bios/firmware with linux?"
date: 2021-02-04
forum: Hardware
---

### Post by rbroen on 2021-02-04
Lat week I updated my MSI Cubi2 motherboard firmware, and it was was not easy. In the end I had a buddy drop byr with a Windows usb stick to get it done. There was simply no way to perform the update from Linux.

I am still considering buying a new computer, but which branch of motherboard will let me run updates (bios/firmware) from Linux?

---

### Post by tea for one on 2021-02-04
Are you familiar with LVFS [https://fwupd.org/](https://fwupd.org/)

Secondly, I think that the question should be:--

Which motherboards have UEFI firmware that can be upgraded without Linux or Windows or Apple i.e. distro agnostic?

As an example, the firmware on many Intel NUCs can be upgraded with the file on a USB stick (i.e. before the OS loads).
I suspect that there are other devices with similar features.

---

### Post by oldfred on 2021-02-04
Both my Gigabyte & Asus motherboards allowed direct update from UEFI, reading update file from a FAT32 formatted partition.
Most motherboard manufacturers have relatively easy ways to do it without Windows.

Many also may have a DOS bootable update flash drive and of course the update from Windows.

Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

My Samsung NVMe drive has an ISO that I was able to loopmount boot from grub. It only had the one update for the one model and looked like a very simple update screen.

---

