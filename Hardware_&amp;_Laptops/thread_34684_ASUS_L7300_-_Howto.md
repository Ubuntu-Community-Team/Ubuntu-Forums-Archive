---
title: "ASUS L7300 - Howto"
date: 2005-05-16
forum: Hardware &amp; Laptops
---

### Post by nautilus on 2005-05-16
Greets!  Here's a short & sweet howto to get your Asus L7300 laptop working like a champ with Ubuntu.  The *only* piece not covered is the modem, only because I simply have no use for it.

First, install Hoary.  This should go as planned.  If you wish to use hibernate, you'll need to reserve a vfat partition at least the size of your installed RAM.

Next, to get X nice and filling your screen, ensure your Monitor section looks like this:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       20-60
        VertRefresh     20-120
EndSection

```

And, above this in the Device section for the video card, it should look like this:

```
Section "Device"
        Identifier      "Silicon Motion, Inc. SM910"
        Driver          "siliconmotion"
        ChipSet         "lynx"
        Option          "NoMTRR"
        Option          "NoDDC"
        BusID           "PCI:0:2:0"
EndSection

```

NoMTRR will make it so X doesn't lock your system up, and ChipSet will fix the 'ghosting'.  NoDDC is just to enforce our own refresh settings we added in the Monitor section.

Now!  For audio:

Open /etc/modules in your editor (as root, or sudo vi, sudo nano) and add this to the end:

```
snd-opl3sa2
```

Finalyl, also as root, add this to /etc/lilo.conf prior to your kernels list:

```
append=" noinotify apic=off acpi=off pci=norouteirq noapic nolapic noacpi noapm noonotify video=vesafb:nomtrr"

```

inotify is used to notify programs when certain files are modified, but doesn't work on this system (for whatever reason), and APIC/ACPI are disabled since they're rather old on the board and are rather flakey.  

I hope this helps others, I know I spent a day or so banging my head against the wall trying to get this 'perfect'.

---

### Post by Yapser on 2005-06-27
Thanks! I have such a laptop. Some things:

Ubuntu uses Grub instead of Lilo, i had to edit an other file.

For the folks dat dunno how to edit the files: Press 'ctrl-alt-f1' before Gnome does appear.

---

