---
title: "Competitibility with ISA to PCI bridge in Ubuntu"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by jonlau on 2005-09-26
Greeting,

I am running desperate. So desperate that i am booting up with my Window Partition and trying to get help as quickly as i can.

Here is the deal:

Running Ubuntu on a 200 Mhz P1 (piece of junk) with like 100 mb of ram.
I got it running... pretty well, except anything that's on my ISA slots are not detected. I am assuming that it needs drivers for the ISA bridge.

OK, let's talk about the chipset:
Intel 82371AB/EB PCI to ISA bridge (ISA mode).

now, what's on the ISAs:
1) sound card with chipset that runs YAMAHA OPL3-SAx WDM driver
2) SMC EtherEz 8416

Alright. That's wonderful isn't. Absolute "Junk for Joy".

LOL
Thanks everyone

JON
[email]jonlau@gmail.com[/email]

---

### Post by az on 2005-09-26
The 2.6 kernel cannot safely scan non PNP harwareon the isa bus.  You will be able to use the stuff, but you will need to load the modules by hand.  Once you find the right modules, put them in /etc/modules and they will be loaded on boot for you.

Check out this for your sound card:
[https://wiki.ubuntu.com/forum/hardware/OldSoundCard](https://wiki.ubuntu.com/forum/hardware/OldSoundCard)

As for your Network card, look in /lib/modules/whatev... net/ to find something that looks like the name of your card. 

To load the modules

sudo modprobe snd-opl3sa2

If that works,
sudo gedit /etc/modules

---

### Post by AndrewB on 2005-09-26
How would one detect a USB port that is running off the same Intel bridge?
I modprobed my sound, but haven't come up with any USB ideas...

Thanks,
Andrew

---

### Post by jonlau on 2005-09-26
I modprobe both files. Both come out to be good.
As instructed, I put them in /etc/modules

smc-utlra
snd-opl3sa2

now the thing is that even the modules is changed, the Ethernet is still not detected.

JON

---

### Post by jonlau on 2005-09-26
I activated the cards. It now works like a charm

---

### Post by az on 2005-09-26
[QUOTE=jonlau]I activated the cards. It now works like a charm[/QUOTE]
By that, I take it you configured your ethernet card with the networking utility and are a happy camper?

Maybe you can look in bugzilla (bugzilla.ubuntu.com) to see if this problem is being looked into?  If not, file a bug about it.

---

