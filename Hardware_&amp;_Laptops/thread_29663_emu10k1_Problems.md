---
title: "emu10k1 Problems"
date: 2005-04-25
forum: Hardware &amp; Laptops
---

### Post by ?rious on 2005-04-25
I have a Creative SB Live (not Value...I think) which is working, but not through gstreamer. Could someone give me a hand configuring ALSA & gstreamer, cos I'm confused and the guides on the ALSA website haven't helped me too much.

When I use the Live CD, sound works fine. When I use the open source ati drivers for my sound card, the sound works fine. The moment I get fglrx working, there's some sort of hardware conflict, but not at hardware level! I have got the card working just fine through XMMS using the ALSA plugin and manually selecting the card (hw2,0 if that's any help), but I have no idea how to make those alterations to gstreamer. I've got ALSA selected in the gstreamer menu, and ESD is set to use the OSS plugin anyway (AFAIK it's not in the running processes, killall esd just tells me there's nothing to kill), which should mean it leaves ALSA to the card, but I get the "Failed to construct test pipeline" whenever I try to test alsasink.

I haven't tried to get OSS compatibility working, to try something like frozen-bubble, but I bet it will work. I'd be happy enough if someone could just direct me to the right page or even tell me how to fix my problem. I'd be very grateful!

Oh, any does anyone know if the SB Live has hardware mixing built in? I'd love to know if I can avoid having to use ESD.

*EDIT* I just swapped /dev/dsp with /dev/dsp2 so that the default choice is now my SB Live. I don't know if that'll work for anyone else, nor do I know if it's a good idea, but it's worked for me so far.

---

### Post by jzietman on 2005-04-26
i've a similar problem.  i have an sb live! 5.1 card, and have so far only tested in the final release candidate a64 livecd, but i get no sound whatsoever, even when it says it's playing a cd.  i will be installing the i386 version (not enough working, non-beta plugins like flash etc. for a64 yet) and really want to be able to hear stuff.  is this a problem between hoary and sb live cards in general, and how would i go about fixing it?

---

### Post by jzietman on 2005-04-27
bump^^

---

### Post by jzietman on 2005-04-28
does no one know?

---

### Post by Yeeha on 2005-04-29
[QUOTE=jzietman]i've a similar problem.  i have an sb live! 5.1 card, and have so far only tested in the final release candidate a64 livecd, but i get no sound whatsoever, even when it says it's playing a cd.  i will be installing the i386 version (not enough working, non-beta plugins like flash etc. for a64 yet) and really want to be able to hear stuff.  is this a problem between hoary and sb live cards in general, and how would i go about fixing it?[/QUOTE]

it plays but you cant hear it? I had similar problem with audigy 2 because analog input/output from alsamixer wasnt enabled.

EDIT: ups it was Audigy Analog/Digital Output Jack what was not enabled by default so it wont help you i guess.

---

### Post by graigsmith on 2005-04-30
have you tried moving the SB live to a different PCI slot?

my friends computer wouldn't boot the live cd until i moved the soundblaster to a different slot.

sb live DOES have hardware mixing, except sound blaster live 24 bit, its a "WinBlaster"  and uses software mixing.

---

