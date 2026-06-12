---
title: "Asus X205TA hardware drivers 14.04"
date: 2014-11-25
forum: Hardware
---

### Post by mikhail7 on 2014-11-25
I have 14.04 running on a ASUS X205TA. 
I can't seem to get the internal wifi, bluetooth, sound, or sd card reader to work.
when I run a lshw command this is all I get.

=========================================
                   system     X205TA (ASUS-NotebookSKU)
/0                 bus        X205TA
/0/0               memory     64KiB BIOS
/0/b               memory     2GiB System Memory
/0/b/0             memory     2GiB DIMM DDR3 1333 MHz (0.8 ns)
/0/10              memory     224KiB L1 cache
/0/11              memory     1MiB L2 cache
/0/12              processor  Intel(R) Atom(TM) CPU  Z3735F @ 1.33GHz
/0/100             bridge     ValleyView SSA-CUnit
/0/100/2           display    ValleyView Gen7
/0/100/1a          generic    ValleyView SEC
/0/100/1d          bus        ValleyView USB Enhanced Host Controller
/0/100/1f          bridge     ValleyView Power Control Unit


I know there is more hardware in this system than what is listed.
I am thinking that one of the bridge controllers does not have the right driver.
I have access to the windows drivers, can anything be done with those?

---

### Post by Pilot6 on 2014-11-25
Give output of

lspci -knn
lsusb

---

### Post by mikhail7 on 2014-11-25
Thanks for the responce.

lspci -knn output:

00:00.0 Host bridge [0600]: Intel Corporation ValleyView SSA-CUnit [8086:0f00] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:18cd]
00:02.0 VGA compatible controller [0300]: Intel Corporation ValleyView Gen7 [8086:0f31] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:18cd]
    Kernel driver in use: i915
00:1a.0 Encryption controller [1080]: Intel Corporation ValleyView SEC [8086:0f18] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:182d]
00:1d.0 USB controller [0c03]: Intel Corporation ValleyView USB Enhanced Host Controller [8086:0f34] (rev 0f)
    Subsystem: Device [ec6d:ef8c]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation ValleyView Power Control Unit [8086:0f1c] (rev 0f)
    Subsystem: ASUSTeK Computer Inc. Device [1043:182d]

lsusb output:

Bus 001 Device 005: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN Adapter
Bus 001 Device 004: ID 05e3:0610 Genesys Logic, Inc. 4-port hub
Bus 001 Device 003: ID 0bda:57b5 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 8087:07e6 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The usb WLAN adapter is the wifi dongel I'm using to post this, not the built in wifi

---

### Post by Jon Bradbury on 2014-11-26
I'm going to watch this thread. I have 14.10 running off a USB stick but like the OP there are some key features not working, so it is a bit too soon to be doing a full install.

---

### Post by mikhail7 on 2014-11-26
FYI you can not boot directly off the HD, the 32 bit EFI BIOS will not detect the Ubuntu installation.

The solution to this is to chain boot off the usb stick you used to install Ubuntu.
This it simpler than is sounds, all you have to do is change the grub.cfg file on the usb stick to load the grub on the HD
After making a backup, change the first line of the grub.cfg file to this:

set prefix=(hd1,gpt2)'/boot/grub'

The system will now load off the HD
The only wrinkle is that I have to manually select the kernel to load.
This is probably easily fixed, but my knowledge of boot loaders is rather limited.

---

### Post by ludwig-patrick on 2015-04-05
It's not going to be required to change the grub file anymore. The debian jessie RC2 release now can be fully installed onto the X205TA without changing the installation disk. The only remaining major item that is not working in debian jessie rc2 is the sound card is still yet running. Wifi works as well. I know because I am now running it and it is pretty smooth with XFCE as the desktop. I am sure Ubuntu will soon pick up this change.

---

