---
title: "Suspend work on Mint LiveCD but not Ubuntu"
date: 2008-09-22
forum: General Help
---

### Post by m0ntels on 2008-09-22
I switched from XP to Ubuntu about 2 months ago and have been loving it for the most part.  One thing I haven't been able to figure out is why suspend doesn't work. 

I have Hardy installed on my desktop (1.6 ghz give or take, 1 gig RAM, built in Nvidia) and neither suspend nor hibernate work.  They both put the computer into sleep mode, but when I try to power back on, the monitor wont come back on, otherwise it sounds like it's powering back up.

I've played with Mint a little on a Live CD while trying to make sure Ubuntu was the one for me, and while hibernate still doesn't work, suspend does work properly.  

I'll be reformatting and switching to Intrepid when the final release comes out so I don't know if it will work then, but if I cant get it to work then, I guess I will switch to Mint.  Is there a way to copy some of Mint's configuration or a file over into Ubuntu to get the suspend function to work properly?  Mint was fine, and maybe a little faster, but for no real reason in particular I just feel like sticking with Ubuntu.  Thanks.

---

### Post by Taxman415a on 2008-09-22
See this post [http://ubuntuforums.org/showthread.php?t=926517](http://ubuntuforums.org/showthread.php?t=926517)
I just made and see if that helps any.

---

### Post by m0ntels on 2008-09-22
I followed the directions in your other thread but accidentally used the UUID of the main partition instead at first.  When I tried to come out of suspend then, the monitor did come on for a little, but only to pop up a few lines of boot up code, then the monitor went off and blinked again.  Hibernate booted up until the Ubuntu bootup status bar came up, then the monitor turned off again and blinked.

That's when I noticed I had listed the wrong UUID and changed it back to my swap's UUID, which by looking at the backup "resume" file, it was originally.  When I come out of hibernate or suspend like that, it just turns off the monitor as soon as the computer starts to wake up and it blinks at me.

Any other places I should look at or does the system create any boot log files that may lead us in the right direction?

---

### Post by Taxman415a on 2008-09-22
Not that I know of myself but there are lots of threads on fixing hibernate and suspend, so if you search enough you should find something. It's not a big problem to use Mint if that does what you need I'd think. I'm not really sure what they do differently that causes it to work, but someone may know what to check. Clearly there is something that can be done.

---

