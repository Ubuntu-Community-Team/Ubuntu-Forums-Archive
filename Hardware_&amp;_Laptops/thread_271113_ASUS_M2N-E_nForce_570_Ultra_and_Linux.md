---
title: "ASUS M2N-E nForce 570 Ultra and Linux"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by mojoman on 2006-10-04
Hi,

I've just bought a new computer and it worked nicely, except for the sound and it turned out to be a hardware problem which the guy at the store (damn nitwits!) can't fix so he offers me another card, namely an ASUS M2N-E nForce 570 Ultra. Has anyone tried this? The one I had ordered I knew would work but this one I'm not sure about and I don't want to be stuck with a card that gives me grey hair.

I'd really appreciate if anyone with some experience of this card could give me some help on this one.

All the best
/Mojoman

Just an update for anyone who might be interested in this card. It works good for me. Fact is, everything was detected by Dapper and works out-of-the-box.

---

### Post by tszanon on 2006-12-18
> **mojoman said:**
> Just an update for anyone who might be interested in this card. It works good for me. Fact is, everything was detected by Dapper and works out-of-the-box.

Hey...I'm a little late, but...
thanks for your report. I'm planning on buying this mobo and I wanted to know if it worked fine. :)

---

### Post by Norco_39 on 2006-12-23
I have the same motherboard and am getting alot of erros, did you have any at all?  So you used the newest version 6.10?

---

### Post by alfredo.marchini on 2007-11-07
Hi,
I have the same problems.
Someone I resolved, Someelse don't.

The first problem i have is ACPI (and I think the unique problem).
If I turn off it I don't receive any error, but floppy, dvd, and usb ports doesn't work.
If I turn on it I receive error Error block ecc.... on hda (cdrom) and floppy and from usb ports).

All is relative to ACPI, in bios I set S1&S3, this afternoon I'll make new tests.

Another problem is the onboard network card.
I also tried to compile and install the forcedeth 0.60 driver, but when the state is idle, it disconnects.
I have also a Marvell Yukon external network card, but I have the same problems.
So the problem is always in acpi, I think.

I have also a external Promise controller, after many problems with driver and right kernel, 2.6.15-29 32-bit, now it works perfectly.

My bios version is 1001 BETA: The fact that is beta is incredible, someone sell a motherboard with beta BIOS!!!

I see that now there is available the 1002, released on 10/10/2007.
Today I'll upgrade it, BETA for BETA, is equal.

But If I can give an help: don't buy it, don't use it, and don't install linux or any other os on it, I have a friend that tell me there are many problems also with winzoz.

The strange think is that someone (the reseller) tell me that RHEL supports it at all.
I think that isn't the truth, but If I is the truth, It have also to work well with ubuntu.

I don't have choice, I need to make it works well because my customer buy it.
This evening I will post the result of my afternoon work.

Bye
Alfredo

---

### Post by alfredo.marchini on 2007-11-08
Hi all,
after 8 hours of head over the keyboard, 
I'm not be able to make the ubuntu 6.06 working well.
I upgraded the bios to 1002.
I tried the network card (the most important think that don't work well),
and don't work again.
So I tried upgrade to ubuntu 7.10 with 2.6.22-14 (the desperation of a guy that don't resolv problems), now acpi is ok, sound don't work (but it doesn't interest me), and i making tests on it.

---

### Post by linas on 2007-12-13
I just picked up the same board. Running ubuntu gutsy on it, with kernel 2.6.23.9 

-- The default gutsy gibbon kernel (2.6.22.14-generic) hangs on my system, just after it loads the ehci_hcd driver. I did not try magic-sysrq to see why it hangs. Although -- it seems to hang in userspace?? Because plugging usb devices generates output to the console!

Ethernet works fine, with the forcedeth driver; even connects at full speed (1Gb) Yay!

-- I had trouble with usb not working at first; but after compiling the ohci_hcd kernel module, all is well.

-- Sound doesn't work --  the kernel module "intel HD" driver aka "azalea" does load w/o error, but no sound comes out.

Little things that work: cpu temp sensors! Yay!
Fan speed doesn't seem to be reported anywhere except in bios. Boo.
Cpu freq scaling works great! Am using the "ondemand" scalar, with the powernow_k8 kernel module.

---

