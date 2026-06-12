---
title: "No sound with ASUS W2JC"
date: 2006-08-12
forum: Hardware &amp; Laptops
---

### Post by krugman on 2006-08-12
Hello!

My troubles with Ubuntu continue. I have absolutely no sound with my laptop, an ASUS W2JC. I have seen that it was the case for other people in previous versions of Ubuntu, but I haven't found anything about dapper.
Is there a solution now?

The thing is, my sound card (an Intel HDA or something like that) seems to be detected since I can find it under System->Preference->Sound...
but I am still a newbie so, maybe there is something I can do about that!

Any help would be immensely appreciated:-D

---

### Post by axxs on 2007-01-18
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2565](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2565)

A known issue, assigned, but not fixed as yet

---

### Post by axxs on 2007-04-04
and still waiting :(((

---

### Post by oorban on 2007-04-08
Hi, I got the same problem on a ASUS A8Js, I solved it by adding this line:
[FONT="Courier New"]options snd-hda-intel position_fix=1 model=3stack[/FONT]
at the end of the file [FONT="Courier New"]/etc/modprobe.d/alsa-base[/FONT]

Olivier

---

### Post by axxs on 2007-05-11
unfortunately this doesn't help on the w2jc :(

---

### Post by nickthegreek78 on 2007-05-11
use your alsa mixer turn pcm all the way up  when using headphones mute the sound icon and you only have headphones

---

### Post by nickthegreek78 on 2007-05-11
use the alsa mixer under the sound icon properties and turn the pcm all the way up.  If you plan on using headphones you must mute the sound icon and the sound will only come from the headphones.

---

### Post by TopasPV on 2007-07-17
Thanks to some guys in #ubuntu-de on freenode I found a solution to this problem (same laptop, same soundcard, same problem). I installed a new driver from Realtek and this was enough to get it working. You can download it from the [Realtek homepage]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=24&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false#High%20Definition%20Audio%20Codecs").

Good luck to you, krugman and thanks to those friendly people on the irc!

---

