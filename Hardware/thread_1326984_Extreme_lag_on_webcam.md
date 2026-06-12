---
title: "Extreme lag on webcam"
date: 2009-11-14
forum: Hardware
---

### Post by oldsoundguy on 2009-11-14
Have a brand spankin' new Logitech 9000 web cam I just installed on 8.4. (USB)(USB-2) 

Works beautifully as far as the picture AND sound are concerned with the VERY NAGGING EXCEPTION of a severe video lag.  From what I have determined, this is a COMMON issue, but have been unable to find anyone posting anything near a solution other than writing 30 lines of code and MAYBE it MIGHT work.

Any clues and help appreciated!

(this is not an earth shaking critical issue, but makes Skype a real challenge!!)

---

### Post by oldsoundguy on 2009-11-15
OK, am bumping this a bit early as I HAVE found some information.  Seems that the camera is an HD 2mp camera and the frame rate has to be adjusted. (wish the Logitech software came in a .deb package!!) 

Now the question is, just were and how can I make the adjustments?
Is there some "universal camera control" package I have missed installing (again 8.04 LTS)

---

### Post by oldsoundguy on 2009-11-16
still no more information found!

Somebody has had to have dealt with this since it IS on 8.04!

---

### Post by oldsoundguy on 2009-11-17
cannot believe that there are NO people experience this issue other than myself. (at least here)  Google is filled with them and none have been given an answer!

---

### Post by oldsoundguy on 2009-11-20
This thread is the prime example of why a lot of newbies start using Linux and then quit.  There IS an answer to the problem, but somehow it is considered too petty to respond to it?

With all of the moderators keeping folks in line, it would seem that at least ONE of them would have a clue as to what should or could be tried to address the issue. Or at least could suggest a path to follow for investigation.

---

### Post by Silvernail on 2009-11-23
I do so agree with your comment. Its interesting that I can get better  support for ubuntu problems on  'linuxquestions' than here.

---

### Post by ubunxpm on 2009-11-24
Hello,
I have a quickcam pro and mine is not responsive either. I found a tip at cheese wiki though it did not help me. I'll share it with you anyways.

run gstreamer-properties

Set default video output plugin to X11/XShm/Xv
if it is not already set that way.

Good luck

---

### Post by oldsoundguy on 2009-11-24
Thanks, but you missed it .. the new camera WORKS .. has a great picture, sound works.

Just that VERY ANNOYING delay in the video.

and I really HATE to mention, but it does NOT do that (AS BAD) in Windows using the Logitech program/drivers.

---

### Post by Silvernail on 2009-11-25
> **oldsoundguy said:**
> Have a brand spankin' new Logitech 9000 web cam I just installed on 8.4. (USB)(USB-2) 

You list 8.4 here but show 9.10 under your avatar. ???

Also what is the speed of your  CPU?

---

### Post by oldsoundguy on 2009-11-25
> **Silvernail said:**
> You list 8.4 here but show 9.10 under your avatar. ???

Also what is the speed of your  CPU?

I have seven working computers:
One running 8.04LTS as the main control computer.
(it is running a hyperthreaded 3.06 CPU with 2 gb ram.)
Two running 9.10 to see how it works.
One running Mint Gloria (a low powered old and slow unit I use for testing .. called the "Crash Test Dummy")
One running Mythbuntu 9.04 that I just can't figure out yet and get working as a PVR. (I will, eventually)
Two running Windows XP that hardly ever go on line.  Used primarily as storage machines and for running photography programs that do not run on Linux.
All networked and sharing 5 printers in various locations.

---

### Post by Arup on 2009-11-25
Try installing luvcview, its a control applet for Logitech cams.

---

### Post by oldsoundguy on 2009-11-25
> **Arup said:**
> Try installing luvcview, its a control applet for Logitech cams.

same story .. way too much lag (that DID improve it somewhat). And I may have to settle for that setting until the REAL stuff shows up since Logitech is co-operating with Linux.

BTW, before somebody jumps in and suggests Ekiga, Did that one too, with the same results.

---

### Post by oldsoundguy on 2009-11-30
Sure would like to get this camera working in Ubuntu other than taking snaps and making the recipient sea sick with the motion tracing!

---

### Post by oldsoundguy on 2009-12-15
Darn, still no "fix" for this?

---

### Post by Mrhnhrm on 2009-12-19
I used to have a similar problem with a 04f2:b159 Chicony webcam built into my laptop. You could try what I've done - try using v4l2ucp program, I believe it's available through Ubuntu repositories. Use it to check some options related to your webcam - it's possible that some default setting controls exposure duration per frame and makes this value just a little bit too high. Worked for me at least.

---

### Post by no2498 on 2009-12-31
try using it on wxcam

---

### Post by oldsoundguy on 2009-12-31
really do NOT like running beta anything on my main computer.  But thanks.

---

### Post by Forbees on 2010-03-04
same prob but i found the answer

in cheese, lower your resolution

edit>preferences 

sadly i have to be on 352x288 pixles to get rid of the lad on my laptop

---

### Post by oldsoundguy on 2010-03-04
> **Forbees said:**
> same prob but i found the answer

in cheese, lower your resolution

edit>preferences 

sadly i have to be on 352x288 pixles to get rid of the lad on my laptop

NO preferences under edit in my version of Cheese.

---

