---
title: "Evolution calendar displays wrong current time"
date: 2008-10-21
forum: General Help
---

### Post by enryfox on 2008-10-21
Hi all,

ubuntu 8.04 with Evolution 2.22.3.1. In calendar view, the red line showing current time, is one hour late compared to actual time: e.g now my clock says 15.47, evolution says it is 14.47. 

My system clock is set to Europe/Rome (GMT +2) and Evolution clock is set to the same time zone with daylight saving option checked. I tried unchecking this latter option, but nothing changed. Why the hell is evolution one hour late ?? Can't it simply pick up system clock time ???

console output is
:~$ date
Tue Oct 21 15:28:46 CEST 2008
:~$ date -u
Tue Oct 21 13:28:51 UTC 2008


Can anybody help to fix this issue ?
thanks
bye

---

### Post by bcom on 2008-10-21
I have no idea if this will help at all.  Here is what I found in re setting the date and time.

Linux provides a system date and time; the computer hardware provides a hardware clock-based time.  It is possible for for the two times to drift apart.

To display, set, adjust or synchronize hardware and system clocks you can use the hwclock utility.

To see hardware date and time: sudo hwclock --show
To set hardware clock manually: sudo hwclock -- set --date "10/21/08 11:12:00"

To set the system time from the hardware clock: sudo hwclock --hctosys

To set the hardware clock from the system time: sudo hwclock --systohc

Also, you can set system time and date by typing gksudo time-admin & in Terminal.

---

### Post by enryfox on 2008-10-21
Hi thanks for your reply!

I had already thought about a wrong BIOS clock settings, but it turned out to be perfectly in sync with system time:

:~$ sudo hwclock --show
2008-10-21T17:20:17 CEST  -0.002656 seconds
:~$ date
Tue Oct 21 17:20:18 CEST 2008

It is just evolution thinking it is an hour late ...

bye

---

### Post by ananaza on 2008-10-21
I just noticed that I have the same problem. The red line is at the wrong hour. Funny I haven't seen this earlier - maybe it is a regression in some version of evolution?

```
anmietti@ursula:~$ dpkg-query -W|grep evolution
evolution       2.22.3.1-0ubuntu1
evolution-common        2.22.3.1-0ubuntu1
evolution-data-server   2.22.3-0ubuntu2
evolution-data-server-common    2.22.3-0ubuntu2
evolution-data-server-dev       2.22.3-0ubuntu2
evolution-dev   2.22.3.1-0ubuntu1
evolution-exchange      2.22.3-0ubuntu2
evolution-plugins       2.22.3.1-0ubuntu1
evolution-webcal        2.21.92-0ubuntu1
opensync-plugin-evolution       0.22-2ubuntu1

```

---

### Post by bcom on 2008-10-21
Here's another thought: tzdata is the package responsible for updating the time.  What if you were to got to Synaptic Package Manager and reload the package to make sure you have the latest one.

I think I recall that package being updated recently.

---

### Post by quayal on 2008-10-21
Hiya,

I'm experiencing the same problem. I checked timezone data using zdump and everything seems to be in order there.

```
Europe/Warsaw  Sun Mar 30 00:59:59 2008 UTC = Sun Mar 30 01:59:59 2008 CET isdst=0 gmtoff=3600
Europe/Warsaw  Sun Mar 30 01:00:00 2008 UTC = Sun Mar 30 03:00:00 2008 CEST isdst=1 gmtoff=7200
Europe/Warsaw  Sun Oct 26 00:59:59 2008 UTC = Sun Oct 26 02:59:59 2008 CEST isdst=1 gmtoff=7200
Europe/Warsaw  Sun Oct 26 01:00:00 2008 UTC = Sun Oct 26 02:00:00 2008 CET isdst=0 gmtoff=3600
```

bcom mentioned something about the tzdata package being updated recently; I remember updating my system with it. Maybe that messed things up?

Have you experienced anything similar?

I'm using Evolution 2.22.3.1

