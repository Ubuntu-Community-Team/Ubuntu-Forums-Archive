---
title: "Ubuntu on ThinkPad Tablet 2? Clover Trail and 32-bit UEFI"
date: 2013-02-22
forum: Hardware
---

### Post by roadkillbunny on 2013-02-22
I have a [ThinkPad Tablet 2]("https://shop.lenovo.com/products/us/tech-specs/tablet/thinkpad-tablet/thinkpad-tablet-2/") that I am thinking of loading with Ubuntu. However there are some issues that might prevent me from doing this. I want to see what people here think.

1) The tablet comes with an Intel® Atom™ processor Z2760, which is of the Clover Trail family. I've read that this processor on Linux is not officially supported by Intel. However I've also read that since it is just x86 chip, Linux should run. Just not as efficiently. What are your thoughts on this?

2) This is a Windows 8 tablet, so it comes with UEFI. I've seen that Ubuntu has support for UEFI when it comes to 64-bit, but I have not seen anything about 32-bit. Are there plans for this?

To test, I've loaded Ubuntu 12.10 (32-bit) on a USB stick and plugged it into the tablet. SecureBoot was disabled and the USB stick was set as first boot device in BIOS. However the tablet booted into Windows 8 right away. I am not sure if this is because of (1) or (2) or some other unknown reason.

---

### Post by MarcusMoeller on 2013-03-08
The 32-bit ISOS do not contain the necessary EFI files. When you BIOS offers an option to switch to legacy mode, you can give that a try. But it would lead to an unbootable Windows 8.

---

### Post by ZICODIAN on 2013-04-02
Here is some information that is perhaps work a read:

[http://forums.lenovo.com/t5/Windows-8-Knowledge-Base/Why-can-t-I-boot-from-a-USB-key-on-UEFI-ThinkPad-or-ThinkCentre/ta-p/1004621](http://forums.lenovo.com/t5/Windows-8-Knowledge-Base/Why-can-t-I-boot-from-a-USB-key-on-UEFI-ThinkPad-or-ThinkCentre/ta-p/1004621)

Have you made any progress on getting Ubuntu (or perhaps Ubuntu Touch) on the ThinkPad Tablet 2?

---

### Post by ciryatan on 2013-04-05
I am also very interested in running Ubuntu on my Tablet2.
Windows 8 is a pain ;)

I will also try setting up a USB stick with ubuntu.
As far as I remember there Is an option to boot in legacy mode, as a while ago I searched through the lenovo forums for this.
Ill try to find them again and let you know.

---

### Post by Nidroide on 2013-04-30
I was able to get grub starting from a USB pen on samsung ativ 500t (same ****** z2760) but the linux kernel does not load and just freeze the system.

---

### Post by nor500 on 2013-06-11
I have thinkpad tablet 2, and would like to use ubuntu. When do you think ubuntu 32bit installer would support EFI firmware?

---

### Post by nor500 on 2013-06-26
Any more news or progress? I heard that ubuntu would like to concatrate more on mobile market. Isn't the clover trail windows tablet platform important to them?...

---

