---
title: "Bluetooth Earphones Issue - Both Connects under same name (no master-slave config..)"
date: 2019-12-28
forum: Hardware
---

### Post by ankushkale1 on 2019-12-28
Hi,

I have Ubuntu mate 18.04 & recently I bought[ Haylou GT 1 Pro]("https://www.aliexpress.com/item/4000127727081.html") earbuds, which connects to mobile / laptop directly , each one connects with same name ,
So they are working fine with Android 9 mobile but not working in Ubuntu, I hear no sound and Bluetooth manager shows connected.
I have another earphone from same brand with Master-Slave configuration which is working.

**dmesg**:

[ 1313.700337] input: E8:EC:A3:1E:14:B0 as /devices/virtual/input/input26
[B]
bluetoothctl :[/B]

Agent registered
[Haylou-GT1 Pro]# info
Device E8:EC:A3:1E:14:B0 (public)
    Name: Haylou-GT1 Pro
    Alias: Haylou-GT1 Pro
    Class: 0x00240418
    Icon: audio-card
    Paired: yes
    Trusted: yes
    Blocked: no
    Connected: yes
    LegacyPairing: yes
    UUID: Serial Port               (00001101-0000-1000-8000-00805f9b34fb)
    UUID: Headset                   (00001108-0000-1000-8000-00805f9b34fb)
    UUID: Audio Sink                (0000110b-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control Target (0000110c-0000-1000-8000-00805f9b34fb)
    UUID: Advanced Audio Distribu.. (0000110d-0000-1000-8000-00805f9b34fb)
    UUID: A/V Remote Control        (0000110e-0000-1000-8000-00805f9b34fb)
    UUID: Handsfree                 (0000111e-0000-1000-8000-00805f9b34fb)

---

