---
title: "FireFox 3 Slow to load pages."
date: 2008-11-08
forum: General Help
---

### Post by Coke0 on 2008-11-08
Hello, First and foremost I am new to Linux / Ubuntu so if this is not the proper place to post this, I apologize.

Well the problem is in  Firefox 3(Ubuntu 8.10) every page loads so slow. Its not so much the loading but the initial lookup, once it gets going the page objects load normal speed.  This happens even opening Firefox and going to my home page [www.google.com](www.google.com)  I have tried a number of options but no luck.  I disabled the "tell me if this is a bad site etc..." boxes, I even did an "about:config" and disabled the IPV6 or w/e. No luck there. I know its not my connection as I have a xp box on the same router at home and Firefox is lightning fast.  Any help or pointers to some good info would be amazing.

---

### Post by Coke0 on 2008-11-09
Bump - Still lookin for some love...  A little more info while I am here, Its not desktop effects or stuff like that, the window opens and is blank and the bar at the bottom says "looking up www.google.com" or whatever site im hitting.  This pause is 8-10 seconds long, no joke, but once the page starts to load its normal loading speed.

Free hugs to anyone who can help with this.

---

### Post by exploder on 2008-11-09
Here are some things I do to speed up Firefox.

001- In the first tab of preferences, put a check in " Close it when all downloads are finished".

002- In the Privacy tab,change "Keep my history to 0 days".

003- For "Cookies" set it to "Until I close Firefox".

004- In the "Security" tab, take away the checks for: "Tell me if the site I am visiting is a suspected attack site" and "Tell me if the site I am visiting is a suspected forgery"' (This will help with Flash and besides, what are these warnings going to do if you are already on the site?)

