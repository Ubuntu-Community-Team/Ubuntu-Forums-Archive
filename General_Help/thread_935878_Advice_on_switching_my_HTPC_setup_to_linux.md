---
title: "Advice on switching my HTPC setup to linux"
date: 2008-10-02
forum: General Help
---

### Post by nikidinsey on 2008-10-02
Hi all,

I have currently got a Vista HTPC running MediaPortal as my TV setup. 

On this there is probably:

5000+ photos, (Using Picasa as the album app)
150Gb+ Music
150 films of varying quality (700Mb xvid to 10Gb mkv etc)
10 seasons of 6/7 shows (running with an excellent plugin to mediaportal)

I also have an external drive attached to the HTPC for backing up the most important stuff like the photos & music

This box is also used to share the files to other machines/laptops around the house for various reasons here are two of the important ones:

1, Wifey uses it to store and view photos on her laptop using Picasa.
2, Another laptop in the kitchen doubles up as a great digital photoframe using "slicker" screensaver and our main net radio/TV (BBC iPlayer). I also currently use this machine with iTunes, an almost working library share with the HTPC and the iPhone Remote app which is probably the coolest thing about it.

Right... so you get the jist of the current Windose setup :)

I need some advice if possible, 

1, What's the best linux media centre that could replace mediaportal? I don't use any TV cards, just downloads..

2, What's a decent backup app for linux? especially for letting me know if there is problems via email, sms etc. (currently use syncback)

3, Will this setup will need a decent Picasa replacement? or should I use the Wine version

4, I need to somehow share all the content with both windows and linux machines. I've used soemthing like Twonkeyvision DLNA before. Any suggestions on the best way to make the HTPC our networked content hub?

5, I also fancy rebuilding the kitchen lappy to linux, any ideas on replacements for:
 a, Digital Photo slideshow like slickr that can be used as a screensaver
 b, The best replacement for iTunes that can: 1, connect to the HTPC for it's choons 2, has some sort of iPhone/web interface that can be used as a remote control


phew! I think that's it :) Thanks in advance for any help you can offer, I'll keep this thread posted which the switchover if anybody would be interested.

niks



Currently I'm quite happy with the setup

---

### Post by wintermute115 on 2008-10-21
I'm using [XBMC Media Centre]("http://xbmc.org/home/"), which can play pretty much any video / audio / image file you throw at it. Unless Picassa does something pretty fancy, it should be able to handle your picture needs without a problem.

It even has a web interface that comes with an iPhone skin for handy remote control. And I think I saw that someone had created an iPhone app that controlled XBMC over BlueTooth, but I don't remember, exactly.

Anyway, I'd recommend it.

---

### Post by nidelius on 2008-11-06
I'm also using XBMC and it works like a charm, its in the repos so just sudo apt-get install xbmc

---

### Post by clancymf on 2008-11-07
> **nikidinsey said:**
> Hi all,


3, Will this setup will need a decent Picasa replacement? or should I use the Wine version



There is a linux version of Picasa.

---

### Post by smoinen on 2009-01-14
> **clancymf said:**
> There is a linux version of Picasa.

Actually, the Linux version of Picasa Google is offering runs on top of modified Wine. It works fine, but isn't a native Linux app.

---

### Post by steve.lorimer on 2010-05-25
Hi Niks

I'd love to have an update as to your progress on this project?

I've got a similar project in mind... what I'm thinking is this, and would love some input:

1. Server running Linux & NFS acting as my file server
2. Mini ITX HTPC running Linux connected up to my TV for serving up digital content (primarily movies, photos and music) to my TV. No keyboard or mouse connected.
3. Ability to control the HTPC using my iPhone as a remote. This is for browsing/searching movies and music, and playing, forward, stopping etc. If I need to jailbreak my iPhone to be able to do this then so be it.
4. My MacBook having access to NFS 
5. My wifie's Dell netbook (Dell Inspiron 1012) running Windows v7, having access to NFS.

All this will be on WiFi, which I'd like to be secure.

Has anyone done this? 
Can anyone offer any recommendations? 
What flavour of Linux would you suggest? 
What apps running on Linux would achieve what I'm after?
What app can I use on my iPhone to control a Linux HTPC over WiFi?
Once these design decisions have been made, connecting MacBook and Windows 7 to NFS should be negligible.

TIA
Steve

---

### Post by Swashbunglar on 2010-12-04
I have a few question on the topic. I know very little about xbmc, but I know what I like about media portal.

I don't want something to just "play" my movies.
Media portal does the following for me, and I now that I'm spoiled I just will not accept anything less than the following features. lol

Download and store movie info from IMDB with covers, movie details, and sorting by genre, as well as details on format (HD/SD, Stereo/5.1). Mediaportal - Moving Pictures.

Download and store Tv season/series info and show details. Combine and sort tv shows by season/series.
Mediaportal - MP-TVSeries

These two things are huge for me as I have over 700 of my dvds and blu-rays ripped to drive.
Even if I could find these both in separate stand alone programs, I'd be happy.
I'd like to let go of windows, but this is one of the big ones holding me back.

---

### Post by peely on 2011-03-21
XBMC also has a live CD which provides the main XBMC UI as the native session, has additional power features and works with most IR devices out of the box, definitely worth burning to a USB stick and trying.

@Swashbunglar, All of the stuff you mention works out of the box with XBMC. I came from MediaPortal and am so glad I moved to Linux/XBMC.

---

### Post by theteju on 2011-03-21
I you really want to challenge yourself, Go for Linuxmce.

Once set up, that system is way better than anything else. Its a complete home automation solution.

---

### Post by el_Paraguayo on 2011-03-21
I'm using XBMC too. With the Aeon Mq 2 skin installed, it's a fine looking system!
 
I also run it as a front end for MythTV which handles my PVR needs.

---

