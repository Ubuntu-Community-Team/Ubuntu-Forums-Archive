---
title: "liblame0 and libmp3lame0 won't play nice - again..."
date: 2008-07-26
forum: General Help
---

### Post by stelekpl on 2008-07-26
Hi everyone,

I just found this old thread here:

[http://ubuntuforums.org/showthread.php?t=29861&highlight=libmp3lame0]("http://ubuntuforums.org/showthread.php?t=29861&highlight=libmp3lame0")

and I have exactly the same problem (3 years later, on Ubuntu 8.04). Unfortunately there's no answer in the thread...

So I need to have liblame0 and libmp3lame0 installed at the same time but the package manager will not allow it. What can I do?

---

### Post by pir on 2009-11-07
Also looking for the answer.

---

### Post by mc4man on 2009-11-07
I see you have 2 posts on this, though with slightly differing ?'s.

You may want to post what release you're using (assuming hardy) and why you want both liblame0 and libmp3lame. 

They both provide the same .so, if you were building sources the liblame0, liblame-dev will provide libmp3lame.

If you're trying to install a package(s) that depend on libmp3lame you may find it easier to hack the control file of the .deb(s) and change the dep to liblame0 than set up an install of both at once.
(can post script to do so if desired

It is however possible in a couple of ways, I had a hardy install from last spring where I was testing something and never got rid of it. ( testing building a current ffmpeg svn to install in place of the hardy medibuntu packages

So with the use of 2 dummy packages went ahead and satisfied the liblame0, liblame-dev deps along side having a current libmp3lame 
install(s)  
(you could also do the opposite - real liblame0, liblame-dev, dummy libmp3lame, libmp3lame-dev.

Still, wondering why you need this...?

---

