---
title: "Replacement of DELL Vostro 3500 Laptop"
date: 2021-10-01
forum: Hardware
---

### Post by cigtoxdoc on 2021-10-01
My DELL Vostro 3500 laptop has been the heart of my scientific consulting business for well over a decade.  I added Ubuntu in 2014 and sm currently running 21.04 with Evolution 3.40.0-1 as the email client.  Laptop is still dual-boot with Win XP Pro SP3.  Earlier this year, I had the SSD replaced by a local computer shop and disk space no longer an issue.  What I am looking for is a newer (not necessarily new) laptop  that has 16 or more GB RAM and is sufficiently similar in architecture that all I need to use it is put my current SSD in it and I am back in operation.  Cost is not an issue, compatibility, size of screen (at least 15 inches on the diagonal), keyboard, and reliability are.  Current laptop has made three trips to Asia and numerous trips to Europe. The only critical failure was of one of the original HDD, and that was replaced by a DELL service tech when I was traveling in Europe.

Your suggestions for a replacement laptop would be much appreciated.

Thank you,

John

---

### Post by drpjkurian on 2021-10-18
I was using Dell Vostro A860 for 9 years and moved to Dell Latitude pre-installed with ubuntu.

---

### Post by oldfred on 2021-10-18
New systems are UEFI/gpt.
If your system is XP era, then it is BIOS boot from MBR partitioned drive.
Microsoft with release of Windows 8 required vendors to install in UEFI boot mode from gpt partitioned drives.
I started to convert to gpt partitioning in 2010, but had to have XP on MBR drive with Ubuntu on gpt  drive.

If your drive is gpt, conversion to UEFI boot is relatively easy. You just need to add an ESP - efi system partition.

Most UEFI systems until recently could boot in CSM/Legacy/BIOS mode. There was an UEFI setting for type of boot.
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

But Intel has recommended vendors use UEFI class 3 or no CSM mode.
Not sure about most vendors, but have seen questions on some systems that were UEFI only.

Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)


Long term, you should just plan on new clean install in UEFI mode to new(er) system and restore from your normal backup.

---

### Post by mastablasta on 2021-10-19
get Dell per your needs. Vostro is more robustly built (business laptop).

or Lenovo business line ThinkPad E or T series (they come with no OS installed, but have full linux compatibility). 

business grade laptops are better built, more durable, slightly more bulky, but can be repaired or upgraded more easily. they are also a bit more expensive and often support more RAM (e.g. 32 GB). 

a couple of HPs are also sold with Suse or no OS installed. you could look at those as well.

another option (if you are in US) is System76.

depends on how much you want to spend.

---

