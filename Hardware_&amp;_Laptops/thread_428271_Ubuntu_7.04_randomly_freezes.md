---
title: "Ubuntu 7.04 randomly freezes"
date: 2007-04-30
forum: Hardware &amp; Laptops
---

### Post by Hohoman on 2007-04-30
Hi!

This forum has helped me a lot with different issues in the past months, since I decided to try Ubuntu.

I started with 6.10 on my ASUS laptop where I had to configure the network manually in /etc/network/interfaces to get the WPA2 security up and running. With the new 7.04 everything regarding the network worked "out of the box".

Now to the issue. My computer freezes, from what I can tell, randomly. It happens when I use firefox, it happens when I read pdf-files and with other software.

The mouse is still movable, and it stores the clicks in the buffer. Same thing with the keyboard. After a minute or two everything starts to work again. (While I was editing this text, the computer halted on me again.)

Where do I start to look? I'm a linux newbie, so be gentle with me ;)

---

### Post by gewitty on 2007-04-30
Can't offer you any explanation, but my system does the same thing since upgrading from Edgy to Feisty. The only difference is that mine freezes completely and needs a hard reboot to get going again. I've tried to link the failures to specific apps or events, but as you say, it seems to be completely random.

---

### Post by ajgreeny on 2007-04-30
What are you system specs, particularly your grtaphic cards?  These freezes are often associated with graphic driver issues, or perhaps an incompatibility between your graphic card and beryl/compiz, if you have them installed and in use.  Don't forget these are still in development and can cause all sorts of problems with certain hardware.

---

### Post by Hohoman on 2007-04-30
Thanks for the quick response!

My laptops specs:

ASUS A6JC Q003H - Core Duo T2300 1.66 GHz
NVIDIA GeForce Go 7300
Intel PRO/Wireless 3945ABG

I installed the nvidia drivers that came with automatix, because the handler for proprietary drivers would'nt install them (I checked the box, but it would'nt install it, no error message given).

I don't use beryl or compiz.

---

### Post by gewitty on 2007-04-30
The system that I'm having problems with has an AMD Athlon XP 1.6Ghz processor, with 1Gb memory and an ATI RagePro 9800 graphics board.

The freezing problem has only happened since upgrading from Edgy to Feisty.

I have also got problems with my Epson 1670 scanner, which worked perfectly with Xsane under Edgy, but is now out of action and throwing up errors when I try to use it (Failed to open device 'snapscan@libusb:004:004': Error during device I/O).

I'm beginning to regret upgrading. Maybe I should have waited for a few weeks until the bugs are resolved.

---

### Post by Bealer on 2007-04-30
I get the same problem.. There is a long running thread here:
[http://ubuntuforums.org/showthread.php?t=412125](http://ubuntuforums.org/showthread.php?t=412125)

I'm running a fresh install of Feisty:
Core 2 Duo E6300
Gigabyte DS3
ATI X1900GT

I can only work out that's it's (or seems to be) graphically related. If I use the "vesa" drivers (can only get a maximum of 1024x768 :() it runs fine, not a single problem. It's upon installing fglrx that it randomly freezes. 

It can freeze anytime within the first minute or two, or last up to an hour or more. It always freezes if it goes into screensaver/power saving mode.

Very frustrating, and something that is putting me off Ubuntu. I would switch back to Edgy, but would rather use something newer. Might try Fedora or SUSE.

---

### Post by Hohoman on 2007-04-30
Thanks Bealer!

Can a moderator please lock this thread? Sorry that I did'nt find the other thread before I started this one.

---

### Post by Rotarychainsaw on 2007-04-30
Sounds like the ATA thing. Does leaving a CD in the cd drive fix it?

---

### Post by Bealer on 2007-04-30
Nope not for me. I've tried various fixes, none have worked:

- No cd in the drive
- the noapic addition to the grub boot option of Ubuntu
- the pci busses (yes double s) addition the the grub entry
- turning off all desktop effects etc...

Typical too, I started watching the logs last night so I could so what happened just before a crash....and I couldn't get it to crash! The damn thing must be watching my moves.

Also one thing I have noticed. My ATI card gets very hot when using fglrx. I'm sure (although can't remember) it wasn't that hot when using Vista (my case is well modded/ventilated). Could this be driver related? Maybe if I try Edgy I'll see how it differs.

---

### Post by zgornel on 2007-04-30
> **Hohoman said:**
> Hi!

This forum has helped me a lot with different issues in the past months, since I decided to try Ubuntu.

I started with 6.10 on my ASUS laptop where I had to configure the network manually in /etc/network/interfaces to get the WPA2 security up and running. With the new 7.04 everything regarding the network worked "out of the box".

Now to the issue. My computer freezes, from what I can tell, randomly. It happens when I use firefox, it happens when I read pdf-files and with other software.

The mouse is still movable, and it stores the clicks in the buffer. Same thing with the keyboard. After a minute or two everything starts to work again. (While I was editing this text, the computer halted on me again.)

Where do I start to look? I'm a linux newbie, so be gentle with me ;)
Do you have the swap enabled and running ? try givig the 'noacpi' 'nolapic' parameters to the kernel when booting, it might be a kernel issue.

---

### Post by Smarto NL on 2007-09-27
I also had this problem. everytime I reinstall i get it. Then i installed my video driver for 8600 GTS. everything fine. never the problem again. Got the driver off nvidia website. works great.

---

