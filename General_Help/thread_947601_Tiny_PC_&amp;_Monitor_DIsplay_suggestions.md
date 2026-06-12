---
title: "Tiny PC &amp; Monitor DIsplay suggestions"
date: 2008-10-14
forum: General Help
---

### Post by dwanders on 2008-10-14
I am looking for a very small, low powered fan less PC unit that has a NIC (or possilby WiFi instead or also) and video out (working with standard LCD monitors. It needs to be able to run Linux (preferably Ubuntu Server min install), X server (min), and Web Browser. Want it cut down as much as possible. I would like to split the video out to two monitors (maybe up to 4 - same display just split out to 1, 2, 3 or 4 identical monitors). 

This will be a display unit that we would like to set up to continuously display a static web page. Basically - we figure we can set up the little PC with a cron entry that every 60 seconds or so kills the web browser, then reloads it requesting the static page. 

Any suggestions or ideas would be greatly appreciated.

---

### Post by jimv on 2008-10-14
You want an Asus EEE Box:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16883220003](http://www.newegg.com/Product/Product.aspx?Item=N82E16883220003)

---

### Post by dwanders on 2008-10-14
I have seen those - never used on though - I guess I was thinking they may be a bit over kill for what we need. I will check it out again. 

And would any one know if it is even possible to split the video display like I am hoping?

---

### Post by cariboo on 2008-10-14
Have a look at the Mac Mini:

[http://www.apple.com/macmini/](http://www.apple.com/macmini/)

This should fit your needs. The store seems to be off line at the moment, but they do provide phone numbers.

Jim

---

### Post by jimv on 2008-10-14
I suggested the EEE Box because I think it's about the cheapest little computer that you'll find (I looked...didn't see anything cheaper/better).

For the connecting of multiple screens, they do have such devices.  Here's a google search:

[http://www.google.com/search?q=vga+splitter&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vga+splitter&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by dwanders on 2008-10-16
I think I have to agree - for the cost and bang for the buck, I could probably make some thing work by dinking around with boards and a lot more configuration time and know how, or just bang out one of these EEEboxs, and work with something more comfortable. 

I am currently building a Demo on old hardware, using XUbuntu. The problem I am experiencing now is disabling the screen blank. I have tried turing the screen save off, and running:

setterm -blank 0 -powersave off -powerdown 0
xset s off 

but the system seems to ignore these commands - any suggestions would be greatly appreciated. 

Having discovered this screen blank issue, I also think I will need a controlled screen re-fresh to keep the screen from burning - I was thinking along the lines of restarting the X every 5 minutes or so would do the trick. Any advice or pointers for accomplishing this would also be greatly appreciated.

---

### Post by jimv on 2008-10-16
For the screen blanking issue:

[http://www.doctort.org/adam/nerd-notes/disabling-screen-blanking-in-xorg.html](http://www.doctort.org/adam/nerd-notes/disabling-screen-blanking-in-xorg.html)

And if the monitor is <10 years old, I don't think screen burning is an issue...unless it's a older plasma screen.

---

### Post by dwanders on 2008-10-17
Smashing worked like a charm!

---

