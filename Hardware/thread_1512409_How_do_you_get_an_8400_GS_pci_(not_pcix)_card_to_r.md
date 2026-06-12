---
title: "How do you get an 8400 GS pci (not pcix) card to run on a D945GCLF2 motherboard"
date: 2010-06-18
forum: Hardware
---

### Post by bwallum on 2010-06-18
Hi

How do you get an 8400 GS pci (not pcix) card to run on a D945GCLF2 Intel motherboard running Ubuntu Lucid?

This motherboard has onboard graphics, the CMOS can be setup to use graphics on the PCI slot. However, the card does not work. It does work on the same rig running Windows 7.

There is some indication that /etc/modprobe.d/blacklist.conf needs 

blacklist intel_agp
blacklist agpgart

to make streaming work [http://www.dabs.com/products/pny-geforce-8400gs-576mhz-512mb-pci-vga-dvi-i-5K9L.html#reviews](http://www.dabs.com/products/pny-geforce-8400gs-576mhz-512mb-pci-vga-dvi-i-5K9L.html#reviews)

Any ideas?

---

### Post by dino99 on 2010-06-18
give it a try: sudo update-pciids && update-usbids 

and watch at usefull errors into .xsession-errors and logs (system admin logviewer)

---

### Post by ronnielsen1 on 2010-06-18
I don't remember all of the steps that I used to get my 8400GS working. I downloaded compiz check which told me about my blacklisted card where I had to unlist it and then I used the driver from nvidia's site
[http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check)

[http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html](http://www.nvidia.com/object/linux-display-ia32-195.36.31-driver.html)

---

### Post by ronnielsen1 on 2010-06-18
After being pestered to upgrade xserver and xorg forever, I finally let it and promptly lost my compiz. I downloaded the newest driver from nVidias site and:

Opened a terminal and typed in sudo /etc/init.d/gdm stop

This shuts down X and opens a terminal

Login with your username and password

Cd to where you downloaded. On mine it was

cd /home/ron/Downloads

sudo init 3

chmod +x NVIDIA-Linux-x86-195.36.31-pkg1.run

sudo ./NVIDIA-Linux-x86-195.36.31-pkg1.run

Go through the questions accepting what sounds right. Hopefully you don't get any errors

If successful, type

sudo /etc/init.d/gdm start

---

### Post by ronnielsen1 on 2010-06-18
By the way, I do have an onboard Intel video card I'm not using (which my BIOS won't let me turn off) so the onboard shouldn't be a problem

---

### Post by ronnielsen1 on 2010-06-18
> There is some indication that /etc/modprobe.d/blacklist.conf needs 

blacklist intel_agp
blacklist agpgart

This is what I added to 
> blacklist amd76x_edac
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

I'm not sure we have the same intel card but lspci is

> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 Display controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
01:05.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)


---

