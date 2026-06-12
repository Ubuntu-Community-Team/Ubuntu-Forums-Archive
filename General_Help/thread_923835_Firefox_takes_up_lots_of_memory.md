---
title: "Firefox takes up lots of memory"
date: 2008-09-18
forum: General Help
---

### Post by malachi1990 on 2008-09-18
So whenever I try playing a video in firefox, its memory usage skyrockets (usually from about 30 mb to 120-150) and I was wondering if either a) there is a fix for this) and/or b) this has to be fixed in the next firefox release.

I really think this belongs in another thread, but couldn't find a suitable one.

---

### Post by mb_webguy on 2008-09-18
How are you playing the video?  Is it Flash, or are you playing embedded or streaming media using a plugin like Totem or MPlayer?

---

### Post by Nitefang on 2008-09-18
I have seen lots of problems with resource usage lately and I experience them a lot to like for the past 5 minutes (since I opened Firefox) I have been using 328MEGAbytes of memory, yes I am sure. And my processors peak every few seconds at 30% or so each(I have a quad core 2.3GHz each).

 I find this rather odd because I never had such problems with vista and I thought Linux was supposed to use up fewer resources, I think it must be a user-end problem, but I don't know what I could have done.

---

### Post by mb_webguy on 2008-09-18
Open a terminal and type "top".  Then type ">" to sort the processes by memory usage rather than CPU usage.  This will show you what processes are using so much memory, and give you more accurate output than the System Monitor.

---

### Post by nitro_n2o on 2008-09-18
are you talking about firefox 3? if not, get firefox 3 that should reduce memory consumption somewhat!

Also, I notice that anything has to do with Java..will just make the machine go crazy, especially those java applets on webpages. If you video is being played from a Java app, then I don't see a way of fixing that

---

### Post by Nitefang on 2008-09-18
For me Firefox(3) is taking up 63megabytes. That doesn't sound right to me but I never really paid attention to that when I was using Vista.

---

### Post by nitro_n2o on 2008-09-18
> **Nitefang said:**
> For me Firefox(3) is taking up 63megabytes. That doesn't sound right to me but I never really paid attention to that when I was using Vista.

63M .. and why they panic :) you are lucky

---

### Post by Nitefang on 2008-09-18
> **nitro_n2o said:**
> 63M .. and why they panic :) you are lucky

Wait you mean 63MB isnt that bad or do you mean my computer could catch on fire at any minute?

 And if that isn't that bad then why does it crash so often? Could it be that it isn't recognizing my Graphics card and is running off the virtual Graphics memory?

---

### Post by malachi1990 on 2008-09-18
Well, this is Firefox 3, and I guess that youtube runs java, so that may be the answer.  

Does anyone know if this will be fixed in 3.1?

---

### Post by NoWayBill on 2008-09-18
I had Ubuntu 7.10 and Fedora 8, both 64-bit, installed at one time.
When a web page had a lot of Flash in it the resources would go through the roof.
I can't remember for certain but I believe the process was npviewer.bin.

Installing/using the 32-bit browser solved it.

Running XP right now, FF using 63.3MB

---

### Post by mb_webguy on 2008-09-18
I'm running Firefox with currently 4 tabs open, and I use a lot of extensions, and Firefox is using about 120MB.  

If I use "gksu firefox" to start Firefox as root (and therefore with no extensions, and only one tab open), then it uses about 60MB.

I think that's about normal...

---

### Post by nitro_n2o on 2008-09-18
> **Nitefang said:**
> Wait you mean 63MB isnt that bad or do you mean my computer could catch on fire at any minute?

 And if that isn't that bad then why does it crash so often? Could it be that it isn't recognizing my Graphics card and is running off the virtual Graphics memory?


How many megabytes of memory your have?? 

For example, if you have 1GB = 1024MB's then you are using (100*64/1024)% is only about 6% of your memory!! how bad is that!!

---

### Post by RequinB4 on 2008-09-18
> **Nitefang said:**
> Wait you mean 63MB isnt that bad or do you mean my computer could catch on fire at any minute?

 And if that isn't that bad then why does it crash so often? Could it be that it isn't recognizing my Graphics card and is running off the virtual Graphics memory?

Let's put it this way - I'm running firefox 3 with one tab open to ubuntu forum and it's using slightly more than 5% of my 2GB RAM.

As for crashing, do you have the flash 9 plugin installed? libflashsupport? things like that can cause some known issues.

---

### Post by Nitefang on 2008-09-18
> **nitro_n2o said:**
> How many megabytes of memory your have?? 

For example, if you have 1GB = 1024MB's then you are using (100*64/1024)% is only about 6% of your memory!! how bad is that!!

 Thats what i thought, I must have read it wrong or something. I have 3Gb.

---

### Post by Nitefang on 2008-09-18
> **RequinB4 said:**
> Let's put it this way - I'm running firefox 3 with one tab open to ubuntu forum and it's using slightly more than 5% of my 2GB RAM.

As for crashing, do you have the flash 9 plugin installed? libflashsupport? things like that can cause some known issues.

I will try that and just to make sure because I want to try and use the terminal more often the command for libflash support would be this


```
sudo apt-get install libflashsupport
```

or is that wrong?

---

### Post by mb_webguy on 2008-09-18
Yes, that's wrong unless you want to increase the memory load on your system.  The libflashsupport package is intended to fix some compatibility problems between Flash 9 and PulseAudio.  These issues have been resolved in the Flash 10 plugin found in the backports repository.  Install it instead (using the instructions found in the link in my signature).

That is, like I said, unless you *want* to increase the memory load on your system.

Also, for those people who are worried about how much memory Firefox uses versus how much IE uses, you might find [this page]("http://dotnetperls.com/Content/Browser-Memory.aspx") interesting.  Or [this one]("http://arstechnica.com/news.ars/post/20080317-firefox-3-goes-on-a-diet-eats-less-memory-than-ie-and-opera.html").

---

### Post by RequinB4 on 2008-09-18
> **Nitefang said:**
> I will try that and just to make sure because I want to try and use the terminal more often the command for libflash support would be this


```
sudo apt-get install libflashsupport
```

or is that wrong?

I'm asking because libflashsupport sometimes CAUSES flash to crash - see if it helps uninstalling it if you have it and flashplugin-nonfree

so i'm suggesting try (this might remove all flash support from your box, just reinstall to fix, unless your system is set up weirdly):

```

sudo apt-get uninstall libflashsupport flashplugin-nonfree

```

---

### Post by Nitefang on 2008-09-18
> **RequinB4 said:**
> I'm asking because libflashsupport sometimes CAUSES flash to crash - see if it helps uninstalling it if you have it and flashplugin-nonfree

so i'm suggesting try (this might remove all flash support from your box, just reinstall to fix, unless your system is set up weirdly):

```

sudo apt-get uninstall libflashsupport flashplugin-nonfree

```

I tried that, it says that uninstall isn't a command??

---

### Post by mb_webguy on 2008-09-18
It should be "sudo apt-get remove ..." not "sudo apt-get uninstall ...".

---

### Post by RequinB4 on 2008-09-19
> **mb_webguy said:**
> It should be "sudo apt-get remove ..." not "sudo apt-get uninstall ...".

Yep, my bad

---

