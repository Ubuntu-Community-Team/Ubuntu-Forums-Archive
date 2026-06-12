---
title: "Please how to ACPI drivers"
date: 2009-12-22
forum: Hardware
---

### Post by ju4nj0 on 2009-12-22
Hi
need install AGP drivers for BIOS ACPI Asus A7V880 because have problem:

> 
k1316@k1316-Machine:~$ sudo lshw -C video
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: NV44A [GeForce 6200]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 maxlatency=1 mingnt=5
       resources: memory:fd000000-fdffffff memory:a0000000-afffffff(prefetchable) memory:fc000000-fcffffff memory:fe200000-fe21ffff(prefetchable)
in windows  i have drivers but no in ubuntu
y si puede ser en español mejor jejeje
thanks

---

### Post by ju4nj0 on 2009-12-23
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. KT880 Host Bridge (rev 80)
00:00.1 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. KT880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:09.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by ju4nj0 on 2009-12-23
Enable PATA/IDE DMA Mode in VIA South Bridge Chips HOWTO:


2. Step by Step
   In this section, it teaches users how to modify the code and rebuild the kernel step
   by step to enable the DMA mode in their system.
  2.1 Get the kernel source
      First of all, users have to download and decompress the kernel source package.
      The kernel 2.6.18.2 is used to be the example.
          # cd /usr/src/
          # tar xjf linux-2.6.18.2.tar.bz2.
          # cd linux-2.6.18.2
      Alternatively, if users want to use the default kernel in an installed Linux OS,
      please install the default kernel source package from installation CD/DVD. Then
      copy the configuration file from /boot/.
          # cp /boot/config-2.6.18-y-z     /usr/src/linux-2.6.18-y-z/.config
          # cd /usr/src/linux-2.6.18-y-z
          # vi Makefile
      Assume the kernel version is 2.6.18-y-z, then modify the 4th line of the Makefile
      from “EXTRAVERSION = XXX” to “EXTRAVERSION = -y-z”
  2.2 Modify the via82cxxx.c
      Then modify the drivers/ide/pci/via82cxxx.c file. Go to line 69 and define the
      following variables.
          #define VIA_BAD_AST                           0x200 /* Don’t touch Address Setup Timing */
          #define PCI_DEVICE_ID_VIA_CX700                      0x8324
          #define PCI_DEVICE_ID_VIA_CX700-IDE                  0x5324
          #define PCI_DEVICE_ID_VIA_8237S                      0x3372


but file  via82cxxx.c doesnt exist in drivers/ide/pci/

weris the file via82cxxx.c ?

---

