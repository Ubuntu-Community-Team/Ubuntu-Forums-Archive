---
title: "ATI - Dual head (fglrxconfig)"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by SWAT on 2005-05-13
I read/used a lot of howto's about getting ATI graphics to work, but I'm left with one problem. When I use fgrlxconfig, then my dual screen works partially. It works fine when my primary is a TFT and my secondary is a CRT. When I switch the values; CRT primary and my TFT secondary, then my CRT works and my TFT get black lines all over the place. It's strange because the option CRT/TFT doesn't exist in the config tool either (but all other combinations TFT/CRT/TV-out are there  :mad: )
Is this a ATI problem or will Xinerama also have these problems? I'm going to try Xinerama and I will post here, if it works, or not. If anyone has tips I'm all ears!

---

### Post by dacosta123 on 2005-05-13
Hi,

I almost switched back to w2k whilst trying to get my ATI 9800 Pro to work in BigScreen mode. After many wasted cycles i found a post (on the unbuntu forums) that explained it all pretty well *and* there was a xorg.conf attached. (Still don't understand why there's no sticky on it  :???: )

Please find attached my own xorg.conf that works with the following:
- restricted kernel (for it contains the fglrx stuff)
- the fgrlx package (obviously)
- An ati card ( ;-) )

---

### Post by SWAT on 2005-05-14
Dacosta123, as I see in your config file you're using 2x CRT. That works, I know that for a fact.
My problem is that I want my CRT as primary and my TFT/LCD as secondary. That's the only option that somehow won't work. All other possibilities are present in the fglrxconfig tool; so TVout/TFT/CRT options are all available. EXCEPT the one with CRT as primary and TFT as secondary. Perhaps there is a workaround for this?
A lot of my co-workers use CRT-TFT set-ups at their homes, and this is a  reason for them NOT to switch to Ubuntu/linux.... Can anyone help me?

---

### Post by dacosta123 on 2005-05-14
Having run in more than one 'interesting' things using linux i just wondered whether it's the CRT + TFT combo that doesn't work or just specifically the <CRT, TFT> (asking whether TFT-CRT does work?).

Guessing that there are no funnies in the log either?

I'm sorry i can't help you further because i only have ctr screens and not 1 tft.

Good luck.

---

### Post by SWAT on 2005-05-14
CRT (primary) + TFT (secondary) => Does NOT work
TFT (primary) + CRT (secondary) => DOES work

---

### Post by dacosta123 on 2005-05-15
Hmm, i wish i could say i'm surprised but i'm not

Having said that however, i guess it's now just down to switching stuff around a bit and you should be ok, right  :smile:

---

### Post by SWAT on 2005-05-15
Switching monitors around isn't a possibility, because I don't have the space. Another disadvantage of running TFT as primary is that I can't watch my movies decently, because my CRT has far better quality. The videos are alway displayed on the primary display, that's why I want to keep my CRT primary.
Another thing, is this a config problem or a driver problem? (ATI's fault?)

---

### Post by dacosta123 on 2005-05-17
Since the config is just a way of telling the driver what to do i would be inclined to suggest that the fault lies with ATI. Seems like someone went for a cop of coffee after  the first combo worked and forgot to take care of the second combo as well  ;-) 

Strange though that you can't get the movies to come up on the second monitor.
Esp. since y'r working with one framebuffer (at least my file is). That would imply just dragging the window to the appropriate monitor. Or doesn't it?

---

### Post by SWAT on 2005-05-17
I used to work with 2 seperate devices mode, because that worked better for me. I'll try the bigscreen mode again soon.

---

