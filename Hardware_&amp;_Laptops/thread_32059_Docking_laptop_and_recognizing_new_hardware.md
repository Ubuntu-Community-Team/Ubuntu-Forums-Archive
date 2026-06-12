---
title: "Docking laptop and recognizing new hardware ?"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by elsewhere on 2005-05-05
My docking station at work is connected an external monitor, USB mouse, speakers and ethernet connection.  I sometimes suspend my notebook at home and then just wake it up at work after I've docked it.  Works fine for the most part but I've got a couple of issues.

a) How can I have K/Ubuntu "recognize" the new ethernet port on my docking station that was not there at boot time ?  In FC3, I would just cheat and run Kudzu in a shell window, never got around to a slicker fix.  How can I do something similar in K/Ubuntu ?  I tried modprobing the appropriate driver and aliasing it as "eth1", but I still can't get it to see it.  This is probably noobish of me, but is there any easy way to do this ?

b) The speakers connected to the lineout on my docking station don't work, sound continues to come from the built-in speakers in the laptop.  This was also an issue in FC3 that I never got around to addressing.  In XP, sound automatically channels through the speakers when they're connected.  I always figured it was some kind of mechanical switch that re-routed the sound when speakers were plugged in, but I guess it's controlled by software ?  Any ideas on how to activate them ?

Thanks much for any ideas or advice...

Cheers,
KV

---

### Post by baharlou on 2005-05-23
[QUOTE=elsewhere]My docking station at work is connected an external monitor, USB mouse, speakers and ethernet connection.  I sometimes suspend my notebook at home and then just wake it up at work after I've docked it.  Works fine for the most part but I've got a couple of issues.

a) How can I have K/Ubuntu "recognize" the new ethernet port on my docking station that was not there at boot time ?  In FC3, I would just cheat and run Kudzu in a shell window, never got around to a slicker fix.  How can I do something similar in K/Ubuntu ?  I tried modprobing the appropriate driver and aliasing it as "eth1", but I still can't get it to see it.  This is probably noobish of me, but is there any easy way to do this ?

b) The speakers connected to the lineout on my docking station don't work, sound continues to come from the built-in speakers in the laptop.  This was also an issue in FC3 that I never got around to addressing.  In XP, sound automatically channels through the speakers when they're connected.  I always figured it was some kind of mechanical switch that re-routed the sound when speakers were plugged in, but I guess it's controlled by software ?  Any ideas on how to activate them ?

Thanks much for any ideas or advice...

Cheers,
KV[/QUOTE]
 In a quick me too, I am having similar problems with my Dell 600m

---

### Post by rps63ifid on 2005-07-18
I am seeing similar behavior with the speakers and docking station on my Dell D600. I can get the sound through the laptop's on-board speakers, and through the laptop's headphone port. No sound, however, through the headphone port on the docking station, and when I have the speakers plugged in on the docking station, it turns off the laptop's on-board speakers.

Any ideas?

---

### Post by Breneez on 2005-09-17
I've got the same audio problem on my 600M while it's in the docking station.  No issue with the ethernet or USB though.  Haven't tried the other ports yet, but I'm planning to pick up a Monitor and PS2 KVM soon.  Have you tried/had any problems with these other ports?

---

### Post by baharlou on 2005-09-17
nope, everything else worked great, although you can't always easily dock/undock it w/out turning it off

---

### Post by Breneez on 2005-09-17
I had a problem docking it (not undocking though) in FC4, it would cause the entire system to lock up hard, holding down the power button was the only way to restart it.

I haven't had the same problem with Ubuntu though, only the docking station eject button doesn't really do anything, just blinks for a while and then gives up.  I've just been using the hard release, whether the laptop was ready or not.

---

### Post by salvatore on 2005-10-05
Anyone had any luck resolving this?  My Dell Latitude D600 plays audio perfectly within 5.10 as long as its not in its docking station.  Once I dock it I lose all audio; nothing comes from the onboard speakers or the external speakers.
Thanks.

---

### Post by BeefGeek on 2005-10-29
I have a Dell D600 too, and experience the same issues with my docking station.  With the sound I've just acquiesced and plug my speakers into the headphone port on the laptop itself (it's just 6 inches away from the docking station headphone port) and get my sound fine.

Docking the laptop will shut down your PC speakers, I think that'll even happen in Windows XP too.  Will have to check that.  But the headphone port on your laptop will still work.  It's not the most convenient, but just plugging your speakers into you laptop works fine.  Of all the cords you have to move, that's got to be the easiest one.

All other devices on my docking station work though.  I don't close my laptop lid because I run with dual screens (big desktop) mode.  But I've noticed that it doesn't shut off either when docked and closed.

---

### Post by salvatore on 2005-10-30
Thanks for the reply.  The sound works fine in Windows XP, just not in Ubuntu.  I havent tested with any other distribution yet.

I'll give the headphone port test a try and report back.

---

