---
title: "Simple instalation problem"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by solus.ipse on 2006-01-31
Before I get into anything and get beaten with the idiot stick let me point out that I have searched all day for any info on this and have found nothing. If it really is a completly obvious answer though beat away (with an answer :) )

So, lets keep this simple. Rebooted with disc in drive. Opening install screen comes up as it should. Press enter, list of a few things being loaded......black screen.....computer restarts and I'm back at the opening install screen.

This pattern could could go on all day.

I even tried to go the server route just to see if that would even work. Nothing.

Thanks for ANY help.

---

### Post by agapito on 2006-01-31
Do you have any SATA drives?

---

### Post by solus.ipse on 2006-01-31
(dumb answer) Considering I've never encountered that name I wouldn't say so. Any quick way of finding out.

Sorry if i'm starting a babysitting thread.

EDIT: I did a quick look up. I do have a seagate external hardrive. I'm not installing on it though.

---

### Post by agapito on 2006-01-31
I'm just here to help you. :)

Small steps:
1. SATA info [here]("http://en.wikipedia.org/wiki/Sata").
2. Is it a laptop or a desktop pc?
3. Can you check your mainboard manual to see it you have SATA?
4. If you don't have the manual, but know the vendor and model you can find it on the web.
5. On the BIOS, do you have an that option on? 
6. If it's a desktop pc, and you don't have a problem with opening it, do you have cables like the ones on the wikipedia article above?

I think this could be your problem because a friend of mine had the the same problem due to SATA...

---

### Post by solus.ipse on 2006-01-31
Popped open the case. Both ATA connectors.

And i'm running a desktop PC.

---

### Post by agapito on 2006-01-31
That's good! :)
Maybe your CD is the problem.
Have you tried with another ubuntu cd? Can you do this?
I've had my troubles with some Ubuntu cds in the past...

---

### Post by agapito on 2006-01-31
[QUOTE=solus.ipse]So, lets keep this simple. Rebooted with disc in drive. Opening install screen comes up as it should. Press enter, list of a few things being loaded......black screen.....computer restarts and I'm back at the opening install screen.
[/QUOTE]

Does it say anything before the instalation hangs?
Where exactly does it hang?

---

### Post by solus.ipse on 2006-01-31
You wouldn't believe how many combos I've tried. Did the original, re-burned it, re-downloaded and re-burned and even tried an older V5.04 CD I had (install and live cd).

What shows up on the screen goes away way too fast to read in complete but as far as I know it says shows 2-3 installation files being loaded. I'm going pop the cd back in and check it out once more. i'll edit this post if I find anything.

EDIT: I was able to snap a quick shot of the screen with my camera. 

Boot:
Loading /install/vmlinuz......................
Loading /install/initrd.gz........................

Ready

(then blank screen)

---

### Post by agapito on 2006-01-31
Wow... ](*,) 
I found [this]("http://ubuntuforums.org/showthread.php?t=33853"). Can you tell me more about your pc?

---

### Post by solus.ipse on 2006-01-31
Well I found this: [http://ubuntuforums.org/showthread.php?t=3539]("http://ubuntuforums.org/showthread.php?t=3539")

But I'm really not sure how to use this info.


Haha, Great minds think alike huh?

---

### Post by solus.ipse on 2006-01-31
I wouldn't want to leave anything out so here are the [full specs]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&lang=en&cc=us&product=391951&dlc=en&docname=c00058482")

---

### Post by agapito on 2006-01-31
I guess so :)

I'm back from another google session, and this is what I found:
[http://lists.debian.org/debian-boot/2005/03/msg00161.html]("http://lists.debian.org/debian-boot/2005/03/msg00161.html")

I guess you are trying to install on an old machine, right?
It's probaly(my guess) a BIOS or memory thing...

Here's what you could try, if you can boot Knoppix:
[https://wiki.ubuntu.com/Installation/FromKnoppix]("https://wiki.ubuntu.com/Installation/FromKnoppix")

Or even better:
[http://wiki.ubuntu.com/SmartBootManagerHowto]("http://wiki.ubuntu.com/SmartBootManagerHowto")

EDIT: This last one wouldn't help... You boot can form the CD, and that doesn't work.

Your "simple instalation problem" is not that simple...

---

### Post by agapito on 2006-01-31
You souldn't be having these problems... My pc is older than yours and I never had any problems with any linux distro. You could try [Dapper Drake]("http://wiki.ubuntu.com/DapperFlight4"). It's the next version. It's still a work in progress, but a lot of people are allready using it. Maybe you'll get lucky...

---

### Post by agapito on 2006-01-31
I've got to go now. Here It's 4:38am. Zzz... Zzz... Zzz...
But I'll be on the lookout for your posts. If you do manage to install, please tell me how. I'm curious. :)
Good luck.

See U around.

---

### Post by solus.ipse on 2006-02-01
The Knoppix solutions seems to be far beyond my own knowledge.

I've even tried to install Mandriva (mandrake). Same exact problem.

Maybe i'm just not meant to run it.

---

### Post by solus.ipse on 2006-02-01
So i've done a lot of digging around and it seems that Linux really has a big problem with the Compaq Presario line in general. Lots of people asking about it and no one finding a solution.

---

### Post by solus.ipse on 2006-02-01
BUMB

If anyone has any info on this strange phenomenon or somewhere where I could find out please let me know.

---

