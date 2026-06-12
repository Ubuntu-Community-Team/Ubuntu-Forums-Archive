---
title: "Too Many Audio Devices"
date: 2007-12-11
forum: Hardware &amp; Laptops
---

### Post by RSVampire on 2007-12-11
alright guys here's what seems like a common but advanced or unanswered problem I have.

I have 3 audio devices to choose from in the volume control/mixer

Audigy 2 Platinum [SB0240P]
VIA 8237
SigmaTel STAC9721,23

alright, my problem WAS that sometimes I booted into Ubuntu Gutsy and I wouldn't have sound. The problem was the VIA 8237 and the Audigy 2 kep changing default positions based on whatever Ubuntu detected first (based on their IRQ settings at startup).

So I ran asoundconf set-default-card Audigy2 to set my default playback device to my Sound Blaster. Now that's all well and good and I can get audio after I've logged into my desktop.

My problem now arises that in certain applications (mainly Wine and Ardour 2) they won't use my "default" soundcard from my asoundconf file they'll just use whatever Ubuntu detected first... my stupid useless VIA device.

So I'm now back to if I want audio working in these few specific programs... I have to reboot Ubuntu until my Audigy card is the first detected device. I don't know what the VIA device is, I'm assuming it's my onboard sound card. But if it is, I have no idea why Ubuntu is even detecting it because I disabled it in my BIOS (and I just double checked all my settings before posting this)


Somebody please help me with this because I KNOW there is a better way to doing this.

---

### Post by Yellow Pasque on 2007-12-11
Do you use the integrated audio?
If not, there should be an option to disable it in the BIOS.

---

### Post by RSVampire on 2007-12-12
looks like you didn't read my post...

I don't use my integrated audio, I have no idea why Ubuntu is even detecting it or giving me options of a second sound card because I disabled the integrated audio in my BIOS (I just triple checked my settings now to be 100% sure)


I also just did a google search to see what the VIA 8237 even is... and it's a SATA chipset controller. So why is it showing up as a sound card? I've read like 2 things about people having sound issues with the VIA 8237 but how can that be if it's a SATA chip?

I also just mounted my SATA drive and clicked properties and it says it's mounted as a SCSI drive... so it sounds like my SATA driver isn't set up or working correctly. Can anybody help me with this?

---

### Post by RSVampire on 2007-12-16
ok I fixed my problem.

I had to disable the driver completely.

I did that by adding the driver to the blacklist file ( /etc/modprobe.d/blacklist)

---

