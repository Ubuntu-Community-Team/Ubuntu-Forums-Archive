---
title: "Problem with Cheese video recording"
date: 2010-07-12
forum: Hardware
---

### Post by julianb on 2010-07-12
I have found a problem that occurs in Cheese. I can't record video. "top" shows high processor usage (not entirely consistent, but usually 100% of one processor core, sometimes substantial work on the other processor as well). Cheese becomes nonresponsive while using lots of processor cycles.

Tested with several different ASUS EEEpc's running Ubuntu or Fedora. The problem occurred regardless of desktop environment, Gnome, LXDE, Xfce. They have two different built in webcam models, 0.3 megapixel and 1.3 megapixel.

Problem might be related to video codecs or the low-end processors on these machines (tested on 900mhz celeron M and 1.6mhz Atom). Using Windows, I can record video on another eeePC using the same processor.

If you can help me resolve this issue, I'd appreciate it. 

If you'd like to give me advice on where to do a bug report & how, please do.

---

### Post by AltomineUK on 2010-07-12
It's not the processor...... I run Ubuntu Desktop edition on my netbook which has an Intel Atom N270 @ 1.60 GHz and everything works fine (including all the peripherals). I can only imagine it's probably due to whatever process is taking 100% of your processor's resources, however i'm not sure..... but it's NOT the processor.

---

### Post by julianb on 2010-07-12
Have you been able to record video in Cheese?

---

### Post by AltomineUK on 2010-07-12
Yes, I'm able to record videos but it is very slow...... cheese is working quite well and does not become unresponsive. My system monitor states that CPU usage is around 55-68%.

I think some of the earlier version of Intel Atom processors might have some performance limitations as I'm using the latest N270 Atom processor that came out just before Intel phased out the N270s.

---

### Post by AltomineUK on 2010-07-13
Ok i think I know a make shift solution for this.....

Change the resolution with which the videos are taken...... I got the best results with resolutions between 176 x 144 and 160 x 120. At these resolutions the processor copes better (due to lower resource demands required for encoding, compression etc...) and there is little or no jerkiness although the image quality is slightly compromised. Photo capture works in all resolutions.

---

### Post by julianb on 2010-07-13
Thanks for getting back to me! I was not aware of the resolution setting in Cheese before. On the 900mhz processor, cheese is still failing to create files that I can play back. On the 1.6ghz atom, it takes about ten seconds before the speed picks up so the machine can record properly, so the file has 10 seconds of "video" that consists of a still image.

---

### Post by AltomineUK on 2010-07-13
> **julianb said:**
> Thanks for getting back to me! I was not aware of the resolution setting in Cheese before. On the 900mhz processor, cheese is still failing to create files that I can play back. On the 1.6ghz atom, it takes about ten seconds before the speed picks up so the machine can record properly, so the file has 10 seconds of "video" that consists of a still image.

Hmmmm 10 seconds eh?.... if you can edit out the first 10 seconds all is well :D

Personally I use my netbook for non-video purposes so I can't really make a good judgement on this..... can you video chat using empathy or pidgin or any such programs on the Atom without any 10 second delay?

---

### Post by brocktice on 2010-08-20
I'm having this problem on a Core i7 so I doubt it's the processor that's causing the issue.

---

### Post by afrodeity on 2010-08-24
I have this problem with a friends samsung NP-R522 which has a Pentium duel core 2.0ghz CPU and Intel graphics mobile 4 series. Cheese was working perfectly in Karmic, but when he upgraded to lucid, the problem arose. Changing resolution doesn't work. Sound and video playback appear to be out of synch and the video in cheese just sticks after three seconds.

---

