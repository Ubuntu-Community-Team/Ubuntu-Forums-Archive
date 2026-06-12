---
title: "Raspberry Pi 4 &amp; Ubuntu 20.10 Server"
date: 2021-06-05
forum: Hardware
---

### Post by ppcm on 2021-06-05
Hello there,

I need to install Ubuntu 20.10 on my RPi4. Do you know where it can be downloaded?
I really need this specific version, not the 20.04 or 21.04

Thanks fo your help

---

### Post by coffeecat on 2021-06-05
The 20.10 server images for Raspberry Pi 4 are on this page: [http://cdimage.ubuntu.com/ubuntu/releases/20.10/release/](http://cdimage.ubuntu.com/ubuntu/releases/20.10/release/)

Please be aware that 20.10 goes end of life in July this year (next month). After that: no support or updates.

---

### Post by ppcm on 2021-06-05
Thanks for the link
But I have no choice, 20.04 doesn't work (easely) with SSD disk, and 21.04 doesn't work with the app I need to use

---

### Post by coffeecat on 2021-06-05
> **ppcm said:**
> 20.04 doesn't work (easely) with SSD disk

I'm surprised. If you want to get help with that, you are certainly welcome to start a new thread with more details.

---

### Post by QIII on 2021-06-05
Is this a problem specifically with the ARM port?  From what source did you find that one particular release works when others don't?

Is this an issue specifically with the R Pi, or do other SBCs suffer from the same issue?

What specifically does not work?

---

### Post by david504 on 2021-06-08
> **QIII said:**
> Is this a problem specifically with the ARM port?  From what source did you find that one particular release works when others don't?

Is this an issue specifically with the R Pi, or do other SBCs suffer from the same issue?

What specifically does not work?

A lot of people don't know the xci driver checks for usb3 compatibility and of course it fails because none of the usb ports are usb compliant. Maybe we need to modify that driver Linus and Rosie made for Linux.

Their work around is passing the argument :u on the onboard interface in their config.txt. There is a sticky on their forum for this. This of course forces usb mode and does not initiate the super speed mode checks.

There are a few complaints I have with the port. 1 there is no apci controller, so all of that power management can be uninstalled (which is one of things I can see what could be causing the keyboard and mouse to stop responding when installing a gui on ubuntu server). 2nd the lack of a lightweight desk environment, as XUbuntu package should have been ported instead of unity/metacity because it runs horrible even on a raspberry pi 4b with 8 GB.

Also, I found out system.d that we got from Redhat has security flaws, and Redhat fixed it for themselves, but didn't share the fix across Linux. Please be aware of this.

Also, no password-less sudo! I can't believe the pi foundation doing that and please don't fallow their lead on that and discourage this. 

One last thing: add to the installs the regenerate openssh keys, and installation of ufw and the gui control: gufw to the desktop versions.

---

