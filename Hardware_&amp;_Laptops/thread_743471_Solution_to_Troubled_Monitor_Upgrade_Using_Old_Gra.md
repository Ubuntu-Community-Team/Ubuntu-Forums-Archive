---
title: "Solution to Troubled Monitor Upgrade Using Old Graphics Card"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by noctiphile on 2008-04-02
I tried to do a smooth monitor upgrade with Ubuntu and it didn't work.  The best advice I could find was to run```
sudo dpkg-reconfigure -phigh xserver-xorg
```if I had any trouble after plugging it in.  I did have trouble and that didn't help, so I wanted to post what finally did.

I have a Hercules 3D Prophet II GTS 64MB graphics card with the nVidia GeForce2 GTS chipset.  This card is like 5-8 years old.  I just bought a current model LCD monitor to replace my old CRT.  It is a Samsung SyncMaster 943BX.  The monitor's native resolution is 1280x1024 at 60Hz.  What I didn't realize is that the card supports the monitor's resolution, but at a higher frequency than the monitor supports.  Tests with Windows XP and the Kubuntu 7.04 CD showed me that the 1024x768 resolution would work.

When Ubuntu was starting up, X crashed and put me into the console after supplying me with the message that no usable screens were found.  No changes to /etc/X11/xorg.conf made any difference at all.  The command above did nothing helpful.  It didn't even probe the Plug-n-play monitor correctly.  I still had to edit the frequencies and resolutions by hand.

I found the difference between the Kubuntu startup and the Ubuntu one, was a frame buffer paramenter given to the kernel.  The xorg log (/var/log/Xorg.0.log) in Ubuntu was stating that the "panel" size was 720xsomething.  In Kubuntu it was bigger.  **After I added vga=792 to the kernel command line options in grub (/boot/grub/menu.lst) I was able to boot normally again.**  The number 792 came from a [table]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions#Linux_video_mode_numbers") I found in Community Docs under BootOptions.  It corresponds to a resolution of 1024x768.  I tried 1280x1024 but logically no software setting is going to help if the hardware is incompatible.

I hope this helps many people having monitor upgrade trouble!

---

