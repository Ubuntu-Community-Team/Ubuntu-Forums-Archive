---
title: "New notebook, old system, some issues to be solved..."
date: 2021-12-14
forum: Hardware
---

### Post by 4l3x2 on 2021-12-14
As the object, I bought a new notebook due to the death of my old one.
The new unit is the HP 655.

I updated this new one substituting a 2Gb module of ram with a 4Gb module, so now I have 6Gb total and substituting the hard disk (a 300Gb classic) with my old solid state 60Gb taken from the old notebook.
Running memtestx86 and badblocks resulted in 0 errors, so the "new" hardware is ok.

I have 2 annoying issues now:
- at the boot the system hangs with a totally black screen (after the bios screen) and I have to reboot several times to make it run (XUbuntu 20.04 fully updated)
- even if I installed the right (I suppose...) firmware for Atheros wireless net devices I have the wifi networking disabled and I can't enable it

I fear that both the issues are caused by the wireless interface.
I didn't format the hard disk, I just substitute the hardware wishing that the autodetect could do anything needed, but this time it has some problem (it worked fine several times tough).

To help you helping me, I attached a zip file containing the output of 3 commands:
- sudo dmesg > dmesg.txt
- sudo lsmod > lsmod.txt
- sudo lshw > lshw.txt

I had to compress them due to the file size limit to post here.

Thank you very much in advance

---

### Post by Bashing-om on 2021-12-14
4l3x2; Hello

here I can offer to assist with the graphics.
Let us "suppose" that the graphic's driver that is on the old drive is not compatible with the new hardware.

Let's take a look at what is:
Post back - between code tags - the results of terminal command:
```

sudo lshw -C display
lspci -k | grep -iEA5 'vga|3d'

```
where we will see if a driver is loaded and then what the hardware is.

[INDENT]longest journey
[INDENT][INDENT]begins with that first step
[/INDENT][/INDENT][/INDENT]

---

### Post by 4l3x2 on 2021-12-15
Any help is appreciated, both because the several reboots can be caused by the graphic card and I can learn something new.

Here is the output of the commands:
```

alex@Alessandro:~$ sudo lshw -C display
[sudo] password di alex: 
  *-display                 
       description: VGA compatible controller
       product: Wrestler [Radeon HD 7310]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:30 memory:e0000000-efffffff ioport:3000(size=256) memory:f0300000-f033ffff memory:c0000-dffff
alex@Alessandro:~$ lspci -k | grep -iEA5 'vga|3d'
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler [Radeon HD 7310]
    DeviceName: AMD Radeon HD 7310 Graphics
    Subsystem: Hewlett-Packard Company Wrestler [Radeon HD 7310]
    Kernel driver in use: radeon
    Kernel modules: radeon
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Wrestler HDMI Audio
alex@Alessandro:~$ 

```

Meanwhile the problem has become less annoying:
at the first reboot after installing the wifi drivers nothing changed, but this morning the reboots are less than 3 and I can enable and disable wifi. Moreover, it shows several access points, but not my smartphone.
I have a Samsung J5 2016, the access point is configured in Wps2 (the only other option is uncrypted/open), I'm browsing using the usb tethering.

---

### Post by grahammechanical on 2021-12-15
So, the Hp 655 has an AMD Radeon HD 7310 video adapter. And Ubuntu is running on the Radeon open source video driver. What video adapter did the old laptop have? Was the old laptop using a proprietary video driver?

Ubuntu comes with a recovery mode. We access it at the Grub boot menu by selecting Advanced options for Ubuntu and then selecting a Linux kernel with recovery mode. We get a recovery menu and the top option is Resume. This should load to the desktop using a low resolution open source video driver. If that proves to be a more acceptable way to load Ubuntu then it might indicate that the problem is with the video driver.

If you are now getting access to the internet you can open Software & Updates>Additional Drivers tab. Allow time for the system to search the internet and you might be offered a proprietary video driver for installation. 

Regards

---

### Post by 4l3x2 on 2021-12-16
Since I set the Grub's timeout to 0sec I pushed Shift to force the system showing the menu.
Starting in Recovery mode went fine, but the Additional Drivers tool says "No additional drivers available" and, in the bottom part of the window, "No proprietary driver in use".

The first machine on which the disk were mounted had Amd processor and Ati video card, the second had Intel processor and Intel video card (when I updated the system from 18.04 to 20.04), until now it worked like a jewel.

You can say: "It's time to do a clean install..."
I agree, but I should do so many tweaks and say goodbye to Docky, I don't wanto to... :tongue:

---

