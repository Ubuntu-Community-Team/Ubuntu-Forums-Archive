---
title: "The speakers to not work"
date: 2009-07-23
forum: Hardware
---

### Post by Recco on 2009-07-23
I just bought a HP Mini 110-1030NR and but Ubuntu Netbook Remix on it.  I like it so far but the one thing that is really bugging me is the speakers do not work.  I cannot get any sound thought the main speakers.  The headphone work but no sound thought the main speakers.  I hope that someone can help me out with this.  Thanks a lot.

---

### Post by don_pucci on 2009-08-04
> **Recco said:**
> I just bought a HP Mini 110-1030NR and but Ubuntu Netbook Remix on it.  I like it so far but the one thing that is really bugging me is the speakers do not work.  I cannot get any sound thought the main speakers.  The headphone work but no sound thought the main speakers.  I hope that someone can help me out with this.  Thanks a lot.

Most people with the 110 models (including myself) have issues with sound and UNR.  Do a search for no sound on the HP Minis and there are many things to try...

Keep us posted if you get it working.

---

### Post by zodiac09 on 2009-08-04
[COLOR=black]I had this problem with my laptop. I had to update the ALSA drivers to get it to work. Maybe u have to do the same. U can get a script for updating it from here [/COLOR]
[COLOR=black][/COLOR] 
[[COLOR=black]http://www.4shared.com/file/115011575/e130751c/AlsaUpgrade-10x-rev-117.html[/COLOR]]("http://www.4shared.com/file/115011575/e130751c/AlsaUpgrade-10x-rev-117.html")
[COLOR=black][/COLOR] 
[COLOR=black]then run it by [/COLOR]
[COLOR=black][/COLOR] 
[COLOR=#006600]*[COLOR=black]sudo ./AlsaUpgrade-1.0.x-rev-1.17.sh -di[/COLOR]*[/COLOR]
[COLOR=#006600]*[COLOR=black][/COLOR]*[/COLOR] 
[COLOR=#006600]*[COLOR=black]Aftter that, reboot, and check out your gnome sound settings. And u should be able to see speakers in the there, with head phones, amoung other stuff. Give it a shot!![/COLOR]*[/COLOR]

---

