---
title: "Bluetooth USB Dongles with Xenial"
date: 2017-02-07
forum: Hardware
---

### Post by johnaaronrose on 2017-02-07
Bluetooth works OK with Xenial on my newish Barebones which has integrated Bluetooth. However, on my other PCs using Xenial, none of my 3 USB Bluetooth Dongles work. lsusb is able to see them all:
Bus 001 Device 010: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 012: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 011: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x UART Bridge / myAVR mySmartUSB light

The same bluez* (bluez, bluez-cups, bluez-obexd) and libbluetooth3 packages are installed as on the Barebones.

My other PCs can't see my phone but my phone can see my other PCs.

Any ideas?

---

### Post by efflandt on 2017-02-08
This tiny one I got on sales at Fry's Electronics works for me to link to my Samsung J7 or Logitech Di Novo Edge keyboard in 16.10:
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)

But I am not exactly certain what Bluetooth is supposed to be able to do with a phone. In Ubuntu it appears that I should be able to send files to the phone (there is a "Send Files..." button or link). But selecting files in Ubuntu seems to do nothing. Bluetooth on the phone itself only says "Connected for media audio", which if I play music on the phone comes through my computer speakers (phone speaker silent) or that would probably work as a speaker phone during a phone call.

If you want to send files back and forth to an Android phone not using wires, it is probably easiest using **AndFTP** app on the phone to do sftp over WiFi (assuming you installed ssh server in Ubuntu which is not installed by default). You can use Linux ssh keys instead of passwords. Note that newer Android versions (I have 6.0.1) seem to block write access to microSD from internal storage. But for AndFTP you can configure one sftp connection with internal storage as home and a 2nd connection with microSD as home, so you can transfer files to it.

In the other direction I use **SimpleSSHD** on the phone. That uses dropbear and requires an ssh public key in an authorized_keys file, unless you want to look on the phone for a random password it generates if no authorized_keys file. Nautilus (file manager) can connect to that with ssh://IP:2222 URL. What is confusing is that the default home path **/sdcard/ssh** in SimpleSSHD really loops back to internal storage at **/storage/emulated/0/ssh**, so an ssh directory in internal storage is where you should put authorized_keys. So when you log in you end up in /storage/emulated/0/ssh (= /sdcard/ssh) where you have read-write access. The microSD is actually under /storage/UUID, which with a factory formatted microSD may be /storage/0000-0000 where you have read & execute permission, but not write permission. Even though internal storage is ext4 it will not allow you to use ext2 or ext4 on microSD (phone says it is corrupt), it seems to want FAT32 or exFAT (or little old FAT16 worked).

---

