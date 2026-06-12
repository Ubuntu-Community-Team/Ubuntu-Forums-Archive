---
title: "UEFI/BIOS: Ubuntu killed my motherboard? (again)"
date: 2013-12-17
forum: Hardware
---

### Post by dvteixeira24 on 2013-12-17
[COLOR=#333333]So...[/COLOR]
[COLOR=#333333]I have this laptop (Samsung NP300E5C) which used to triple-boot Mac OS X, Windows (8) and Ubuntu (13.10)[/COLOR]

[COLOR=#333333]They were all installed to separate partitions and were all booted using the Chameleon boot-loader, with all of their respective boot-loaders on their own partitions. Just now, I attempted to install a different flavour of Ubuntu (Xubuntu 12.04) over my existing one. (I have done this before, successfully)[/COLOR]

[COLOR=#333333]The mistake I made though, was to boot the live CD in UEFI mode. I didn't really notice though so I just continued installing it normally as I would. (Format the old Ubuntu part. and install the new one onto that partition along with the GRUB boot-loader.)[/COLOR]

[COLOR=#333333]When I restarted I noticed something devastating, the PC would not boot (start up then just switch off, like when you pull the power in the middle of the bios boot.), then, it restarted but this time showing all the available boot options. Only "ubuntu" was there. Selecting it has no effect, just a screen refresh, looks like it.[/COLOR]

[COLOR=#333333]"Simple!" I thought to myself. "I'll just go into the BIOS settings and set it to legacy boot only, right?" WRONG. My BIOS settings are gone, just gone. Like "Press F2 but then the PC just dies-gone."[/COLOR]

[COLOR=#333333]It's not the first time Ubuntu has done something to render my motherboard useless, it killed it a while back. The warranty people couldn't tell that it was me who broke it though since it seemed like a hardware problem but this time it's easy to see it's a software problem and I don't think they'll help me this time round.[/COLOR]

[COLOR=#333333]But still, I am so confused and can't even understand what happened?? [/COLOR][IMG]http://mybroadband.co.za/vb/images/smilies/confused.gif[/IMG]

[COLOR=#333333]Thanks in advance to anyone who knows anything about this problem.[/COLOR]

---

### Post by tgalati4 on 2013-12-17
I have seen some reports on the web about Samsung laptops becoming bricks (although lightweight bricks) by installing linux.  I have not read about a fix though.  I presume you had the latest BIOS on your laptop since it was new.  It's possible that this is intended behavior.  UEFI is designed to protect the installed operating system from changes.  I'm not sure what the protections are, but bricking the machine is one way to do it.

---

### Post by oldfred on 2013-12-18
The bricking issue was thought to be Linux as that was when it was first found. But one of the main UEFI Linux developers was able to create the bricking with Windows and is a major UEFI design issue on some PCs. Linux now has a work around as it relates to UEFI's internal memory not being correctly released and getting over 50% full. Older versions may not have the fix. 

I would not recommend any older Ubuntu installs for those type systems. Just 13.10 and then 12.04.4 in Jan should be ok.

       [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

            UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
[http://mjg59.dreamwidth.org/25091.html](http://mjg59.dreamwidth.org/25091.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

---

### Post by dvteixeira24 on 2013-12-18
Thanks Guys, will take it into warranty and see if I can get the motherboard replaced.

---

### Post by tgalati4 on 2013-12-18
New Samsung Laptop?
Careful with UEFI Linux.
Brick in your future.

---

