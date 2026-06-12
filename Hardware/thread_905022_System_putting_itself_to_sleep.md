---
title: "System putting itself to sleep"
date: 2008-08-29
forum: Hardware
---

### Post by malocite on 2008-08-29
I am running Mythbuntu 8.04.1 on a new box that I am using as a frontend with a remote backend.  I have three other machines running relatively problem free but this one is a real thorn in my side. 

Basically the machine appears to be putting itself to sleep.  The screen goes black, and the keyboard and mouse die, but the fans stay running.  I can only bring it back up by holding in the power button, shutting it off and turning it back on again.  

I am fairly sure it is going into some sort of suspend or hibernate mode because when the system goes to boot up again the boot process appears to be different than a normal coold boot.  

I looked for everything I could to disable acpi and the like but have still not been able to figure out where its coming from.  

Looking at syslog the last thing that seems to run is an ntp time syncronisation, or a cron job of myth status update...

Does anyone have any ideas?

--malocite

---

### Post by Loaded.len on 2008-08-29
Mmmm, I know you said "new box" but your symptoms really sound like a Dell GX series desktop with bad capacitors.

---

### Post by ercferret18 on 2008-08-29
you could try pressing control+alt+delete or something, and does the monitor turn off or just go blank?

---

### Post by malocite on 2008-08-29
Well, it's new to me :)  It is a small form factor HP that I .... found :)  literally.  I was thinking it could be hardware related for the longest time, but what I forgot to mention was that the system only seems to be putting itself to sleep when playing a video in mythvideo.  And it does it after about 10 minutes or less.

However - I have since disabled three new services, Scheduler (I think that something to do with cron) and the ntp time sync.  Since doing so I have been watching a 41 minute episode of the office and its been fine.

BTW, great news, as I wrote that very friggen line, my screen went black and the problem ocurred again.  It is 11:17 pm... grrrr.

I CAN leave the system totally idle... and have done so for up to 36 hours without the problem happening, it only happens when I am doing something like watching a video...  This has happened with the mythtv internal player and with mplayer.

The video is a divx file if that makes any difference.

---

### Post by Loaded.len on 2008-08-29
I seem to remember having a similar problem when i first installed mythbuntu 8.04.  I noticed it primarily when using emulators, but my kids were complaining that it was going to sleep all the time.

```
chmod a-x /usr/bin/gnome-screensaver
```

did the trick for me.  I'm not sure if your problem is actually caused by the screensaver, but it's worth a try.

---

