---
title: "Dell Studio 15 - Headphone Jack Not Working (Speakers Work)"
date: 2010-05-02
forum: Hardware
---

### Post by oxsyn on 2010-05-02
I have a Dell Studio 1558.  It has two headphone jacks.  Speakers work perfectly out of the box, however when I plug headphones in, sound doesn't work.  Any suggestions?

---

### Post by demizer on 2010-05-03
I have this exact same laptop with the exact same problem. There is sound, but it is veeeeery low, and I can barely hear it. I tried uninstalling pulse, and playing with also, but I got nothing. I am reeeeeally starting to hate proprietary hardware.

---

### Post by demizer on 2010-05-03
Yo. Fixed it. See here: [http://ubuntuforums.org/showpost.php?p=9184185&postcount=3](http://ubuntuforums.org/showpost.php?p=9184185&postcount=3) and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). In short, put "options snd-hda-intel model=del-eq" into "/etc/modprobe.d/alsa-base.conf".

---

### Post by oxsyn on 2010-05-12
Thanks dude.  Very much appreciated.  Will try this when I get home.

---

### Post by boru33 on 2010-05-28
> **demizer said:**
> Yo. Fixed it. See here: [http://ubuntuforums.org/showpost.php?p=9184185&postcount=3](http://ubuntuforums.org/showpost.php?p=9184185&postcount=3) and [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto). In short, put "options snd-hda-intel model=del-eq" into "/etc/modprobe.d/alsa-base.conf".

I was having the same problem (Dell 15 Ubuntu 10.04). Solution worked great, I just want to point out what i assume to be a typo from demizer. 

"**del-eq**" should read "**dell-eq**"  

in the "options...." line of the alsa-base.conf file. (At least I needed to make that correction).

Thanks

---

### Post by bcooperb on 2010-06-01
I have found that **[COLOR="Lime"]dell-m6[/COLOR]** works better than dell-eq

I have a Dell studio 1747 | Intel core i7 | 4GB RAM 

so for those who don't know try this:

Open a terminal window
type: sudo gedit /etc/modprobe.d/alsa-base.conf
when gedit opens, just paste [COLOR="Lime"]*options snd-hda-intel model=dell-m6*[/COLOR] on the last line, save it, restart computer. See if that works!


**FILE TO EDIT:** */etc/modprobe.d/alsa-base.conf*
[B]
LINE TO ADD:[/B] *options snd-hda-intel model=dell-m6 *

---

### Post by Raik.48 on 2010-08-27
the solution given by bcopperb solved my prob, and I too have Dell Studio 1747 i7, 6 gigs of ram, 17inch.

---

