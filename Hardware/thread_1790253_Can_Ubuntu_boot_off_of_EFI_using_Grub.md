---
title: "Can Ubuntu boot off of EFI using Grub?"
date: 2011-06-24
forum: Hardware
---

### Post by thattypicalnerd on 2011-06-24
I've looked around a while about this, and I've seen mixed answers. I want to reinstall all my OS's (Windows 7, Mac OS X, Ubuntu, OpenSUSE, Fedora, and Mint), and I would like to do this on a GPT disk for partitioning and flexibility reasons. However, I am aware that Windows 7 cannot be installed on a standard BIOS based system with GPT. Lucky this computer supports EFI :P 

So my question remains the same- can Ubuntu boot off of EFI using GRUB? I plan to use Chameleon as my primary bootloader, but that itself can't boot Linux (yet), so I need GRUB.

---

### Post by srs5694 on 2011-06-25
Yes, Linux can boot using EFI; however, Ubuntu's EFI support is still rather flaky, IMHO, largely because of barely-adequate GRUB support for EFI and weak GRUB configuration for EFI in Ubuntu. My preference is to use [ELILO,](http://elilo.sourceforge.net/) which is much simpler and more reliable, in my experience. In fact, if at all possible I recommend installing Ubuntu to a GPT disk in BIOS mode and then switch to (U)EFI mode after the fact -- *especially* if it's not the first OS you install, otherwise you could be in for a nasty surprise: Ubuntu's installer, when running in UEFI mode, *erases* the EFI System Partition (ESP), which is where other EFI-based OSes install their boot loaders. [A bug report on this problem exists,](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669) but doesn't seem to have gathered much attention from the Ubuntu developers.

Incidentally, Chameleon is a BIOS-based boot loader; AFAIK, it doesn't work on (U)EFI-based systems. You might find it harder, not easier, to install OS X on a UEFI-based PC than on a BIOS-based PC, if that's what you're planning. If you've got a Mac, then Windows won't install using the Mac's variety of EFI (and Chameleon doesn't work on real Macs, AFAIK). If you're planning on doing some Hackintoshing, then you should take the OS X discussions elsewhere, since the forum moderators frown on such discussions here. For the Ubuntu side of it, though, here's good.

Oh, one more thing: You might want to check out [this page of mine,](http://www.rodsbooks.com/bios2uefi/index.html) which describes use of UEFI software that can be installed on a BIOS-based PC. Most of that page is inapplicable to you, but I do have notes on installing Fedora, OpenSUSE, and Ubuntu on systems using that software, and much of those discussions are applicable to "real" (U)EFI computers. (The stuff about copying installation files to USB flash drives is irrelevant, though.)

---

### Post by thattypicalnerd on 2011-06-25
> **srs5694 said:**
> Yes, Linux can boot using EFI; however, Ubuntu's EFI support is still rather flaky, IMHO, largely because of barely-adequate GRUB support for EFI and weak GRUB configuration for EFI in Ubuntu. My preference is to use [ELILO,](http://elilo.sourceforge.net/) which is much simpler and more reliable, in my experience. In fact, if at all possible I recommend installing Ubuntu to a GPT disk in BIOS mode and then switch to (U)EFI mode after the fact -- *especially* if it's not the first OS you install, otherwise you could be in for a nasty surprise: **Ubuntu's installer, when running in UEFI mode, *erases* the EFI System Partition (ESP)**, which is where other EFI-based OSes install their boot loaders. [A bug report on this problem exists,](https://bugs.launchpad.net/ubuntu/+source/partman-efi/+bug/769669) but doesn't seem to have gathered much attention from the Ubuntu developers.

Incidentally, **Chameleon is a BIOS-based boot loader; AFAIK, it doesn't work on (U)EFI-based systems. You might find it harder, not easier, to install OS X on a UEFI-based PC than on a BIOS-based PC, if that's what you're planning**. If you've got a Mac, **then Windows won't install using the Mac's variety of EFI (and Chameleon doesn't work on real Macs, AFAIK). If you're planning on doing some Hackintoshing, then you should take the OS X discussions elsewhere, since the forum moderators frown on such discussions here.** For the Ubuntu side of it, though, here's good.

Oh, one more thing: You might want to check out [this page of mine,](http://www.rodsbooks.com/bios2uefi/index.html) which describes use of UEFI software that can be installed on a BIOS-based PC. Most of that page is inapplicable to you, but I do have notes on installing Fedora, OpenSUSE, and Ubuntu on systems using that software, and much of those discussions are applicable to "real" (U)EFI computers. (The stuff about copying installation files to USB flash drives is irrelevant, though.)

1) Oh gosh... I guess it's a good idea to get that installed first then :P
2) Yes, I know Chameleon is BIOS based, but my PC supports somewhat of a hybrid, so I do believe it'll boot just fine (it's not a Mac). Sorry about talking about hackintoshing, didn't know that the moderators didn't like it. 
3) Thanks for the link to your page!

I suppose I'll use a different bootloader (like the one you suggested). Thank you!

---

