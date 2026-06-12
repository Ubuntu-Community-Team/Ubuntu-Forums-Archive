---
title: "SSD Drives and Touch Screens"
date: 2010-08-08
forum: Hardware
---

### Post by Donn224197 on 2010-08-08
i'm rather new to ubuntu and i'm not that much of a nuts and bolts kinda user. 
i first starting using it cause my windows 7 rc1 crashed and my hard drive was failing.
now i can't see my using anything else.
that point aside i was wondering about two items.
1. i recently got my girlfriend warmed up to the idea of switching from 7 to ubuntu. (she hates change) she's real tired of it being slow.
my question is that she has an HP touchsmart laptop and i'm very sure that she would like to retain usage of her screen, stylist, and still have her screen orientate to the way she has the screen (you can lay it flat like a tablet). from what little i have read so far the touch part isn't as simple as installing, what would have to be done (if it can) to retain this functionality? as well, what for the screen? 
2. as stated in the beginning, my harddrive is on it's last leg. it goes static for a minute every 5 or so then works again. now i'm starting to see some data "drop off" and i need to act fast to keep my laptop alive. 
my question to this is are there any problems with SSD drives and ubuntu? 
off the top of my head it wouldn't seem to have any but again stated above i'm not too keen to the world of ones and zeros. at the moment i'm running 64bit with 6gigs and 3.5 dual. i doubt that has little to do with hard drive compatibility but you never know. as well, it's and HP dv5.
thanks 
Donn

---

### Post by utilitytrack on 2010-08-08
Hello, I not understood nothing. Do you can to formulate the question clearly?

---

### Post by S.R on 2010-08-08
As to part two of your post. Back up your files that you want to keep ASAP. 

Any one reason you are going with a solid state drive? Just curious increased cost and less capacity. I have seen several HP's with drive failure. You can buy a replacement drive for little of nothing.

---

### Post by Favux on 2010-08-08
Hi Donn224197,

With a default Lucid setup the TX2z stylus should work out of the box and so should touch.  The stylus is assigned to the linuxwacom driver by the 10-wacom.conf, which might need some tweaking.  Single finger touch falls through and is picked up by the evdev driver touchscreen (or touchpad?) catchall in the evdev.conf.

So you can make a hybrid screen rotation script that picks up both the wacom controlled stylus and the evdev controlled single finger touch.

It gets a little more complicated if you want to go to multi-touch or use the linuxwacom drivers two finger gesture support.

See the [Ntrig HOW TO]("http://ubuntuforums.org/showpost.php?p=7863677&postcount=1").

---

### Post by Donn224197 on 2010-08-08
> **S.R said:**
> As to part two of your post. Back up your files that you want to keep ASAP. 

Any one reason you are going with a solid state drive? Just curious increased cost and less capacity. I have seen several HP's with drive failure. You can buy a replacement drive for little of nothing.

most of the reasons i'd care to go to a SSD drive is cause of the LOW power consumption, and SPEED! haha.
i don't really keep anything important on my laptop as stated before the drive is dying. so having gone 4 months with this practice i'm more then used to using minimal space.
i have a 320 external for all my music and important data. the only thing that is really on my laptop are my links, podcasts, and a picture for my background. 
aside from from the two benefits stated above i also would love some more stablity, i pull alot of data and host alot as well so my laptop is ALWAYS on. it's been my experence that 2.5 drives don't like being on for 2 months at a time. (and believe it or not i'm not talking of bittorrent)

---

