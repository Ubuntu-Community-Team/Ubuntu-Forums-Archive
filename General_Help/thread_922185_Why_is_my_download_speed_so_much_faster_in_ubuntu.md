---
title: "Why is my download speed so much faster in ubuntu?"
date: 2008-09-17
forum: General Help
---

### Post by schreckles on 2008-09-17
OK, sorry, and I realize this is gonna be pretty off topic, as I'm trying to find the problem with my windows box, not my linux box, but these are the best computer tech forums I know of and I'm sure someone will be able to help me in some way.

I'm trying to download a computer program (Centrafuse front end for my CarPC...it's a direct download, not a torrent or anything else.) that I bought from their website. When I go to download it on my windows box (running vista, but it's a much MUCH faster PC that I built than my linux box) I get speeds of 5-20 kbps, no matter what I try. However, I hop on my ubuntu box (piece of crap laptop that's a few years old) I get speeds of at least 358kbps, usually closer to 600 kbps (this is through a comcast 8 MB service). Does anybody have any idea as to what I should check on my windows box to actually get the speeds I'm supposed to be getting? Both are over a wireless connection, using somewhat similar hardware (once again, crappy laptop versus a fast desktop), as far as specs would go for the wireless adapters. I've run the same type of wireless adapter on other PCs with fine results, but I can't seem to get MY windows box to download at anything above a miserable pace. If anyone could help me, I'd appreciate it greatly.

Once again, I'm sorry for the off topic post, and thanks in advance,
Darrel

---

### Post by IamReck on 2008-09-17
My first guess would be your Windows Firewall.  But don't turn that off.

---

### Post by schreckles on 2008-09-17
> **IamReck said:**
> My first guess would be your Windows Firewall.  But don't turn that off.

That's definitely not it, I get the same results with it off or on. I hate windows' built in firewall and keep it disabled and run a different firewall. Have since XP.

---

### Post by schreckles on 2008-09-17
I'm no newb to Windows or computers in general, I've been building them for a few years now, and always tweaked every version I've ever used of windows to get better speeds, etc, but for whatever reason this has me stumped. Don't think you're gonna go above or below me on this though, it could easily be something I've just never had a problem with before, or it could be an obvious mistake on my part. Any and all suggestions, no matter how complicated are simple are very welcome.

---

### Post by shane19174 on 2008-09-17
Are you using a wireless card? Can you swap out cards and see if it's just the hardware? Otherwise, it might be browser related or a setting in Windows' "network settings."

I suppose it could be lots of things, but maybe you should check these first.

Shane

---

### Post by schreckles on 2008-09-17
> **shane19174 said:**
> Are you using a wireless card? Can you swap out cards and see if it's just the hardware? Otherwise, it might be browser related or a setting in Windows' "network settings."

I suppose it could be lots of things, but maybe you should check these first.

Shane

I don't think it's the card. For whatever reason, my roommate's XP PC is pretty slow as well, using a different card, but not as bad as mine. My old wireless PC card had the same problem, but it died when I got drunk and kicked the big antenna part of it cuz the downloads were slow. Opera, FF, and IE tend to have all the same problems. I don't really know what network settings I should be messing with on Vista, as I'm more used to messing with XP (before they made it "fool-proof" and of course by fool-proof, I mean so convoluted to change anything you'll pass out from screaming.)

---

### Post by worx101 on 2008-09-17
Sounds like a hardware issue

DOn't know about everyone else, but my desktop wireless devices ALWAYS have issues :/

---

### Post by shane19174 on 2008-09-17
Sorry, I don't know either. But I seem to remember that the Vista network settings aren't really so different from XP, just a little harder to discover and manipulate. I don't know either which settings would come into question. If it were me, I would just look through them all and see if could find anything. Not a very professional methodology, I admit...

And if that doesn't work, you can always just do your bigger downloads on the Ubuntu machine and carry them over on a USB stick. Or install Ubuntu on your Vista machine...

One more thought: are file transfers also slow from your local network? Or only from the internet?

---

