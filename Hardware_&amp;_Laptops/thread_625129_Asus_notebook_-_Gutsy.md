---
title: "Asus notebook - Gutsy"
date: 2007-11-27
forum: Hardware &amp; Laptops
---

### Post by Edho on 2007-11-27
New notebook  A7SV-7S058C.
Intel 2.2 Ghz , 2 Gb ram, 250 Gb HD ,17 inch , Nvidia 8600m gs.

Live cd Gutsy works.
Install works.

Not tested :
Blue Thoot - cam - microfoon - wireless.

The wificard is.
PRO/Wireless 3945ABG - Intel.

Noob with wireless...

Tips for choosing a wireless router , please?

---

### Post by Edho on 2007-11-29
- PRO/Wireless 3945ABG - Intel.

- Ubuntu 7.10

Recommandations for a fast and stable wireless-router please?

Brand, type ??

---

### Post by technologik on 2008-01-02
I'm running Kubuntu Gusty on my A7SV  Everything works great. Even the webcam.  As far as a router goes...I really like the Linksys WRT-54G.  Never had a problem with any of them that I've installed.  I run one at work and home.

---

### Post by LP25000 on 2008-01-23
Hello,

The sound of my **asus a7sv** under gutsy supports **only 2 speakers, but not with 4 speakers** :(. It is configured with alsa 1.0.14 with the intel chipset hda (ich8). How do I get the sound on 4 speakers in 4.0.

thanks

---

### Post by xrs on 2008-01-31
I'd like to just get my sound working at all.
I moved my hard drive from an Asus F3Sv to my new A7Sv (every thing is the same, but has a 17" screen instead of a 15.4") Everything works fine, but have no sound at all. Put the HDD that came with it in, and I do get left and right sound... Didn't even no it had 4 speakers. Any Ideas on what the issue might be?

(Oh and my bluetooth could see other bluetooth items, but could never sync same with the A7Sv)

---

### Post by xrs on 2008-02-02
> **LP25000 said:**
> Hello,

The sound of my **asus a7sv** under gutsy supports **only 2 speakers, but not with 4 speakers** :(. It is configured with alsa 1.0.14 with the intel chipset hda (ich8). How do I get the sound on 4 speakers in 4.0.

thanks

The no sounds issue was fixed by recompiling and reinstalling alsa. Installed the latest 1.0.15.

Also got all four speakers working with a little help from here

> **Forvrknight said:**
> Never mind I fixed it after quite a bit of searching.

Added options snd-hda-intel model=6stack-dig to the end of /etc/modprobe.d/alsa-base

So now I get 
Front - teeny speakers
Center - Front left
LFE - Front right

3stack-dig worked too but the one added sounded better and had more volume output.

:guitar:

Now if i can just get my keyboard volume to control all of them since it is now randomly deciding which one to control even though I have them all selected in the volume control.

```
Open up a terminal and type this
sudo gedit /etc/modprobe.d/alsa-base

and at the very bottom just add

snd-hda-intel model=6stack-dig

close and save - might like to reboot

```

WoW sounds alot better now, and just remember from the quote above the front is the back and the back is the front when using snd-hda-intel model=6stack-dig

:guitar:

---

