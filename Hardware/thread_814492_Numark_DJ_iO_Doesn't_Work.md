---
title: "Numark DJ iO Doesn't Work"
date: 2008-05-31
forum: Hardware
---

### Post by interim descriptor on 2008-05-31
Does anybody know how to make the Numark DJ iO USB Soundcard work on Ubuntu?

When I plug it in, /var/log/messages says:

[INDENT]
May 31 16:11:16 id kernel: [73470.143614] usb 5-2: new high speed USB device using ehci_hcd and address 3
May 31 16:11:16 id kernel: [73468.382261] usb 5-2: configuration #1 chosen from 1 choice
[/INDENT]



It comes with a special driver CD, and Numark tech support says they don't support linux.

Does anybody have a recommendation for an external USB 4-channel soundcard? I previously had two Creative Labs Audigy 2 NX cards, but both died on me, and I don't want to buy another Creative card, because they were idiots when that dude improved the Vista driver, and had their lawyers attack him.

---

### Post by jrusso2 on 2008-05-31
If there is no drivers for it I don't know how it would work on Linux.

Why do you need external usb sound?  Is it a laptop or something that you can't put a card in for sound?

---

### Post by interim descriptor on 2008-05-31
> **jrusso2 said:**
> If there is no drivers for it I don't know how it would work on Linux.

I was hoping it would show up as a standard USB soundcard, like my Audigy did, and like any soundcard arguably should.

[Edit: This is what I'm referring to: [http://www.usb.org/developers/devclass_docs]("http://www.usb.org/developers/devclass_docs")]



> **jrusso2 said:**
> Why do you need external usb sound?  Is it a laptop or something that you can't put a card in for sound?

I've got a laptop on which I develop and use DJ software. The software requires a pair of stereo outputs: One for headphone output, one for speaker output. My internal soundcard only has one stereo output.

---

### Post by interim descriptor on 2008-06-01
Actually, while I'm at it, my M-Audio Xponent only shows up as a 2-channel soundcard, when it's supposed to support 4 channels.

It works great as a MIDI controller, though.

---

