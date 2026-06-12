---
title: "webcam troubles"
date: 2010-06-20
forum: Hardware
---

### Post by leopex on 2010-06-20
Hey all, I am having some troubles with my webcam, in the amsn configure webcam window, it says after configuring that i am behind a firewall. I tried too turn off my firewall in my router, still it dont work, is there a firewall build into ubuntu 10.4 wich is blocking this?

Tanks for answers.

---

### Post by tacotime on 2010-06-20
> **leopex said:**
> Hey all, I am having some troubles with my webcam, in the amsn configure webcam window, it says after configuring that i am behind a firewall. I tried too turn off my firewall in my router, still it dont work, is there a firewall build into ubuntu 10.4 wich is blocking this?


This is under the amsn FAQ page, try that and see if it helps-
[http://www.amsn-project.net/wiki/FAQ#You_are_firewalled_or_behind_a_router](http://www.amsn-project.net/wiki/FAQ#You_are_firewalled_or_behind_a_router)

if it doesn't check out this thread on ubuntu forums-
[http://ubuntuforums.org/showthread.php?t=168140](http://ubuntuforums.org/showthread.php?t=168140)

This guy says he enabled port 8080 on his router and it worked, so try that.


There is a firewall built in called iptables, it's turned off by default. If none of the above work for you, you may want to play with its settings. 
[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

---

### Post by irv on 2010-06-20
A simple test to see if you webcam is working is to type this command in a terminal or hit the Alt/F2 key and type:
```
mplayer tv://
```
You must have mplayer installed. This will only test you webcam not the firewall.

---

### Post by leopex on 2010-06-20
Well, i am not behind a firewall (in the router) It is all disabled.
My webcam is working with cheese, and in the webcam testing. I cant see others webcam either... So i cant quite understand what it wrong here---

---

### Post by tacotime on 2010-06-20
Can you take a screen shot of exactly what's happening?

---

### Post by irv on 2010-06-20
I thought I would play around with aMSN to see if I could get the webcam to work on my system and after setting up an account login on and setting up my webcam here is the message I got.
> Audio/Video call capabilities have been disabled in this protocols again and disabled access to their SIP servers, blocking aMSN from giving you access to this feature.
It is not on my end but on MSN's end. they are blocking audio and video. Microsoft is at it again.

---

### Post by irv on 2010-06-20
These are the two screens I get. If this is what you are getting then it is not your system.
[ATTACH]161047[/ATTACH]

[ATTACH]161048[/ATTACH]

---

### Post by tacotime on 2010-06-20
> **irv said:**
> I thought I would play around with aMSN to see if I could get the webcam to work on my system and after setting up an account login on and setting up my webcam here is the message I got.

It is not on my end but on MSN's end. they are blocking audio and video. Microsoft is at it again.

I think we can mark this is solved then?

---

### Post by irv on 2010-06-20
You can do video conferencing with Skype.

[http://www.skype.com/intl/en-us/support/user-guides/call-with-video/]("http://www.skype.com/intl/en-us/support/user-guides/call-with-video/")

---

