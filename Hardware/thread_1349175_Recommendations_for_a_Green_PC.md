---
title: "Recommendations for a Green PC"
date: 2009-12-08
forum: Hardware
---

### Post by Cue2 on 2009-12-08
I have a low watt synology NAS device which they recently dropped support for, so now I'm looking to replace it with a low watt ubuntu box. The only real criteria I have so far are

1) Low power consumption
2) gigabit ethernet
3) Sata HDD

I'm trying to kill as many birds with one stone as possible, so to speak. I'd like to use this as a NAS device, perhaps a capable server to ssh some X11 apps, and maybe even a HTPC.
I'm currently leaning towards an ION 330HT-BD but have no idea what its power consumption is like when idle. Do people have any other hardware recommendations?

Not sure if this is the right section to post this discussion.

---

### Post by MyR on 2009-12-08
I'm no expert.

If low power is your goal, then you should look at the processor. Pentium M and Atom processors consume minimal power.
A "headless" system eliminates the power needed to run a display; you probably knew that already.
Keeping the system cool by removing the case or otherwise cooling the environment helps reduce the fan power.
Remove unneeded CD drives, wireless cards, audio cards, etc.
RAM doesn't use much power but still a little, so less is more.

Beyond that you have your software to deal with like disk spin down when idle.

hope this helps

---

### Post by pollcolingwood on 2009-12-08
[SIZE=2]Hi All,

I have a query. Being a newbie, I am not sure if this is the right section to post this discussion. My query is:[/SIZE]

  	 	 	 	 	 	  [SIZE=2][B]I am buying a QNAP NAS to act as a storage medium for my home theatre.

I am using Plex on a 2009 Mac Mini which currently accesses my data from a FireWire connected Drobo.

I will be selling the Drobo, buying the QNAP NAS and configuring the hard drives as RAID 5.

My question is what format do the I need to setup the hard drives as so I can access the data from OS X via an SMB, AFP share.[/B][/SIZE]
 
[SIZE=2]Any help would be highly appreciated.[/SIZE]

---

### Post by sliketymo on 2009-12-08
> **pollcolingwood said:**
> [SIZE=2]Hi All,

I have a query. Being a newbie, I am not sure if this is the right section to post this discussion. My query is:[/SIZE]

                                 [SIZE=2][B]I am buying a QNAP NAS to act as a storage medium for my home theatre.

I am using Plex on a 2009 Mac Mini which currently accesses my data from a FireWire connected Drobo.

I will be selling the Drobo, buying the QNAP NAS and configuring the hard drives as RAID 5.

My question is what format do the I need to setup the hard drives as so I can access the data from OS X via an SMB, AFP share.[/B][/SIZE]
 
[SIZE=2]Any help would be highly appreciated.[/SIZE]

Might be a good idea to start a new thread.Also see :

[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by Yellow Pasque on 2009-12-08
SPCR's a good site for low-power/noise computing advice. For example: [http://www.silentpcreview.com/forums/viewtopic.php?t=54314](http://www.silentpcreview.com/forums/viewtopic.php?t=54314)

---

### Post by Cue2 on 2009-12-08
Thanks for the tips. The ION 330 is atom based so that is a tick in the checklist there MyR. as for the software side, I kinda hoped the energy star rating and ubuntu would sort that out for me, without any real input from my side. if I see it's too power hungry I'll probably just end up using WOL.

For anybody interested, I've read from the site Temüjin provided (thanks Temüjin) that most via or atom based mini-itx boards are low power, and to avoid celeron based boards. I also looked into the ION 330s power comsumption and it's apparently only 45watts (not idle) which isn't quite as low as the synology NAS at 23watt but for what it has It's still very green.


thanks sliketymo for clearing that up and sorry i couldn't help you with your problem pollcolingwood but I hope you found your solution.

---

