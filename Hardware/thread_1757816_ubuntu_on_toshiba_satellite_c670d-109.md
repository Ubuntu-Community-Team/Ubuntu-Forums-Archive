---
title: "ubuntu on toshiba satellite c670d-109"
date: 2011-05-13
forum: Hardware
---

### Post by grantortino on 2011-05-13
TOSHIBA C670D-109.
17'' LED TFT Toshiba TruBrite, 1600x900 pixel
AMD Radeon HD 6310

**problems with ubuntu 11.4**
cannot install: black screen

**problems with ubuntu 10.4 installed**
1) no shutdown, always restart
2) no 16:9 resolution, 4:3 only. and if i install ati drivers: black screen

any ideas?

---

### Post by grantortino on 2011-05-15
same problems with MINT

---

### Post by fritz269 on 2011-05-16
I am using Toshiba Satellite C655 with only min issues. Are you trying to install from a cd or flash drive and are you trying to dual boot or use the whole drive?

---

### Post by grantortino on 2011-05-23
dual boot.

shutdown ok with battery only

---

### Post by fritz269 on 2011-05-23
Ok, l had some issues when I first installed Ubuntu on my Toshiba Satellite C655-S5049. 

I had problems booting from a flash drive so you might want to try booting from a live cd if you are trying that. Try booting instead of installing and see what happens. 
Also, during install, allow third party drivers. This fixed the 6:9 issue for me. You might also try the 64-bit version which I installed last night if your computer supports it. It seems that my laptop likes the 64-bit version better. 

As for the shutdown issues, have you checked the power settings, I think there is an option on how to shut down when on battery and when on AC.

Hope this helps.

---

### Post by marcobiso on 2012-01-20
> **grantortino said:**
> TOSHIBA C670D-109.
17'' LED TFT Toshiba TruBrite, 1600x900 pixel
AMD Radeon HD 6310

**problems with ubuntu 11.4**
cannot install: black screen

**problems with ubuntu 10.4 installed**
1) no shutdown, always restart
2) no 16:9 resolution, 4:3 only. and if i install ati drivers: black screen

any ideas?

You can start it in safety mode, than go to a console and install fglrx driver, it works. The free radeon driver does not work with this graphic card.

Even with fglrx gnome3 doesn't work, something is broken in graphic acceleration.

If on battery only it shuts down, with power supply it reboots.

Sometimes keyboard and trackpad freeze before login, must drastically reboot with power switch, or external mouse.

Suspend locks everything in an infinite loop with black screen, must disconnect power cord and battery (!) to restart.

Definitively the worst computer I have ever seen.

Ciao.

Marco

---

### Post by Buntbart on 2012-06-10
same issues here with toshiba satellite c670d-126.

did you find any fixes?

---

### Post by djhell on 2012-12-24
I solved one of this issues.
Notebook reboots after shutdown due to a kernel trouble. Linux kernel when shutting down, seems to set a low battery status. Due to this, the toshiba has a setting in BIOS for poweron the notebook when battery is low and in suspension.
Due to kernel mistake, BIOS thinks this two conditions happens and starts notebook.
The solution? Set in BIOS to not start when battery is in critical state.

I have the black screen bug too in debian stable after waking up a suspension (same happens on fedora 17, ubuntu 12.10 12.04, lubuntu 12.10, mint 14 and with slackware 14 xorg doesn't start).

When waking up a hybernation, I had a partition data corruption (in debian stable 6.0.6!!!!! ).

Sorry for my spaghetti english :P. I hope my post can help someone.

---