---

### Post by enryfox on 2008-10-21
Hi,

ubuntu is updated with all latest packages, but i will check again.

Anyway it is not a big issue to have the red line at the wrong hour, calendar displays all my meeting at the correct hour, but remainders pop-up one hour later ...

thanks

---

### Post by plopp37 on 2008-10-22
I am having the same problem with Evolution calendar, it is one hour late. It started to suck on the weekend, but I can not remember what updates have I installed that could have messed things up. I am using Europe/Prague summer time, everything is set up as it should be, just the Evolution calendar sucks! In Evolution calendar preferences, there is an option, which translation to Czech is something like "make up for summer time"; I think this option shoud shift the time one hour up or down, but it has no effect and the Evolution calendar clock is damn wrong all the time.

---

### Post by pbiglr on 2008-10-22
I have the same problem. It was not wrong before, and have changed nothing. It is october 2008 now and I notice that all the postings about this problem are in months May or April and October or November. Can it be that evolution interprets the Daylight Saving Time in the wrong way?
I have the time synchronized with a public time server. When I set it to manual and change the date (only date not time) to 1 month earlier, the evolution time indication is correct again! 
Can someone tell me where to find the DST definitions for evolution?

---

### Post by quayal on 2008-10-22
hi,

I read somewhere that somebody had a similar problem with Europe/Brussels timezone, it changed to DST one week to early. Maybe we just need to wait one week and it'll go back to normal. I don't know where Evo takes the tzone info from; I suppose it's from the system. I checked what's there using ```
 sudo zdump -v Europe/Warsaw | grep 2008 
```and everything is OK there.

pbiglr said: > It is october 2008 now and I notice that all the postings about this problem are in months May or April and October or November. 

As far as I can see, all postings in this thread are only a few days old, so it might be an issue with changing to DST one week to early.

---

### Post by pbiglr on 2008-10-22
Evo has its own dialog to set the timezone. Edit -> Preferences -> Calendar and Tasks -> Time. When I open the dialog at "Time Zone" it shows a world map. When moving the mouse over Europe/Amsterdam it shows "UTC +01.00". That is wrong, because we still have DST at this location today ( 22 oct 2008 ). Its should show "UTC +02:00". 
The system time however is correct. So it seems that Evo uses its own timezone info

We could just wait and, very likely, the error will disappear next week when DST in Europe/Amsterdam will be over. But, someone will start this discussion again next year.

---

### Post by pellito76 on 2008-10-23
Hi!
My evolution calendar is displaying the correct time , but my appointments are one hour early ... :-(
The appointments are "originating" from an MS Exchange system, which might the real issue :-D  The appointments look "OK" in Outlook
Thx for any ideas

---

### Post by quayal on 2008-10-23
AFAIK this has been reported as a bug on launchpad. so we might hope it won't reappear in the Spring.

---

### Post by dcstar on 2008-10-25
> **pbiglr said:**
> Evo has its own dialog to set the timezone. Edit -> Preferences -> Calendar and Tasks -> Time.
........

It also has a checkbox saying "Adjust for daylight saving time", so what have you set that to?

---

### Post by quayal on 2008-10-26
Checking/unchecking daylight saving time doesn't do much. I've read somewhere that it doesn't work anymore, supposedly Evo knows better when to change to DST :)

As it's the end of DST in Poland today (26 Oct), Evolution's current time is back to normal. Let's wait and see what happens in March. Maybe they'll fix it by then.

What's your situation? Is it OK now?

---

### Post by Theseusiv on 2008-10-27
In Prague is situation fixed too ;)

---

### Post by infoseeker on 2008-11-02
I have a problem with the current TIME displayed.  My PC clock time was set correctly in the CMOS time setting, but when I boot into Ubuntu 8.10 my time is 2 hours ahead of local time.  I checked the timezone settings (GMT +2) and that is set correctly.

I booted back into Ubuntu 8.04 and the clock is correct (same PC).

Any help?

---

