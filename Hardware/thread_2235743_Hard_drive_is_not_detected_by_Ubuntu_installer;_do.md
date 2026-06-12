---
title: "Hard drive is not detected by Ubuntu installer; does show up in BIOS"
date: 2014-07-22
forum: Hardware
---

### Post by evencoil on 2014-07-22
If I go into my BIOS, all of my 3 hard drives are detected.

However if I load the Ubuntu 14.04 Live disk, one of the three drives (it happens to be a SSD) does not show up.

If I run GParted within the Live disk, the SSD drive also does not show up.

Nor does it show up if I do "sudo fdisk -l" or "sudo blkid", etc.

It is also not listed as a potential drive for me to partition/install on if I try to proceed with installing Ubuntu 14.04

Some background: this drive contains the / directory for an older version of Ubuntu. I was running this older version fine this morning, then when I tried to switch users I had a strange blank screen with a blinking cursor. I rebooted (with Ctrl + Alt + Del) and upon reboot had a Grub error saying "error: out of disk" with the SSD listed as the disk in question. Some Googling led me to believe that this error indicates a corrupted boot sector. However most of the solutions involve using a Live disk and if I try that I run into the above problem.

At this point I would ideally like to fix the boot sector (or whatever the problem is), however I would be fine with just installing a new version of Ubuntu on the SSD. But since the SDD does not show up in the Live disk even this is not an option for me.

Any help or suggestions are greatly appreciated.

---

### Post by slooksterpsv on 2014-07-22
You may need to get diagnostic utilities from the vendors site - e.g. Western Digital, Samsung, Intel, etc. - and seeing if there's an issue with the drive. How old is the drive? Does it support TRIM or have you seen if there was a firmware upgrade for TRIM?

---

### Post by evencoil on 2014-07-23
It's an older (4 years or so) Intel drive. I found a diagnostic tool on Intel's website here 
[https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=18455]("https://downloadcenter.intel.com/Detail_Desc.aspx?DwnldID=18455")
but it looks like it runs from within a Windows installation.

---

### Post by evencoil on 2014-07-23
Turns out Intel also has a boot-disk for updating firmware.

On the first boot there were many error messages and my drive was not detected at all.

On the second boot there were again many error messages, but the drive was detected. Proceeded with firmware update, and it appeared to all work correctly. However same Grub rescue error when trying to boot from the drive again.

---

### Post by oldfred on 2014-07-23
Do not run auto fix from Boot-Repair when you have more than one drive. It installs one grub to every drive.

But do post link to BootInfo report so we can make suggestions on what to do.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

