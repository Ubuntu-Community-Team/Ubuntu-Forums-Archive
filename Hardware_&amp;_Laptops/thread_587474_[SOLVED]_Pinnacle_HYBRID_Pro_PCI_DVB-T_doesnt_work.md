---
title: "[SOLVED] Pinnacle HYBRID Pro PCI DVB-T doesnt work in linux without first booting win"
date: 2007-10-22
forum: Hardware &amp; Laptops
---

### Post by Onurzaim on 2007-10-22
Strange but I realized after I open my computer from 0 first I have to go windows and open DVB-T channels from the Pinnacle program and come back to linux to see it properly working.

I dont know how or why this happens. I think this is related to firmware stuff or a program issue.

I use kaffeine for DVB-T channels.

note: Wihtout booting in windows I can see standard old school PAL broadcasts. I only have problem with DVB-T channels when I firstly boot my computer in Linux.

---

### Post by potnoodles on 2007-10-25
I have that problem too. read here

[http://ubuntuforums.org/showthread.php?t=587130](http://ubuntuforums.org/showthread.php?t=587130)

had no replies/help from the forum and the topic soon disappears off the page in here.

regards

potnoodles

---

### Post by potnoodles on 2007-10-25
I solved my problem

[http://ubuntuforums.org/showthread.php?t=587130](http://ubuntuforums.org/showthread.php?t=587130)

regards,

potnoodles

---

### Post by Onurzaim on 2007-10-27
Looks promising. I'll try asap. :)

---

### Post by Onurzaim on 2007-10-27
Those posts gave me the idea why my card didnt work my Pinnacle PCTV Hybrid Pro PCI card.

And OMG! with the same logic I solved the problem.

My card is recognized as Philips TDA10046H in Kaffeine. So I googled it and found the firmware file. 

[U]This is the way I solved it.
[/U]
I downloaded **[http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.gz)** and extracted get_dvb_firmware file from it and executed 

> ./get_dvb_firmware  tda10046

then copied into /lib/firmware folder.

Afterwards it worked.

I took help from this page which is spanish, I dont understand spanish but its so simple that its hard not to understand for a mediocre linux user.

> [http://forum.ubuntu-fr.org/viewtopic.php?pid=1252169](http://forum.ubuntu-fr.org/viewtopic.php?pid=1252169)

Thanks for the walkthroughs and the ideas you gave.

Regards.

Note: I also attached dvb-fe-tda10046.fw to this post you can benefit. Have good use of it :D .

---

### Post by roseway on 2007-11-17
Rather belated thanks for this. It enabled me to get my Hauppauge HVR-1100 working.

---

