---
title: "Envy - Nvidia Cards and more?"
date: 2008-09-10
forum: Georgia Team - US
---

### Post by siafulinux on 2008-09-10
Wanted to share an interesting experience I had while re-installing my main system the other day. I hope this may be of use to anyone suffering with any Nvidia installation issues.

I have an Nvidia GeForce2 MX/MX 400 with 64mb video memory. With this card I usually suffer incorrect screen resolution issues, *when* I get Nvidia working. 

[INDENT]**Side Note:** Last week I had the opportunity to install Ubuntu for a friend of mine who finally decided to give it a go. He too has an Nvidia, but a newer model. With this, Nvidia was picked up perfectly and the resolution was correct without any issues whatsoever! It was a dream.[/INDENT]

So while doing a fresh install and a number of unsuccessful attempts at getting Nvidia to work on my main machine, I came across Envy - [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") - in the repo's. 

I decided to give it a go and was expecting the usual nonsense, but what was I to lose? To my surprise and elation, upon reboot, everything worked without any hiccups at all! In fact, it even got the resolution correct and was just as much a fantastic experience as it was doing that other newer machine described earlier.

From the Envy website:

> "Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
[LIST=1]
[*]detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
[*]install the right driver for your card and all the required dependencies
[*]configure the Xserver for you
[/LIST]
Envy features both a GUI (which you can launch only inside a Desktop Environment) and a textual interface which you can use if, for example, you cannot start the Xserver.

I have to say it lived up to it's promises for me and I give it 5 / 5 stars! From now on, this will be the first bit of software I download to get my Nvidia working.

Nicely done!

---

### Post by jhenager on 2008-09-17
This contributor helped me first get Beryl working, back when the current version was Dapper Drake.
Glad you got your hardware to cooperate. It is always satisfying when man triumphs over machine.

---

### Post by siafulinux on 2008-09-20
*nods* :-)

---

### Post by sorel on 2010-06-03
Hey, what Ubuntu did you install? 
Coz I'v 9+ and the same video card and Envy doesn't help.

---

### Post by BslBryan on 2010-06-04
> **sorel said:**
> Hey, what Ubuntu did you install? 
Coz I'v 9+ and the same video card and Envy doesn't help.

Sorel, this thread is quite old, so the chances of the OP responding are quite small.  Please try to avoid necromancy from now on.  Also, this subforum is not read by nearly as many people as the "Absolute Beginner Talk" or "General Help" forum.  Still, I will help you.  If I cannot resolve this right here, please search for existing threads in the bigger subforums and see if that can help you.  If not, you can start a new thread there.

Go to System --> Administration --> Hardware Drivers.  This will probe your system and find the necessary drivers for you to install and activate.

---

