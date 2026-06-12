---
title: "Suggestion for webcam to use with Skype"
date: 2010-03-29
forum: Hardware
---

### Post by CaKiwi on 2010-03-29
Can anyone suggest a modestly priced webcam compatible with Ubuntu which I can use with Skype? I have a Winbook webcam which works well with Windows 7 but, not surprisingly, does not work with Ubuntu. (At least, I have not been able to make it work)

---

### Post by gordintoronto on 2010-03-29
Have you tried Cheese with your webcam?  If that works, it can probably be made to work with Skype, perhaps by using the command:
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

If not, my webcam works.  It's a no-name I bought a couple of years ago in China for the equivalent of $10. Its ID:
Bus 006 Device 002: ID 0ac8:303b Z-Star Microelectronics Corp. ZC0303 WebCam

---

### Post by CaKiwi on 2010-03-30
I tried 

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

with my current webcam but it didn't help. Any other suggestions?

---

### Post by harrisonk on 2010-03-30
[SIZE=2]The video camera I have (again a no name brand I don't know any specks) Works with that command thanks.
[/SIZE]

---

### Post by kostkon on 2010-03-30
You may find [this page]("https://wiki.ubuntu.com/SkypeWebCams") useful.

---

### Post by Peter T on 2010-04-02
Hi 
I tried 

env LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype 

and it worked fine using Trust tesc-120 ic Gear Travel cam

Peter T
:D

---

### Post by bill516 on 2010-04-02
Perhaps this site might help you?  It offers guidance with regard to those Logitech webcams that work with Linux.

[http://www.quickcamteam.net/documentation/faq/does-my-logitech-webcam-work-on-linux](http://www.quickcamteam.net/documentation/faq/does-my-logitech-webcam-work-on-linux)

---

### Post by CaKiwi on 2010-04-04
Thanks Kostkon and Bill516 for the links. Anyone else with suggestions?

---