005- In the "Security", "Update" tab remove the checks for: Firefox and Installed addons. (You can manually update addons at a time of your choosing and Firefox is updated through your package manager anyways.

006- Make sure you have Flash 10 installed.

007- Try to keep the number of addons to a minimum. I do not have any 
installed.

008_ Clear your private data. This keeps the browser from filling up with junk.

That is everything I can think of to improve performance. Hope this helps.

---

### Post by Coke0 on 2008-11-09
Thanks for the tips my friend but its not like that.  This computer has a AMD 3800 x 2 64 with a 7900Gt video card so a few cookies or addons shouldnt be the problem.  Its like the DNS lookup is stalling or going super slow, over 8 seconds on every new page or a refresh.  Once firefox gets the page it loads normally.

---

### Post by exploder on 2008-11-09
You might be surprised what a little tweaking can do. I understand what you are saying though.

---

### Post by Portmanteaufu on 2008-11-10
Bump.

I'm experiencing the same issue on Arch Linux. Even when Firefox is the only process (not even a WM) it hangs unexpectedly after a page request. Then, after 6 - 8 seconds, it finally remembers it was in the middle of something and loads it.

I configured firefox long ago for pipelining / increased maxrequests; this isn't a general performance issue, it's actually borked.

I suspect it had something to do with the 3.03 update as that's the only thing I've installed in the last week or two. Even if no one knows how to resolve the issue, could someone walk me through posting a bug report on Mozilla? I'd be happy to do a write-up for them.

---

### Post by scouser73 on 2008-11-10
> **Coke0 said:**
> Hello, First and foremost I am new to Linux / Ubuntu so if this is not the proper place to post this, I apologize.

Well the problem is in  Firefox 3(Ubuntu 8.10) every page loads so slow. Its not so much the loading but the initial lookup, once it gets going the page objects load normal speed.  This happens even opening Firefox and going to my home page [www.google.com](www.google.com)  I have tried a number of options but no luck.  I disabled the "tell me if this is a bad site etc..." boxes, I even did an "about:config" and disabled the IPV6 or w/e. No luck there. I know its not my connection as I have a xp box on the same router at home and Firefox is lightning fast.  Any help or pointers to some good info would be amazing.

Here's a tutorial for optimising Firefox; [http://www.ubuntugeek.com/speed-up-firefox-web-browser.html]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

---

### Post by philinux on 2008-11-10
> **Coke0 said:**
> Hello, First and foremost I am new to Linux / Ubuntu so if this is not the proper place to post this, I apologize.

Well the problem is in  Firefox 3(Ubuntu 8.10) every page loads so slow. Its not so much the loading but the initial lookup, once it gets going the page objects load normal speed.  This happens even opening Firefox and going to my home page [www.google.com]("http://www.google.com")  I have tried a number of options but no luck.  I disabled the "tell me if this is a bad site etc..." boxes, I even did an "about:config" and disabled the IPV6 or w/e. No luck there. I know its not my connection as I have a xp box on the same router at home and Firefox is lightning fast.  Any help or pointers to some good info would be amazing.

It sounds like maybe a isp or router issue. First lets check this.
Whats the contents of /etc/hosts
```
cat /etc/hosts
```

---

### Post by Portmanteaufu on 2008-11-10
I don't want to speak for anyone else, but at least in my case the problem is specific to Firefox. It's not affecting any other internet-centric programs; I can use ping / dig / lynx / pidgin / whatever else without the hideous delay I experience in Firefox.

---

### Post by Coke0 on 2008-11-10
eric@server:~$ cat /etc/hosts
127.0.0.1	localhost
127.0.1.1	server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I don't know if its my router or ISP, as I have two boxes and my xp machine runs fine, even when I had xp on the box with the problems Firefox was normal.  I originally put fedora 9 on it last weekend and Firefox 3 was behaving the same way, so I just switched to Ubuntu hoping it was just a Fedora issue.

---

### Post by masterpop on 2008-11-11
I had the same problem, after upgrading from 8.04 to 8.10 (without any issues) Firefox 3.0.3 was frustratingly slower as compared with 8.04.

Only issue I had during upgrade was that network-manager was not loading properly so I had to remove+re-install.

What I did notice is that Firefox would hang (window sometimes became greyed out (as if it had crashed)) and generally become unresponsive until all of a sudden the page would load.

In my case, the status bar was "Waiting for..." and the type of page it was waiting for was "doubleclick" or similar.

I never found the bug, as I did a fresh re-install of 8.10 and now have no issues. Hope this helps.

---

### Post by Coke0 on 2008-11-14
Man, this is still going on... I even downloaded Ubuntu again make a fresh install CD and ran it... still a problem, I followed the link above and used all the performance tips, still no love.  I think my thread title may be misleading though, its not the loading of pages thats slow its the finding the page data or something.  I'm telling you though this is pretty lame :( waiting for 8-12 seconds every time i click a link just for Firefox to find the page.  Please somebody help if you have a spare minute, I swear I'll whore out "Thank You"s like there is no tomorrow if you can solve this.

-Coke Zero
 No calories...

---

### Post by michaelzap on 2008-11-15
> **masterpop said:**
> I never found the bug, as I did a fresh re-install of 8.10 and now have no issues. Hope this helps.

I had a similar experience. Starting with Hardy (which I installed fresh), Firefox loaded all pages slow as molasses. It would hang on every URL lookup, and I noticed that other machines that I used with the same basic setup also hung in the same way.

When I upgraded my desktop computer to Intrepid, it still had this issue but in addition Firefox became extremely unstable. It would crash on me constantly, to the point that I practically couldn't use it at all. The problem wasn't limited to Firefox, either; Opera and Epiphany crashed constantly as well.

I tried a number of things, but nothing could resolve this so I reformatted and installed Intrepid from scratch. This resolved the browser instability issue (which was critical), but in addition it also fixed the slow page loads due to hung lookups. I was actually kind of ecstatic when I realized this, since I'd been living with slow pages for six months and I'd almost forgotten how fast browsing could be when it works properly.

So my advice would be to try browsing from the Intrepid Live CD. If that works, then I recommend you reinstall Intrepid from scratch. I never did figure out the cause of the problem, but this fixed it for me.

---

### Post by ubuntologist on 2008-11-21
had the exact same issue but found a workaround...both opera and konqueror were happy as larry - this only affected firefox!

in my case, i had to change my DNS settings under Ubuntu's Network Connections (NOT in my modem connecting to my ISP) to that of OpenDNS - 
208.67.222.222 
208.67.220.220

all's dandy!

---

### Post by RT236 on 2008-11-22
> **Coke0 said:**
> Hello, First and foremost I am new to Linux / Ubuntu so if this is not the proper place to post this, I apologize.

Well the problem is in  Firefox 3(Ubuntu 8.10) every page loads so slow. Its not so much the loading but the initial lookup, once it gets going the page objects load normal speed.  This happens even opening Firefox and going to my home page [www.google.com](www.google.com)  I have tried a number of options but no luck.  I disabled the "tell me if this is a bad site etc..." boxes, I even did an "about:config" and disabled the IPV6 or w/e. No luck there. I know its not my connection as I have a xp box on the same router at home and Firefox is lightning fast.  Any help or pointers to some good info would be amazing.

Hi, I replied to someone having similar difficulties in the 64 bit group, so this is not a true cross-posting, I did not start a new thread.  I saw your difficulties and had had the same frustration, so I thought the below might possibly be helpful.

I am using Ubuntu 8.10.  I was having similar problems since I upgraded to Firefox 3.0.4.  I also have a fast computer and additionally a career background in Unix/Linux for more years than I want to think about, so I tried some good fixes I had found...

In searching and searching the Internet other groups of people have noticed Firefox is recently far slower for them too.  I tried many fixes, also tried Swiftfox and some others including Tweaking tools...  I was getting nowhere with this, really, and could not find anyone in my initial searching that really had an answer that worked for me...  and I prefer using Firefox.  Firefox has always been fast for me in the past.

I'm assuming your system is set up correctly, of course, and that you have a reasonably fast connection...  and that certainly sounds it is the case for you.

In another group they were discussing trying using the Firefox "Fasterfox" extension / Add-on by "spinball" which can be loaded from the normal mozilla extensions / Add-ons pull-down "Tools" menu on Firefox. I tried it and the results are unbelievable. It is an experimental extension, but I've not had any difficulties. If I do, I will add to this reply.

**VERY IMPORTANT NOTE: If set too aggressively this extension has the potential to really load down a server(s) you are trying to reach, possibly crash it if enough users are using tools like this with aggressive settings.  I ONLY use it in the Optimized and Courteous modes which gives network optimizations only within the RFC specs. so as to not exceed the RFC specs. load on servers.**

Firefox 3.0.4 is now exceptionally fast on my system.:)  This worked well for me, hopefully it might help you too.

