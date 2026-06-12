---
title: "me-tv and pinnacle 800i"
date: 2008-07-03
forum: Hardware
---

### Post by jmore9 on 2008-07-03
This what i have tried to get this card working.

I followed the instructions on linuxtv.org.  I installed the firmware , then i did the make and make install of the v4l-dvb file.

After i rebooted i did the lsmod and all the tv stuff that was there before was gone.  So i only did the make part and then rebooted and the modules were back !

Then i installed the repositories for me-tv and installed me-tv.

I started me-tv and it asked if i wanted it it make a channels.conf ?  I said yes and it started scanning.  It found 11 stations .  Then it saved the channels.conf and started the me-tv viewing app.  I got the following error/s at that time.

Me TV-Message: Exception message: 'Failed to evaluate XPath expression: '/epg/channel[@name="WGVU-HD\u0008\u0010"]/event''
Me TV-Message: 07/03/2008 01:03:03 - Exception in static gboolean Application::on_timer(void*): Failed to evaluate XPath expression: '/epg/channel[@name="WGVU-HD\u0008\u0010"]/event'
Me TV-Message: 07/03/2008 01:03:07 - Purging remaining EPG events
Me TV-Message: 07/03/2008 01:03:07 - EPG events purged
Me TV-Message: 07/03/2008 01:03:07 - Terminating application normally

XPath error : Invalid expression
/epg/channel[@name="WGVU-H"]/event

And this is where i am a the moment.  If anyone has any ideas my ears and eyes are open.

---

### Post by jmore9 on 2008-07-03
AH-HA

I copied the channels.conf that me-tv made and it had some strange box characters between the channel name and the numbers.  I deleted the strange box characters and started me-tv and I HAD HDTV !!

My channels.conf looks like this :

WGVU-HD:201028615:8VSB:49:52:3
WGVU-SD:201028615:8VSB:65:68:4
WGVUSD2:201028615:8VSB:81:84:5
WGVUSD3:201028615:8VSB:97:0:6
[0009]:201028615:8VSB:0:0:9
[000a]:201028615:8VSB:0:0:10
FOX 17-DT1, West Michigan's Digital FOX!:503028615:8VSB:49:52:3
My ABC is WOTV4:509028615:8VSB:49:52:3
WXSP My Netwoerk TV:509028615:8VSB:65:68:4
WTLJ Digital Television:533028615:8VSB:49:52:3
WZZM-DT:623028615:8VSB:49:52:1
24/7 WX:623028615:8VSB:65:68:2
WLLA-DT:659028615:8VSB:49:52:3
WLLA-D2:659028615:8VSB:65:68:4

All the above channels come in just like in windows and the sound is perfect so far.  As i said in the previous post The modules disappeared after i did the make and make install.  they reappeared when i only did the make.  I hope i don't have to do that every time i start ubuntu !  Time will tell.

---

### Post by jmore9 on 2008-07-03
OK I did a cold restart of ubuntu 8.04 and did nothing to the pinnacle card install and just started up me-tv and it worked just as before so i guess the problem of HDTV in linus with a pinnacle 800i is solved.

---

