---
title: "A BIG problem and nobody can help me"
date: 2006-01-11
forum: Installation &amp; Upgrades
---

### Post by stefanv on 2006-01-11
Hello,

This is my first post and I want to excuse myself for my poor english... I hope you will understand what I'm will say :).
My problem is that I want to install Ubuntu on an old Compaq Proliant 2500 (this is what my boss wants) and the computer halts at the message "input: AT Translated Set 2 keyboard on isa0060/serio0". I'm not a Linux expert but I've asked many people and nobody could help me. I've tried to give some parameters before the installation starts, but... the system halts in the same place :(. Can someone tell me what to do?

---

### Post by deNoobius on 2006-01-11
Sounds like it's bogging down at the keyboard...have you tried to isolate the problem by plugging in another keyboard, then installing?

---

### Post by stefanv on 2006-01-11
Yes.. no luck :(

---

### Post by stefanv on 2006-01-11
I guess I can't find an answer :(.

---

### Post by deNoobius on 2006-01-11
You'll eventually get one, be patient.  It's taken me a few days to get answers sometimes.  Bump it up or repost it if it takes too long.  In the meantime, any more details you can provide will be helpful.  For example, more information on the computer--the size of the HD, the amount of RAM, etc--would be helpful.  Are you sure there is enough HD space to install Ubuntu, for example?

---

### Post by WWTiger on 2006-01-11
Did you have another OS on the computer before you tried installing?

If so, was it working appropriately?

---

### Post by dcstar on 2006-01-12
[QUOTE=stefanv]Hello,

This is my first post and I want to excuse myself for my poor english... I hope you will understand what I'm will say :).
My problem is that I want to install Ubuntu on an old Compaq Proliant 2500 (this is what my boss wants) and the computer halts at the message "input: AT Translated Set 2 keyboard on isa0060/serio0". I'm not a Linux expert but I've asked many people and nobody could help me. I've tried to give some parameters before the installation starts, but... the system halts in the same place :(. Can someone tell me what to do?[/QUOTE]
I believe it is stopping at the section where it tries to detect the mouse (after it has detected the keyboard ok - hence that message you can see).

Do a search for "disable APIC" and you might get a boot string that will allow you to continue with the install, otherwise have a look in the BIOS and see if changing the Mouse settings help.

---

### Post by stefanv on 2006-01-12
Thanks for your answers! 
deNoobius>My system has 2 processors running at 200 MHz each, 512RAM and 5 RAID HDD (9,1GB each).
WWTiger>I had an old version of redhat (without graphical interface) and was working fine
dcstar>I will  try to pass "linux noapic" at the boot promt and see what happens

I will tell you later this day if I had any luck.

---

### Post by nocturn on 2006-01-12
[QUOTE=stefanv]Hello,

This is my first post and I want to excuse myself for my poor english... I hope you will understand what I'm will say :).
My problem is that I want to install Ubuntu on an old Compaq Proliant 2500 (this is what my boss wants) and the computer halts at the message "input: AT Translated Set 2 keyboard on isa0060/serio0". I'm not a Linux expert but I've asked many people and nobody could help me. I've tried to give some parameters before the installation starts, but... the system halts in the same place :(. Can someone tell me what to do?[/QUOTE]

Is your keyboard plugged in directly or via a KVM switch? 

In any case, as far as I can google for the error, it shouldn't halt the machine.

Can you try booting the system with the options noapic apm=off?

---

### Post by stefanv on 2006-01-12
[QUOTE=nocturn]Is your keyboard plugged in directly or via a KVM switch? 

In any case, as far as I can google for the error, it shouldn't halt the machine.

Can you try booting the system with the options noapic apm=off?[/QUOTE]

The keyboard is plugged directly. I will try with "noapic apm=off" and I will tell you the result later. Thanks.

---

### Post by stefanv on 2006-01-12
I've tried and still dosen't work...

---

### Post by codejunkie on 2006-01-12
try ```
linux acpi=off
```

---

### Post by tseliot on 2006-01-12
[QUOTE=stefanv]I've tried and still dosen't work...[/QUOTE]
I know that perhaps it might seem superfluous but can you access your BIOS and set the USB Legacy to OFF?

If it's on it can cause several problems sometimes.

---

### Post by dcstar on 2006-01-12
[QUOTE=stefanv]Thanks for your answers! 
deNoobius>My system has 2 processors running at 200 MHz each, 512RAM and 5 RAID HDD (9,1GB each).
.......[/QUOTE]
You may want to disable one of the processors in the BIOS to try and get it up and running.

---

### Post by waydaws on 2006-01-12
[QUOTE=stefanv]Hello,

This is my first post and I want to excuse myself for my poor english... I hope you will understand what I'm will say :).
My problem is that I want to install Ubuntu on an old Compaq Proliant 2500 (this is what my boss wants) and the computer halts at the message "input: AT Translated Set 2 keyboard on isa0060/serio0". I'm not a Linux expert but I've asked many people and nobody could help me. I've tried to give some parameters before the installation starts, but... the system halts in the same place :(. Can someone tell me what to do?[/QUOTE]

Hi stefanv, 

Can you try it with a ps/2 mouse, instead of the serial mouse? It's just a guess, but it might be as simple as that.  

Wayne

P.S. If you aren't using a serial mouse or keyboard at all, then make sure the PS/2 mouse and keyboard are plugged into the correct ports.  If I remember right Compaq/HP color codes them on newer models because people always used to always get them backwards.

---

### Post by stefanv on 2006-01-12
I've tried everything and still doesn't want to start. I use a ps/2 mouse and keybord but tomorrow i'll put a serial mouse (if I can find one).

---

### Post by Cool J on 2006-01-12
Same here.

Config: Compaq Proliant 2500
single 200MHz proc
256Mb ram
Compaq smart array 2/p (SCSI)
2x 4.3G SCSI-UW as 1 logical drive (currently W2K pro sever installed)
HP Dat24 (SCSI) 
CDRom on IDE
PS/2 keyb & mouse (through ADDERVIEW KVM Switch)
Bios E24 (9/25/1997)

used all suggested combinations of options. NOK
Boots and stops at same messy STEFANV encounters. BUT... a bit up the screen it says:
EISA: Mainboard CPQ0551 detected
cannot allocate resource for EISA Slot 6   (where the dat scsi controller sits)
cannot allocate resource for EISA Slot 7   (which is not to be found on the outside, but I guess the array controller might be there)
EISA: Detected 0 cards

suggestions anyone?

btw: machine is not fitted with (visible) USB ports. dunno if there is any usb controller on the mobo. guess not.
if you swap keyb and mouse plugs it gives you an "FF - Keyboard error"

---

### Post by stefanv on 2006-01-14
[COLOR=red]IT'S WORKING!!![/COLOR]
 
I've erased the server configuration, reconfigured the disk array and deactivate the SCSI controller and the installer has started after I typed "linux memmap=496M@16M" (this 'cose I have 512 RAM but the bios only raport 16MB) at the boot promt :). I tought that if I'll deactivate the SCSI controler, the disks won't work anymore but they do. Now Ubuntu is installing :). Thanks!