**UPDATE: 11/29/2008**

Despite the above, difficulties eventually returned.  Firefox became "sticky."  Although loading websites fairly well but still sometimes slow, overall responsiveness of Firefox did not seem the same as in past years.

I have always carried .mozilla forward throughout Firefox upgrades.  Reading about the new release of Firefox, bookmarks, for example, are no longer an .html file, but rather now a database. When upgrading, Firefox now does a conversion of your old .html bookmarks to the new bookmark database.

I had also previously disabled all of my extensions, did not help and a number of standard things.

I decided to try a "from scratch" load of Firefox 3.0.4 again after having renamed, of course, .mozilla to .mozilla-bu. Performance was much better. In my reading, a long story short, I had noticed there are sometimes significant conflicts when going to the later releases, Firefox 3.0.4, and carrying forward your old .mozilla.  I am hoping as Firefox creates new bookmarks in the new database I can return again to copying forward .mozilla for new releases.

I made notes of all of my old extensions and decided to just lose my bookmarks. Also in reading a number of groups said carrying forward extensions now can lead to problems, it is best to just install them from scratch when trying to correct this nature of difficulties.

I Installed the latest Firefox 3.0.4 via Synaptic, then installed all of my extensions via the Firefox extensions database. I now have exceptionally stable performance. As a note, I use a lot of extensions, 28, because of how I use Firefox. All work perfectly, no hangs or conflicts. Although sometimes extensions conflict, this was not the case for me. I think also what might have contributed to my difficulties is over the years I have manually and correctly modified the about:config file to my customizations. Perhaps my old customizations were not applicable to Firefox 3.0.4. Whatever, it all works perfectly now. As a note I also have Fasterfox still installed per my earlier notes.

