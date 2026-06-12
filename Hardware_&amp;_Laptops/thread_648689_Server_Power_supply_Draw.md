---
title: "Server Power supply Draw"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by briansvgs on 2007-12-23
A little while ago I took a desktop computer that I had lying around and turned it into a server, which I leave on all the time. This server doesn't get that much traffic, and isn't used for anything but a server, so it doesn't normally have a very high load on it. I know that parts like RAM and CPU draw different amounts of power based on their load. I was wondering if the hard drive and psu do this too so that I am not drawing all 300 or so watts that my power supply is rated for all the time. Does anyone know the answer to this?

-Brian

---

### Post by Dngrsone on 2007-12-23
The good news is, your PSU is not drawing a full 300 watts.

If your server machine is of relatively recent vintage (P4 or better), then you might consider having it [fold](http://folding.stanford.edu/) for you when it is idling.

---

### Post by briansvgs on 2007-12-24
Okay, thank you....the processor is an athlon 64 3000+, so I might end up tryijng the folding at home thing. I tried installing it, but it said that the file could not be found when I tried to execute it, so I will play around with it some more later.

---

### Post by tgalati4 on 2007-12-24
Your computer probably draws 90 watts continuously, so after a year of 24/7 operation with electricity costs of 11 cents per kilowatthour you are looking at:

8,760 hours * 90 watts/1000*0.11= $86.72 per year in electricity costs.

Walmart Green Everex computer uses ~20 watts, at $200 computer cost/investment your electricity cost would be $19.27 per year.  The difference ($67.45) will pay for the green computer in 3 years.  

Alternatively, you can set a cron job to shut your server down late at night and have the BIOS wake it up in the morning.  That would save you ~$29/year.

---

### Post by w5cgu on 2008-01-02
Very well done and very good ideas.

One thing to remember also is that if you use SCSI drives, they use more power than
the IDE drives.  Using a 'drive down' routine will also save you money.  You can down the
drive after say, 10 minutes of non-use.

Good luck,  John

---

### Post by w5cgu on 2008-01-02
:confused:

Can someone point me in the direction of a good, quick, right-up for Samba.

I sure would like to get it running.  I am retired from Sun Microsystems and am
still learning Linux but do enjoy it very much.

Also, is there any Amateur Radio operators out there with a good site or two that 
has Amateur software for Linux?

Thanks in advance,  John

---

### Post by briansvgs on 2008-01-02
Thank you all for the advice on power draw. As far as the gpc is concerned, I usually build my own computers. I have thought about building a gpc but don't know what it uses for a power supply. Does anyone know what power supply it uses, or where I can find some low wattage power supplies like it? 

Thanks,
Brian

---

### Post by Yellow Pasque on 2008-01-02
For this type of deal, I would consider looking at SPCR. Some people there have built some   low-wattage stuff, even low enough to run a whole system off the picoPSU (PSU on a little circuit borad) and a 12V power brick.

---

