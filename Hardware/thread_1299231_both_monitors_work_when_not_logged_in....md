---
title: "both monitors work when not logged in..."
date: 2009-10-23
forum: Hardware
---

### Post by a cup of tea on 2009-10-23
I got this silly idea in my head that I wanted to use two monitors, both displaying different things, at the same time. It doesn't work on the computer I usually use, either in Ubuntu or Windows (the computer dual boots). I tried it on my other computer, which I don't use because the hard drive is dead, using an 8.10 live USB. It worked.

I got excited and installed 9.04 onto a 16 GB flash drive. It's not a live USB, it's a regular install on a flash drive. I am able to boot that computer from the flash drive. 

The second monitor doesn't work while I'm logged in. I go into the display settings and the second monitor is set to off. I click to turn it on, and it says I need to log out and back in. I log out, see the login screen displayed on both monitors, and when I log back in, the second monitor is off again. 

The laptop's screen is recognized as laptop 15" and the second monitor is recognized as Hewlett-Packard 20".

---

### Post by earthpigg on 2009-10-23
what video card and driver are you using?

---

### Post by a cup of tea on 2009-10-23
I don't know. How do I find that out?

---

### Post by Cybie257 on 2009-10-23
> **a cup of tea said:**
> I don't know. How do I find that out?

lspci | grep VGA in a terminal will return that information.

-Cybie

---

### Post by a cup of tea on 2009-10-23
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

:)

---

### Post by Cybie257 on 2009-10-23
Hate to sound negative, but good luck. The Intel chipset on laptops have always created a headache with external monitors. I did, however, have things working with an older version of Linux (and even Windows) at one point. There are a lot of things that went wrong with later versions of the Intel driver(s), including the Windows side. Supposedly, this problem has been alleviated with Ubuntu 9.10, but I have yet to test that and won't until the final version of Karmic comes out at the end of this month and do a fresh install on my Laptop. (Been using 9.10 for past 2 months on Home Tower)

I would suggest trying a LiveCD version of the latest Beta/RC of 9.10 and see if that works. If so, then I'd go with 9.10. Also, since it will be a live version and it will ask you to reboot, just do a log out and log in and that will work as rebooting a livecd will reset any changes. 

Hope this helps.
-Cybie

---

### Post by a cup of tea on 2009-10-23
Ok, thanks. I'm downloading 9.10 and I'll give it a try.

---

### Post by a cup of tea on 2009-10-24
I'm trying the 9.10 live CD and it seems...like it might work. :confused:

I can't log out and back in while using the live CD, so I can't change the resolution, although it seems like a good thing that it's offering me the right resolution for the second monitor (which wasn't an option in 9.04). If I just un-check the "mirror screens" box, it definitely un-mirrors them. It just uh... well they go black except for my white cursor, which I can move around and see that they're unmirrored. I guess then it sets the display back to the way it was because I didn't click when it asks if I want to keep it.

---

### Post by Cybie257 on 2009-10-24
Actually, you CAN log out and back in. Just don't "Restart" the computer. It will take you to the boot/login screen and just hit enter as there are no passwords. I've done this a few times, and actually doing it right now on a second computer to test something with as it has Vista :( and even though it's got onboard nVidia graphics with up to 2GB of accessible RAM, the Blu-Ray video skips and I don't think it's hardware related by far as it is a quad core and HD capable Video. 

but, glad to see things look like they are going better with 9.10, which I thought would help as I have read about improved Intel Video..

-Cybie

---

