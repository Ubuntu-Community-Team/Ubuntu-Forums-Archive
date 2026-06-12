---
title: "T-Mobile GC89 broadband card--no solution??"
date: 2007-01-22
forum: Hardware &amp; Laptops
---

### Post by jerrynewt on 2007-01-22
Been trying for about two weeks now to locate driver for T-Mobile broadband pci card. I have a Toshiba 6100 Satellite Pro--768 RAM--40 Gig hd--Pentium D processor (dual boot with Ubuntu 6.06.1 and Windoz XP). When I am on the road (I am a truck driver). I use XP and the card works just fine but I am trying like the dickens to get away from M$, but can't find any drivers (nothing in ndiswrapper list either) that are compatible with linux. Seeing as how this is a laptop forum, I thought maybe someone here had run across the same problem. Thanks for the input in advance.

---

### Post by jerrynewt on 2007-01-22
**Bump**](*,)

---

### Post by aws910 on 2007-12-14
This page made mine work within minutes:

[http://erikstambaugh.com/gprshowto.html](http://erikstambaugh.com/gprshowto.html)

At first it didn't work, but when I changed internet2.voicestream.com to wap.voicestream.com it worked like a charm.  Using it to post this.  PM me if you need more help.

If I had known it would work in linux(and so easily), I would have tried it earlier.  Being that my sound card took me 4 months to get working, I thought that only a brain-surgeon would be able to get the GC89 working.

---

### Post by linxuser14 on 2008-04-16
I originally couldn't get kppp to access gc89 till I set the modem speed to 57600. Otherwise it communicated jiberish to gc89 and no response. Then it did ATZ to gc89 with response of ERROR. After reading Squinky's how to I copy/pasted his /etc/ppp/peers/tmobile , gc89chat files it was 3 files. Ran pppd call tmobile and it didn't connect. But after that kppp can communicate with gc89. Setting dialing # to *99***1# enabled it to connect. Then...

        -next is copy/paste from my kate-

In /etc/ppp/options I commented out lcp-echo-failure 4 and removed the comment-out (#) from the line -vj (something about jacobson compression) I think it disabled it but I did (#lcp-echo-failure 4) to disable it I think. Anyway kppp no longer hangs up and reconnects every 2 minutes. there was a line saying lcp-echo-interval 30 that I left unchanged. i guess that explains the 2 minute hang up/reconnect time. Anyway it works fine. Just speed is maybe not at optimal. speedtest shows 40 kb/s using LAX and Mpls,Mn servers. 50 kb/s doing Scottsdale.AZ server. But it works. Anyone know specifically what files contain settings I've stumbled on that make it work, request and I'll be glad to post em. I'm not sure if my other problem where kppp couldn't communicate with gc89 till after I do a pppd call tmobile is still an issue till I halt and try again another day. But yeah! Internet in kubuntu. p.s. I'm running 6.06 I think.

---

### Post by linxuser14 on 2008-04-16
> **jerrynewt said:**
> Been trying for about two weeks now to locate driver for T-Mobile broadband pci card. I have a Toshiba 6100 Satellite Pro--768 RAM--40 Gig hd--Pentium D processor (dual boot with Ubuntu 6.06.1 and Windoz XP). When I am on the road (I am a truck driver). I use XP and the card works just fine but I am trying like the dickens to get away from M$, but can't find any drivers (nothing in ndiswrapper list either) that are compatible with linux. Seeing as how this is a laptop forum, I thought maybe someone here had run across the same problem. Thanks for the input in advance.
See my posts in  	
T-Mobile Sony-Ericsson GC89 
something may help.

---

