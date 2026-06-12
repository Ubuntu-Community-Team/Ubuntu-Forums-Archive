---
title: "Only front speakers working in 5.1 surround :("
date: 2005-11-10
forum: General Help
---

### Post by Ryanmt on 2005-11-10
Ok i used to use an onboard soundcard but i installed a nice audigy2 recently, only problem i have is that only the front two speakers work. 
Sames goes for the volume controls. Ive added all the extra ones in alsamixer but they all do nothing apart from the "analog front" control.. which works the front speakers

yes ive checked they are all plugged in correct everythings fine hardware wise, so i think its possibly the driver causing problems? im using the ESD deamon 


Can anybody help? Cheers

---

### Post by Kyral on 2005-11-10
It might be ESD...try switching it over to ALSA in the "Multimedia System Selecter" in System -> Preferences

---

### Post by jamesford on 2005-11-10
have u unmuted (press m) 3D contr in alsamixer and upped all the bars all the way to the one called 'side' ? i think this fixed it for me

---

### Post by rama on 2005-11-10
Try out the availiable bars in the Volume Control (Edit->Preferences) till you find the ones that control the rear speakers. In my case (SB audigy 2 + 4.1 speakers) "Surround" did the trick.

---

### Post by Ryanmt on 2005-11-10
i tried changing it to alsa and it made no difference, yes james all the volumes are turned right up but it makes no difference only the "analog front" has any effect

---

### Post by Ryanmt on 2005-11-10
ive got got a surround volume control, ive added all of the ones in peferences none of them work :(

---

### Post by pickarooney on 2005-11-11
I had to install kmix to activate my rear speakers, as the rear sound ports were being used as input or bass by default.

---

### Post by Ryanmt on 2005-11-12
isnt that for kde though? im using gnome

---

### Post by pickarooney on 2005-11-12
yeah, it is, but I couldn't be arsed finding a gnome equivalent, so just used it.
it's not like there are laws against using K apps in G or vice-versa.

---

### Post by grsing on 2005-11-12
[QUOTE=pickarooney]I had to install kmix to activate my rear speakers, as the rear sound ports were being used as input or bass by default.[/QUOTE]

Thanks, that works for me, and that was one of my last annoyances with ubuntu.

---

### Post by peterzal on 2005-11-13
[QUOTE=pickarooney]I had to install kmix to activate my rear speakers, as the rear sound ports were being used as input or bass by default.[/QUOTE]

Did you have to change anything in KMix to get your rear speakers to work? I have KMix installed and I can only get 2 (out of 4) speakers to work.

---

### Post by Ryanmt on 2005-11-13
i installed kmix, played with all the settings and still no joy :(

---

### Post by pickarooney on 2005-11-13
[QUOTE=peterzal]Did you have to change anything in KMix to get your rear speakers to work? I have KMix installed and I can only get 2 (out of 4) speakers to work.[/QUOTE]

On the switches tab, select **Rear Output** for the line-in mode.

---

### Post by Ryanmt on 2005-11-17
bump any ideas people?

---

### Post by Ryanmt on 2005-11-19
alsamixer says its playing via chip SigmaTel STAC9750,51 .. shouldnt that be changed to soundblaster?

how do i get this up and running somebody please help! pllleeasse! :(

---

### Post by callit on 2005-11-19
Well, it seems my speakers have been working "as expected" but not necessarily as I'd like.  I installed kmix, and found a switch that said Duplicate Front.  

I'd like it if programs could do this natively for stereo output (ie the average mp3 player).  Maybe I just haven't played around enough, but haven't found anything.

On a side note, doing this has an interesting effect when I Mute the master - only the front speakers mute, not surrounds.

---

### Post by sirlancelot on 2005-11-19
Applications -> Sound & Video -> Volume Control

In the menu:
Edit -> Preferences

Scroll down until you find:
Surround, Center (not PCM)

Select them and close the preferences, now you can adjust them as you like.

---

### Post by Ryanmt on 2005-11-25
i dont have surround anything in volume control, ive got stuff AC97 Mic Select though. Makes me think it is still using the old soundcard driver?

really doing my fruit in now :(

---

### Post by Ryanmt on 2005-11-28
bump :(

---

### Post by hav0x on 2005-11-28
[QUOTE=pickarooney]
it's not like there are laws against using K apps in G or vice-versa.[/QUOTE]

I believe there are. In some countrys at least.
FYI i refuse to use QT :p

---

### Post by mha109 on 2005-11-29
Try enabling "wave" in preferences for sound control . that's how I got my 5.1-speakers to work.

---

### Post by Vlammetje on 2005-11-30
I do not have that option in sund control (Gnome)

Also, even though I've installed Kmix, and according to Synaptic it is indeed installed, I cannot seem to find it anywhere in my Gnome menus. Where should I look? :(

---

### Post by TheCraiggers on 2005-11-30
I was having the same problem with my Audigy 1.  I simply went into alsamixer and upped the 'surround' volume and that was it.  I don't usually use gnome of kde, so I don't know about those other mixers.

Good luck.

---

### Post by Ryanmt on 2005-11-30
i dont have surround volume, i need to tell ubuntu its got a 5.1 surround sound card in not the crappy onboard one which it currently thinks!

---

### Post by Vlammetje on 2005-11-30
You can disable the onboard dound in your BIOS. That will force Ubuntu to onsider the surround card.... as it did for me. however it still does not play proper surround for me, and I have no 'surround' option in alsamixer either. Also no matter how many times i use 'sudo alsactl store' to save changes i've made to alsamixer it will always revert back to what it was... wtf am i doing wrong? :(

---

### Post by oofnik on 2005-11-30
What program are you trying to play out of? If it's XMMS I had to change the default output driver from OSS to ALSA, and it worked for me after pushing all the levels up in alsamixer.
I think my sound card was the only thing that worked out of the box with Breezy. Most things that worked with Hoary took some work on Breezy, ...not good. Oh well.

---

### Post by tabnaka on 2006-07-16
Yea, after switching from Kubuntu to Ubuntu, I had problems with my rear and center speakers too. Luckily, I was able to fix it.

1) I checked "alsamixer" in command prompt to make sure surround sound was activate and not muted.

2) in Edit -> Preferences after double-clicking the volume icon in panel, I checked that Duplicate Front speakers was on. And for the Surround Jack option I chose "Shared". This fixed the rear spearkers

3) for the center speakers, I'm using a Nvidia onboard audo by Gigabit MB. For some reason after plugging in all my 5.1 connections to the color coded port on the backpanel of the MB I was not getting center speaker.  But when I switched the Orange connector to the Blue-colored port, the center speaker started working. 

Hope this helps.  Thanks.

---

### Post by JOKEREMPIRE on 2007-09-25
> **tabnaka said:**
> Yea, after switching from Kubuntu to Ubuntu, I had problems with my rear and center speakers too. Luckily, I was able to fix it.

1) I checked "alsamixer" in command prompt to make sure surround sound was activate and not muted.

2) in Edit -> Preferences after double-clicking the volume icon in panel, I checked that Duplicate Front speakers was on. And for the Surround Jack option I chose "Shared". This fixed the rear spearkers

3) for the center speakers, I'm using a Nvidia onboard audo by Gigabit MB. For some reason after plugging in all my 5.1 connections to the color coded port on the backpanel of the MB I was not getting center speaker.  But when I switched the Orange connector to the Blue-colored port, the center speaker started working. 

Hope this helps.  Thanks.

Thanx a LOT [-o<

This really did the trick!

Steve

---

