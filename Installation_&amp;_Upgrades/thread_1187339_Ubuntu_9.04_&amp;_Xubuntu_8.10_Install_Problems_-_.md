---
title: "Ubuntu 9.04 &amp; Xubuntu 8.10 Install Problems - Black Screen"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Johan-Steyn on 2009-06-14
Hi All,

I have an Intel P3 desktop pc with 1 GHz processor and 512 mb RAM.

The system previously had Windows XP installed.

I successfully installed Jaunty inside Windows using Wubi. However, it failed to boot every time. Black screen after boot.

The Intel Boot Agent gave me problems, until I figured out to press and hold F1 during POST to get the real boot menu and set the boot priority.

Jaunty 9.04 booted from the livecd but froze to black screen immediately after the initial boot and flash screen loaded.

Xubuntu 8.10 alternate install cd booted correctly and managed to load successfully.

However, after a successful install, THE SAME THING! Boots up load to the splash screen and then the cursor blinking twice and the system freezes up. Black screen only.

I suspect it's a video problem (on-board).

Please help!

Thanks,

JS

---

### Post by iiiears on 2009-06-14
It's much more fun when things work without taking a look under the hood. This command will give you some helpful information. 

 sudo lspci | grep vga  

 In a terminal to discover the graphics adapter.
CTRL+Alt+F1 or (A single user root terminal)

With information about the graphics card you can easily find a more specific article here in the forums.

Had any success with this link?
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Best Wishes.

---

### Post by Johan-Steyn on 2009-06-14
Hi,

I am posting from my laptop and currently reinstalling Xubuntu on the pc.

I will boot to recovery and run the suggested lspci code as soon as completed.

The PC has an integrated (on board) video. It is set at 1mb (shared) would increasing the aperture size to 8mb or 16mb help??  

Regards,

JS

---

### Post by Johan-Steyn on 2009-06-14
Hi All,

No, unfortunately the Xubuntu re-install did not work.

Initial splash screen with logo and then nothing. Frozen computer, no keyboard lights, no HDD activity, NOTHING!

I have no terminal; nothing! Xubuntu alternate install disk has no recovery options - it just wants to install.

I have been at it all day and I don't know anymore.

Please Help!

Thanks,

JS

---

### Post by iiiears on 2009-06-14
It appears that yet again i am beyond my depth (Really it isn't that uncommon. It happens about 7 days a week and twice on sundays.) What i can do is offer to help you in gathering more information. Someone much more skilled will undoubtedly jump in with the answer you want.

1.Reboot your computer
2.Hit “Esc” when prompted in order to enter the GRUB menu.
3.Select the proper kernel and hit the letter “e” to edit
4.Arrow down to the Kernel line, and hit the letter “e” again.
5.Take the last few words in the line. Remove “quiet splash” then hit enter.
6.Hit the letter “b” to boot the kernel without the Ubuntu splash screen.

[http://ubuntuforums.org/archive/index.php/t-604326.html](http://ubuntuforums.org/archive/index.php/t-604326.html)
[http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/](http://www.foogazi.com/2007/10/27/remove-the-ubuntu-splash-screen/)

Best Wishes.

---

### Post by Johan-Steyn on 2009-06-14
Hi iiiears,

Thanks for the reply.

Unfortunately my problem is worse than the splash screen loading. The video fails to mount at all.

Right after the splash screen & logo, just when grub is supposed to kick in - nothing. The computer totally freezes with not input from mouse or keyboard. No HDD activity.  

I have searched the forums and found one similar case from maclinux with similar problem and **no solution**, see: [http://ubuntuforums.org/showthread.php?t=1141597](http://ubuntuforums.org/showthread.php?t=1141597)

This describes my problem exactly. I reinstalled XP to get the system specs. Please see attached.

Your assistance is highly appreciated.

Regards,


JS

---

### Post by DAVVVVE on 2009-06-14
I have the same problem and i know the answer in xp . Disable your Intergrated grafic card in ubuntu , and in bios . Now to the questin , How do ill do that in ubuntu =? I figured it must be in a blacklist option . SOrry for my bad english . Im swede . In xp . turn on your comp and press f8 . Boot in safe . Rightklick My computer , then settings , hardware (i think ) Deactivate your intergrated card . Reboot and voila :)  .

---

### Post by DAVVVVE on 2009-06-14
> **DAVVVVE said:**
> I have the same problem and i know the answer in xp . Disable your Intergrated grafic card in ubuntu , and in bios . Now to the questin , How do ill do that in ubuntu =? I figured it must be in a blacklist option . SOrry for my bad english . Im swede . In xp . turn on your comp and press f8 . Boot in safe . Rightklick My computer , then settings , hardware (i think ) Deactivate your intergrated card . Reboot and voila :)  .
  

Only if u have another grafic card installed :KS

---

### Post by Johan-Steyn on 2009-06-15
Hi davvvve,

I think you have hit the nail on the head!!! 

It makes absolute sense! What could it be other than the graphics card?

It's an office machine and we are phasing windows out and replacing all our pc's operating systems with ubuntu. 

This machine gave me the most trouble! It has a small 1mb on-board graphics card.

I will install a pci or agp graphics card this afternoon, to test whether it will sort it out. 

I will post back.

Thanks!

JS

---

### Post by Johan-Steyn on 2009-06-16
Hi Guys,

Solved!

Managed to get Ubuntu Jaunty installed!

It was hardware issues. Installed Nvidia 64 mb AGP graphics card. Pulled out the HDD and slotted in another one, and viola! Ubuntu installer not only runs - but installs flawlessly!

Also, apparently windows XP has no qualms about formatting a faulty HDD (with hidden flaws) with NTFS and install on it - data integrity issues aside.

Also although Ubuntu minimum graphical requirements is VGA it is preferential to have something larger than a 1mb on board graphics card.

Thanks everyone.  

Kind Regards,

JS

---