### Post by prshah on 2008-09-17
> **schreckles said:**
> 
(running vista, but it's a much MUCH faster PC that I built than my linux box) I get speeds of 5-20 kbps, However, I hop on my ubuntu box I get speeds of at least 358kbps, usually closer to 600 kbps 


Maybe vista is downloading something else in the background at the same time? You can confirm by checking the task manager's (Ctrl+Alt+Esc; does it still work in Vista?) network transfer graphs / stats on the resources tab to see total (system-wide) download activity.

Just a suggestion...

---

### Post by schreckles on 2008-09-17
> **shane19174 said:**
> Sorry, I don't know either. But I seem to remember that the Vista network settings aren't really so different from XP, just a little harder to discover and manipulate. I don't know either which settings would come into question. If it were me, I would just look through them all and see if could find anything. Not a very professional methodology, I admit...

And if that doesn't work, you can always just do your bigger downloads on the Ubuntu machine and carry them over on a USB stick. Or install Ubuntu on your Vista machine...

One more thought: are file transfers also slow from your local network? Or only from the internet?

File transfers aren't ridiculously slow, but they aren't fast by any means, and tend to get some sort of error where it'll cut out (more between vista and the xbox360). I think I'm gonna have to agree with the person above and assume it's hardware in this case. Anybody have any suggestions on a really really good wireless adapter for desktop?

---

### Post by schreckles on 2008-09-17
> **prshah said:**
> Maybe vista is downloading something else in the background at the same time? You can confirm by checking the task manager's (Ctrl+Alt+Esc; does it still work in Vista?) network transfer graphs / stats on the resources tab to see total (system-wide) download activity.

Just a suggestion...

Oh yeah...I'm well aware of that trick from trying to cut some of the fat out of vista (and it is quite the chunky OS)

---

### Post by sailor2001 on 2008-09-17
more junk in the vista registry...don't think a registry cleaner will help that bloated os

---

### Post by sailor2001 on 2008-09-17
black viper may help you on your windows...[http://www.blackviper.com/](http://www.blackviper.com/)

---

### Post by forger on 2008-09-17
I think windows operating systems have their own internal download/upload speed regulation system. They probably limit the download/upload so you can browse websites and download window updates and upload files at a file-sharing site at the same time.
Linux doesn't limit you, example I can't browse any website while uploading or downloading at full speed.

---

### Post by IamReck on 2008-09-17
Check out your MTU.  That may have something to do with it.  Does Ubuntu have a MTU?

---

### Post by prshah on 2008-09-17
> **IamReck said:**
> Check out your MTU.  That may have something to do with it.  Does Ubuntu have a MTU?

Yes, very much... in fact see my post on [MTU problems (and solution)]("http://ubuntuforums.org/showpost.php?p=4514356&postcount=12"), but I don't think that is applicable here.. I only had browsing problems, no downloading problems.

---

### Post by bingoUV on 2008-09-17
1. As hardware companies are a bit behind schedule on Vista drivers, maybe your network card's Vista driver is not yet fully optimized.

2. Long ago, in Vista's infancy, it was reported that Vista download speeds got reduced a lot when playing music together with downloading. Critics were quick to blame DRM for this, the internet burned in flames for some days. But I guess it was resolved amicably with Vista supplying a patch on the next Patch Tuesday. Are you fully updated? Try closing media playing applications.

---

### Post by EmanresuusernamE on 2008-09-17
Here's a test for you, burn a live CD of Ubuntu, and then run it on your Vista machine.  Then test out your wireless speeds.  If they're fast with Ubuntu, Vista once again proves it's over-bloated beond compare.  If they're slow, then you probably have a hardware issue.

When in doubt, blame Windows Anything.

---

### Post by rlj1965 on 2008-09-17
Could I suggest that you run this speed test from both machines ([http://www.speedtest.net/](http://www.speedtest.net/)). I am on a Comcrap Speed Tier (8-16 Mb/s) Comcrap connection in NW Philly and get the following results with my desktop running Hardy:

Down 13770kb/s
Up 2174kb/s

My other desktop running Vista gets similar results. Note that Comcrap uses Speedboost and that prolonged downloads of a larger size yield weaker results. 

I would suggest the issue is related to hardware. You could also try tweaking Vista using TCP Optimizer. )[http://www.speedguide.net/downloads.php](http://www.speedguide.net/downloads.php))

Read this thread... ([http://technet.microsoft.com/en-us/library/bb878127.aspx](http://technet.microsoft.com/en-us/library/bb878127.aspx)) it suggests that Vista and Wireless are more of a problem than Vista and Wired connection. Also this: ([http://forums.speedguide.net/showthread.php?t=215629](http://forums.speedguide.net/showthread.php?t=215629))

Please report back any improvements. Good Luck

Pharoah

---

