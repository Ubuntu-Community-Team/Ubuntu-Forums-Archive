---
title: "Laptop integrated subwoofer(Beats Audio) Not Working!"
date: 2016-06-02
forum: Hardware
---

### Post by inverged on 2016-06-02
This problem has eluded me for quite some time.
I have an HP Envy notebook running 14.04 that has 3 speakers.
[COLOR=#111111][FONT=Ubuntu]It's a [/FONT][/COLOR][m6-n010dx]("http://support.hp.com/us-en/document/c04223655#AbT1") with an AMD A-10 5750 Richland APU.
This is a "Beats Audio" model.
The soundcard is a Realtek ALC3241
The two left and right speakers on top and a small subwooder located on the bottom of the unit.
I've found guides online for other "Beats Audio" sound chips but none for mine exactly.
I have tried:

Adding these options to [COLOR=#111111][FONT=Consolas]/etc/modprobe.d/alsa-base.conf[/FONT][/COLOR]
 [COLOR=#111111][FONT=Consolas]snd-hda-intel model=auto 
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu] enable-lfe-remixing = yes
 default-channel-map = front-left,front-right,lfe

My alsamixer looks like this :
[ATTACH=CONFIG]269399[/ATTACH][/FONT][/COLOR]

i've also tried enabling pins with hda-jack-retask to no avail.
I know there must be some way to get this working.
Any help appreciated.
I also asked this some time ago [here]("http://askubuntu.com/questions/675012/hp-envy-m6-subwoofer-beats-audio-not-working").

---

