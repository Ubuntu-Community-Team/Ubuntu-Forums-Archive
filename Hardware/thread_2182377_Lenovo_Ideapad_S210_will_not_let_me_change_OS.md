---
title: "Lenovo Ideapad S210 will not let me change OS"
date: 2013-10-21
forum: Hardware
---

### Post by Ernst_Renan on 2013-10-21
Hi everyone,

I have a brand new Lenovo Ideapad S210. It comes with Windows 8 pre-installed. However, try as I might, I simply cannot get this damned OS to budge so I can install Ubuntu 13.04 (64 bit). All of the available information on the Internet at the moment is for my machine's predecessor, the S205.

The UEFI won't  recognize my LiveUSB, not even when I reboot directly from it, nor will it let  me deactivate FastStartup (it doesn't even appear as an option). The disk management program won't even let me partition my disk (again, it won't even appear as an option: refer to the attached jpeg). The only thing I can do is make a VHD.

Can anyone help? Thanks!

[IMG]http://img822.imageshack.us/img822/3267/xx0l.jpg[/IMG]

---

### Post by varunendra on 2013-10-23
Welcome to the forums Ernst_Renan !

Have you tried the suggestions in the [UEFI wiki]("https://help.ubuntu.com/community/UEFI") page? Especially this part to access BIOS : [https://help.ubuntu.com/community/UEFI#Accessing_the_UEFI_settings_from_Windows8](https://help.ubuntu.com/community/UEFI#Accessing_the_UEFI_settings_from_Windows8)

---

### Post by NoBugs! on 2013-10-23
The secure boot workarounds shouldn't be neccesary - Mostly you need the first 2 steps:

"Create a LiveDVD or LiveUSB of Ubuntu (>=12.04.2) **64bit**."

"In your BIOS, disable QuickBoot/FastBoot and Intel Smart Response Technology (SRT). If you have Windows8, also disable **FastStartup**. "

Then use F12 or whatever boot choice button it uses, you should be able to choose Ubuntu disk.

---

### Post by ArdentMoth on 2014-01-14
FastStartup is not an option on this model of netbook.

Try as I might, with many different settings, it never advanced beyond the acknowledgement to H. Peter Whatever.

TAILS, Debian Wheezy, and presumably other non-Ubuntu distros, work fine.

I would _prefer_ to run Ubuntu on this machine. Touchscreen support in Debian blooooows, ie, is nonexistent or terrible if using libts.

What kills me is that suggestions about this issue have yielded nothing fruitful. "Oh, it's just like any other pre-install of windows 8, it should be so simple a monkey's child with google should be able to solve it" but it *isn't* the same. 

OP, I'll notify you if I figure this out.

---

