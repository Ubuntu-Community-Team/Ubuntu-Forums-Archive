---
title: "Intrepid Automatic Updates"
date: 2009-04-19
forum: Installation &amp; Upgrades
---

### Post by phyre-x on 2009-04-19
Its been a while now and its bugging me. Running ubuntu 8.10 but it never checks for updates automatically even though its set in the software sources dialog under administration menu. Any thoughts on what could be causing this ? I'm getting bored of doing a apt-get update all the time. Not too keen on adding a manual cron job either, just want to fix whatever used to be there :(

Thanks!

---

### Post by cariboo on 2009-04-19
I haven't notice a lot of updates lately, I think there was an update to tzdata a couple of days ago.

Jim

---

### Post by phyre-x on 2009-04-21
I've got frequent updates for a range of packages most days but i have to trigger the update of the package list manually

```
sudo apt-get update
```

If I don't after a week I get a notification saying the package list is out of date and recommends updating.

It's a case of something failing, somewhere but I just don't know what or where since the option is selected in the software sources dialog.

Thanks for the contribution :)

---

### Post by stilling on 2009-04-21
> **phyre-x said:**
> Its been a while now and its bugging me. Running ubuntu 8.10 but it never checks for updates automatically even though its set in the software sources dialog under administration menu. Any thoughts on what could be causing this ? I'm getting bored of doing a apt-get update all the time. Not too keen on adding a manual cron job either, just want to fix whatever used to be there :(

Thanks!

you can try this for you and never have a problem again system -> Administration -> update manager -> settings in the left down corner -> updates tab and in the lower part of that tab whare automatic updates is 
check for updates daily and select install security updates without confimation. 

i hope this will help you ... if not sorry

---

