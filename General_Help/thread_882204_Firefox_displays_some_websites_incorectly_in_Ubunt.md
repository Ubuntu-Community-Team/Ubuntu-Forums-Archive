---
title: "Firefox displays some websites incorectly in Ubuntu?"
date: 2008-08-06
forum: General Help
---

### Post by FinalJenemba on 2008-08-06
Whats the deal with that?  Iv noticed it in every version of Ubuntu iv used (current using Hardy 64bit).  Some websites that look fine in firefox on windows or os x look terrible in ubuntu (gamespot.com is a big one).  By terrible I mean images in the wrong place, text in the middle of nowhere, etc.  Anyone know what causes this?  Is it a font issue?

---

### Post by furlabs on 2008-08-10
Hardy uses firefox 3. I imagine your windows and os x machines would have firefox 2. 

FF3 renders a lot of things differently to FF2. It's closer to the w3c specification, but it means that a lot of (badly written) sites that looked fine in FF2 look horrendous in FF3.

---

### Post by Bdanger on 2008-08-10
I have the same issue, I just came on to post about it actually.

I'm running 8.04 and firefox 3.01.  

For example, when I try to visit [www.funnyordie.com](www.funnyordie.com) I get the following:
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=81016&stc=1&d=1218397382[/IMG]

Even worse though, most web pages simply don't load at all.  When I try to access them I get a "Failed to connect" error like the website doesn't exist at all, but then when I try to access it on my normal computer it works fine. [www.break.com](www.break.com) is an example of this.

Also, I've tried using epiphany and for some reason all the same things happen in that too.  This makes me wonder if it is possibly an Ubuntu issue and not a firefox issue.

---

### Post by SunnyRabbiera on 2008-08-10
Epiphany uses the same engine as firefox.
More then likely this is a issue with the gecko used in firefox 3, if you need to you can just go to firefox 2 if needed.
you can just uninstall firefox 3 and replace it with firefox 2.

---

### Post by Bdanger on 2008-08-10
> **SunnyRabbiera said:**
> Epiphany uses the same engine as firefox.
More then likely this is a issue with the gecko used in firefox 3, if you need to you can just go to firefox 2 if needed.
you can just uninstall firefox 3 and replace it with firefox 2.

Thanks for the suggestion.  I just uninstalled 3 and installed firefox 2 and unfortunately I'm getting the same problem with 2.

any other suggestions?

---

### Post by MickS on 2008-08-10
I can't help directly but the site seems OK here using Firefox 3.01 and Hardy, Maybe a setting is wrong somewhere?

Mick

---

### Post by SunnyRabbiera on 2008-08-10
It could be a plug in or something, have flash and java installed?

---

### Post by Bdanger on 2008-08-10
> **SunnyRabbiera said:**
> It could be a plug in or something, have flash and java installed?

I have both installed.. I just removed flashplayer and still no change

I also used profilemanager to delete my firefox profile (and all my addons/extensions) and there is still no change...

---

### Post by furlabs on 2008-08-10
"Failed to connect" doesn't sound to me like a browser issue, sounds like a network issue. Trying opening a terminal and pinging the sites that don't work:
```
ping www.break.com
```
and see if you get dropped packets.

I suspect it's the same issue for funnyordie.com: you can connect long enough to download the text, but the connection is dropped before the stylesheet and images get downloaded.

---

### Post by Bdanger on 2008-08-10
> **furlabs said:**
> "Failed to connect" doesn't sound to me like a browser issue, sounds like a network issue. Trying opening a terminal and pinging the sites that don't work:
```
ping www.break.com
```
and see if you get dropped packets.

I suspect it's the same issue for funnyordie.com: you can connect long enough to download the text, but the connection is dropped before the stylesheet and images get downloaded.

Here's what I got:

```
PING www.break.com (216.69.227.70) 56(84) bytes of data.
From brian-desktop.local (192.168.1.109) icmp_seq=1 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=2 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=3 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=4 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=5 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=6 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=7 Destination Port Unreachable
From brian-desktop.local (192.168.1.109) icmp_seq=8 Destination Port Unreachable

```

```
PING funnyordie.com (72.3.200.168) 56(84) bytes of data.
64 bytes from 72.3.200.168: icmp_seq=1 ttl=113 time=55.0 ms
64 bytes from 72.3.200.168: icmp_seq=2 ttl=113 time=53.5 ms
64 bytes from 72.3.200.168: icmp_seq=3 ttl=113 time=54.0 ms
64 bytes from 72.3.200.168: icmp_seq=4 ttl=113 time=53.9 ms
64 bytes from 72.3.200.168: icmp_seq=5 ttl=113 time=54.4 ms
64 bytes from 72.3.200.168: icmp_seq=6 ttl=113 time=54.0 ms
64 bytes from 72.3.200.168: icmp_seq=7 ttl=113 time=54.2 ms
64 bytes from 72.3.200.168: icmp_seq=8 ttl=113 time=53.0 ms

```

OK, so I guess your right?  So what does that mean? I can access the sites from other computers on this same network why not this one?

---

### Post by Bdanger on 2008-08-11
bump

---

### Post by fragos on 2008-08-11
I develop web sites. There are differences between all browsers. The worst is IE which is filled with non-standard markup. Browsers make a best effort with the markup they are given. Successful sites avoid the use of markup that isn't compatible between browsers. I test my sites with Firefox, IE, Safari, Opera, Epiphany and the Nokia N810. Spread the blame around but don't forget the webmasters.

---

### Post by furlabs on 2008-08-13
@Bdanger:

I'm not sure why you'd be able to ping funnyordie.com but not break.com, unless it's just an intermittent problem. 

Are you on a wireless connection by any chance? You said earlier your normal computer works fine, I assume that means a Windows machine? Are they connecting the same way, eg over WiFi, through the same hub/switch/router, etc? If you have a wired connection, it could be the cable -- have you tried using the cable from your other machine?

---

### Post by Bdanger on 2008-08-13
> **furlabs said:**
> @Bdanger:

I'm not sure why you'd be able to ping funnyordie.com but not break.com, unless it's just an intermittent problem. 

Are you on a wireless connection by any chance? You said earlier your normal computer works fine, I assume that means a Windows machine? Are they connecting the same way, eg over WiFi, through the same hub/switch/router, etc? If you have a wired connection, it could be the cable -- have you tried using the cable from your other machine?

My ubuntu comp with the problem is on a wired connection and my other computer that doesn't have the problem is running windows on a wireless connection.  But they're both connected to the same Linksys.  How would an ethernet cable restrict access to some sites but not others?  I don't understand.

---

### Post by cariboo on 2008-08-13
All the sites you seem to be having problems with, work like they should here. I would suggest trying a new network cable, an intermittent connection could cuase the problems you are having. I have seem similar problems with a bad cable.

Jim

---

