---
title: "want to convert to hardy, what hardware will/wont work on my comp?"
date: 2009-01-31
forum: Installation &amp; Upgrades
---

### Post by jackechanprime on 2009-01-31
ok, i'm running an acer aspire 6920. here's my hardware list as given by vistas 'device manager', your the experts (namely, that is to say: i'm NOT) so please guys, tell me what parts of this machine will/ wont work if i go to hardy. here goes:

batteries:
-Microsoft AC adapter
-Microsoft ACPI-compliant control method battery
Computer:
-ACPI x64-based PC
disk drives:
-ST9250827AS
Display adapters:
-Mobile intel(R) 965 Express Chipset family
DVD/CD-Rom drives:
-Slimtype DVD A DS8A1p ATA Device
Human interface devices:
[I'll abridge this part]
- HID-compliant consumer control device [listed twice]
- HID-compliant device [listed three times]
- ITECIR Infrared Receiver (EC)
- Microsoft eHome infrared Transceiver
- USB Human Interface Device
IDE ATA/ATAPI controllers:
- ATA channel 0
- ATA channel 1
- Intel(R) 82801HEM/HBM SATA AHCI controller
- Inter(R) ICH8M Ultra ATA Storage Controllers - 2859
Imaging devices:
- Acer Crystal Eye webcam
Keyboards:
- Launch manager
- Microsoft eHome MCIR 109 keyboard
- Microsoft eHome MCIR Keyboard
- Microsoft eHome Remote control Keyboard keys
Mice and other pointing devices:
- HID-compliant mouse [again listed twice]
- synaptics PS/2 Port TouchPad
Modems:
- Agere Systems HDA modem
Monitors:
- Generic PnP monitor
Network adapters:
- Atheros AR8121/AR8113/AR8114 PCI-E ethernet Controller
- Intel(R) Wireless WiFi Link 4965AGN
Personal identification devices:
- Validity Sensor
Processors:
- Intel (R) core(TM)2 Duo CPU t5750 @ 2.00GHz[again listed twice]
Sound, video and game controllers:
- Realtek High Definition Audio
Storage controllers:
- Microsoft iSCSI initiator
System devices:
- ACPI fan
- ACPI fixed Feature button
- ACPI lid
- ACPI power button [please tell me that will work. lol]
- ACPI thermal zone [listed 4 times]
- Consumer IR Devices
- Direct memory access controller
- Generic Bus
- High definition Audio Controller
- Intel(R) 82802 PCI bridge -2448
- Intel(R) 82802 Firmware Hub device
- Intel(R) ICH8 family pci Express root port1 - 283f
- Intel(R) ICH8 family pci Express root port2 - 2841
- Intel(R) ICH8 family pci Express root port3 - 2843
- Intel(R) ICH8 family pci Express root port4 - 2845
- Intel(R) ICH8 family pci Express root port5 - 2847
- Intel(R) ICH8 Family SMBus Controller - 283E
- Intel(R) ICH8M LPC Interface Controller -2815
- Microsoft ACPI-compliant embedded controller
- Microsoft ACPI-compliant System
- Microsoft Composite Battery
- Microsoft System Management BIOS driver
- Microsoft Windows Interface for ACPI [listed twice]
- Mobile Intel(R) PM965/GM965/GL960 Express Prossor to DRAM controller - 2A00
- numeric data processor
- PCI bus
- Plug and Play software Device Enumerator
- Programmable interrupt controller
- system CMOS/Real time clock
- System timer
- UMBus Enumerator
- UMBus root bus Enumerator
Universal Serial Bus controllers:
- Intel(R) ICH8 family USB Universal Host Controller - 2830
- Intel(R) ICH8 family USB Universal Host Controller - 2831
- Intel(R) ICH8 family USB Universal Host Controller - 2832
- Intel(R) ICH8 family USB Universal Host Controller - 2834
- Intel(R) ICH8 family USB Universal Host Controller - 2835
- Intel(R) ICH8 family USB2 Enhanced Host Controller - 2836
- Intel(R) ICH8 family USB2 Enhanced Host Controller -283A
- USB composite DEvice
- USB root hub [listed 7 times]

*wheeeeeeze* and that's it.
if worst comes to worst, just tell me weather or not the important stuff will work. (wifi, video, ect.) i think we can stand loosing a few bells and whistles as long as the system as a general whole still works fine.

---

### Post by mikewhatever on 2009-01-31
There is quite a lot of hardware by Microsoft,. Is that a joke (vistas 'device manager' being funny), or is MS making hardware apart from peripherals? As for the rest of it, all Intel related hardware should be good to go, Atheros may not work.
That said, you should really download either 8.04 or 8.10 desktop cds and simply boot from it. Provided there is enough RAM, the OS will load running from the cd and leaving the HDD untouched. You can then test the hardware extensively and reliably.

---

### Post by cariboo on 2009-02-01
You  forgot the two most important things,  how much ram does your laptop have and how big is the hard drive. 

If you decide to install, I would advise you defrag the hard drive at least twice and use Vista's disk management tools to resize the hard drive. 

Be warned that ATI does not provide the greatest graphics adapter drivers. THe rest of the hardware should be supported out of the box.

Jim

---

### Post by mikewhatever on 2009-02-01
I think, since the OP runs Vista, there is at least 512 MB of RAM and quite a lot of hdd space.

---

### Post by albinootje on 2009-02-01
> **jackechanprime said:**
> ok, i'm running an acer aspire 6920. here's my hardware list as given by vistas 'device manager'
It makes sense to burn an Ubuntu 8.04.2 cdrom and boot from that using the "try without installing" option.

A quick search for :
```

acer "aspire 6920" ubuntu hardy

```
showed this :
[https://bugs.launchpad.net/ubuntu/+bug/218165](https://bugs.launchpad.net/ubuntu/+bug/218165)
[https://answers.launchpad.net/ubuntu/+question/42289](https://answers.launchpad.net/ubuntu/+question/42289)
so .. sounds might not work out of the box.

See also here :
[http://www.linlap.com/wiki/acer+aspire+6920](http://www.linlap.com/wiki/acer+aspire+6920)

---

### Post by jackechanprime on 2009-02-02
yeah, the HDD is multi-gig, 120gig to be exact.

and the thing has a monsterous 4 gig's of ram, so that's not gonna be a problem.

keep up the good work guy!

so just by skimming these results, i can see that the sound might be an issue. if anyone knows of any bugfixes for this issue, PLEASE SPEAK UP!!

i'll do my own rooting around too.

thanks all!
jack

---

### Post by jackechanprime on 2009-02-02
bump

---

### Post by albinootje on 2009-02-02
> **jackechanprime said:**
> bump

I've looked up 3 links for you, from which at least one seems to offer a solution afair, so please do some more reading.
And did you try the "live session" of the Ubuntu installation cdrom on your machine to get a first impression ?

We can hold you hand for your first steps in Ubuntu, but you will have to move your feet yourself every now and then ;-)

---

### Post by jackechanprime on 2009-02-03
oh, man, i'm sorry guys. i only had time to skim over the links. i had yet to make time to really look at everything there. and were actually about to try the live session as we speak, since we had to go out and get a blank cd (meant going shopping... in more ways than one)

thank you for putting up with me though!!

will get back to you with the results.
jack

---

### Post by jackechanprime on 2009-04-21
(months later)

er... right, poor follow through there on my part. the owner of the laptop decided to take a miss for now. she's big on music, and having only some of the speakers working doesn't quite suit her fancy. >_> personally i would have done it cause vista's CRAP, but... well, what can u do...

we tried the CD, gave it a test run. Worked like a charm. i think the sound was null without the fix though. (months ago now, so i can't remember too well.) till a stronger driver hits the circuit, that comp's staying vista. :(

---

