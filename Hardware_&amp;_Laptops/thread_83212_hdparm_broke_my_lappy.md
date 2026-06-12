---
title: "hdparm broke my lappy?"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by Kuolio on 2005-10-28
OK, this is the situation:

Late last night I was tweaking my HD's performance with different hdparm-options, to find "the ultimate settings". All of the sudden, when I issued command "sudo hdparm -d1 /dev/hda1" my lappy just froze. Everything, no commands worked so I had to a hard reboot.

After the boot, Breezy loaded up just fine untill just before login it sayed "critical temperature reached, system is going to shutdown now" and then it shuts down. Buah, as my install was rather new and I have separate /home partition for all my important files, I decided to reinstall whole breezy.

I installed breezy, installation froze couple of times as usual but finaly it ran through OK.. and then when it 1st booted, the problem is still there. "Critical temperatures reached blaablaa..". Uh, this was about the time I realy started to scratch my head.. I tried installing breezy with "linux noapic" boot-option but it didn't help, as it came to my mind that API could be broken or something.

Now I just have downloaded Knoppix and ubuntu live-cd's, I'm gonna go and test them out soon (I&#180;m at work atm). I currently only have that lappy as my iBook and desktop-systems are loaned to my familymembers. 

If my hdparm-session realy f**ed up my hardware and if live-cd's wont work either, does anyone know any way to get some important files from my HD? Yea I know, "backup before tweaking" but I didn't. NOTE: I mostly need my workrelated documents, the porn I can re-download ;)

Any help, ideas and suggestions are most welcome.. what should I do now? the "easy" sollution would be to take my lappy to the shop wich I bought it as it has som 8 months guarantee left. But, what's the fun in that ;)

EDIT: specs for da lappy: Acer Aspire 5021WLMi, Turion(amd64) 1.6Ghz, 512mt DDR, Radeon X700, 80GB-HD, DL-dvd and using breezy amd64. Breezy has been very sweet to me before doing this hdparm-fidling, as api-stuff like powersaving and even 3d-graphs are working beautifully.

---

### Post by MrCheese on 2005-10-28
It sounds like a really horrible coincidence that your cpu fan has died shortly before you restarted the machine. A cold-boot with a sticking fan means that the cpu overheats really fast. Shit like that usually happens to me.....!

---

### Post by Kuolio on 2005-10-28
Hehe, it's not a bad cpu-fan, it's blowing quite fast and spinning like normal. I'm now using Knoppix to backup all important data and I can explore and move files around my HD as normal.

It's just that when ever I boot any OS from HD itself, I get into trouble. Realy, truly weird. I mean, I've been working as a sys-admin and general computerhelper for few years, and this is unique. I've never encountered anything like this. HD works when im not running OS from it :D

At this point I have tried several linuxes with loads of different boot options, and most die with the same "overheating problem". Some live-cd's do work like nothing, like Knoppix. Also windows restarts itself before desktop. The thing is, that cpu-fan etc. cooling is working very normal, and my lappy seems cool as normal.

Oh-well, after I backup everything I need I'll take this back to shop where i bought it.. they promised to replace my machine while my own goes through their repairs.

---

