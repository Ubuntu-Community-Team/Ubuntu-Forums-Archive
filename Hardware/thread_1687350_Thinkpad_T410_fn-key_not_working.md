---
title: "Thinkpad T410 fn-key not working"
date: 2011-02-13
forum: Hardware
---

### Post by schum3,1415 on 2011-02-13
Hi there,

I came to install Ubuntu 10.10 alongside the windows 7 professional OS a few weeks ago and everything worked fine.

My laptop (December 2010):
Lenovo thinkpad T410
intel i7 2,67GHz dual core vPro
Intel HD Graphics
Nvidia Quadro NVS 3100 (using Nvidia Optimus)
4 GB RAM
500 GB harddrive
bootloader: grub

Until yesterday.
I was working with it and finally shut down the laptop and put it back on the desk. 
What was strange was that it actually rebooted after a few minutes automatically (although I performed a shut down and not a restart).
So I shut it down from the login screen. 
But it rebooted again. So I shut it down a third time, this time pulling out the battery after it went off.

When I used it today, I noticed, that the fn-key didn't work.
Another strange thing is that the audio mute button, which has a red light on when enabled doesn't go on (although it's working). 

After performing *xev*, there was no reaction when pressing the *fn*-and *F8*-key.
The fn-key doesn't work in Windows 7 neither.

What is going on here? Did some connecions/cables loosen or did I push, by error, a key combination which changed it (I'm new to Ubuntu and Linux)? 
How can it be that 3 keys on totally different placements don't work (correctly)?

The laptop was just lying on my legs, nothing else. The only thing I did was shortly vacuum cleaning the keyboard, that but that was before yesterday evening.

Thank you very much for your help/opinions/guesses.

P.S.: 
1. is it normal that by holding down the ALT-key a window named "shut down the computer" pops up? I didn't notice this before.
2. at start-up the laptop performs a short test of all key lamps (ThinkLight, audio-mute, microphone-mute, caps-log..) by switching them on and off again. The only lamp not working is the audio-mute lamp.

---

### Post by williamts99 on 2011-02-13
> **schum3,1415 said:**
> 
The fn-key doesn't work in Windows 7 neither.

The only thing I did was shortly vacuum cleaning the keyboard, that but that was before yesterday evening.

P.S.: 
1. is it normal that by holding down the ALT-key a window named "shut down the computer" pops up? I didn't notice this before.
2. at start-up the laptop performs a short test of all key lamps (ThinkLight, audio-mute, microphone-mute, caps-log..) by switching them on and off again. The only lamp not working is the audio-mute lamp.

If the function(fn) keys are not working in either operating system, most likely a hardware failure, you can test with a liveCD, but most likely hardware.

Using a vacuum can create huge amounts of static electricity, static electricity can harm electronics.

That is not normal for holding down the alt-key in ubuntu.

If the computer is doing a self test through the bios(before the OS loads) and the light isn't coming on, then it is a hardware failure, unless they forgot to program that light to come on :)

---

### Post by schum3,1415 on 2011-03-01
Hey williamts99,

just wanted to say thanks.

The issue is solved. Got a new keyboard from Lenovo and everything works fine again.

---

