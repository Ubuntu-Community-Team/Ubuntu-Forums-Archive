---
title: "copy and paste"
date: 2008-08-11
forum: General Help
---

### Post by majikhotline on 2008-08-11
i can not copy and paste, when i try to paste i get ```
http://windowsxp-privacy.net/?id=198760099
```
i put this in a browser and get a spam of antivirus 2009 is spanning your computer.......what is going on and how do i fix this?

---

### Post by oldsoundguy on 2008-08-11
Gee, that is a problem in Windows.  

Since that crud does not get into Linux, two choices .. dump Windows or FIX it.  (try SUPERAntiSpyware . free)  Then take some time to immunize that POS operating system!

---

### Post by majikhotline on 2008-08-12
i do have a windoze machine, but the problem is on my ubuntu machine, could linux have a virus?

---

### Post by bruceJ on 2008-08-12
It's happening in OS X as well. This is a generalized JavaScript hack of some sort.

---

### Post by zuner2012 on 2008-08-12
I've come across this many times while web browsing. When you click on a link, it sometimes re-directs you to the spamming site. Can't remember what I did, but it was a pretty easy fix.

---

### Post by oldsoundguy on 2008-08-12
latest browser and java updates are supposed to lessen the problem of getting flipped, but if the site has been hacked itself, you still will have issues.

I surf with scripts blocked and then choose which ones are granted permission.  Takes a bit more time, but saves a lot of time also when you get to a site that has 6 scripts on their home page, and only one of those is pertinent to the site itself! (lots of tracking going on .. biggest offender is Google Analytics!)

---

### Post by nixHead101 on 2008-08-13
Man I have this problem too.  I just installed Ubuntu last night.  I was browsing monster.com  when I noticed the problem. I have all the latest updates.

What are some things I can do to avoid this in the future.

---

### Post by majikhotline on 2008-08-14
i delete my cookies and restart the machine and havent had a problem with copy and paste, now for the reason it happened was maybe i visited the wrong page.

---

### Post by freak42 on 2008-08-19
heise a german it-newsportal links to this thread.
They claim that flash-banners hijack your clipboard and copy spam urls to the clipboard constantly, effectifely destroying the ability to use the clipboard as long as the 'evil' flash ad is displayed.
They also link to a demo that copies [www.evil.com](www.evil.com) into your clipboard constantly.
This allegedly works on Windows, Linux and OSX with flash installed.

Demo: [http://raffon.net/research/flash/cb/test.html]("http://raffon.net/research/flash/cb/test.html")

Newspost (German):
[http://www.heise.de/newsticker/Flash-Werbebanner-manipulieren-Zwischenablage--/meldung/114474/from/atom10]("http://www.heise.de/newsticker/Flash-Werbebanner-manipulieren-Zwischenablage--/meldung/114474/from/atom10")

---

### Post by elwillow on 2008-08-19
To continue Freak42 report:
[http://www.heise-online.co.uk/security/Flash-banners-manipulate-the-clipboard--/news/111353](http://www.heise-online.co.uk/security/Flash-banners-manipulate-the-clipboard--/news/111353)

---

### Post by balaknair on 2008-08-19
Right. It's a confirmed Adobe flash-based attack(uses flash-based banner ads on major sites) which takes control of the clipboard. It affects Windows, OSX and Linux. 
Read more at [http://blogs.zdnet.com/security/?p=1733&tag=nl.e539](http://blogs.zdnet.com/security/?p=1733&tag=nl.e539)
You have to restart the system to clear the url from your clipboard.
To be safe(r) use Firefox(preferably 3.0.1) with NoScript.
Checked the test page linked to above(see screenshot), NoScript does make it harder for the hack to affect your system, since you would have to manually allow the script/flash to run. It doesn't make it impossible though. 
The best antivirus utility(and the most vulnerable) is still the user. Browse safely, don't go to suspicious sites and don't click on links from people you don't know(even from people you do know if it looks suspicious) and Never Ever allow cross site scripts---> Use updated FF3 with NoScript and AdBlock Plus.

---

### Post by squee on 2008-08-21
haha, I love when it was searching through my C drive (which i dont have, called something else.) and searching though .dll files and stuff. I wish I had a virus scanner that could scan 160Gb that fast (less than 1 min.)


another reason to block ad banners and use scriptblocker in firefox.

---

### Post by martman1 on 2008-08-21
It's a javascript hack that's been going around.  I think there is a fix for it somewhere.


--------

[Are you addicted to gambling?  Get free help now.]("http://www.gamblinganon.blogspot.com")

---

### Post by freak42 on 2008-08-21
> **balaknair said:**
> You have to restart the system to clear the url from your clipboard.

Correction: no you don't have to restart, just close the webpage that contains the malicious flash-script, which simply keeps copying the url to the clipboard while it is running.


> **squee said:**
> haha, I love when it was searching through my C drive (which i dont have, called something else.) and searching though .dll files and stuff. 

This flash-script doesn't and cannot access your drive (not on win nor linux), it also doesn't search through your dll files.

hth

---

### Post by Benanov on 2008-09-03
The best defense from this, as unpopular as it may be, is to uninstall flashplugin-nonfree and use gnash-mozilla-plugin instead.

Adobe Flash is the vulnerable product here.

Alternately, Flashblock or NoScript extensions for Firefox will also work. NoScript is GPL-licensed so it won't add non-Free software to your system. (Unsure about Flashblock.)

--BK

---

