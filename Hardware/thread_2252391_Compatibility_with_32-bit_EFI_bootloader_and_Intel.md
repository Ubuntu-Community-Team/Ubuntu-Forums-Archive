---
title: "Compatibility with 32-bit EFI bootloader and Intel Atom."
date: 2014-11-11
forum: Hardware
---

### Post by amut00 on 2014-11-11
[COLOR=#333333][FONT=UbuntuRegular][FONT=arial][SIZE=2]In the last month or so, Microsoft pretty much declared war against Chromebooks, so today there are 3 199$ laptops avaliable. Due to their super low price I'm thinking about buying one and installing Ubunto on it.[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][FONT=arial][SIZE=2]I know I't won't be a problem with HP Stream 11 and Acer Aspire E 11 ES1, but I do wonder about ASUS X205TA.[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][FONT=arial][SIZE=2]The thing that worries me is the processor, Intel Bay Trail-T Z3735F 1.33GHz (Turbo up to 1.83GHz). Due to the fact that the system requirments says Ubuntu needs at least "Atom 1.6 GHz", and the processor is 1.33/ 1.83 I don't know. 
The Second thing is that I read somewhere that "Intel® Bay Trail-T Quad Core Z3735 1.33 GHz Processor requires a 32-bit EFI bootloader. No version of Linux currently supports EFI for their 32-bit spins.", I'm still new at this, I don't know what it means.

So, Will Ubuntu / Xubuntu / Lubuntu work on this processor?[/SIZE][/FONT][/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][FONT=arial][SIZE=2]Thank you![/SIZE][/FONT][/FONT][/COLOR]

---

### Post by oldfred on 2014-11-11
If you try you will be out there at the bleeding edge.

 Linux 3.15 Kernel Gains EFI Mixed Mode Support
[http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI](http://www.phoronix.com/scan.php?page=news_item&px=MTY0OTI)
New  32 bit UEFI class 3 (no CSM) Only with recompile UEFI/grub/Ubuntu
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)
Packard Bell ENME69BMP InsydeH2O  or Gateway LT41P04u
32-bit UEFI Support Proposed For Ubuntu Linux
[http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE](http://www.phoronix.com/scan.php?page=news_item&px=MTU1NjE)


 Don't ship 32-bit UEFI firmware on x86
[http://mjg59.dreamwidth.org/26734.html](http://mjg59.dreamwidth.org/26734.html)
Some new 64 bit low cost systems with 32 bit UEFI
[http://ubuntuforums.org/showthread.php?t=2189855](http://ubuntuforums.org/showthread.php?t=2189855)

Now older:

 New Intel Atom - Nov 2013 x86 secure boot can be turned off, but only 32 bit UEFI which no one else has.
 Intel Atom SoC systems that ship with Windows 8/8.1 32-bit provide 32-bit UEFI-only firmware with no BIOS compatibility option (no CSM). In UEFI terms these systems are called Class 3 systems (this term is not specific to 32-bit), ie. UEFI-only with no BIOS CSM.
Windows with Atom 
[http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux](http://www.extremetech.com/computing/136276-intel-clover-trail-atom-chips-cannot-run-linux)

      
 Bay Trail -The ASUS "Bay Trail" T100 Is Not Linux Friendly
[http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTQ5NzE)
But someone has it partially working:
[http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html](http://liliputing.com/2013/10/booting-ubuntu-asus-transformer-book-t100.html)
Asus T100 Compile own grub 32 bit
[http://ubuntuforums.org/showthread.php?t=2191557](http://ubuntuforums.org/showthread.php?t=2191557)
Linux 3.15 Kernel Gains EFI Mixed Mode Support

---

### Post by amut00 on 2014-11-12
Thank you for the answer!
Unfortunately my English is not very well so I didn't understand if it will work or not...
"[COLOR=#000000]bleeding edge" means it will work?[/COLOR]

---

### Post by oldfred on 2014-11-12
It means you are one of the first to test or experiment with it.
One post did show a user who recompiled grub to get it to work. 
Some development then took place after that, but you still may need to be more than a new user to be able to get it to work.

---

### Post by amut00 on 2014-11-13
Yes. Thank you very much!

---

### Post by oldfred on 2014-11-13
They discuss 32 bit UEFI in the middle of this. 
They say it is not implemented at all?

 Developer's discussion of de-empahsis of 32 bit Ubuntu - Nov 2014 
[http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/](http://summit.ubuntu.com/uos-1411/meeting/22353/when-should-we-stop-making-32-bit-images/)

---

