---
title: "meebo.com crashes firefox .. Anyone else?"
date: 2008-07-28
forum: General Help
---

### Post by kernelhaxor on 2008-07-28
when I type meebo.com in the address bar and press enter, firefox (3.0.1 with all updates through the update manager installed) crashes .. it crashes even before the home page opens up ..

I see somebody reporting this here:
[http://ubuntuforums.org/showthread.php?t=699904](http://ubuntuforums.org/showthread.php?t=699904)
but there isn't a solution in that thread ..

I don't think there is much flash on the home page .. May be a lot of Javascript .. 

Does anyone else experience the same problem? Any ideas?

by the way, I am on Hardy Heron (all updates installed)

---

### Post by ad_267 on 2008-07-28
I'm on hardy heron with all the updates and I don't have this problem. I don't know why it wouldn't be working for you.

---

### Post by jackflap on 2008-07-28
Yup, same here.

On two different machines as well: Firefox 3 on Gutsy and ff3 on 8.04.1..

I'm actually googling to see if I can find a bug reported anywhere right now. I'll let you know how I get on.

---

### Post by jackflap on 2008-07-28
Yup, just found this bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/212814](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/212814)

That's the error on the command line that I get when I try to go to meebo.com. I cant find any other bugs around, and they specifically ask for a new bug to be created if the problem persists (which it obviously does):

"If you are still seeeing this issue please report a new seperate bug and attach the strace or backtrace to that bug report."

I don't have time to report a new bug, so if someone else could get round to that and post back here when they're done, it would be very appreciated.

Thanks,
Alex

---

### Post by kernelhaxor on 2008-07-28
> **jackflap said:**
> Yup, just found this bug on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/212814](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/212814)

That's the error on the command line that I get when I try to go to meebo.com. I cant find any other bugs around, and they specifically ask for a new bug to be created if the problem persists (which it obviously does):

"If you are still seeeing this issue please report a new seperate bug and attach the strace or backtrace to that bug report."

I don't have time to report a new bug, so if someone else could get round to that and post back here when they're done, it would be very appreciated.

Thanks,
Alex

Thank you.
I restarted my system and now meebo opens fine, firefox doesn't crash anymore :confused:
I'll post a new bug when I see this happen again.

---

### Post by rykel on 2008-08-24
As of today, which is 24 August 2008 Singapore time, I am still getting random Firefox 3 crashes upon visiting Meebo.com. Sometimes, I do NOT even need to login to Meebo, the website itself is enough to close Firefox without my permission. However, I _think_ the crash occurs only on the first visit - subsequent visits do not pose a problem, at least not consistently.

Hope someone can help!!

---

### Post by doggie.dog on 2008-09-19
My Firefox was crashing consistently when accessing [https://wwwm.meebo.com](https://wwwm.meebo.com), but it worked fine with the non-SSL [http://wwwm.meebo.com](http://wwwm.meebo.com).

Interestingly enough, if you block the flash content (Firefox add-on: Flashblock), the HTTPS site runs fine.

Today, I replaced 'gij' with 'sun-java-6', disabled the Flashblock add-on, now Firefox stays on when going to the SSL meebo!  Woohoo!

:popcorn:

---

### Post by rykel on 2008-10-02
Fresh report: As of 2 October 2008 my Firefox still CRASHES almost everytime I try to load Meebo.com. I am getting FRUSTRATED!!   :confused:

---

### Post by justleen on 2008-10-02
Works fine here.
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.16) Gecko/20080715 Ubuntu/7.10 (gutsy)

edit: Thank you for that brilliant site!!

---

### Post by Roasted on 2008-10-05
Oct 5th. After 1:00 AM.

Ubuntu Hardy Heron 8.04 32 bit. Fresh install (as of two days ago).

Firefox 3. Flash 9. 

Meebo still crashes.

---

### Post by heikor on 2008-10-05
Same for me, 5th Oct., ~9AM UTC, Ubuntu 8.04, Firefox 3, Flash enabled. The problem existed for months, several Firefox updates ago.
It always crashes on the first visit, but after a restart of firefox there's a slim chance that the site might work. I successfully logged in right now.

---

### Post by Asem on 2008-10-10
with me meebo crash if i se the remember password thing 
i cleared the cache and it didn't crash 
i have firefox 3.03

---

