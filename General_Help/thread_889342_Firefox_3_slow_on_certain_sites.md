---
title: "Firefox 3 slow on certain sites?"
date: 2008-08-14
forum: General Help
---

### Post by TheOrangePeanut on 2008-08-14
There are two sites I frequent that scroll extremely slow using Firefox 3, Facebook and a private forum I go to.  This is with my older computer with a Radeon 7000 and the open source ati drivers, and with my newer computer with a Radeon 9500 Pro and fglrx.  Does anyone else experience this..?

---

### Post by Pro-reason on 2008-08-14
Yes!

I've just installed Ubuntu for someone, and she has immediately reverted to Windows because she complains that Facebook is slow on Ubuntu.  She tried Opera, but that was slow too.  On XP, she uses Firefox 3 too, but it seems to be running at full speed.

Whatever can we do about this?  I spent a long time setting it up and evangelising, but she finds Ubuntu unusable because of this!  Very annoying.

P.S.  I think it's OK on my own computer.  I have no idea what I would have done differently when installing it.

---

### Post by Thedjatclubrock on 2008-08-14
In my experiances, web pages will slow down if they contain any Flash Media. This applies to Fbook, Youtube etc.. Am I making sense?

---

### Post by Pro-reason on 2008-08-15
Yes, it probably is Flash.  I should try disabling it and then see if the browser gets faster.

---

### Post by Azegul on 2008-08-15
Try this. It might help:)


[http://ubuntu-snippets.blogspot.com/2008/07/jerky-firefox-scroll-try-disabling.html]("http://ubuntu-snippets.blogspot.com/2008/07/jerky-firefox-scroll-try-disabling.html")

---

### Post by morbid_bean on 2008-08-15
Isn't face book like that one website???? The users pages are just LOADED with random little animations, videos, pictures, audios, etc.  I would think that really slows it down.

---

### Post by Pro-reason on 2008-08-16
> **morbid_bean said:**
> Isn't face book like that one website???? The users pages are just LOADED with random little animations, videos, pictures, audios, etc.  I would think that really slows it down.

Facebook isn't MySpace.  Most of the time, you're not on a profile page but on an application page, with just one Flash app.  Linux Firefox ought to be able to handle it.  Windows Firefox can.

---

### Post by fart_flower on 2008-08-16
I also find Firefox horribly slow under Linux.

Because I'm getting old, I often browse fullscreen (F11) and increase the font size using "Ctrl -/+" or "Ctrl scroll-wheel".  On some pages (often depending on length) it can take several seconds (!) to redraw the text when I enlarge the fonts.  (Disabling image zoom can speed things up, but not by much.)  In comparison, using this same computer with Windows, the redraw time is almost instantaneous.

Furthermore, pages with a fixed backgrounds can become almost unusable when scrolling.

And like one of the posters above, I know of several people who tried Ubuntu 8.04 for a short while, but went back to Windows because Firefox is so terribly slow on many sites, including Facebook.  (Which I've personally never used, but oh well...)

---

### Post by fart_flower on 2008-08-16
Apparently this is an nVidia issue.  (And the open source nVidia drivers aren't much better.)

[http://www.phoronix.com/forums/showthread.php?t=11044](http://www.phoronix.com/forums/showthread.php?t=11044)
[http://www.nvnews.net/vbulletin/showthread.php?t=114858](http://www.nvnews.net/vbulletin/showthread.php?t=114858)

---

### Post by johnny9794 on 2008-08-16
On my dell inspiron 1300 with 512 MB ram + ubuntu 8.04.1, firefox runs sloggish and at 60 or 70 cpu percent on facebook, on the other hand with my Desktop System which is p4@3.75Ghz with 2 gigs of ram + ubuntu 8.04.1, Firefox Runs like a champ on facebook :).

---

### Post by starcannon on 2008-08-16
I have nvidia graphics, use youTube, and google video a lot, don't really go to facebook (and since I don't have/want an account can't seem to open any of its user pages). But I have no performance issues here. Pages load fast and function correctly for me.

---

### Post by fart_flower on 2008-08-16
Yeah, pages load fine and usually scroll fine, so long as the background image is not static.  However, zooming fonts and/or graphics is glacially slow -- it can literally take several seconds on larger pages.

---

### Post by Pro-reason on 2008-08-16
If it's all an Nvidia issue, then that would explain the difference in behaviour between my computer and the one I was talking about before.  I have a 7900 GS and she has an FX5200.  The older card might have more trouble with rendering pages when Flash is enabled.

I have the slow zooming issue too.  The other computer also has it, but not as much.  It takes about a second on mine and half a second on hers.

---

### Post by avra911 on 2008-08-17
Another reason that makes Firefox very slow on Ubuntu:

'DNS problem for people using routers. By default the DNS server is the IP of the router and that is making firefox runs slow. If you can manualy put the DNS servers of the ISP provider it will run like an UFO.'

I must say that Ubuntu should increase network-manager. I personaly can't insert a manual configuration of my wireless connection because it stops working. Fedora 9 is using another netowrk manager where i was able to put a static ip, the dns of my isp and everything worked. i still can't make it work on ubuntu. i tried editing 'etc/network/interfaces' and no luck.

why this thing is so hard in ubuntu!?

it seems the dns servers are automaticaly owerwrited by /etc/dhcp3/dhclient.conf
i uncommented the line
"prepend domain-name-servers x.x.x.x,y.y.y.y;" and replaced xxxx and yyyy with my isp dns and now everything is great.
firefox is better then ever

best regards,
r

---

### Post by majabl on 2008-08-25
> **TheOrangePeanut said:**
> There are two sites I frequent that scroll extremely slow using Firefox 3, Facebook and a private forum I go to.  This is with my older computer with a Radeon 7000 and the open source ati drivers, and with my newer computer with a Radeon 9500 Pro and fglrx.  Does anyone else experience this..?

Also happening for my on my parents' computer (Athlon 2800+ with 1.25GB RAM).  It seems to be caused by Flash, because disabling Flash (Tools>>Add-ons>>Plugins>>Shockwave Flash>>Disable) turns their PC's CPU use down from ~90% to ~30%.  However, this still seems on the high side with Firefox performance still a little sluggish.  More tellingly, Firefox performance is still not as good as it is if this computer boots into Windows XP, but I suppose it's fixed the problem enough for it to be tolerated.

---

### Post by djinn1973 on 2008-08-25
back to top

---

### Post by fragos on 2008-08-25
If the problem is with flash then it isn't a Firefox issue -- it's an Adobe flash issue. From my perspective I don't see Firfox 3 as poor performer. Performance of a particular site has a lot to do with how it's implemented and the size of the files that must be downloaded. Let's not forget the impact of the speed of your Internet connection -- I've a very fast cable connection. That being said, I've not had an MS OS on any of my systems for many years and can't speak to the difference in performance between Windows flash and Linux flash. Having a faster flash implementation would'nt change that for me. My Internet browsing performance more than meets my expectations.

---

