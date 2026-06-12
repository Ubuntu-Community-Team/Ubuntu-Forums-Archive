---
title: "Solving the backlight problem the clean way"
date: 2013-04-13
forum: Hardware
---

### Post by shatteringlass on 2013-04-13
Good morning everyone!
I am the owner of an Acer B113-e (which is a business remake of the Acer AO756, which in turn is the pc-version of the google chromebook C7). I've been distro-hopping and always coming back to 'buntus, because I've been a quite-long time Debian user. No distro ever supported the backlight regulation OOTB. I always had to edit /etc/default/grub to include acpi_backlight=vendor and acpi_osi=Linux (the latter made the backlight dim more smoothly, but on the other hand it made the OSD disappear).

The other day, I felt curious and downloaded a Vanilla build of the latest version of Chromium Os and (surprise) brightness and stuff was already working on boot, and the smooth way (every distro always had a choppy way to dim the backlight). Of course, I could not live with Chromium OS, the first reason being that it would not let me connect through Wi-Fi. 

I would like to know if there were a way to include the brightness fix from Chromium OS code into any Linux distro. I am not an avid debugger so I couldn't figure it out myself...I have run lsmod and such on both Chromium OS and my Xubuntu 13.04 and I only managed to figure that the first isn't loading the i915 module at the time of first-boot (so maybe it's more complicated than it seems).

Please somebody help me figure this out. I would like to wipe my HDD and live with Linux only, but sometimes I'm bugged with how flawed hardware integration is in Linux (although latest upstream kernels are fixing many acpi related issues).
Have a good day!

---

### Post by Colabear8900 on 2013-06-01
> **shatteringlass said:**
>  ...I always had to edit /etc/default/grub to include acpi_backlight=vendor and acpi_osi=Linux...

I have found this thread - [http://ubuntuforums.org/showthread.php?t=1864513](http://ubuntuforums.org/showthread.php?t=1864513) - and edited my grub file accordingly. The only difference I see is the additional "vga=792" however, I do not know what it means. My OS is Ubuntu 13.04 64-bit (UEFI mode) and the laptop is an Acer Aspire V3-771G-6485 17.3" with Core i5 CPU, NVidia GeForce GT730m graphics (also the Intel HD 4000). The backlight now stays ON during the boot process and dims smoothly.

The Terminal command is (for those not wanting to hop around the forum) this:

sudo gedit /etc/default/grub

Edit these 2 lines thusly:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor vga=792"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"

Save the file, then, back in Terminal:

sudo update-grub
sudo reboot

Thanks given to Ubuntu Forum Member "techfighterminal" for his October 19th, 2011 post.

---

