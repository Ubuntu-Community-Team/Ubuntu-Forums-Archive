---
title: "creative sound blaster audigy se..no sound"
date: 2009-05-09
forum: Hardware
---

### Post by 500sd on 2009-05-09
well i just installed ubuntu 9.04 today and i cant get sound working. 
i tried various things that didnt work obviously and i would list them but i cant remember exactly what i did...so just point me in the right direction please :)

thanks

---

### Post by 500sd on 2009-05-10
bump

---

### Post by 500sd on 2009-05-10
just tried plugging it into my motherboard and using the nvidea settings in sound preferences, and it works. so its not my speakers for sure and i also get sound in vista. im using an evga 680i if that helps.

---

### Post by funeralthirst on 2009-05-10
i have the audigy 2zs and same problem. upgraded to 9.04 and no sound.

---

### Post by 500sd on 2009-05-10
bump

---

### Post by jrickard on 2009-05-11
Creatove :abs SB0400 Audigy 2.  Upgraded to 9.02 and lost sound here as well.  
No help in this forum apparently.

Jack Rickard

---

### Post by DraconPern on 2009-05-11
bump

---

### Post by 500sd on 2009-05-11
damn nobody knows how to fix this?

---

### Post by 500sd on 2009-05-12
bump

---

### Post by 500sd on 2009-05-13
bump!!! i want to use linux so badly but i need sound

---

### Post by 500sd on 2009-05-14
bump

---

### Post by 500sd on 2009-05-16
bump

---

### Post by 500sd on 2009-05-17
bump...this is ridiculous

---

### Post by mustangzach on 2009-05-18
Hmm.. I just installed 9.04 on a system with an Audigy, I think it's working..

Have you checked the ALSA settings and all? It could just be something simple.

---

### Post by 500sd on 2009-05-18
> **mustangzach said:**
> Hmm.. I just installed 9.04 on a system with an Audigy, I think it's working..

Have you checked the ALSA settings and all? It could just be something simple.

yea i checked everything possible...

---

### Post by 500sd on 2009-05-21
bump

---

### Post by 500sd on 2009-05-23
bump

---

### Post by Hutchewon on 2009-05-26
> **500sd said:**
> just tried plugging it into my motherboard and using the nvidea settings in sound preferences, and it works. so its not my speakers for sure and i also get sound in vista. im using an evga 680i if that helps.
I have the 680i motherboard too. Same problem. System knows the card is there but will not use it. I have spent hours messing with pulse and alsa, no joy.

---

### Post by j0eb0b on 2009-05-26
I use 9.04 with an Audigy 2 Zs and the sound works well.  The only thing I can suggest from previous experience with Unbuntu and no sound is to ensure that the OS is not defaulting to the onboard sound chip on your motherboard.  Make sure in the bios that onboard sound is disabled.  If sound is disabled or your motherboard does not support onboard sound then I don't know what to tell you.

I have had this  default problem with AMD motherboards that use Nvidia NF II and NF IV chipsets.  Don't know whether it with Intel or other chipsets.

---

### Post by deadlockedgamer on 2009-05-26
I had this problem in 8.10 when I had to plug the speaker into the front head phone jack of an creative audigy soudblaster 2 platinum it is an older one however my problem was fixed on a fresh install of 9.04 i suggest checking if the front head phone port gives sound though this is an ugly fix. If it works report the bug to ubuntu devs or even if it doesn't and it may get fixed either this release or on 9.10. (due in October) Sorry about your problem because ubuntu has a great experience for me and I have gotten 5 people to use it so far. Don't give up someone will figure it out.

---

### Post by BrainStorms on 2009-07-07
I've experienced this problem in 8.10 and 9.04.  In fact, I've done a bit of testing, since I have two Audigy 2 Platinum cards (0240) and two Audigy 2 ZS "budget" cards (0353).  I've tested this on a Pentium III system (no on-board sound), a Pentium 4 system (on-board 5.1 sound, disabled), and now a 64-bit Xeon system (on-board 5.1 sound, disabled).

Here's my consistent results:  
* In 8.04, both cards worked fine on all systems.  
* In 8.10, the Audigy 2 Platinum cards did NOT work, but the ZS cards worked.  
* In 9.04, the Platinum cards work once again, but the ZS cards do NOT.  
:mad:

I just tried the suggestion above, which is to plug my ***front*** speakers into the front panel sound jack that the "budget" ZS card provides for.  That worked -- for 9.04 and the ZS card in my 64-bit system.

Oy!  :mad:

---

### Post by BrainStorms on 2009-07-07
I just found out how to "fix" this...

* Right-click on the speaker icon in the toolbar and select "Open Volume Control".  
* From the pull-down at the top, select "Audigy 2 ZS [SB0353] (Alsa Mixer)".
* Select the "Switches" tab.
* Check the "Audigy Analog/Digital Output Jack" checkbox.

That should route the sound to the rear ports of the card.

Forum thread 843012 notes "Updates seem to reset this switch regularly so keep this in mind."

---

