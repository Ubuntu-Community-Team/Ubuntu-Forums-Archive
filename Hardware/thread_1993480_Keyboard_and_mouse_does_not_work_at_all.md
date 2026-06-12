---
title: "Keyboard and mouse does not work at all"
date: 2012-06-02
forum: Hardware
---

### Post by b3ta on 2012-06-02
Hello!

Yesterday I tried to install ubuntu using the Ubuntu 12.04 amd64 desktop iso. When the installer launched with the welcome screen, the mouse was very laggy, like moving the mouse and 5 seconds later the the pointer would move. After a few minutes I could move the mouse normally, but I could not click on anything like the continue button. The keyboard was completely dead. So today I figured I would try the alternate install, everything worked well (the keyboard worked with the text install). When the installation was complete and I booted into ubuntu, the same thing happend again but at the login screen, exactly the same phenomena.

Since I normally use bluetooth keyboard and mouse I used standard wired usb-keyboard and mouse, Microsoft Comfort Optical Mouse 1000 and Logitech Deluxe 250 keyboard. I have also tried with an PS/2 keyboard, same thing.

I also tried to run in low graphics mode through the recovery mode. It said something like it could not recognize my monitor/keyboard/mouse settings and fallsback to the menu in recovery mode. 

I have tried setting USB to legacy in BIOS, no success.

My hardware:

ASUS P6T DELUXE V2 X58 S-1366 ATX
INTEL CORE I7 950 3.06GHZ 8MB S-1366 
CORSAIR DDR3 XMS3 INTEL I7 PC16000 2000MHZ (Total 12GB)
INTEL X25-M 2.5" 160GB SSD SATA/300 MLC 34NM
KFA2 GEFORCE GTX 580 1536MB PCI-E DVI/HDMI 
DELL U2711 ULTRASHARP 27" WIDE TFT BLACK (Connected with Dual-Link DVI)

Does anyone know where to go from here? Thanks in advance!

Edit: Everything works fine in Windows 7.

---

### Post by b3ta on 2012-06-02
Ok, so I fixed it. It was this bug:
[https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/990411](https://bugs.launchpad.net/ubuntu/+source/libdrm/+bug/990411)

Workaround found here:
[http://askubuntu.com/questions/126193/12-04-stuck-at-the-login-screen/126336#126336](http://askubuntu.com/questions/126193/12-04-stuck-at-the-login-screen/126336#126336)

Everything works perfectly now. :-)

Edit: Marked as solved.

---

