---
title: "Lenovo ThinkPad E520 display problem"
date: 2011-06-22
forum: Hardware
---

### Post by tonymoloney on 2011-06-22
I've just bought the above laptop and installed Ubuntu 10.04 and JoliCloud on it. The display under Ubuntu is terrible. When I click on System/Preferences/Monitors it comes up as "Unknown" with a display resolution of 1024 x 768 and nothing better. This is not much better than Windows95 could achieve and I'd like to make it much crisper. Any help???

---

### Post by tonymoloney on 2011-06-22
Bump!
Sorry having to bump this, but it seems that when I put in a request from Western Australia, by the time the rest of the world wakes up, my request has disappeared from the front page of the forum.
And just to add tp my request, I have just found that JoliCloud also sees my monitor as "unknown" but gives it a display resolution of 1366 x 768 (16:9) which looks much better.

---

### Post by CTBuckweed on 2011-06-26
> **tonymoloney said:**
> Bump!
Sorry having to bump this, but it seems that when I put in a request from Western Australia, by the time the rest of the world wakes up, my request has disappeared from the front page of the forum.
And just to add tp my request, I have just found that JoliCloud also sees my monitor as "unknown" but gives it a display resolution of 1366 x 768 (16:9) which looks much better.

I just bought my son a Thinkpad E520. With Ubuntu 10.04, I can't figure out how to get the display into 133x768. It runs at 1024x768. How can I stretch it out?

The 1024x768 display that 10.04 does is 4x3 mode but it is stretched out to full screen, rendering all things too wide looking.

---

### Post by pointym5 on 2011-07-05
What is the output from running xrandr?

---

### Post by tonymoloney on 2011-07-15
Not sure if you're talking to me or Buckweed, but here's my output from xrandr:

Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   960x600         0.0  
   800x600        61.0  

which is all that is shown by System/Preferences/Monitors

Tony

P.S. Sorry about the slow response. I've been in hospital.

---

### Post by CTBuckweed on 2011-07-18
> **pointym5 said:**
> What is the output from running xrandr?

Here is my output of xrandr:

Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   960x600         0.0  
   800x600        61.0  

I have tried to add 1366x768 via the instructions at --- [http://www.linuxquestions.org/questions/linux-desktop-74/ubuntu-10-04-xandr-cant-change-video-resolution-808058/]("http://www.linuxquestions.org/questions/linux-desktop-74/ubuntu-10-04-xandr-cant-change-video-resolution-808058/")

I changed the example to settings that reflect 1366x768. I don't understand the refresh rate or the other parameters. My attempt didn't take. The thing is, I don't understand the relationship between xrandr and cvt, nor do I really know what they do. I suppose that they modify some X11 config files.

I would like to understand this but I can't find any helps / documentation on the subject.

---

### Post by CTBuckweed on 2011-08-05
I solved the Lenovo E520 display problem -- I upgraded from 10.04 to Natty, 11.04. The display came up as 1366x768 when I tried the live CD, so I upgraded it.

Now, everything is OK --- EXCEPT --- the wireless LAN does not work. It seem to not even be recognized. The laptop has a built-in Intel built-in wireless hardware. Windows 7 reports the wireless hardware as "Intel(R) WiFi Link 1000 BGN".

The wireless worked fine with 10.04 but not with 11.04.

Now, I work on that....

---

### Post by marshcast on 2011-10-18
Hey! This would be great to sort out. I have the same problem, it means I have no consoles (alt+f1 etc)

this is my xrandr output, there's no offered drivers in system>hardware drivers :(

Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   960x600         0.0  
   800x600        61.0 

lspci only offers:

00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)

can anybody offer any ways forward? I don't want to upgrade, as i want the stability of LTS.

is there a decent thread for graphics-sorting that anyone can reccomend?

thank you :D

M.

---

### Post by CTBuckweed on 2011-10-21
Well, if you do go ahead and upgrade to 11.04, you may have the same problem with your WiFi not working, refer to to the thread/post to fix the WiFi --- [http://ubuntuforums.org/showthread.php?p=11121162#poststop](http://ubuntuforums.org/showthread.php?p=11121162#poststop). Now it all works.

---

### Post by marshcast on 2011-10-23
have upgraded to 11.04, no wifi probs, but I upgraded to wicd with ubuntu (network-manager I've always had probs with on random routers). Needed to use dconf to put wicd in toolbar in unity (google it, it's easy enough to find and do).

unity received well by clients so far, about an hour each so next week'l be the tester... cross yr fingers ;)

cheers for threads/advice,

M.

---

