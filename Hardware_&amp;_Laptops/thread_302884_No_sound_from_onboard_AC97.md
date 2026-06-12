---
title: "No sound from onboard AC97"
date: 2006-11-19
forum: Hardware &amp; Laptops
---

### Post by Jedigorf on 2006-11-19
I am mucho need of some help. I have gotten all of the "hard" stuff set-up on my 6.10 MythTV box (lirc working, mythtv working). I can't, however, get any sound from my onboard soundcard. 

I am using an MSI RX480 Neo2 motherboard, which uses an ATI XPRESS 200 chipset with the SB400.

lsmod | grep snd returns what appear to be the proper drivers... atiixp, etc.

lspci returns the ATI IXP AC97 audio controller.

alsamixer settings seem to be correct.

I am truly at an impass here, and any help would be greatly appreciated.

---

### Post by David Corrales on 2006-11-19
Have you tried booting other livecd's and trying out sound to see if it works?

---

### Post by Mimsy on 2006-11-19
For what it's worth, the onboard AC97 on my laptop Just Worked (TM) in Dapper.

Perhaps roll back to the LTS version would help? If you don't want to do that, it works in Dapper, so it should be possible to make it work in Edgy as well.

Good luck!

/Mimsy

---

### Post by Captain Pugwash on 2006-11-19
I had exactly the same problem with my Clevo D630S laptop. The AC 97 sound card couldnot be found once I installed Edgy. I checked out the Internet and it appears that there isnt a simple solution so I went back to Dapper. I figured there might be some new patches released in the next few weeks. The sound card is no problem in Dapper. I tried both the 6.10 live cd and the alternative install cd and both did not install the sound card.

I hope you find a solution.

---

### Post by Jedigorf on 2006-11-19
I had the Dapper LiveCD in this morning and couldn't get it to play any sound either...

---

### Post by David Corrales on 2006-11-19
Hmmm... if you're on broadband. Could you try knoppix and see if it works? Just trying to try more options. Also, does the sound work in Windows (if it's available)?

---

### Post by superm1 on 2006-11-19
Check and see if the device is listed in /proc/asound

For example, i  see this on my computer:

```
supermario@portablemario:~$ ls /proc/asound/
card0  cards  devices  I82801DBICH4  modules  oss  pcm  seq  timers  version

```

---

### Post by Jedigorf on 2006-11-19
mythtv@darwin$ ls /proc/asound
card0  cards  devices  IXP  modules  oss  pcm  seq  timers  version

Tried Knoppix and SLAX Live CDs.
Tried installing the ALSA drivers from the Realtek website.

This may be hopeless.

---

### Post by superm1 on 2006-11-19
Ok, so it looks like your card is listed in /proc/asound  (IXP).

Can you change mixers with alsamixer?  Perhaps you will have to adjust 3D audio pre/post processing switches in alsamixer.

---

### Post by Jedigorf on 2006-11-19
Not exactly sure what you mean here about changing mixers...

---

