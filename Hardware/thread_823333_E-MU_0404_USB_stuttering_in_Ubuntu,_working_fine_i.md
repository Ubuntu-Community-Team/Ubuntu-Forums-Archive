---
title: "E-MU 0404 USB stuttering in Ubuntu, working fine in Fedora... why?"
date: 2008-06-09
forum: Hardware
---

### Post by z0idberg on 2008-06-09
I know people have had some varying success with the EMU 0404 USB and that there are instructions for getting the card to work in various places. 

What interests me is, though, is that the card seems to work perfectly "out of the box" for me in Fedora 9 and OpenSUSE 11.0, while in Ubuntu (Hardy) I get a lot of stuttering and in latest Mandriva, Arch Linux no sound at all. 

As far as I understand, according to ALSA's site the module associated with the card is emu-10k1. I tried modprobing the module in Arch and got very distorted playback. However, in Fedora where the card works well, if I write lsmod, the emu-10k1 module is not even there.

So now I'm hoping that some of you can point me in the right direction... basically, what I want to do is find out why the card works in Fedora and OpenSUSE and not in other distros. If you can tell me what commands to run in Fedora to find out what kind of magic is making it all tick, I'd be very grateful!

---

### Post by bofphile on 2008-06-13
Same problem here with my E-MU 0202 USB. The card seems to work fine for 20-30 secs then stops. Like you I tried the live CD of Fedora 9 and the card worked flawlessly.

I can't understand why it doesn't work on Ubuntu, the version of alsa-driver seems to be the same (1.0.16) maybe the pulse audio configuration is different ?

The module for our usb device is not emu10k1 but snd_usb_audio.

---

### Post by klss on 2008-09-05
Hi.

I also got the stuttering, which are actually XRUNS and must have
something to do with the buffering and/or the asynchronous USB mode
of the 0404 USB. 

I am also using the snd_usb_audio. There is no real logic built in to drive the card properly. If you run 44.1 it works ( as long as you have the latest firmware on the EMU, which defaults to 44.1)
So I think we're lucky that it works at all, rather by coincidence.

I looked up the quirks file in the ALSA sources for the usb driver. There you'll find the USB 0404 listed. I am wondering what the emu-10k1 discussion is all about? 

Cheers

---

