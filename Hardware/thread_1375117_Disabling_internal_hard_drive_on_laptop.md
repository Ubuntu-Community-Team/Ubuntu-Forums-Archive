---
title: "Disabling internal hard drive on laptop"
date: 2010-01-07
forum: Hardware
---

### Post by UnderTheRadar on 2010-01-07
I'm trying to install Linux on a USB-based external hard drive. I'm on a Toshiba Satellite laptop with the InsydeH20 Rev. 3.5 BIOS, which supports booting from USB devices.

I didn't see anything in the BIOS setup that will let me disable the internal hard drive.

In the main tab, you can change system time, date, and language.

In the advanced tab, there's dynamic CPU frequency mode, pointing devices, built-in LAN, wake-up on LAN, critical battery wake-up, legacy USB support, wake on keyboard, and SATA controller mode.

Then there's a tab for display, one for passwords, and one for changing the boot order. My current boot order is (1) CD; (2) USB; (3) HDD.

So my question is: for the BIOS I have, is it possible to disable internal drives? If yes, then how?

If I were on a desktop, I could just detach the internal drive manually, but I don't have one handy. Also, I don't feel comfortable taking my laptop apart, so I won't resort to that.

---

### Post by nastyguard on 2010-01-07
Why would you want to disable your harddrive?

Many BIOSs (BIOSii?) detect bootable USB drives as Hard-Drives instead of Removable media, including my own.

Not all BIOSs/ii are the same, in fact - most of them are different.

But I can tell you what I had to do.

I had to go to the "Boot" tab in BIOS, and there will be a "Hard-Disks" or "Hard-Drives" link near the bottom. Click on that, and it will list all your HDD/USB drives.

If you see your drive on there, click the corresponding button to increase it's priority (move it to the top of the list). The buttons for actions in BIOS are most often displayed somewhere in the bottom-right side of the window.

Then you should save your settings and reboot, and it SHOULD boot from your flash-drive.

Tell me if you run into any problems. ;)

---

### Post by UnderTheRadar on 2010-01-07
Unfortunately it doesn't look like I have the BIOS option to list all the drives I have.

I want to disable the internal just to be safe. I don't want anything being accidentally written to it, or anything like that, while I'm installing to the external.

---

### Post by nastyguard on 2010-01-07
Check the "SATA Controller" option, I'm not sure, but I THINK you should be able to disable your SATA drives through there.

---

### Post by UnderTheRadar on 2010-01-07
I can set SATA controller mode, but I only have two options: AHCI or compatibility.

I feel my BIOS is lacking in a lot of areas...

---

