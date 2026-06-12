---
title: "Audigy 2 - The Sound of Silence"
date: 2005-03-08
forum: Hardware &amp; Laptops
---

### Post by devpotato on 2005-03-08
Greetings all - 

I recently installed Hoary (Array 6) on my primary desktop machine with has an  Audigy 2 installed. I have not been able to get any sound either from Gnome or other apps, like XMMS.

Here's a list of the things I've tried, in rough chronological order:

1) Installed alsa-utils and frobbed about with mixer settings and insured no outputs were muted - No sound

2) Tried "pointing" XMMS at the different mixers (first alsa, then oss) - No sound. It is interesting to note that XMMS appears to be playing happily (no error messages of any kind) - just no sound is produced.

3) Lastly - hand built a kernel (2.6.10) with emu10k1 driver "baked in" the kernel and all oss stuff (even the alsa emulation layer) turned off - No sound

After some help from geppy and tizen on #ubuntu, we discovered that I am lacking  /dev/dsp* and/or /dev/audio* entries. This is quite curious. . . 

Here is the Audigy section of lspci output:

0000:01:09.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
0000:01:09.1 Input device controller: Creative Labs SB Audigy MIDI/Game port (rev 04)
0000:01:09.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)

The motherboard does have some sort of Realtek integrated audio chip, but that has been disabled (and verified) in BIOS. Neither lspci nor dmesg report any sign of it.

As I write this, I'm building another kernel with the alsa oss emulation layer re-enabled and the emu10k1 driver built as a module. _All_ other sound card modules, ISA, PCI, and USB are disabled.

I _really_ like Ubuntu and would love to get sound working so I can get back to using my computer for more interesting things :-)

Any help or suggestions is gratefully accepted. . .

---

### Post by devpotato on 2005-03-09
Ooook. Call me impatient. I rebuilt a new kernel with alsa and alsa's oss emulation layer enabled. _Still_ no sound.

At this point I tried paving the box and reinstalled Hoary from scratch. Checked /dev, and yup, no audio* or dsp* entries. I cannot explain this problem. emu10k1 is loaded (via lsmod). dmesg shows no errors on boot nor does perusing various logs in /var.

Just to prove I'm not losing it, I booted into XP and verified that the sound card is still working.

I'm at work now, but I left a Warty install running when I left this morning. Guess I'll try this again when Hoary is finalized, although this doesn't fill me with much hope :-(

---

### Post by Plex on 2005-03-09
I fixed partialy my problem with my audigy2 not giving sound with the instalation of gnome-alsamixer and then checked the option "Audigy Analog/Digital Output Jack".
but the problem is, everytime I reboot the sound goes away, and I need to tick that option again to have sound back.
 :confused:  :confused:

---

### Post by RoccoD on 2005-03-16
Plex,

Try to store the alsa settings by doing a:
sudo alsactl store

This stores the alsa mixer settings.

Greetz,

RoccoD

---

### Post by trigg on 2005-03-17
[QUOTE=devpotato]Ooook. Call me impatient. I rebuilt a new kernel with alsa and alsa's oss emulation layer enabled. _Still_ no sound.

At this point I tried paving the box and reinstalled Hoary from scratch. Checked /dev, and yup, no audio* or dsp* entries. I cannot explain this problem. emu10k1 is loaded (via lsmod). dmesg shows no errors on boot nor does perusing various logs in /var.

Just to prove I'm not losing it, I booted into XP and verified that the sound card is still working.

I'm at work now, but I left a Warty install running when I left this morning. Guess I'll try this again when Hoary is finalized, although this doesn't fill me with much hope :-([/QUOTE]
 One problem with the kernel is that alsa is not the latest and greatest.  Try recompiling with sound support as a module, but NO soundcard modules compiled (or selected in any way shape or form), then install the alsa-base package, or compile the alsa-drivers from scratch (very easy to do - just check out the alsa website).  That should give you the most recent support for the Audigy 2 (whether it be the original, ZS, or value editions . . .)

trigg

---

### Post by genti on 2005-03-20
something strange over here. my audigy 2 works but only from the front panel. I have tried everything but nothing happened. And it picked up my onboard sound card that i had disabled. Is warty better?

---

### Post by trigg on 2005-03-21
[QUOTE=genti]something strange over here. my audigy 2 works but only from the front panel. I have tried everything but nothing happened. And it picked up my onboard sound card that i had disabled. Is warty better?[/QUOTE]

Which program are you using to unmute the channels?  Alsa mixer is great, but you have to remember to scroll all the way over to the right to get all the channels.  Not sure what to do about your onboard sound - you can check the etc/modules file and delete any references to your onboard sound - also go to your /etc/modprobe.d/alsa-base file and comment out any refs to your onboard sound.

trigg

---

### Post by genti on 2005-03-21
thanks trigg,
I had tried almost everything. I installed KDE and it came with kmix, with all the channels already active. After clicking over  everything finally the sound came out. With gnome probably i had forgotten the analog/digital jack.
and ubuntu(the community as well) is cool

---

### Post by c_dog on 2005-03-22
I think that main problem here is with the little quirk that the gnome-alsamixer doesn't seem to have the digital/analog switch button setting in it's panel. I went around with this one the first time that I installed Ubuntu. It wasn't until I tried the CLI alsamixer (Remembering the same problem occurs in SuSE)  and used the 'm' key to unmute the muted channels. At least the CLI alsamixer has the analog/digital switch to get the Audigy2  thumping again.

---

### Post by trigg on 2005-03-23
[QUOTE=genti]thanks trigg,
I had tried almost everything. I installed KDE and it came with kmix, with all the channels already active. After clicking over  everything finally the sound came out. With gnome probably i had forgotten the analog/digital jack.
and ubuntu(the community as well) is cool[/QUOTE]

Glad that you got it working! 

trigg

---

### Post by trigg on 2005-03-23
[QUOTE=c_dog]I think that main problem here is with the little quirk that the gnome-alsamixer doesn't seem to have the digital/analog switch button setting in it's panel. I went around with this one the first time that I installed Ubuntu. It wasn't until I tried the CLI alsamixer (Remembering the same problem occurs in SuSE)  and used the 'm' key to unmute the muted channels. At least the CLI alsamixer has the analog/digital switch to get the Audigy2  thumping again.[/QUOTE]


The console can always be your friend.  ;)

**EDIT:** (and I have a degree in English Lit!)

---

### Post by keuleJ on 2005-03-30
Thanks guys, you're great! I'm finally listening to Isaac Hayes!

---

