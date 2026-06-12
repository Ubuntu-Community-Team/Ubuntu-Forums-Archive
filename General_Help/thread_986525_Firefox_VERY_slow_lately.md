---
title: "Firefox VERY slow lately?"
date: 2008-11-18
forum: General Help
---

### Post by x C0MMAND0 x on 2008-11-18
I have noticed Firefox has been INCREDIBLY slow, I mean a minute+ to load a simple page on facebook or a google search or anything.  Has anybody else noticed anything?  I tried a purge/re-install, as well as clearing all cookies and settings and starting from scratch.  Additionally, my DL and UL speeds are just fine, and my other computers work just fine as well.

---

### Post by Th3Professor on 2008-11-18
What are your computer specs?
CPU?
RAM?
HDD?
etc.?

---

### Post by x C0MMAND0 x on 2008-11-19
My PC specs: AMD Athlon(tm) 64 Processor 3500+ , 512 KB Cache, 1000.000 MHz Frequency
2gb Mem

I tried SeaMonkey and also another browser.  I found out it seems to occur whenever I am logging into or accessing secured web pages...I wonder why?  The given browser I'm using will lock up, the screen will dim, and then it will come back after about 30 seconds.  It works fine on the SAME computer when I boot into windows...I wonder what the problem could be?

---

### Post by x C0MMAND0 x on 2008-11-20
I think I may have solved my own problem, though I'm not sure how it's all connected.  I did not know that I had to re-do my flash setup since I upgraded to 8.1, and I did not make the connection that that is when I started having internet problems.  I noticed it once I tried watching some Youtube videos.  I got flash working again and since then all websites have been loading just fine.  I'll update if I have any more problems.

---

### Post by kuscsik on 2008-11-20
I compared the firefox 3.0.4 windows version (under wine 1.1.4) and the Linux version of firefox 3.0.4. The result is surprising: the windows version runs faster under wine than the native Linux firefox.
While the windows version running in wine reacts on window zoom immediately, the Linux version spends 1-2 seconds on this operation ( core 2 duo 2GHz CPU).

Running the online javascript benchmark:

 [http://celtickane.com/webdesign/jsspeed.php](http://celtickane.com/webdesign/jsspeed.php)

the windows version under wine also outperforms the Linux version. 

I m disappointed.

---

### Post by frankleeee on 2008-11-20
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

---

### Post by orrie on 2008-11-20
It could be that you are at sites containing an flash-element.
If you install "flashplugin-nonfree" you will get the flashplayer and it will perhaps be a bit faster ;)

---

### Post by Th3Professor on 2008-11-20
Opera has always had a tendency to run much faster, even under "pressure", on all operating systems (in my experience). I use both web browsers, each for various things.

---

### Post by RT236 on 2008-11-21
> **x C0MMAND0 x said:**
> I have noticed Firefox has been INCREDIBLY slow, I mean a minute+ to load a simple page on facebook or a google search or anything.  Has anybody else noticed anything?  I tried a purge/re-install, as well as clearing all cookies and settings and starting from scratch.  Additionally, my DL and UL speeds are just fine, and my other computers work just fine as well.

I was having similar problems since I upgraded to Firefox 3.0.4. I also have a relatively fast computer. I was reading in some other groups of people having noticed Firefox was far slower for them too. I tried similar fixes as you, also tried Swiftfox and some other things...

In another group they were discussing using the Fasterfox extension by "spinball" which can be loaded from the normal mozilla extensions / Add-ons pull-down "Tools" menu on Firefox. I just tried it and the results are unbelievable. It is an experimental extension, but I've not had any difficulties. If I do, I will add to this reply.

**IMPORTANT NOTE:  I only  use it in the Optimized and Courteous modes which gives network optimizations only within the RFC specs. so as to not exceed the RFC specs. load on servers.**

Firefox 3.0.4 is now exceptionally fast on my system.:)

**UPDATE: 11/29/2008**

Despite the above, difficulties eventually returned. Firefox became "sticky." Although loading websites fairly well but still sometimes slow, overall responsiveness of Firefox did not seem the same as in past years.

