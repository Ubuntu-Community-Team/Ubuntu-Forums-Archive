---
title: "Ubuntu installation on MSI GT780DXR"
date: 2012-01-11
forum: Hardware
---

### Post by zvyagin on 2012-01-11
I am starting this thread to log my progress with installation of Ubuntu on MSI GT780DXR notebook. Please feel free to send comments and recommendations.

2012/01/07 - 2012/01/10
I bought the thing. Windows 7 is preinstalled, works fine. Total disk space is 1.5TB, 2 hard disks form raid0 (to gain speed, but no redundancy). Windows partitions: 8GB (recovery), 100MB (boot?), 900GB (system disk C: ), 500 GB (disk D: ). Partition D: is destroyed, partition D: is shrunk to 500GB.

---

### Post by zvyagin on 2012-01-11
2012/01/10 - 2012/01/11
The following 64bit distributions (CDs) did not boot:
ubuntu 11.10, 11.04, fedora (latest)

Ubuntu 10.04 did boot. Wifi does not work. Screen resolution is bad (something like 800x600 against the naitive 1920x1080). The rest looks fine.

Grub (installed to the MBR, with all default settings) works perfectly fine. Both Windows7 and Linux boots.

At this moment I downloaded and installed all updates. There were no new problems so far.

Allow upgrades. Start Ubuntu upgrade. I got a problem with the GUI, switched to console and continued. At the moment of updating GRUB config files, I kept the old config files style. 

Booting to the new distr: works. Screen resolution has increased to 1024x768. I started anogher upgrade, this time from the console. It finished OK. And again I kept the old Grub config style. The new kernel (2.6.38-13-generic) did not boot. Old kernel (2.6.32-37-generic) still works (thanks to Grub, it kept the previous versions). Windows7 still works.

Kernel 2.6.38-13-generic (recover mode) hangs after the message "loading initial ramdisk". I need to power off the notebook, and I choose agsin exactly the same Grub line. This time it goes further (and this 2-steps booting procedure is very reproduceble). I see the boot log messages. The last one is "usbhid: USB HID core driver". There is no boot progress after it. The keyboard works. But there is no reaction to Ctrl-Alt-Del (it could be problem of the mapping - I cannot use PgUp/PgDwn buttons as well). I tried to blacklist USB drivers, no luck so far - they are still loaded!!!

---

### Post by zvyagin on 2012-01-12
2012/01/12

This image also did not boot:
Ubuntu 12.04 LTS (Precise Pangolin) Daily Build,
64-bit PC (AMD64) desktop CD

There is only the cursor on the screen, no messages.

I compiled kernel 3.2.0 (make .... make install). File grub.conf was not updated correctly, I had to modify it manually. Still, kernel 3.2.0 did not boot, but the failure  was at the very end. Right now I am trying to redirect and save the boot messages.

---

### Post by zvyagin on 2012-01-13
2012/01/12

with the working 2.6.32-37-generic kernel I upgraded UBUNTU to 11.10 version. Luckily 3.0.0-14-generic kernel also works. But I need to choose "recovery" mode in grub and go with the "normal boot" when I am asked about the "rescue" procedure.

video: everything works, full power (including NVIDIA GPU programming SDK).
Sound: simple recording does not work, but SKYPE works fine.
Ethernet (wired): works
wifi: works
touchpad: works
USB mouse: DOES NOT!!!!!!
connecting phone to USB port: works

Overall, the notebook is in the working condition now.

---

