---
title: "ASUS Zenbook UX434F - not linux compatible?"
date: 2020-01-20
forum: Hardware
---

### Post by alainhenry on 2020-01-20
Hello, 

I just puchased an ASUS Zenbook UX434F. I launched Ubuntu 19.04 from a USB stick, and then GPartEd, in order to resize the existing partition and make room for an Ubuntu install (for a dual boot machine).

- GParted only shows the USB drive, not the PC hard drive. 
- TheLve Ubuntu session froze several times while I was using GPartEd.

I thus wonder is my new PC is Linux (or Ubuntu) compatible ? Or is there anything I missed ?

Thanks for any suggestion.

---

### Post by CelticWarrior on 2020-01-20
Yes, it is compatible but...

You need to know a couple of details:

[LIST]
[*]Some SATA modes aren't compatible, reason why the internal drive isn't showing up in the live session (and Gparted). If you intend to dual-boot then first install AHCI support in Windows (some Google search is highly recommended) and then go to UEFI settings and change the SATA mode to AHCI from the default "RAID" or "Intel RST". Please note that failing to install the AHCI support in Windows will render this OS unbootable after changing to AHCI. 
[*]You have a new Nvidia graphics card. In order to run the live session and install Ubuntu you probably need to add boot parameter as well, 'nomodeset'. 
[/LIST]

---

### Post by alainhenry on 2020-01-21
Thanks for the hint, I'm exploring what's possible.

---

### Post by alainhenry on 2020-01-23
Thanks again for the hint. After reading a few other threads here and there, I did the following:
1. update the BIOS (version 300 in this case)
2. AHCI was now porposed as a choice for SATA operations
3. Reboot in safe mode
4. Reboot 
Now my live Ubuntu and GPartEd can detect my SSD drive. 
What remains to be done (before adding the SOLVED tag) is to install linux in dual boot. I'll keep you informed

---

### Post by alainhenry on 2020-01-25
And I have installled unduntu 19.10, no problem. The touchpad/screenpad is not supported as in Wndows, but it works fine as a touchpad. 
Thanks again
Alain

---

### Post by gnz-1 on 2020-01-27
> **alainhenry said:**
> And I have installled unduntu 19.10, no problem. The touchpad/screenpad is not supported as in Wndows, but it works fine as a touchpad. 
Thanks again
Alain

You mean it's much better supported than in windows right? 

Its presented as a fully functional separate screen, arrange your display settings so that the screen pad is below your main screen, then bring up your emails or a terminal with "top" running on it and press SHIFT+SUPER+DOWN to fling it down to to the screenpad.

this post typed to you on screenpad :)

Edit: I should mention that it doesn't power up 100% of the time from the suspended state, but it is much more functional than just a touchpad. 
Installing the Gnome Extension called "OLED dimmer" will let your screen brightness buttons dim the screenpad and not just the main screen.
I'm on 19.10 (Kernel 5.3.0)

---

