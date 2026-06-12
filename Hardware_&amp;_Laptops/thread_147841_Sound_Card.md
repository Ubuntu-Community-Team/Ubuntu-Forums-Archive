---
title: "Sound Card"
date: 2006-03-20
forum: Hardware &amp; Laptops
---

### Post by kruser619 on 2006-03-20
I am running Ubuntu on this computer but it wont detect the sound card:

333mhz AMD 32bit
128MB RAM
**Crystal 3D Sound Card (Cant find Model Name)**


Anyone know of places i can download drivers for Linux?

---

### Post by kruser619 on 2006-03-21
:( Guess not....

Back to DamnSmallLinux.... stupid Mounting.....

---

### Post by colo on 2006-03-21
Paste the output of ```
lspci
```, and someone may be able to help (in case the soundcard is actually PCI-based).

---

### Post by kruser619 on 2006-03-21
Hmm.. just enter that into the terminal?? Im not much for CLI. So just open the terminal and enter it? And Post the results?

---

### Post by kruser619 on 2006-03-21
I dont see anything about a sound card in this.. if someone wants to dechipher it, they're welcome to.




0000:00:00.0 Host bridge: VIA Technologies, Inc. VT82C598 [Apollo MVP3] (rev 04)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT82C598/694x [Apollo MVP3/Pro13 3x AGP]
0000:00:07.0 ISA bridge: VIA Technologies, Inc. VT82C596 ISA [Mobile South] (rev  06)
0000:00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT82 3x/A/C PIPC Bus Master IDE (rev 06)
0000:00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Contr oller (rev 02)
0000:00:07.3 Bridge: VIA Technologies, Inc. VT82C596 Power Management
0000:00:13.0 Communication controller: Conexant HSF 56k Data/Fax Modem (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (re v 7a)

---

### Post by kruser619 on 2006-03-21
Hehe.. can someone make out this code? I sure can't..

I would love any help on the sound card.

---

### Post by taurus on 2006-03-21
It doesn't say anything about your soundcard!!!  I assume you have it turn on in BIOS!

---

### Post by kruser619 on 2006-03-21
Ok.. i might as well try that.... although ive gone through XP, 95, 98, DSL without doing it. Hopefully it'l work.

---

### Post by colo on 2006-03-22
Your soundcard is most probably incorporated into your system via the ISA-Bus. You should get a more recent replacement for PCI, a SoundBlaster Live! or PCI128, for example. Starting around 2US$/Euro at eBay.

---

### Post by kruser619 on 2006-03-23
Well, i downloaded and booted Damn Small Linux, and it plays sound just fine.... So there must be some way to make it work on Ubuntu...

---

