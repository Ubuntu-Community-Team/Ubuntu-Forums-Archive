---
title: "buying a hp pavilion dv6645"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by thebrotherofasis on 2007-11-11
Hello... I'm buying a hp pavilion dv6645. I want to know if any of you guys have experience in installing ubuntu in the hp pavilion computers, and to hear some of your experiences in terms of hardware support, and all in all, satisfaction using it.

Another question: Is it safe to install ubuntu on a laptop, in spite of the known issue of hard disk exagerated usage with the new gutsy?

I am actually planing to install ubuntu as soon as i recieve my brand new hp, with vista preinstalled. I have heard vista is crap... so what I plan to do is to install ubuntu, and virtualize xp with virtualbox. Never done this before, even in my desktop computer... but i need to run some applications that don't work under ubuntu.

The tech specs of this laptop are: (will ubuntu recognize ad install this hardware?)

Product Features and Technical Details
Product Features

    * Entertainment-centric notebook PC with widescreen 15.4-inch LCD and stylish high-gloss finish with wave imprint, integrated webcam
    * 64-bit 1.9 GHz AMD Turion 64 X2 TL-58 processor, 160 GB hard drive, 2 GB RAM (4 GB max), LightScribe dual-layer DVD drive
    * 54g Wi-Fi (802.11b/g); 10/100 Ethernet; Nvidia GeForce Go 7150 graphics (up to 559 MB of available memory)
    * Connectivity: 3 USB, 1 FireWire, 1 VGA, 1 S-Video, expansion port 3 connector, ExpressCard 54/34, 5-in-1 memory card reader
    * Pre-installed with Windows Vista Home Premium (with Media Center capabilities)

Processor, Memory, and Motherboard

    * Hardware Platform: PC
    * Processor: 1.90 GHz AMD Turion 64
    * Number of Processors: 2
    * RAM: 2000 MB
    * RAM Type: DDR2 SDRAM

Special Features

    * Condition: New
    * Operating Systems: Windows® Vista? Home Premium
    * Platform: Notebook PC
    * Expansion Ports: 1 - Express Card Slot/54 or 34
    * PS/2 Keyboard Connectors: N/A
    * PS/2 Mouse Connectors: N/A
    * Serial Communication Ports: N/A
    * Parallel Ports: N/A
    * USB Ports: 3
    * FireWire Ports: 1
    * Fast Infrared Ports (FIR): 1 - Consumer IR
    * LAN Ports: 1
    * Modem Ports: 1
    * Audio Out Jacks: 2
    * Line In Jacks: N/A
    * Microphone Jacks: 1
    * VGA Ports: 1
    * S-Video Connectors: 1 - TV Out
    * DVI Video: N/A
    * Port Replicator/Connector: 1

Hard Drive

    * Size: 160 GB
    * Type: Serial ATA

Cases and Expandability

    * Size (LWH): 10.12 inches, 6.5 inches, 1.69 inches
    * Weight: 9.1 pounds

---

### Post by scorp123 on 2007-11-11
Stay away from computers with Broadcom WiFi chipsets. Some of those Pavilions use Intel-based chips, e.g. Intel 3945ABG Wireless ... those are good and will work. Those with Broadcom chipsets most likely won't work or are at least complicated to setup.

My Pavilion dv2108ea has Intel everywhere and works almost perfectly. The only thing I can't get to work --and honestly I really don't care-- is the webcam. Despite having installed the right driver the webcam refuses to produce a picture ... but as I said, I don't care. The rest works.

---

### Post by thebrotherofasis on 2007-11-11
Ok, thanks for your opinion. Anything to say about this [bug]("https://bugs.launchpad.net/ubuntu/+bug/104535") ?

It mentions that running Gutsy Gibbon on a laptop could possibly end up causing an early demise of the laptop hard disk.

Have you run the 

$ sudo hdparm -B 255 /dev/sda

command?

Thanks

---