I hope this might help someone with similar problems.

---

### Post by ender1598 on 2008-11-29
> **Coke0 said:**
> Man, this is still going on... I even downloaded Ubuntu again make a fresh install CD and ran it... still a problem, I followed the link above and used all the performance tips, still no love.  I think my thread title may be misleading though, its not the loading of pages thats slow its the finding the page data or something.  I'm telling you though this is pretty lame :( waiting for 8-12 seconds every time i click a link just for Firefox to find the page.  Please somebody help if you have a spare minute, I swear I'll whore out "Thank You"s like there is no tomorrow if you can solve this.


I've got this exact same problem and it does the same thing in both Opera and Firefox.  It started not too long ago and adding the opendns doesn't seem to have changed anything.  Any help would be appriciated!

---

### Post by RT236 on 2008-11-29
> **ender1598 said:**
> I've got this exact same problem and it does the same thing in both Opera and Firefox.  It started not too long ago and adding the opendns doesn't seem to have changed anything.  Any help would be appriciated!

Hi, I just updated one of my earlier replies above just now.  Maybe you've not seen it yet, just did this.  I share your misery with this...  I think in my case it is now fixed.  I don't know, but maybe something like this below might help you with Firefox 3.0.4...  I hope so...

Firefox for me now became "sticky." Although loading websites finally fairly well but still sometimes slow, overall responsiveness of Firefox did not seem the same as in past years.

I have always carried .mozilla forward throughout Firefox upgrades. Reading about the new release of Firefox, bookmarks, for example, are no longer an .html file, but rather now a database. When upgrading, Firefox now does a conversion of your old .html bookmarks to the new bookmark database.

I had also previously disabled all of my extensions, did not help and a number of standard things.

I decided to try a "from scratch" load of Firefox 3.0.4 again after having renamed, of course, .mozilla to .mozilla-bu. Performance was much better. In my reading, a long story short, I had noticed there are sometimes significant conflicts when going to the later releases, Firefox 3.0.4, and carrying forward your old .mozilla. I am hoping as Firefox creates new bookmarks in the new database I can return again to copying forward .mozilla for new releases.

I made notes of all of my old extensions and decided to just lose my bookmarks. Also in reading a number of groups said carrying forward extensions now can lead to problems, it is best to just install them from scratch when trying to correct this nature of difficulties.

I Installed the latest Firefox 3.0.4 via Synaptic, then installed all of my extensions via the Firefox extensions database. I now have exceptionally stable performance. As a note, I use a lot of extensions, 28, because of how I use Firefox. All work perfectly, no hangs or conflicts. Although sometimes extensions conflict, this was not the case for me. I think also what might have contributed to my difficulties is over the years I have manually and correctly modified the about:config file to my customizations. Perhaps my old customizations were not applicable to Firefox 3.0.4. Whatever, it all works perfectly now. As a note I also have Fasterfox still installed per my earlier notes.

I hope this might help someone with similar problems.

---

### Post by mkvnmtr on 2008-11-29
I just installed FasterFox. Seems to be a good bit faster and I haven't found anything broken yet. I am on 8.04 and have not been having the problems that some of you have had.

---

