---
title: "[SOLVED] Sound Capture Error"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by BandD on 2007-11-28
I know there are a lot of posts out there about mic and sound capturing problems, but I couldn't find anything after two days of searching through the forums and google to help.  So I thought I'd give it a try.

I have an HDA Intel card with a Realtek ALC260 chip.  The PCI id is 8086:2668.  I'm working on a Vaio notebook, VGN-FS620.  

All my audio works GREAT except for the mic.  When I go to System--> Preferences--> Sound and click on the 'Test' button next to 'Sound Capture' I get the following error message:

[IMG]http://www.7thyear.com/dci/media/c32%201196258905%20Screenshot-gnome-sound-properties-1.png[/IMG]

So obviously that limits anything I can even begin to do.  Any suggestions would be GREATLY appreciated.  

Also, I'm a bit of a Linux noob.  So if you have some ideas, please give me the steps.  

THANKS!!

*edit* my info from lspci: 

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
06:03.0 CardBus bridge: Texas Instruments PCI7420 CardBus Controller
06:03.2 FireWire (IEEE 1394): Texas Instruments PCI7x20 1394a-2000 OHCI Two-Port PHY/Link-Layer Controller
06:03.3 Mass storage controller: Texas Instruments PCI7420/7620 Combo CardBus, 1394a-2000 OHCI and SD/MS-Pro Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 03)

---

### Post by BandD on 2007-11-29
*bump*

---

### Post by BandD on 2007-12-02
So I've tracked the main problem here down to Pulse Audio.  I uninstalled it via the package manager.

(System--> Administration--> Synaptic Package Manager, then click on a package and type pulse to search for the installed components.  Click on the installed pulse components and mark them for uninstall.  Then click apply.)  

I rebooted and then the mic seems to be working, more or less.  I still get an error when I try to test it in the Sound Preferences, but it is a different error.  See the screen shot below:

[IMG]http://www.7thyear.com/dci/media/c33%201196642154%20Screenshot-gnome-sound-properties.png[/IMG]

But Skype can now use the microphone and so can Audacity.  So removing Pulse seemed to have fixed all my sound troubles.

I also realized that I couldn't get any sound from flash movies (like youtube and addictinggames) and this solved my problem with that as well.

So uninstalling Pulse FIXED sound recording issues (mic not working) and no sound in flash ( youtube and addictinggames).

Still no sure about the unable to create the test pipline error though.  But what the hey, it doesn't really seem to matter!!

---

