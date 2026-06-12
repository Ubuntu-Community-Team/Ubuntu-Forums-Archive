---
title: "Can't boot any linux distro"
date: 2013-09-28
forum: Hardware
---

### Post by daniel87 on 2013-09-28
Hi,

I have a relatively new desktop computer with Windows 8, and I want to dual boot it with ubuntu.

Specs:
CPU - Intel i7-4770K
Motherboard - Gigabyte GA-Z87X-UD3H
Graphics - EVGA Nvidia GTX 660 FTW

When I first bought this pc back in July, I installed Windows 8 and tried to install Ubuntu 13.04. I can't remeber if I installed Ubuntu on EFI mode or not, although I do have UEFI. However, the partitions are already made.

So now I was trying to install Ubuntu and I can't even boot in the live CD - or any other linux distro I've tried, including boot-repair-disk ([http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)). When I try to boot Ubuntu, I can get to the acessibility menu (the one with the keyboard and human figure on the bottom), and get access to the boot options. I've tried nomodeset, acpi=off, noapic, nolapic in both "Try without installing" and "Install Ubuntu" variations. When I try without installing, it goes to a blank screen and doesn't do anything else. When I try to install Ubuntu, I get a message saying that it will go into low resolution mode (or something like that, I guess it can't find my graphics card or something). If I accept, screen goes blank and nothing else, if I try to go to terminal it doesn't do anything.

One other thing, after I tried installing Ubuntu for the first time (back then I could use the live session, and after the installation was finished I thought everything had gone ok), I used easyBCD to try to boot into linux. This means that I have a menu for selecting Windows 8 or Ubuntu (which doesn't actually work) when I boot the computer. If I hit cancel on that menu, it shows a half "ubuntu-purple"/half blank screen and just stops there. This also happens when I boot in Legacy mode instead of UEFI.

The problem seems similar to the one described in [http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854), which the user seems to have solved by turned NIC off in the BIOS. However, I see no option to do that in my BIOS :\

Any thoughts would be appreciated :)

Edit: ended up finding how to turn off NIC, but didn't help :(

---

### Post by oldfred on 2013-09-28
If you are getting accessibility screen you are booting in BIOS/CSM mode. Is that what you want? However you installed Windows UEFI or BIOS is how you do want to install Ubuntu.

With nVidia you will need nomodeset, but is system configured for dual video? And can you turn one or the other off for the install? Settings for Intel video are different.

I do not normally suggest 13.10 until it is out, but it is currently beta and will be released in Oct. It has newer kernel & drivers that may support a new Haswell based system better. Since beta you still may have bugs and breakage, and should report bugs if consistent and repeatable.

---

### Post by daniel87 on 2013-09-29
Apparently 13.10 in UEFI had no problem.

Btw, I just discovered that for some reason the version I had of 13.04 was 32 bits. No idea how I did that. Still have no clue as to why I couldn't boot the few other distros I tried (even tried Fedora, thinking maybe my pc just didn't like ubuntu based OS), but that's not a problem :)

Thank you for your suggestions oldfred :)

---

### Post by oldfred on 2013-09-29
Glad that worked.

The 32 bit version has no UEFI support and now almost all systems with enough hardware to support full Ubuntu with Unity are systems that are 64bit. If hardware is older then Lubuntu or Xubuntu would be better choices anyway. Or I do not understand why they have a 32bit version and up to 13.10 they always recommended the 32 bit version.

---

