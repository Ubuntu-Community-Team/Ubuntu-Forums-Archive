---
title: "Acer Aspire V7 482P"
date: 2014-01-04
forum: Hardware
---

### Post by dldeskins on 2014-01-04
I would like to install xubuntu on my new Acer Aspire V7 482P.  I tried several different ways to startup or run on a USB.  With the windoze LiLi Usb creator, it would not start. I got a grub menu then the screen went black and the flash drive stopped flashing.  It also installed portable VirtualBox.  When I tried to start the virtual machine, it said that the kernel was 64 bit but the machine was only 32 bit.

I also created a usb flash drive from unetbootin under Linux Mint.

Does anyone know what I am doing wrong?

---

### Post by dldeskins on 2014-01-07
This probably has to do with the graphics... does anyone know how I can start to get it to work?

---

### Post by dldeskins on 2014-01-28
Fedora works... can anyone help me?

---

### Post by dldeskins on 2014-02-17
It will boot and install with the following additions to the grub menu:

acpi_osi=Linux acpi_backlight=vendor libata.force=noncq

This has to do with using an SSD and the new Intel 4400 graphics

---

