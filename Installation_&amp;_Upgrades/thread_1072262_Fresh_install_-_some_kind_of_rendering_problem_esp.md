---
title: "Fresh install - some kind of rendering problem especially with fonts"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by scoober on 2009-02-17
Hi 

I just did a fresh install of intrepid from a live cd.  My screenshot is (hopefully) linked below.  The fonts are all fuzzy and I think some other elements of the desktop aren't rendered properly either.  ANy idea what is going on?

So far I have enabled the nvidia driver, installed all the recommended updates and tried to change the font and resolution settings.

I have previously installed gutsy on this machine with no problems.  

screenshot
[[IMG]http://img14.imageshack.us/img14/8941/screenshotcl6.th.png[/IMG]](http://img14.imageshack.us/my.php?image=screenshotcl6.png)

---

### Post by 3rdalbum on 2009-02-17
The screenshot looks exactly as I'd expect - which means that Ubuntu probably isn't detecting the correct resolution or display rate for your monitor.

As an example, with my monitor Ubuntu gives me two options: 50hz or 51hz. The 50hz option makes everything look fuzzy, the 51hz option makes everything look correct.

---

### Post by scoober on 2009-02-17
hi, thanks for your reply.

You were right, and for some reason, I didn't have to do anything to fix it.  I had already tried rebooting, but after a bit of a break (installing Debian on my 3rd partition) I booted into ubuntu again thinking i could dpkg-reconfigure xorg, and it had fixed itself - I checked the resolution, and the refresh rate had changed from 60 to 50.

However, thanks to your post, I now know how to fix it in future - I remember the last time I tried debian it did the same thing and I had no idea how to sort it out and gave up in the end.

---

