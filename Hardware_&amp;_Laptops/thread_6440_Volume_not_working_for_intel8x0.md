---
title: "Volume not working for intel8x0"
date: 2004-11-28
forum: Hardware &amp; Laptops
---

### Post by mikaelu on 2004-11-28
Hi,

I have an onboard soundcard:Intel Corp. 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)

It works (both in and out) but there is no way to control the volume !
I've tried several mixers (gnome, alsamixer, built in in applications)

The mixers find the card and presents the usual sliders (master, pcm....) but they do not affect the volume (the PCM sometimes mutes the sound if I pull it all the way down). I've inserted another card (cs4297) and it works perfect (giving me lot of funny tabs in the mixers...). I've found a module option "ac97_quirk=1" but it does not work. Any ideas ?

As a side note: How do I specify which sound card to use in rythmbox/gnome ? I kind of like having two soundcards....

My current snd-modules are:
snd_ens1371       
snd_intel8x0      
snd_ac97_codec    
snd_pcm_oss       
snd_mixer_oss     
snd_pcm           
snd_timer         
snd_page_alloc           
snd_mpu401_uart   
snd_rawmidi       
snd_seq_device

---

### Post by lockenkeyster on 2004-11-29
for my laptop (same card) I had this issue and I had to go to Computer -> Desktop Preferences -> Sound and then deselect "enable sound server startup" to keep ESD from starting

(of course you then have no system sounds, but this has been the only solution for me so far)

---

### Post by mikaelu on 2004-11-30
Thanks for your answer. 

I've already disabled esd. It does not make any difference.....

---

### Post by ronin69hof on 2005-01-23
thanks, that worked for me.  i dont really care that i dont have any system sounds so long as i can hear my music while i work

---

### Post by piedamaro on 2005-01-23
Unfortunately this kind of soundcard doesn't have a pcm volume mixer in it.
There is only a _plan_ to support software resampling in order to raise and lower the volume on these cards.

---

### Post by mikaelu on 2005-01-31
[QUOTE=piedamaro]Unfortunately this kind of soundcard doesn't have a pcm volume mixer in it.[/QUOTE]

You actually mean that it is a rather advanced 5.1 sound card WITHOUT any hardware for volume control? I find it hard to believe, but you are probably right. Any links where I can read more about this?

---

### Post by piedamaro on 2005-01-31
You'll find the discussion on the volume control on the alsa mailing-list, but I was wrong, your card should have volume control, but there is a bug: the sliders work only with the headphone output, my girlfriend has the same card on her ubuntu pc, and it's the same deal. Try to see if it works :)

---

### Post by satnelav on 2007-12-26
> **lockenkeyster said:**
> for my laptop (same card) I had this issue and I had to go to Computer -> Desktop Preferences -> Sound and then deselect "enable sound server startup" to keep ESD from starting

(of course you then have no system sounds, but this has been the only solution for me so far)

Thank you. This helped for me with 82801FB/FBM/FR/FW/FRW (ICH6 Family) which also uses intel8x0. Albeit, there was some strange behaviour: the sound was after random experimenting with alsamixer. I've been struggling or could not install this card on Gentoo, FreeBSD, Windows. Ubuntu took me only 2 hours :).

---

### Post by Yellow Pasque on 2007-12-26
Try switching to OSSv4, which has software/virtual mixing. The link's in my sig.

---

