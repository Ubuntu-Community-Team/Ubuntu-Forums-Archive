---
title: "Cannot upload pictures to photobucket, Hardy, FF3"
date: 2008-10-07
forum: General Help
---

### Post by parabellum9x19 on 2008-10-07
Hello.

I have been an ubuntu user for a little while now.  I'm far from a power user, but I am comfortable getting my hands dirty.

I did extensive searching before starting this thread, but I didn't find what I was looking for.

Problem:  I cannot upload photos to my photobucket account when using Hardy with FF3.  I click on the Choose Files button and NOTHING happens at all.

I am running NoScript, but I have tried to globally enable scripting and that has no effect.  I am also running AdblockPlus but I have enabled it fully for the page, so I ruled that out.

I have also ruled out network, router, ISP and firewall considerations, as my apple laptop handles this just fine, running the same version of FF3 through my network.

Specifics:  FF version:  3.03

Ubuntu verison:  8.04 Hardy, Kernel Linux 2.6.24-19-generic.

At this point, I am not sure where to look to continue my analysis of the problem...I may try to install Opera or another browser to rule out a browser specific issue...but I really doubt that is it, since I run the same browser with the same add-ons from my other machines without the same issue.

Any help is greatly appreciated.

Parabellum

---

### Post by parabellum9x19 on 2008-10-07
Well, I installed the latest version of Flash for Mozilla, no change.

I installed Opera, and I can't get past the first page...it claims I need to install flash to see the freaking ads (ANGRY!) and will not even allow me to login, but Adobe lists no flash support for opera.

:(

---

### Post by parabellum9x19 on 2008-10-07
Damn.

After more and more searching, I found a thread from a window$ user with the same problem.

He was running flash 10 and downgrading to flash 9 solved it.

I just installed flash 10 a few days ago to get Hulu streaming working.

Man...I'm really not sure how to downgrade to flash 9 cleanly on Hardy, and having to choose between hulu working and pb working really sucks.

:(

---

### Post by cariboo on 2008-10-07
I just tried to upload a file to my Photobucket account. The java enabled uploader doesn't work, but if you tell noscript to forbid Photobucket, you get a choice to use the old uploader which works like it should.

Jim

---

### Post by parabellum9x19 on 2008-10-08
> **cariboo907 said:**
> I just tried to upload a file to my Photobucket account. The java enabled uploader doesn't work, but if you tell noscript to forbid Photobucket, you get a choice to use the old uploader which works like it should.

Jim

That is awesome, thank you! 

I finally narrowed it down to exactly what is causing the problem.

I installed flash 10 RC as per this guide:

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

It fixes ALL of the problems I was having with flash streaming (HULU is a perfect example) being choppy and generally looking like crap.

But on this version of flash, I have the problem described above for photobucket, as well as myspace picture uploads.

If I back out to flash 9 via the following command:

sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree

Then run:

sudo apt-get install flashplugin-nonfree

...it fixes photobucket and other similar file uploaders...but I am back to craptastic flash performance, especially with HULU.


So, I will stay on flash 10rc for now, use your wondcerful workaround, and wait for the first full release of flash 10.

Since switching from flash 9 to 10rc takes a whopping 1 minute, I was planning to bounce back and forth depending on my need...but your little trick seems to solve that.

Cheers!

parabellum

---

### Post by AlexBellisBrown on 2008-10-08
Yep, for me there has  always been something wrong with my Myspace multiple photo uploader, you have the same problem, its some kind of bug, but to be honest, the workaround works fine, and i can live with it also for the time being.;)

---

