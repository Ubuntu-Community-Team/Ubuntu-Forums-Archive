---
title: "Inspiron e1505, Ubuntu, broke"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by Taigrr on 2006-10-30
Well, I think Ubuntu broke my laptop.

I bought an Inspiron and upgraded the wireless purely because people were saying it worked, and it doesn't. Edgy especialy.

I think Dapper went okay, apart from having never gotten WiFi to work. But Edgy really messed with things. I figured it would be more updated, and it was! It at least detected the Intel 3945 was there. However, it really messed with the screen. Completely and totaly distorted. 

Ever since trying to install Edgy, there's an annoyingly high-pitches squeel comming from what I can assume to be the processor. I really have no idea, it's like that shreek you hear on a regular huge TV. But on a laptop.

It was only after the complete failure of Edgy that the noise was aparent. Maybe I just overloaded the laptop with too much installing, but who knows.


I'm severely disapointed with Ubuntu, which has been held in high reguard as my favorite distro of all time. In fact, I think Linux  is the most worthless pile of cow dung, unless it's Ubuntu. I also hold Ubuntu much higher than Windows. So i'm kinda screwed.

Dell is sending me a replacement laptop.


Anyone else have such a problem? My distrust and avoidance of Dell has been long-upheld, and it shocked me that they were just going to send me another laptop. No arguments or anything!

---

### Post by pvegdahl on 2006-11-02
I also just got an E1505. Getting the video to work properly at 1680x1050 took a bit of doing, and there are still many other quirks I'm trying to work out. I had to piece together information from several guides and forums before I had anything working. I'm fairly confident that it can be done, so best of luck to you with the replacement laptop!

---

### Post by davebed on 2006-11-02
Taigrr,

I also have an e1505 / t2300e / ATI x1400 / Seagate 100GB 7200rpm.

I experienced the deafening high-pitch you described out of the box - with Windows XP. I played with it for a few weeks and traced it to the multi-core processor. When i disabled the dual core in the bios, the sound went away.

Anyhow,they also sent me a new one, no questions asked (I'm very happy with Dell's service :) )

I'm on my 3rd week of Ubuntu with this machine (my first real Linux experience). I've had pretty good results - though obviously some minor tinkering with the video card / wifi / bluetooth and Laptop-mode to controll the frequency scaling of this unit. The fans also required some tweaking with GKrellm and the dell plugin, though I'm not convinced the fans won't kick in on their own without it. 

The one thing I'd say to *anyone* who wants to get Ubuntu working on this unit is to get some temperature monitoring plugins going and just keep an eye on the mercury - i've heard a few horror stories (your's maybe one - hard to tell), but like I said, I'm not totally convinced that the fans won't regulate themselves.

Aside from the, the only *real* issue with this unit, as I've seen on the Dell forums, is that there is no 2nd heat pipe for the hard drive, as there is in the 17" model. This has tragic consequences for those of us who chose the Seagate 7200 rpm drive. The heat just builds and builds as we helplessly cook our hard drives at over 55 deg.C.](*,)  From what I can see, Dell is not adressing this issue, other than replacing cooked drives that are within warranty. Standard 5400rpm drives should be fine.

Good luck.

---

### Post by en3rgy on 2007-06-01
> **pvegdahl said:**
> I also just got an E1505. Getting the video to work properly at 1680x1050 took a bit of doing, and there are still many other quirks I'm trying to work out. I had to piece together information from several guides and forums before I had anything working. I'm fairly confident that it can be done, so best of luck to you with the replacement laptop!I have an e1505 and the same video problem. Mines a Go7300. What did you do to get yours to work @ 1680x1050 please?

---

### Post by pvegdahl on 2007-06-01
Hi en3rgy,

Unfortunately I'm not sure I'll be able to help you much. My laptop has the ATI X1400, and to get 1680x1050 working, I installed and set up the ATI binary drivers. I would expect your solution to be along the same lines. Install the NVIDIA binary drivers and restart your X-server. If that doesn't automatically fix it, you may have to mess with /etc/X11/xorg.conf.

Best of luck to you. If you do figure out how to fix it, post your solution for the benefit of the next person, or perhaps even for your own benefit if you end up reinstalling Ubuntu at some point.

---

