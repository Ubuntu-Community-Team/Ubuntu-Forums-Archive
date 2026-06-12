---
title: "Help me find the problem with my X server, please!?"
date: 2007-09-11
forum: Hardware &amp; Laptops
---

### Post by MaxxJ on 2007-09-11
Hello!

I purchased a Kodicom 4400r card (PCI card with video inputs) for video monitoring. I installed it in my Linux server and restarted it...

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"
Is the message I get now...

If I ask to get the details, it says the following :
"[...]
Module loader present
Markers: [...]
[...]
(WW) VESA: No matching Device section for instance (BusID PCI:6:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found"

Before I added this card, everything worked very fine. Now I really need to have this working.
I'm running on the last Ubuntu version. If you need any more details, just ask, I will be happy to add required details, I'll be watching this often.

Thanks a lot in advance!
- MJ in trouble.


(You can also answer on Yahoo Answers (for 12 pts) : [http://answers.yahoo.com/question/index?qid=20070911160221AAy7OY8](http://answers.yahoo.com/question/index?qid=20070911160221AAy7OY8) ;))

---

### Post by TNakos on 2007-09-11
I was having the same problem and it took me about.... 3hrs to fix. Lots of emacs and coding.

---

### Post by MaxxJ on 2007-09-11
> **TNakos said:**
> I was having the same problem and it took me about.... 3hrs to fix. Lots of emacs and coding.

:confused:
Well, that doesn't help me much, but thanks for reading!

If you ever remember where exactly was the problem, feel free to share!
](*,)

MJ

---

### Post by JC Casiano on 2007-09-11
Question: is this a replacement card or an additional card?  Can you go back to your previous card?  Do you know what chipset is on the card?  Sounds like you'll have to edit /etc/X11/xorg.conf.  I don't know if "xga" or "svga" is a valid option, but perhaps you can replace the boardname in the "Device" section.  Take the usual precaution and make a back up copy of the .conf file before you start dinkin' with it.

---

### Post by MaxxJ on 2007-09-11
Hi JC Casiano,

I had no such card in any of my computers before. It's new. The chipset is CONEXANT bt878 (4 chips).

Well, after a little research, I found a few links with instructions I might try... I don't know if this is going to make things better or worse though.
This is the card : [http://www.linuxtv.org:80/v4lwiki/index.php/Kodicom_4400R](http://www.linuxtv.org:80/v4lwiki/index.php/Kodicom_4400R) (I will probably try what they say tomorrow if nobody can give me precise instructions for Ubuntu 7...)

Thanks for helping and the reminder of making backups, I will do!

If anyone can still simplify all this for me, I would be very grateful!

MJ

---

### Post by JC Casiano on 2007-09-11
Ah, sorry, my mistake, maybe I should enlarge my fonts so that I can read better.  You have a video input adapter, this is not a new video card problem.  Sorry, my mistake...

However, does your X server come back if you remove the card?  Just a curiosity question.  What type of card is it, and does it have it's own video input port?

---

### Post by JC Casiano on 2007-09-11
I just located the information on that device.  This one definitely is beyond my abilities, I've only had experience with various digital video cams and TV cards.  Cool device though...

---

