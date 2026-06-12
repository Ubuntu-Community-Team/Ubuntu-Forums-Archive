---
title: "Ubuntu 13.04 with NVIDIA GeForce 6150SE nForce 430"
date: 2013-07-01
forum: Hardware
---

### Post by nlippincott on 2013-07-01
I have recently installed Ubuntu 13.04 having previously run 12.04. I had found that Firefox would consume excessive CPU resources, but even without running Firefox, the system is incredibly sluggish. I suspect the problem is the combination of 13.04 with NVIDIA, but I cannot confirm.

Having noticed the problem mainly when running Firefox, I posted the question to Mozilla support. It was suggested that I turn off the option in Firefox to use hardware accelleration. Having done this, my system is now usable, but overall performance still leaves something to be desired. Still sluggish, but at least I can switch to another Firefox tab in under 5 seconds (which might take up to 10 seconds, with the screen graying out as if not responding, before I changed the aforementioned option).

I am running version 304.88 of the NVIDIA driver, but have tried every one of the four available driver options.

Ubuntu 13.04 has a few featured that I wanted, but I am considering dropping back to 12.04 as the performance of that version was excellent. I really hate to say this about Ubuntu, but since installing 13.04, it's worse than using Windows.

I have see a few online references to people having such problems with 13.04, but from most of what I have read, it seems that 13.04 is supposed to perform better than previous versions. From prior experience, I have found that the Ubuntu+NVIDIA combination has always been a headache, but I have always gotten it to work very well, until now.

Are there any sources that state how best to configure this particular graphics card with Ubuntu 13.04? Or am I barking up the wrong tree? Any suggestions will be appreciated. I have expended a lot of time on this, and I really need to return to productivity.

I will also note that I am currently running "top" in a terminal window and, just by typing this post, Firefox is running from 50% to 85% CPU usage. Seems to be a bit high to me, but much better than the 110% or more it would use before disabling the hardware accelleration option.

---

### Post by dino99 on 2013-07-01
should not it be nvidia-173 for that card ?
firefox is a heavy app, maybe chromium is a better choice on that hardware.

---

### Post by nlippincott on 2013-07-01
Thank you for the note, dino99. When I first installed 13.04, I was using nvidia-173 as it was the only one that worked. I have since tried them all, and I figured 304 was the latest so I tried that. I'll switch back to 173, but did not have luck with it.

Yes, Chromium may be the answer. I depend heavily on the Firebug add-on for my consulting work, however. I will note that I had completely removed all add-ons and my Firefox profile in diagnosing the problem, thus removing Firebug from the picture.

Funny thing, I have an old laptop, nearly 10 years old, running Ubuntu 12.04, and Firefox runs beautifully. The system with the problem is a couple of years old, with an AMD Athlon 64 X2 Dual Core 5200+. Granted, not state of the art, but has served me very well until 13.04. So, the whole thing has me scratching my head.

---

### Post by Yellow Pasque on 2013-07-01
I'd try Xubuntu. If that works better, than the graphics requirements of compiz/Unity are what's holding you back.

---

### Post by grahammechanical on 2013-07-01
Ubuntu 13.04 uses 15 - 20% less memory than 12.04. When I was running 12.04 memory usage stood at about 70% of 1GB with just system monitor running. With 13.04 memory usage was down to just over 50%. A key player in all this is the graphic card and the amount of memory on it. 

Regards.

---

### Post by nlippincott on 2013-07-02
Yes, I am convinced that this NVIDIA card is causing all my problems. It is always a struggle getting this card to work, and it's a different path to a working system with each version of Ubuntu. It realy didn't perform all that great on 12.04, but running 13.04 the system is painfully slow and unusable.

I noticed that, in checking the NVIDIA settings, it had a 32-bit memory interface? Would I be better off with the 32-bit Ubuntu version? I'm just grasping at staws here, but I think I'll give that a try.

---

### Post by Yellow Pasque on 2013-07-02
I don't normally recommend throwming money/hardware at problems, but if you have an available PCI-Ex16 slot, try to find a cheap GeForce 8400GS or RadeonHD 5450. I've used the 8400GS and a RadenHD 4550, and those both ran Kwin fine.

---

### Post by nlippincott on 2013-07-02
This computer does have on-board graphics, but I assume if I plug in a different card, the new one will take over. I'll check the documentation on the board.

Thank you for the recommendations. Based on past experience, I do intend to stay away from NVIDIA, so the GeForce is out for me. I'll look into the Radeon line.

Since I may be upgrading (replacing) my graphics, I might want to go with a dual-monitor system. That would really help in my work in Web application development. Any recommendations?

---

### Post by nlippincott on 2013-07-03
I have figured out the problem, and wanted to post a note here for closure. I am actually a bit embarrassed to say that the problem appears to have been dust. The vents on the side of the unit looked very dusty so I decided to take the unit apart and clean it. The heat sink was caked with dust, and I suspect the CPU and perhaps other motherboard components were overheating. After a good cleaning, and a re-install of 13.04 (because I made a real mess of the OS), the system is running great. The NVIDIA driver was still a pain to get going, but that seems to be the case with every install. Nonetheless, problem solved. Thank you to everyone for their input on this issue.

---

