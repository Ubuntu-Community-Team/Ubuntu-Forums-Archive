---
title: "HP Pavillion dv9010us - Not starting X"
date: 2006-11-27
forum: Hardware &amp; Laptops
---

### Post by ppvanzella on 2006-11-27
Hey!
I just bought me a DV9010US, a notebook computer by HP, and installed linux in dual boot with windows (Just to play games, I hate Cedega).
The thing is, booting the live CD (both for Dapper and Edgy) works fine, but when I reboot the system and it tries to start the X server, it crashes. I rebooted in safe mode and made all the changes I could think of on /etc/X11/xorg.conf, and I even copied this file from live CDs that are booting the X server, none worked. The screen stays dark and nothing happens. If I try to turn Num Lock or Caps Lock on, the LED won't turn on, which means the PC is not responding. Both VESA and NV drivers have this effect.
I have the Linux Restricted Drivers package installed, though I couldn't use the driver nvidia, it says it doesn't exist.

Computer Config:
Turion 64 X2 TL-56 (I'm running at 32 bits)
2GB of RAM
160GB SATA 5400RPM (30 Windows/30 Linux/256 Swap/Everything Else /home)
VGA GeForce 6150


Thanks in advance, I'm waiting for help (any help).
I'm considered a advanced user, so ANY idea will help me ;)

---

### Post by ppvanzella on 2006-12-16
I guess the problem is with the PCI-Express support by the kernel. FC6 boots X, but I want ubuntu...
Any help here?

---

### Post by fyrestrtr on 2006-12-17
Please post the /var/log/Xorg.0.log

You can get to a working system by booting into run level 3. To do that, edit your grub boot line, and add a '3' at the end of the kernel line, and remove 'quiet' and 'splash'.

---

### Post by ppvanzella on 2006-12-17
That's what the recovery mode does. The thing is that the recovery mode freezes all the time.
I'll try debian now, that should work.

---

### Post by woundedbum on 2007-03-26
I think I have this same problem. About 75% of the time, the boot process just hangs on a blank screen. I know only a little about this system and have no idea what to do. Any help would be greatly appreciated.

---

### Post by ppvanzella on 2007-04-02
Well, I found out that it was a ACPI problem.
I started the computer with the wireless switch turned off, and it worked perfectly. Then I installed ndiswrapper, turned the wireless on and had my wireless working 100%, with WPA.
After that, I had to have the wireless on to start the computer, otherwise it would hang on the x startup. With the new kernels it doesn't matter anymore.

---

