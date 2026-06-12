---
title: "Battery Monitor Applet"
date: 2008-11-14
forum: Hardware
---

### Post by n1zjd on 2008-11-14
Hello all.  Ive googled and tried tons of different ideas for my issue to no avail.  So I'm now starting my own post to see if anyone cant help.  The laptop that I have is a GammaTech Slimnot N14VY.  Running ubuntu 8.04.  I have graphic card issues and for some reason ubuntu tells me I have 2 processors when I only have 1, and no the processor doesnt have hyperthreading.  Thats just to give you folks an idea of whats going on.  The main thing I'm concerned about fixing is the fact that the battery monitor says no battery present.  This machine came with windows vista and the battery monitor with vista worked fine.  I installed ubuntu after the first time booting with vista.  

Nov 14 07:28:18 SecureLaptop kernel: [   32.210463] ACPI: Battery Slot [BAT0] (battery present)

mike@SecureLaptop:~$ acpi -V
     Thermal 1: ok, 46.0 degrees C
  AC Adapter 1: on-line

Nov 13 21:48:14 SecureLaptop kernel: [   18.177505] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.

That basically tells me when ubuntu is booting is sees the battery fine but not after I log on using gnome.

Does anyone have any ideas as to why the battery monitor shows no battery present?  Please help, thanks.

---

### Post by zhangjiewx on 2008-11-14
I also want to know the answer, may be ubuntu didn't support the battery

---

### Post by n1zjd on 2008-11-14
Well I attempted to recompile the kernel, and admittedly I had no idea what I was doing.  However after recompiling the kernel the battery monitor did work!  Unfortunately I lost my wireless LAN hah.  One problem fixed and one problem created.  I need the wireless however so I guess I need to look into recompiling the kernel once again and seeing what I did wrong.  I used the latest kernel from [http://www.kernel.com](http://www.kernel.com)

---

