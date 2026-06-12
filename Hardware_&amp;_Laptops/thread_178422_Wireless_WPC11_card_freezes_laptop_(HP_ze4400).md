---
title: "Wireless WPC11 card freezes laptop (HP ze4400)"
date: 2006-05-17
forum: Hardware &amp; Laptops
---

### Post by clearzen on 2006-05-17
Okay, so I've installed Ubuntu 6.06 beta on a HP ze 4400 laptop. I love the OS I've installed it on 2 other desktops and it works great. However, the wireless card on my laptop (a WPC11) does not work. Not only does it not work but it freezes the entire system whenever it is inserted. I've tried everthing I can think of. I've used NDISwrapper, alien command for install of non debian drivers I even tried to get a copy of the kernal source to make a custom kernal. I found that I don't know near enough to do that currently with linux. Nothing I've done has worked. I need help this is driving me crazy....I'm up for suggestions.

---

### Post by tonyr on 2006-05-17
I don't have any answers, but many people have had this problem.  Type
**wpc11** in the **Search** window at the top of the thread to see what 
some others have tried.

---

### Post by clearzen on 2006-05-18
Can anyone help?....I installed the rtl8180 drivers successfully but it still freezes when I insert the wireless card

---

### Post by nocturn on 2006-05-18
I do not have this hardware, so I can provide little help.

I'm going to modify the thread title though, in the hope that the right people read it and respond.

---

### Post by clearzen on 2006-05-18
Okay, I think it has to do with the pcmcia configuration. I've tried other cards as well and it's always the same result, if the card is inserted during boot it hangs when it loads the pcmcia config, and if I insert a card after boot it instantly freezes. So, now my question is how could I modify the config file for those services to avoid this problem? I know it can be done because I've successfully used this card with Slax and Knoppix live cds.

---

### Post by clearzen on 2006-05-18
For anyone interested I was right it was an issue with the pcmcia setup. I edited the config file in this manner and it loaded and reconizes the card.

#include port 0x100-0x4ff, port 0xc00-0xcff

include port 0xfd00-0xfdff, port 0xfc00-0xfcff

#include memory 0xc0000-0xfffff

#include memory 0xa0000000-0xa0ffffff, memory 0x60000000-0x60ffffff

include memory 0x80000000-0x80000fff, memory 0xffeff000-0xffefffff

include memory 0xfbeff000-0xffefefff, memory 0x000d7000-0x000d7fff



# High port numbers do not always work...

# include port 0x1000-0x17ff



# Extra port range for IBM Token Ring

# include port 0xa00-0xaff



exclude irq 1

exclude irq 2

exclude irq 3

exclude irq 4

exclude irq 5

exclude irq 6

#exclude irq 7

exclude irq 8

exclude irq 9

exclude irq 10

exclude irq 11

exclude irq 12

exclude irq 13

exclude irq 14

exclude irc 15

I don't know how to make the scrolling boxes....sorry for the length of the post. I still haven't gotten it fully up and running but I think the hard part is over.

---

### Post by tonyr on 2006-05-18
[QUOTE=clearzen]
I don't know how to make the scrolling boxes....sorry for the length of the post. [/QUOTE]

Just use the Quote icon(text balloon looking thing) or Code icon (#) at the top 
of the Message editor.  The scrolling business happens automatically if necessary.

---

### Post by dhunter22 on 2006-05-20
I've had this same issue with a WPC45GX4 (Linksys Wireless SRX400 MIMO Card) and a Dell Inspiron 4100 running Win2000Pro. I noticed that if you insert, remove and reinsert the card fast enough it will not freeze, but say "The device cannot start" in the device manager. Ocassionally, if you insert the card at the right point during startup, it will work fine, but if you insert too early, it will freeze before startup. I'm thinking this is a software issue, because it worked the first time I installed it with the disk it came with and now when I reinstall it, it freezes even during installation. I've found hundreds of other cases online, but no one had an answer, so I emailed Linksys today. I also tried upgrading to WinXP, but it gets a fatal error in both upgrade and clean install.

*This forum's format looks very familiar...*

---

### Post by punkybouy on 2006-06-19
[QUOTE=clearzen]Okay, so I've installed Ubuntu 6.06 beta on a HP ze 4400 laptop. I love the OS I've installed it on 2 other desktops and it works great. However, the wireless card on my laptop (a WPC11) does not work. Not only does it not work but it freezes the entire system whenever it is inserted. I've tried everthing I can think of. I've used NDISwrapper, alien command for install of non debian drivers I even tried to get a copy of the kernal source to make a custom kernal. I found that I don't know near enough to do that currently with linux. Nothing I've done has worked. I need help this is driving me crazy....I'm up for suggestions.[/QUOTE]


I could not get my wpc11 ver 4 working either.  Had problems with ndis wrapper too.  You are not alone

---

### Post by clearzen on 2006-10-22
Just to let anyone know I found a solution to this problem. I removed the execute privilges for pcmciautil in /etc/init.d/  
It would seem that the drivers where already loaded in the kernel and it was conflicting with those drivers and causing the laptop to  hang. So if you have this problem the command for a quick fix would be sudo chmod -x /etc/init.d/pcmciautils . I also excluded every irq except 11 in the pcmcia.opts file. But I think that is irrelevant.

---

### Post by NotTheCommonDose on 2008-01-09
Hey, I fixed this problem. My laptop would freeze whenever I used the WPC11. ver4. The caps lock would blink and I would have to restart. However, if you go here;
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=26&PFid=5&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true)

install the 98 version with ndiswrapper or system>administrator>windows wireless drivers and you should be a-ok!
I hope this works!

---

