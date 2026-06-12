---
title: "Can I save data during reinstall?"
date: 2009-07-02
forum: Installation &amp; Upgrades
---

### Post by flatbeard on 2009-07-02
Hi all
My Ubuntu 9.04 crashed a few days ago, and I'm trying to save the data on the hard drive. I can easily install Ubuntu again, but it wants to wipe my HD completely. Can I avoid this and just do a simple "repair installation and overwrite all the system files" installation?
All I really need is access to the hard drive so that I can get my files out. From that point, I can just reformat the entire thing...

But is there no "repair faulty installtion" option with Ubuntu? I tried Ubuntu Rescue Remix, but didn't understand one word of it ... should I give it another go?

Please be aware that I am a beginner in terms of Linux. If you write any console stuff, please write very slowly and gently...

Harrg, all ye ubuntah luvvers!!  :)
Flatbeard

---

### Post by merlinus on 2009-07-02
You can boot from the live cd, and mount your ubuntu partition by clicking on in it nautilus. Then you should be able to rescue important data.

And you may wish to consider creating a separate partition for /home upon reinstall.  That way you will not have to do this again.

---

### Post by flatbeard on 2009-07-04
> **merlinus said:**
> You can boot from the live cd, and mount your ubuntu partition by clicking on in it nautilus. Then you should be able to rescue important data.

And you may wish to consider creating a separate partition for /home upon reinstall.  That way you will not have to do this again.

Excellent!! (Do the dead ant!!) Im saving all my files now. Just one thing to go, and thats my email files. Theyre located in a hidden directory under /home/.mozilla-thunderbird ... but how can I get access to those files?
I tried just to enter via nautilus and via a terminal and cd, but no go. sudo cd is the same. Hmm ... any ideas? 

Ill be back on that separate partition ... good idea. Sigh ... 

Regards
flatbeard

---

### Post by ronparent on 2009-07-04
Do a google search on "separate home partition" (I don't have it bookmarked on this computer). The instructions may be daunting but they work beatifully.

---

### Post by flatbeard on 2009-07-04
Thanks ronparent. Will do that. Now all I need is my emails from Thunderbird. Theyre located in a hidden directory under /home/.mozilla-thunderbird ... but how can I get access to those files?
I tried just to go in via /Places/harddiskname/home but it wont let me enter the directory. I bet its because I am booting from a CD and thus im not logged in with my standard user. Then what the hey do I do... tried sudo in a terminal, but no go.

Help ... whine whine...:(

---

### Post by merlinus on 2009-07-04
Did you try

```
gksudo nautilus
```

---

### Post by flatbeard on 2009-07-04
Wiii! It works! It works! Free cheese for everyone! Um ... oh nevermind. Thanks for the help guys (male, female or otherwise). Now Im on with my reinstallation and Ill probably be back shortly with something including a separate partition for /home. But all in good time. First reinstallation, then beer, movie and job applications!

Cheers, all! ):P ):P ):P
flatbeard the joyful

---

### Post by merlinus on 2009-07-04
Glad it worked out for you.  Enjoy the movie and beer, and get a great job!

---

