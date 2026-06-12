---
title: "No sound since I upgraded to 9.04"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by PaulHuffman on 2009-09-08
I have a Gateway e series with Audigy 2 audio card.  I liked my upgrade from 8.04 to 9.04 32 bit. The upgrade went smoothly, and I didn't have any of the display problems I had with 8.04.  But I haven't heard a peek out of my speakers with 9.04. I went through most of [Comprehensive Sound Problem Solutions Guide v0.5e]("http://ubuntuforums.org/showthread.php?t=205449") but didn't find the problem.  If I boot from an 8.04 CD, the speakers come roaring back to life. Is there any other threads I should be looking at? The Comprehensive Sound Problem Solutions step 3 currently points to a directory listing, rather than a listing of sound card drivers by manufacturers.  I'm getting a failure at step 4, no sound after loading my driver emu10k1 for the current session.
Tried Getting the ALSA drivers from a *fresh* kernel step, and rebooted, but still no sound.



lspci gives me:
03:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs Device 2004
        Flags: bus master, medium devsel, latency 32, IRQ 19
        I/O ports at bc00 [size=64]
        Capabilities: [dc] Power Management version 2
        Kernel driver in use: EMU10K1_Audigy
        Kernel modules: snd-emu10k1

---

### Post by ken_doh on 2009-09-08
I got my sound back after upgrading by:

Applications/Sound & Video/Sound Recorder

File/Open Volume Control

Switches Tab/Tick Audigy/Digital Output Jack

Then adjust the volume on the 'Playback Tab'.

I hope this helps.

---

### Post by PaulHuffman on 2009-09-08
What I find under Applications/Sound & Video/Sound Recorder is PulseAudio Volume Control, then I don't find Switches, so I've jumped your track.  Pulse Audio Volume Control shows sound bouncing the playback stream of a audio CD I put in for testing, but the speakers are silent.

Wait - I went back into the ALSA Mixer, and started pushing buttons rather randomly. I found that the Audigy Analog/Digital Output Jack box needed to be checked.

---

### Post by PaulHuffman on 2010-03-24
I was testing 9.10 and 10.04 on this same PC, booting from the install CDs and can't get any sound from these versions.  I didn't find an app version of Alsa Mixer, but got the alsamixer to run in a terminal window. Turned everything up, but still no sound. [edit] Fixed with the terminal window alsamixer. Found out how to toggle the singe boxes with m, and turned on one far to the right that said "Audigy A". Still haven't figured out the network problem below.  


I couldn't seem to make a network connection outside my Class C block either, but thats a topic for another thread category.  We use fixed IP addresses at this office, and I went in and edited the ip address and subnet mask (255.255.255.0) for auto eth0 as I had done before. The new versions would then connect to the LAN but couldn't ping anything past our building to another IP block and the Internet.

---

### Post by PaulHuffman on 2011-12-09
Now I had to do a complete install of 11.04 from CD.  Trying to figure out this Unity Desktop, but now no sound at all from the speakers.

---

### Post by oldos2er on 2011-12-10
Closed. Please start a new thread in Multimedia & Video for your sound problem.

---

