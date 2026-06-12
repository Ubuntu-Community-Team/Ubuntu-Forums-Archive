---
title: "Weird problems with enm232-8via soundcard"
date: 2010-04-01
forum: Hardware
---

### Post by bilodeau on 2010-04-01
Howdy,

So I just bought an ECS IC780M-A2 motherboard and wanted to upgrade the sound with an add-on card, which I did with an Encore Electronics ENM232-8VIA.  From what I have found, this card requires the snd-ice1724 module.  So far, so good.

But, when I power up the system, the System->Preferences->Sound Preferences window _only_ lists the sound chip built into the mainboard and the sound chip built into the video card for digital out (which I don't use).

If I go to System->Hardware Information, under the PCI devices, the new sound card is listed as:
VIA Technologies, Inc. VT1720/24 [Envy 24PT/HT] PCI Multi-Channel Audio Controller

So, if I try to configure the sound via the Sound Preferences window, the card doesn't show up, but the kernel is aware of it.

I found some other How-To's, and followed the suggestion of using alsamixer.  With:

~$ alsamixer -c 1
wrong -c argument '1'

~$ alsamixer -c 0

The 0 argument gives me the configuration options for the digital out from the video card.  Note that this is when the built-in sound chip is disabled.  If I run the commands when the built-in chip is enabled, alsamixer -c 0 gives me access to the built-in chip, alsamixer -c 1 gives me access to the video card digital audio, and alsamixer -c 2 gives me "wrong -c argument '2'".  So, either with the on-board sound enabled or disabled, alsamixer never 'sees' the new sound card.

Next, I tried this:

~$ lspci -v | grep snd
	Kernel modules: snd-hda-intel
	Kernel modules: snd-ice1724

The snd-hda-intel applies to the video card digital out, and the snd-ice1724 applies to the new sound card.  But, no sound.

How should I proceed?

---

### Post by elnetotaca on 2012-11-30
try with this;
open the terminal and type ''alsamixer''

when the gui opens, move to the right, look for ''AUTO-MUT''.
Change it to "Disable"

and let us know if that works for you.

---

