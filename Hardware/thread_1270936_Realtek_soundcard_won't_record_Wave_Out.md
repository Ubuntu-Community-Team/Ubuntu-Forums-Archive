---
title: "Realtek soundcard won't record Wave Out"
date: 2009-09-20
forum: Hardware
---

### Post by Louigi Verona on 2009-09-20
Hey!
I have an ASUS M51V laptop, running Ubuntu 9.04 and a Realtek ALC663 soundcard.

Sound playback was perfect out of the box. Now I am trying to record things and have run into problems.

**Problem:**
I am trying to record the so-called Wave Out, that is the signal of the soundcard output. That is, record everything that is going on, including live radio streams and such. However, applications like Audacity and terminal recorders like arecord do not capture any sound and record only silence. Tampering with sliders in the Volume Control allows to record from microphone, but not from soundcard.

**Attempted things:**
1. Using alsamixer.
Did not help - the data it output is the same as with Volume Control. It sees my soundcard and does show a Capture:0 slider, but it doesn't seem to do anything. Also, my soundcard surely has line in but it isn't shown.
2. Using alsamixergui.
That at all did not say anything, just said I have a PulseAudio soundcard and has two sliders only - Master and Capture, with Capture being disabled.
3. Installing the realtek-linux-audiopack-5.12
On some forums people suggested to install this package. The drivers compiled okay, however I couldn't do two things which were listen in the installation instruction:
a) run alsaconf - no matter what I tried to install, I only get "unknown command".
b) edit etc/modules.conf - I do not have such a file. I do have a modprobes.d directory, but I do not know what to edit in there. I also have a etc/modules file, but I am not sure it is a correct one.
So if the drivers did install, I couldn't activate them.

I would be very grateful for any help, as at this moment I do not think I am able to do anything further without input from a more experienced user.

---

### Post by Louigi Verona on 2009-09-20
More attempted things
Created modules.conf by myself and pasted the lines which the instructions asked to. Rebooted - no effect.

---

### Post by Louigi Verona on 2009-09-20
Anyone? =)

---

