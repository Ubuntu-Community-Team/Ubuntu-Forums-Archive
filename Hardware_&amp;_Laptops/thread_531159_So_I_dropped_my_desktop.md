---
title: "So I dropped my desktop"
date: 2007-08-21
forum: Hardware &amp; Laptops
---

### Post by monsieurdozier on 2007-08-21
Moving into my dorm, I dropped my Ubuntu Desktop face first on the ground.  No big deal, these things are sturdy right?  Apparently not.

I hook it up, press the power button, I hear the whirs of fans and nothing comes on the screen.  I try to power it off, power button and reset button are not responding.  I crash it.  Replace the video card, same thing.  Replace it again with another video card.  Same thing.  This time the processor fan doesn't work, but my case fan does.  Turn it off leave it alone overnight.  Turn it on, both fans are working, I can hear the hard drive kicking in, still no video.  Change around video cards again, still nothing.  I've replaced the BIOS, thinking maybe somethings wrong with it and it's not directing right.  Same thing.  Replaced the processor thinking that might do it.  Nothing.

I don't care if you lie to me, but please tell me it's not my motherboard, the one thing I don't have spares of.  (Don't lie.  Tell me the truth.)

Monsieur Dozier

---

### Post by tgm4883 on 2007-08-21
Well i'd strip it down to the bare minimum.  Motherboard, Ram, CPU, Videocard (if you don't have onboard video).  If that fails to work, reseat all those components (or better yet, switch them out with known working parts except the motherboard)  If it still doesn't work, then it sounds like the motherboard.  If this is the case, you could either get a new one or try to repair it.

You might also just try reseating the motherboard.

---

### Post by RudolfMDLT on 2007-08-21
Hi there,

It would be great if you have a spare machine! :) even an old one or a room mate's one.

First start with the power - unplug everything from your power supply and then plug in the donor computer's PSU. If you are lucky the cables should just reach without having to unscrew the PSU from the donor box. The fact that one fan turned, and then only after some time the other may be a bad sign for the PSU.

If you still don't get anything, see if you can plug your CPU into another box? I wouldn't go plugging in other CPU's into your board at the moment - if something got broken there it could blow CPU after CPU.

Now try swapping RAM.

Hard drives very rarely will keep a PC from even doing a POST()Power On Self Test).
Plug out the drives, all of them and switch the machine on.

When you switch on your box, do you hear any beeps at all after changing something? No beeps means your PC is a vegetable and that either the CPU or Board and/or sometimes RAM has gone.

If nothing you put into your machine helps, start putting your parts into another machine and see if the parts still work.

Post back with results! :)

Rudolf

---

### Post by monsieurdozier on 2007-08-21
I stripped it to the bare minimum, CPU, one RAM stick, motherboard, video card.  Same thing.

I pulled the RAM out to see if I can get the beep code for no memory, Nope.

I took and old machine and hooked up my Power Supply just to the mother board, and I got the same problems.  Even no beep codes.  

So, my power supply might be shot?

---

### Post by RudolfMDLT on 2007-08-21
That's what I was thinking. See if you can replace it and post back. Goodluck!

---

### Post by monsieurdozier on 2007-08-21
I went out and bought a working power supply, hooked it up.  RAM, Processor, Memory, Video Card.  Same thing still.  Pulled the Memory.  No beep codes.  Nothing new.

Monsieur Dozier

---

### Post by RudolfMDLT on 2007-08-21
Have you gone through the swapping out ritual again?

inspect your motherboard for any pins that might have broken off at the power sockets - though I doubt it.

Here's what might have happened.

You dropped the machine, broke the PSU(Power Supply).
You tried to switch it on and the Broken PSU blew up something, either board, processor or both or your chip got fried because it ran with out a fan.

Plug out EVERYTHING. Only Board and PSU. put on the machine and see what happens, then add the CPU, do it again, then add the RAM and then put back your Graphics card, then Harddrives, then CD-ROM drives, then other add-on card like network cards ect. I'm thinking that something might have blown either on the board or (hopefully) on an expansion card and this is keeping your mother board from working. Some boards, well almost all modern boards have protective circuits in that when something blows or shorts, the board should isolate that part of the board to keep the entire system from going up in smoke.

Basically, the best way to do this is through a process of Elimination.

You machine can work with only CPU, board and RAM, so lets test those three first. then add back everything part by part. Though the board should not blow a processor, don't plug any spare CPU's into it. rather see whether you can't plug your processor into a friends box?

Plug the new PSU into the old machine and see whether the old machine works,

Goodluck!

---

### Post by monsieurdozier on 2007-08-22
Well, I start with it's working, for now.

I called my dad to get his advice on this as well, he mentioned the power buttons up front, maybe I damaged one of them.  With that in mind I completely transferred everything to a new case.  I plugged in the new power supply and the motherboard w/ processor.  I got a beep code.  No annoying sound has ever been so beautiful.  I plugged in my old video card.  Nothing.  I believe it is shot.  I plug in a new video card, beep code.  I know it's working.  I plug in memory and cross my fingers.  I got the boot screen.  From there it was just plug and play.  So she's working well.  All in all I think it was the video card that did her in.

With that in mind, I come to my last question.  Unfortunately the new video card I have is a Nvdia GeForce 2, and I don't have the drivers installed with it.  My GUI doesn't work, but I can get to a command prompt/terminal (Which is it called in Linux?).  From there can I upload the drivers I need with a working internet connection?

That's my final question.  Thanks everyone for all your help.

Monsieur Dozier

---

### Post by RudolfMDLT on 2007-08-22
Hi - sorry, I live in South Africa! :) Only back online now! :)

in the tty prompt,

**sudo dpkg-reconfigure -phigh xserver-xorg**

and select nv or nvidia, can't remember which(If you had a Nvidia card before then Nvidia should be there, other wise select NV).

Now reboot.

This will get you in into Ubuntu from where you can use the restricted driver wizzard to install the drivers.

OR

[B]sudo apt-get install nvidia-glx
[/B]

The above is to manually install the drivers. After the install do a:
**sudo dpkg-reconfigure -phigh xserver-xorg**

and select Nvidia.

You should be fine to reboot now.

Remember that Xorg will run the highest resolution that you select so only select what you need/want.


Cheers,

Rudolf

---

### Post by monsieurdozier on 2007-08-22
It's up and running just fine.  Thanks for your help.

Monsieur Dozier

---

