---
title: "USB card reader causes hang on boot"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by RandomJoe on 2007-01-09
Yesterday I added a USB multi-card reader to my shiny new Core 2 Duo system.  It works great, once I get the system running, but causes the kernel to do one odd thing on bootup.  Thought I would see if anyone might know why.

lsusb shows the product description as 'Atech Flash PRO-Gear X28U' ID 11b0:6208.  Motherboard is an ASUS P5N32-SLI SE Deluxe which uses the nForce 4 chipset.

If I boot with the reader unplugged, the kernel flies right through booting up with almost no hesitation anywhere.  When I plug this reader in, a cold boot halts for a long time and sometimes hangs solid at this point (I have the boot GUI off):
```
...snip...
[17179571.668000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:12.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:14.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:16.0 to 64
[17179571.668000] PCI: Setting latency timer of device 0000:00:17.0 to 64
[17179571.668000] audit: initializing netlink socket (disabled)
[17179571.668000] audit(1168374921.664:1): initialized
[17179571.668000] highmem bounce pool size: 64 pages
[17179571.668000] VFS: Disk quotas dquot_6.5.1
[17179571.668000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.668000] Initializing Cryptographic API
[17179571.668000] io scheduler noop registered
[17179571.668000] io scheduler anticipatory registered
[17179571.668000] io scheduler deadline registered
[17179571.668000] io scheduler cfq registered
```

Sometimes, it will finally continue on after perhaps 30 seconds, otherwise I have to hit the reset button.  If I do that, it will hang here again but only for 10 seconds or so then continue on.

The next line in the log after successfully booting just happens to relate to USB:
```
[17179579.712000] 0000:00:0b.1 EHCI: BIOS handoff failed (BIOS bug ?) 01010001
```
But this line always shows up, it isn't unique to when this device was added.

It isn't a huge deal, and the reader works just fine (for MMC and CF cards anyway) but I thought I would mention it to see if anyone else has seen this.  I haven't found anything similar in my searches yet...

---

### Post by chipsdeluxe on 2007-02-16
I'm having a similar problem. I just got an external USB memory card reader and it prevents my system from starting up. Just like yours it works great once the system is up an running but it halts during boot. One difference is that mine never starts, no matter how long I wait. 

I'd like to see if it's hanging at the same point, but I'm not sure how turn off the graphical startup. Also, what log file did you show in your post?

---

### Post by RandomJoe on 2007-03-03
Sorry, I didn't notice your reply until today.

To shut off the splash screen, in /boot/grub/menu.lst remove 'splash' from the kernel line for the boot option you use.  (They are listed in the order they will appear in Grub when starting.)  If you want to see _everything_ while it's booting, also remove 'quiet'.  

If you want that change to be permanent, a little above the boot entries is a commented section that starts "additional options to use with the default boot option".  Remove those words there, and the next time Ubuntu updates the kernel all boot options will use the new settings.  Otherwise, everything gets put back the way it was.

The file snippet is from /var/log/dmesg.

My system still does this, although oddly it goes in spurts.  It seems I can go a week or so without issue, booting up (with almost exactly a 10 second pause) each time I start.  Then one day I'll fire it up and it hangs, sometimes requiring I hit reset 2-3 times before it'll finally work.  Then go back to starting fine other than the 10 second hang for a while.

---

### Post by aerie on 2007-03-11
Hi, I'm having a similar problem with an internal card reader. I don't know the brand but I've opened it and it has a Genesys GL819 chip. When it was connected to the mainboard I couldn't even start the live cd. Then I realized that the reader was the problem I disconnected it and managed to install edgy 6.10.
Now when booting, sometimes the computer freezes showing the same message as Randomjoe:

[23.784839] io scheduler cfq registered 

but the most of times freezes :

[132.454314] ohci_hcd 0000:00:13.0: new USB bus registered, assigned bus 1

and the card reader power led switches off..

Just now the computer managed to start without any problem.




AMD X2 4200
2GB Kingston 667
MAXTOR SATA 250GB
AsRock AM2-XLI eSATA BIOS 1.2
ATI X550

---

### Post by esodin on 2007-03-21
I to experience similar problems while booting. I have, after trying to add and remove all the various options to the kernel in GRUB (acpi=off, pci=noacpi, acpi=noirq, irqpoll, etc), identified the problem to be in regards to the line "ohci_hcd [number] New USB bus registered, assigned bus number 1"

It was a funny problem, because it only happened some (most) of the time. I run a tipple-boot with Ubuntu 6.10, XP and Vista. Yesterday I established the following: 
- If I selected Ubuntu in GRUB after a reboot where Ubuntu was the last used OS it would hang.
- If I selected Ubuntu in GRUB after a reboot where XP or Vista was the last OS used it would **not **hang.

I am a noob at this, but it would seem to me that loading or unloading Ubuntu leaves some parameter in BIOS set so that it prevents Ubuntu to load. If you have an other OS installed, try what I did and see if it works for you and pls report back.


I have a home built machine with an ASUS A8N32-SLI Deluxe motherboard, AMD Athalon 2X 4400, 4 WD Raptors, 2GB high performance ram, 2x 7800GTX in SLI. The disks are all connected to the Nvidia SATA controller, splitting the disks between that controller and the SI SATA controller causes both Vista and Ubuntu to fail to load. 

The machine also has a USB mem-card reader installed. I'll try to disconnect this when I get home. Thanks for the tip :)

---

### Post by esodin on 2007-03-25
I did some investigating over the weekend on this issue and found the following to hold true for me:
- Any USB device connected to any USB hub other than the MB one, causes Ubuntu not to load if Ubuntu was the last OS to run. If Win XP was the last OS to run all devices in any "extra" USB hubs can stay plugged in, and Ubuntu will load normal.

I tested three different USB hubs:
- The Memory card reader hub, the Logitech G-15 keyboard hub and a Belkin USB 2 hub.

A related issue: When shutting down the system, power is left on on the USB Port - the G-15 keyboard stays lit up and the "Logitech" logo is displayed on the keyboard LCD.

I guess I need to better understand how USB and hubs are manged in Ubuntu. Any tips to were I might start reading?

[COLOR="Navy"]Edit: The problem disapeared once I installed 7.04 Feisty[/COLOR]

---

### Post by aerie on 2007-04-07
Thanks. You may be right. I've seen many posts too  reporting problems installing ubuntu when an usb device like external hard disk is connected. I´ll give Feisty Fawn a try. Anyway I would like to know the reason for Edgy not working with some usb devices.

---

### Post by aerie on 2007-04-13
I've tried Feisty and the problem with the card reader is sorted out. In my case Edgy was slow when recognizing SATA devices too, it spent too much time with each four channels even though only one is used (HDD), but now it goes like a charm.

---