---

### Post by Cool J on 2006-01-15
Have downloaded Compaq Smartstart CD 5.50.
Erased system, rebuilt config. Cannot disable SCSI controler that is onboard, disabled the other one (Where the dat unit is on) Rebuilt the array config. One large logical drive (2x4.3Gb)

rebooted to ubuntu boot prompt.
linux memmap=240M@16M   (bcos 240+16=256)

Rolling on...now at the point where the network is configured..still busy

---

### Post by Cool J on 2006-01-15
After the reboot it panics, cannot find hardisk??

btw can anyone point me to the page where the memmap option is explained?

sorry, should have edited my last post

---

### Post by stefanv on 2006-01-15
[QUOTE=Cool J]After the reboot it panics, cannot find hardisk??

btw can anyone point me to the page where the memmap option is explained?

sorry, should have edited my last post[/QUOTE]

I have the same problem after installing.. Ubuntu can't see my partitions and is dropping me to a shell :(. Anybody can help us?
The page with the memmap parameter is at: [http://www.cpqlinux.com/memory.html#METHOD4](http://www.cpqlinux.com/memory.html#METHOD4)

---

### Post by ztirffritz on 2006-01-16
[QUOTE=codejunkie]try ```
linux acpi=off
```[/QUOTE]

Where/How would I use this?  I'm trying to install the AMD64 version of Ubuntu and it is hanging on the part about the keyboard.

---

### Post by mowney on 2006-08-05
Stefanv,

I have a Compaq Proliant 2500, single 200MHz proc,256Mb ram, Compaq smart array 2/p (SCSI), CDRom on IDE, PS/2 keyb & mouse.

I am having the same problem installing Ubuntu 5.10 as you have, and the computer halts at the message "input: AT Translated Set 2 keyboard on isa0060/serio0".

Can you give me info on exactly how you got your's working? I have your final thread where you said - *"I've erased the server configuration, reconfigured the disk array and deactivate the SCSI controller and the installer has started after I typed "linux memmap=496M@16M" (this 'cose I have 512 RAM but the bios only raport 16MB) at the boot promt . I tought that if I'll deactivate the SCSI controler, the disks won't work anymore but they do. Now Ubuntu is installing"*

Can you give me more information on how? Exactly how did you erase the server configuration, and how did you reconfigure the disk array and deactivate the SCSI controller?

Has it been working well since?:mrgreen:

---

### Post by stefanv on 2006-08-07
Hello,

In order to reset your BIOS, you need the CD-ROM that you got when you bought your Proliant. Boot from that CD and you'll get a step-by-step guide on how to reconfigure your BIOS.
You can't use linux "memmap=496M@16M" as I did to start the setup 'cose you only have 256 RAM. You cold try to use "linux memmap=240M@16M". You can try this even if you didn't reset/reconfigure your BIOS and see if it works.
Sice I've installed Ubuntu on that server, everything is working fine :) 

Good luck!

---

