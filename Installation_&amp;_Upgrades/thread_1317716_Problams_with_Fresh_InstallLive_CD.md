---
title: "Problams with Fresh Install/Live CD"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by jfinner1 on 2009-11-07
I've been using Ubuntu for a few years now, without many problems. But after the upgrade to Karmic, my computer has been crashing, continuously. So I've decided to go back to Jaunty, since I didn't have any problems with that version. I know that you can't downgrade, so I've backed up all my files to my external HD, burned a Jaunty install disc, and prepared myself for a fresh install. But I keep erroring out during the load of the disc. I checked the disc's integrity, and it came back fine. But when I attempt to run as a live CD, I get a full page of errors that scroll very quickly, then disappear to a blank screen. I eventually have to hard shut down my computer. The only part of the error message I've been able to read is something about SQUASH. I've also tried running the disc as a Live CD on another computer, and had no problems. So it's not the disc, but I don't know what could possibly be wrong with the computer, since it obviously had no problems with Jaunty last week. Also, about 2-3 months ago I wiped out my XP partition and did a fresh Jaunty install on the entire hard drive, with no errors. Can anyone give me any advice on what could be going wrong? Karmic really hates me, and I really want to switch back to Jaunty...

---

### Post by Umang on 2009-11-07
Hi,
I upgraded to Karmic too, and had [many many problems]("http://ubuntuforums.org/showthread.php?t=1312649"). A fresh install of Karmic over the current installation fixed everything.

Although, I don't know what is happening in your case, since it's the Jaunty CD you are talking of.

---

### Post by jfinner1 on 2009-11-07
Ok, I found this: [https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors) which may be the same issue I'm having. I ran the memory test, no errors. I checked the disc, no errors. As far as I know, there is nothing wrong with my dvd drive. I don't know what a data cable is. I would like to try the workaround, but I'm not sure what it's telling me to do. Can anyone explain it better for me?

---

### Post by dhavalbbhatt on 2009-11-07
> **jfinner1 said:**
> Ok, I found this: [https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors) which may be the same issue I'm having. I ran the memory test, no errors. I checked the disc, no errors. As far as I know, there is nothing wrong with my dvd drive. I don't know what a data cable is. I would like to try the workaround, but I'm not sure what it's telling me to do. Can anyone explain it better for me?
It seems like your HDD is having some bad sectors. What they are suggesting on the link that you've posted, is try to install with acpi=off. What happens when you put the CD in your DVD drive - do you see the initial welcome screen, from where you can select whether you want to install the OS, or run as LiveCD? If you can get to that screen, then at the very bottom there should be an options menu, I think that is where you can either turn acpi on or off. If not that, then try the other menus at the very bottom on the page. Hope that can help. 

What I would also suggest you do is, try installing using an alternate CD - it won't have a GUI, but it will do the job just fine. I would also suggest you try installing Karmic.

---

### Post by jfinner1 on 2009-11-07
Yes, I can get to the screen that asks me if I want to Install, Run as Live, Check Disc, etc. I'll go check that out now, see if I can get to the options and such. If that doesn't work I'll have to look at an alternate install. Thanks!

---

### Post by Jaziek on 2009-11-07
I'm getting this exact same problem at the moment. I'm going to assume it is because my hard drive is bad, but since it was running windows XP an hour or so previous to the install attempt I know the HDD itself works. My ram is fine, I've tested it, and according to the disc integrity check there are no errors on the disc.
Infuriating to say the least.

---

