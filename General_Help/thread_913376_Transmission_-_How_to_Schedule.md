---
title: "Transmission - How to Schedule?"
date: 2008-09-07
forum: General Help
---

### Post by mkartic on 2008-09-07
hey guys, am using a certain net connection that's got unlimited usage in the night only. So i'd like to schedule Transmission to do just that. But i dont know how its done! any ideas??


thanks!

---

### Post by Ve5ahchoo8ah on 2010-08-14
I have same problem!
it seems that this program doesn't do the basic things!
i also used Deluge and it had other problems!
I missed BitTorrent!:(

---

### Post by Vaphell on 2010-08-14
what problems did you get with deluge?

---

### Post by Ve5ahchoo8ah on 2010-08-14
the main problem is about scheduling! i set the time but when i wake up at the morning i see they are all on pause! the next night it works but very slowly and seems to have problem with firewall! next night i see some of them have resumed but some of them are still paused! o don't know why this program act like this!
I guessed that Transmission is a better program as everyone use it! but really it doesn't have any option for scheduling??!!:confused:

---

### Post by colin.p on 2010-08-14
I have transmission set to use "speed limits". I have the upload/download speed set to "0" from 9am to 11:45pm. Then from 11:46-8:59, it downloads.
Works perfectly.

I just noticed the original post is from 2008. I hope the poor guy figured it out by now.

---

### Post by Ve5ahchoo8ah on 2010-08-14
just to check if I understand you right
you mean because i want to download just from 1am to 6am (at nights) I should set download limit to 0 and set schedule time to "6:15am to 12:45am" ?!
you mean it works on the opposite way?

---

### Post by colin.p on 2010-08-14
That's correct. A weird way of doing things, but it works.

---

### Post by prroots on 2010-08-20
I have a similar requirement. Transmission allows you to set a start and end time with temporary speed. I use Hughesnet which gives me unlimited downloads between 2-7AM EST. I would like to set Transmission to 0 speed from 0700 to 0200, but not sure if the second time can be smaller than the first (ie, on different days). Can anyone help? Thanks
Pete

---

### Post by rubylaser on 2010-08-20
For different times / days, you could just create entries in your crontab to start / stop the transmission-deamon at certain times.

```
00 02 * * MON service transmission-daemon start
00 07 * * MON service transmission-daemon stop
00 03 * * TUE service transmission-daemon start
00 07 * * TUE service transmission-daemon stop
```

etc...

---

### Post by greenarrow-stef on 2010-10-23
My solution to this is this Python script:
[http://gist.github.com/642874](http://gist.github.com/642874)
[FONT=Verdana]
[/FONT][FONT=Verdana]1. Make sure you have installed transmission-remote[/FONT]
[FONT=Verdana]2. Enable web client in Transmission (allow only for 127.0.0.1, do not use authentication)[/FONT]

[FONT=Verdana]I use it with cron myself to start[/FONT][FONT=Verdana] all torrents at 2:30am every night and stop them at 8am.[/FONT] 
```

30 2 * * *    path_to_script/torrentcontrol start
0  8 * * *    path_to_script/torrentcontrol stop
```

---

### Post by nikefalcon on 2011-04-21
> **colin.p said:**
> I have transmission set to use "speed limits". I have the upload/download speed set to "0" from 9am to 11:45pm. Then from 11:46-8:59, it downloads.
Works perfectly.

In addition to that your could also schedule it to connect at a specific time.
I wrote a shell script with a simple graphical user interface to help with that. Check it out at [https://launchpad.net/autoconnect](https://launchpad.net/autoconnect)
Regards

---