I have always carried .mozilla forward throughout Firefox upgrades. Reading about the new release of Firefox, bookmarks, for example, are no longer an .html file, but rather now a database. When upgrading, Firefox now does a conversion of your old .html bookmarks to the new bookmark database.

I had also previously disabled all of my extensions, did not help and a number of standard things.

I decided to try a "from scratch" load of Firefox 3.0.4 again after having renamed, of course, .mozilla to .mozilla-bu. Performance was much better. In my reading, a long story short, I had noticed there are sometimes significant conflicts when going to the later releases, Firefox 3.0.4, and carrying forward your old .mozilla. I am hoping as Firefox creates new bookmarks in the new database I can return again to copying forward .mozilla for new releases.

I made notes of all of my old extensions and decided to just lose my bookmarks. Also in reading a number of groups said carrying forward extensions now can lead to problems, it is best to just install them from scratch when trying to correct this nature of difficulties.

I Installed the latest Firefox 3.0.4 via Synaptic, then installed all of my extensions via the Firefox extensions database. I now have exceptionally stable performance. As a note, I use a lot of extensions, 28, because of how I use Firefox. All work perfectly, no hangs or conflicts. Although sometimes extensions conflict, this was not the case for me. I think also what might have contributed to my difficulties is over the years I have manually and correctly modified the about:config file to my customizations. Perhaps my old customizations were not applicable to Firefox 3.0.4. Whatever, it all works perfectly now. As a note I also have Fasterfox still installed per my earlier notes.

I hope this might help someone with similar problems.

---

### Post by mschering on 2008-11-30
I still experience problems with javascript web applications:

[http://www.extjs.com/forum/showthread.php?t=53972](http://www.extjs.com/forum/showthread.php?t=53972)

I use firefox 3.0.4 on Ubuntu. If I launch WInXP in virtualbox firefox runs much faster.... :(

---

### Post by zika on 2008-11-30
> **orrie said:**
> It could be that you are at sites containing an flash-element.
If you install "flashplugin-nonfree" you will get the flashplayer and it will perhaps be a bit faster ;)

or maybe even better: install Adobe 64 10 alpha flash plugin for Ubuntu ... :)

---

### Post by x C0MMAND0 x on 2008-11-30
Adobe 10 for 64 now?  Please do share how to...

---

### Post by Th3Professor on 2008-11-30
I mentioned in a previous reply how I've noticed Opera web browser generally tending to run faster than Firefox, even under pressure, on all operating systems... I still use both web browsers for various purposes - although, on this system I only use Firefox, right now. The reason is: I cannot find Opera in Ubu's repo lists and am unable to install via apt-get or similar...

Has Opera been removed from Ubuntu's repo lists?

I like using both Firefox and Opera, each for different purposes, though I'd like to install Opera from the repo lists if possible. (I can compile source, just avoiding that.)

Thanks :)

---

### Post by impact on 2008-11-30
> **Th3Professor said:**
> I mentioned in a previous reply how I've noticed Opera web browser generally tending to run faster than Firefox, even under pressure, on all operating systems... I still use both web browsers for various purposes - although, on this system I only use Firefox, right now. The reason is: I cannot find Opera in Ubu's repo lists and am unable to install via apt-get or similar...

Has Opera been removed from Ubuntu's repo lists?

I like using both Firefox and Opera, each for different purposes, though I'd like to install Opera from the repo lists if possible. (I can compile source, just avoiding that.)

Thanks :)

Has Opera ever been in repos? I always had to download and install the .deb file from Opera's site.

---

### Post by zika on 2008-11-30
> **x C0MMAND0 x said:**
> Adobe 10 for 64 now?  Please do share how to...

```
sudo apt-get --purge remove flashplugin-nonfree nspluginswrapper
wget  [http://labs.adobe.com/downloads/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz](http://labs.adobe.com/downloads/flashplayer10/libflashplayer-10.0.d20.7.linux-x86_64.so.tar.gz)
tar xvf libflashplayer-10.0.d20.7.linux-86_64.so.tar.gz
sudo cp libflashplayer.so ~/.mozilla/plugins (create plugins directory if neccessary)  
```

---

