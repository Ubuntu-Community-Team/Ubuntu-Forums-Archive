---
title: "Gateway 4026GZ No Sound"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by jtutt on 2005-06-21
Loaded Hoary on a new Gateway 4026GZ.  Most everything went smoothly but I cannot get it to produce any sound.  Been searching through the howtoos and trying different thinks but no progress.  I am not getting any errors.  All the apps I have tried seem to think they are playing, but nothing is coming out.  Very frustrating.  Has anyone else had any experience with the 4000 series Gateway laptops?

---

### Post by jhorey on 2005-08-04
Try turning off the External Amplifier. If that doesn't work try turning off Headphone and Line Jack Sense. You can do this using KMix or the equivalent tool.

---

### Post by brianw on 2005-10-02
[QUOTE=jtutt]Loaded Hoary on a new Gateway 4026GZ.  Most everything went smoothly but I cannot get it to produce any sound.  Been searching through the howtoos and trying different thinks but no progress.  I am not getting any errors.  All the apps I have tried seem to think they are playing, but nothing is coming out.  Very frustrating.  Has anyone else had any experience with the 4000 series Gateway laptops?[/QUOTE]

Have you ever got this working? I have tried different combinations. I had headphone sound once. That is it. I wonder if the volume switch is hw+sw. In other words, it does not work unless you have some OS intreprit the output from the switch.

Let me know, thanks.

brianw

---

### Post by knappen on 2005-10-03
I had problems getting any sound to work on my IBM T21. Then I realised that the DAC was muted.

Perhaps it is the same for you ...

---

### Post by brianw on 2005-10-06
What do you mean DAC? Is that hardware? Or in alsamixer?

---

### Post by knappen on 2005-10-07
It is in Alsamixer. Part of the Capture section.

---

### Post by RHAnthony on 2007-04-01
I haven't gotten it working on mine either and I've tried everything I can think of.  I also couldn't get it working under Vista and it is reported to work just fine driver wise.  But then again I don't take Vista as being a definitive test.  It is odd though that neither will output sound.

Did you have any problems with your internal wireless on this laptop also?  I am having a few.

---

### Post by voturin on 2007-05-24
I have the same problem - no sound with Ubuntu on my Gateway 4026GZ...
[email]voturin@hotmail.com[/email]

---

### Post by MianoSM on 2007-11-09
I have still yet to find any type of way to get the audio working on my 4026gz. Very disappointing.

This was on a Gusty Gibbon (7.10) Install with GDM. : (

2.6.22-14-generic

---

### Post by Lawrence Talbot on 2007-11-09
First off my computer was put together by myself but I had the same problem when I installed Ubuntu.  I have a sound blaster card and I couldn't get it to work.  I went into the system sound program and changed some things around, rebooted and then it started to work.  I downloaded some updates and new programs and after I rebooted I didn't have any sound.  I changed the sound program around and rebooted.  I then changed back to sound blaster and it started working again.  I downloaded some more stuff and it quit working again after I rebooted.  I went through the same steps again and then it started working. 
It seems like every time I reboot the sound stops and then I have to go through all the steps again.  I like Ubuntu because it does most of the installing it's self but this is getting to be a pain.   [img]http://s35.photobucket.com/albums/d189/dimebar_probably/Smileys/th_chainsaw.gif[/img]

---

### Post by metal4pg on 2008-01-04
I am also having problems with my gateway 4026GZ playing sound. I can see the Intel 82801DB-ICH4 chipset just fine. It looks like it should be working. When I change volume settings on the button (right corner on palm rest) the little volume slider displays what should be the current levels but nada, nope, nothing. Get nothing out of headphones either. I go into the test settings (system->preferences->sound) & all looks good &, in theory, appear to be working properly. On the devices tab I did change all of those to "ALSA" thinking that may have an effect but it didn't change anything. It had previously been set to the chipset description. I've tried the recommendations below & even went to the comprehensive sound solutions guide but nothing helped. [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I even found an entry on the spanish speaking forums for the same issue but nobody responded. [http://translate.google.com/translate?hl=en&sl=es&u=http://www.ubuntu-es.org/index.php%3Fq%3Dnode/72641&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Dlinux%2Bgateway%2B4026gz%2Bno%2Bsound%26hl%3Den%26sa%3DG](http://translate.google.com/translate?hl=en&sl=es&u=http://www.ubuntu-es.org/index.php%3Fq%3Dnode/72641&sa=X&oi=translate&resnum=5&ct=result&prev=/search%3Fq%3Dlinux%2Bgateway%2B4026gz%2Bno%2Bsound%26hl%3Den%26sa%3DG) . 

Does anyone have one of these things to test out ? I'm going nuts with this thing. It works fine under XP & I really don't want to have to go back to using XP exclusively since I'm trying to migrate completely away from it. I used 7.1 & applied all updates. I even installed automatix2 to add codecs. I'm at my wits end.

---

### Post by MianoSM on 2008-05-05
I got this to work on Xubuntu though alsamixer.

On a default install (only modifications to the system were adding java/flash, and wireless capabilities): in alsamixer:

Master is 00 (71)
Master M is 00 (68)
Headphone is MM (I have to manually change this when headphones are in)
Headphone is MM

PCM is 00 (100) - This appears to have been the big one.
Line is MM
Line Jac is MM
CD is MM
Mic is MM 
Mic Boost is MM 
Mic Sele is Mic1
Phone is MM
IEC958 is MM
IEC958 P is 100 
IEC958 P is AC-Link
Aux is MM
Mono Out is Mix
External is MM
Stereo M is MM

---

### Post by m_ch on 2008-05-07
> **MianoSM said:**
> I got this to work on Xubuntu though alsamixer.

On a default install (only modifications to the system were adding java/flash, and wireless capabilities): in alsamixer:

Master is 00 (71)
Master M is 00 (68)
Headphone is MM (I have to manually change this when headphones are in)
Headphone is MM

PCM is 00 (100) - This appears to have been the big one.
Line is MM
Line Jac is MM
CD is MM
Mic is MM 
Mic Boost is MM 
Mic Sele is Mic1
Phone is MM
IEC958 is MM
IEC958 P is 100 
IEC958 P is AC-Link
Aux is MM
Mono Out is Mix
External is MM
Stereo M is MM


Thanks a lot MianoSM, I've just tried your solution and it works great.
This was something I've never been able to accomplish.
Again thanks a lot.

---

### Post by RHAnthony on 2008-07-15
Thanks MianoSM!  I turned everything down to 0 and then put master and PCM back up, and finally I can hear!  Tweaking the rest as needed but now I have a baseline to work from that gives me sound... and that was the only missing part of the puzzle on my 4026gz!

---

