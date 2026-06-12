---
title: "Hard disk &quot;stop&quot; and a noticable overheat"
date: 2011-10-17
forum: Hardware
---

### Post by dwigyit on 2011-10-17
I don't know if these two problems are related, but I thought it best to put them in the same thread just in case they were.

I have Ubuntu 11.10 on a Dell Inspiron and it can sometimes run quite hot. That's the first problem. The second and most significant one is that since a few days ago I've started to get problems whereby the HDD seems to just stop working. Most running programs will freeze and Ubuntu will darken them, and anything which involves opening another program or a dialogue or anything which would have to load from the disk just doesn't work. Rebooting fixes it fine, but it's a bit of an inconvenience and not really a true solution :D

This actually all started when I plugged in an external HDD which has now died (since being plugged in, actually, but it's been under pretty heavy load so I'd be surprised if Ubuntu killed it). I doubt that's connected either - but still worth mentioning I guess ;)

Any help would be appreciated very much

---

### Post by 2F4U on 2011-10-17
What are the hardware specs of that machine? Overheating problems are sometimes caused by dust inside the case that blocks airflow or the fans. Another reason may be the graphics card. Open source drivers often lack power management features equivalent to proprietary drivers.
I have no idea about the hdd. Maybe there are bad sectors which can make things slow.

---

### Post by dwigyit on 2011-10-17
Well the laptop has an i5 processor and integrated intel graphics, that's all I know. I'm sure there's a way to get Ubuntu to list hardware though? Also the problem doesn't happen on Windows so it's not a problem with the hardware itself.

Also, I've realized that every freeze has happened whilst there's been either a long copy process going on or when Banshee's been adding my 4000+ tracks to its music library. I tried the latter just now and it started off racing through them then started to slow down at about 1000, taking my whole system with it. It was noticeable when, say, opening a new tab in firefox; it took a few seconds for the little new tab animation and for the tab to load. Then the whole system froze a few minutes later and I had to reboot :D Now that I think about it, I'm not sure if it's even the hard drive that's at fault - could just be the way Ubuntu handles those sorts of tasks that causes some sort of freeze maybe???

---

### Post by smurphy_it on 2011-10-17
Could be a number of things.  Perhaps you can supply the model of your laptop so specs can be gathered.  Also, you could post the contents of the /var/log/syslog file (Preferrably for 1 day only).

In a terminal, run the following commands.

```
export today=$(date +'%h %d')
sudo grep $today /var/log/syslog
```

---

### Post by dwigyit on 2011-10-17
I've attatched the log straight from /var/log because the one outputted by your terminal command only went back by about a quarter of an hour. This one goes back about two hours so covers the crashes :)

---

### Post by dwigyit on 2011-10-17
Something else interesting has just happened - whilst uninstalling something with Synaptic and typing into the dash, the system froze again but then recovered about about ten seconds and it just did it again as I was typing this post. It's odd how the mouse works fine but it just wont click - the keyboard doesn't work though.

---

### Post by dwigyit on 2011-10-17
Sorry to triple post but it turns out it was a genuine hard drive failure - I rebooted it just now and got a SMART warning from the BIOS about how I should backup now :)

Funny thing is that I also installed 11.10 on the external hard drive which began to show symptoms of failure shortly afterwards. Whilst I appreciate that external HDDs are not designed for this sort of thing, it may suggest that there's something terribly wrong with this version of Ubuntu if it's broken both the HDDs it's been on?

Posted from my iPod :D

---

### Post by smurphy_it on 2011-10-17
> it may suggest that there's something terribly wrong with this version of Ubuntu if it's broken both the HDDs it's been on?

Well isn't that a hoot.  I've heard this a few times over in the Linux world (over the last couple of years), yet I never heard that mentioned before when Microsoft released a new version of the Operating System !

No ill intent towards poster, just an observation over time with Linux vs. Microsoft is all.

---

### Post by dwigyit on 2011-10-17
Perhaps what I should have said is something wrong with the way it works on this particular laptop, as both drives broke within just a few days of each other and both had been booting Ubuntu 11.10 since very recently...

I appreciate that it's next to impossible for it to be Ubuntu's fault - but its still an interesting coincidence :D

---

