---
title: "Ubuntu on HP Pavilion dv6137tx laptop (GRUB help/external usb drive)"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by maverick280857 on 2007-03-08
Hello all

I have recently purchased a HP Pavilion dv6137tx laptop computer. I want to install Ubuntu on an external usb drive. Thankfully, Ubuntu recognizes the drive.

When I start up the installer (Ubuntu live cd), I get the following options as install targets:

/dev/sda: SCSI1 (0,0,0) (sda) - 120.0 GB ATA ST9120822AS (this is the laptop's internal drive)
/dev/sdb: SCSI5 (0,0,0) (sdb) - 40.0 GB ST94011A (this is the external usb drive)

I chose the second one. Then I get a screen which says the following:

--------
[FONT="Courier New"]Language: English
Keyboard Layout: US English
Name: Vivek Saxena
Login Name: vivek
Location: Asia/Calcutta

**GRUB will be installed to (hd0)**

If you continue, the changes listed below will be written to the disks. Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
SCSI5 (0,0,0) (sdb)

The following partitions are going to be formatted:
partition #1 of SCSI5 (0,0,0) (sdb) as ext3
partition #5 of SCSI5 (0,0,0) (sdb) as swap[/FONT]

---------------------

The query is regarding the line in bold (which refers to GRUB)

Where should I install GRUB? Does hd0 refer to the laptop's internal hard drive? If so, what parameter should I pass here instead of hd0? I don't want to mess with my laptop's internal hdd at all. I just want to boot into ubuntu when I've got the USB drive connected.

Also if you have any other suggestions/ideas/comments, please do write back...would greatly appreciate your help.

Thanks and cheers
vivek

---

### Post by daanemanz on 2007-04-23
You should install GRUB to (hd1), if you want your notebook to only boot into Ubuntu if the external drive is attached. Your first drive appears to be /dev/sda, to which GRUB refers to as (hd0), and your second drive is /dev/sdb, which is, in GRUB terms, (hd1). See the logic? ;)

Then, you should configure your GRUB listing to have two entries (maybe it will configure itself automagically, I can't remember because currently I don't use any dual-boot systems): one for Ubuntu and one for the other OS. The second entry should refer to the boot partition of the OS on your first drive, which is the one in your notebook.

Finally, you should configure your bios to boot your external (USB?) drive first and [I]then[/I to boot the notebook HD]. I assume you know how to do this :) but if you don't, just ask.

A GRUB manual can be found at [http://www.gnu.org/software/grub/manual/html_node/]("http://www.gnu.org/software/grub/manual/html_node/")

---

### Post by maverick280857 on 2007-04-24
Hi

Thanks for the reply...I'll check this out soon and post my experience.

Cheers
vivek

---

### Post by maverick280857 on 2007-07-03
Hi daanemanz, I finally installed UBuntu Fiesty Fawn 7.04 on my laptop's primary hdd, after taking out Windoze ;)

It works fine, except sometimes (like now) it becomes very slow (near freezing). I wonder what the reason for that is....

---

### Post by daanemanz on 2007-09-26
Hi,

sorry for the late reply... Haven't checked out my posts lately. I guess the slowness issue is because you run an OS from an external HD. This can be pretty slow, especially when the HD is plugged into a USB 1.x hub. You should use USB 2.0, but my experience is that even this can be pretty slow sometimes...

Hope this helps,

Daan

---

