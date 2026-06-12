---
title: "How do I install a Matrox G550 Driver"
date: 2010-01-20
forum: Hardware
---

### Post by CharlieBanks on 2010-01-20
I'm a NUBE to Linux. I built a computer out of spare parts to try Ubuntu
I used a Matrox G550 Video card. The problem is that when I installed Ubuntu 9.1 the system sees the card but resolution is limited to 800 x 600
 
I downloaded a driver from Matrox (matrox_driver-x86_32-4.4.0.tar.gz) How do I install it?
 
Just as a note - I am using this card with a single  VGA monitor (it's what I had available)  I do not need DVI or Dual configurations just better resolution

---

### Post by anglican on 2010-01-22
> **CharlieBanks said:**
> I'm a NUBE to Linux. I built a computer out of spare parts to try Ubuntu
I used a Matrox G550 Video card. The problem is that when I installed Ubuntu 9.1 the system sees the card but resolution is limited to 800 x 600
 
I downloaded a driver from Matrox (matrox_driver-x86_32-4.4.0.tar.gz) How do I install it?
 
Just as a note - I am using this card with a single  VGA monitor (it's what I had available)  I do not need DVI or Dual configurations just better resolution

I'm using that card on a desktop system running Hardy. You're probably already using the appropriate driver, you can check with:

grep mga /var/log/Xorg.0.log

which should show that the module is loaded already. If not, it may be that the driver isn't installed in which case use synaptic (or other package manager) to install xserver-xorg-video-mga.

The resolution problem is probably caused by the card failing to detect monitor modes and making pessimistic assumptions about available resolutions. You can add some modes to the file /etc/X11/xorg.conf (the file may not exist, create it if not), something like:

Section "Device"
        Identifier      "Matrox Graphics, Inc. MGA G550 AGP"
        Driver          "mga"
        BusID           "PCI:1:0:0"
        Option          "OldDmaInit"            "True"
EndSection

Section "Monitor"
        Identifier      "Your_monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Matrox Graphics, Inc. MGA G550 AGP"
        Monitor         "Your_monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

The BusID entry may differ on your system, use `sudo lspci` to check the right values. Of course Hardy isn't Karmic and you may have some other Karmic specific problem ;)

H

---

