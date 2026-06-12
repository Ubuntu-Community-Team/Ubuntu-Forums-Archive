---
title: "WIFI Card used to use MAD WIFI"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by frito on 2009-11-11
I just upgraded to 9.10 and my wireless stopped working.
I have a WG311T which is supposed to be compatible with Ath5k although it never has been compatible for me.
I liked the fact that ubuntu had the switch to MADWIFI button in "hardware drivers" but i assume this was taken out as I cant find it and i dont think im using MADWIFI anymore.

How can I get it back? Or anyway to make my internet work for that matter.

---

### Post by frito on 2009-11-12
Anybody? is it possible to enable MADWIFI in ubuntu? I cant use linux without internet.

---

### Post by alexterm on 2009-11-15
> **frito said:**
> I just upgraded to 9.10 and my wireless stopped working.
I have a WG311T which is supposed to be compatible with Ath5k although it never has been compatible for me.
I liked the fact that ubuntu had the switch to MADWIFI button in "hardware drivers" but i assume this was taken out as I cant find it and i dont think im using MADWIFI anymore.

How can I get it back? Or anyway to make my internet work for that matter.

Similar thing for me. "Upgraded" from 9.04 to 9.10 (64 bit). Now forced to use eth0 with lead trailing across two rooms. I tried out the live Mandriva 2010 One two days ago - got ath0 set up in ~ 30 seconds. This appears to illustrate some shocking lack of care on the part of the Ubuntu developers.

alexterm

Linux INSPIRON531 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux

---

### Post by alexterm on 2009-12-05
Solved the problem after reading the wifi trouble shooting post in the Networking Forum. The Ath5k driver was blacklisted!! The act of upgrading must have been responsible for this. By commenting out the relevant line, wifi works OK now.

alexterm

---

### Post by drpjkurian on 2009-12-06
> **frito said:**
> Anybody? is it possible to enable MADWIFI in ubuntu? I cant use linux without internet.

Hi Frito
Please visit my thread and a give a try. You can install madwifi like a charm.

[http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

With regards
Dr Kurian

---

