---
title: "[SOLVED] How to tell Ubuntu to set system clock to local time?"
date: 2008-08-21
forum: General Help
---

### Post by nuschii on 2008-08-21
Hi @all,

I have a multiboot installation of WinXP Pro and Ubuntu 8.04. Ubuntu doesn't know about WinXP - and never did - because the Windows partitions are encrypted.

My timezone is Berlin (GMT +1h, i. e. GMT +2h w/ daylight saving). When Ubuntu synchronizes the system time over Internet - or when I set the system time myself - it sets my BIOS clock to GMT, but WinXP takes the system time for local time. So the system time in Windows differs from that in Ubuntu by two hours unless the time is resynched by NTP.

Is there any possible setting that tells Ubuntu to set the BIOS clock to local time instead of GMT?

Thanks in advance.

---

### Post by kerry_s on 2008-08-21
have you tried right clicking the clock> preferences, check or uncheck utc

---

### Post by nuschii on 2008-08-21
Well, that's exactly the problem. In the date/time preferences I can't find any checkbox regarding UTC. I assume this is because Ubuntu thinks that there are no other OS installed.

Is there any way to adjust time settings manually (by editing some files in /etc...) ?

---

### Post by kerry_s on 2008-08-21
> **nuschii said:**
> Well, that's exactly the problem. In the date/time preferences I can't find any checkbox regarding UTC. I assume this is because Ubuntu thinks that there are no other OS installed.

Is there any way to adjust time settings manually (by editing some files in /etc...) ?

not the date & time, the icon. see pics

---

### Post by nuschii on 2008-08-23
Hm. By clicking on "preferences" ("Einstellungen" in german), I get to see another dialog than that in your screenshot. Unfortunately, the forum image upload doesn't seem to be working. The dialog offers the options "12h / 24h format", "show date", "show seconds", "show weather" and "show temperature". There is however a button "time preferences", which leads to the "date/time" dialog mentioned in my second post.

But I got rid of my problem in another way. In /etc/default/rcS there is a line "UTC=yes/no". Switched it to "no" and everything seems to work fine. :)

Thanks for your help anyway.

---

### Post by scottro on 2009-01-11
Just a quick thanks for this post, several months later.  :)

(I don't see the thank you icon, has that changed?  I haven't frequented these forums in awhile)

---

### Post by aspora.isernia on 2009-04-01
Sorry,
I have the same problem: after the Daylight saving time change, my Ubuntu has a wrong clock (one hour of drift). Even after resync via server, it is one hour in the future (now it's 12.24 but it shows 13.24). Nevertheless, in /etc/default/rcS UTC is set to 'no' and Vista has the correct time.
Any hint?
Thanks!!
a.i :D

---

### Post by mjancola on 2009-06-24
Yeah, I have the same problem with Mythbuntu 9.04 and the other suggestions don't seem to work.   First off, my clock doesn't have a checkbox for UTC/NOT.   I changed the setting in rcS but the time is still being adjusted.  I guess I have to be a good Linux user and just change the BIOS clock?  Other suggestions appreciated.

---

