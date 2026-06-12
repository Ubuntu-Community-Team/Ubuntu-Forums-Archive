---
title: "How installing ATI Catalyst Driver was easy ..."
date: 2008-02-21
forum: Hardware &amp; Laptops
---

### Post by em3raldxiii on 2008-02-21
Okay, I know there are a number of posts about the ATI Catalyst driver already, and even some howtos.  But I ended up following my own path to getting it to work, and it was relatively easy.  This was a FRESH INSTALL of Ubuntu 7.10.

First off, here's a brief outline of my setup:

Asus AM2+ Deluxe motherboard (I am at work, and I don't remember the product number)
AMD Phenom 9500 processor
2GB Corsair PC6400 low latency
1 Radeon HD 3850 videocard
1 500GB Western Digital hard drive
1 LG DVD-Burner w/ Lightscribe

So basically, I eventually went to two howtos and followed the directions.  First, I went to this page:

[http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

There, I downloaded the file, saved it to my ~/home directory.  Then I went to the link at the bottom of the page to the "Unofficial Wiki" which is this link:

[http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page)

On that page, on the right is a link to a number of distributions.  I clicked on the UBUNTU link which is this page:

[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

There, I followed the directions to the letter for the "METHOD 2" or Manual installation instructions.

Everything works.  I do have a mild issue with video overlays being slightly persistant (move the window and the video takes a sec to move to where I moved the winow).  I also have a few flickering issues, but I will have to try to fix that when I get home.

Hope this helps anyone else installing the drivers.  And if you have already dealt with the flickering, please leave me a note here :D:)

---

### Post by UKHacker on 2008-02-26
I just wanted to thank you for taking the time in typing up how you got the ati graphics working, having done lots of reasearch myself and running across verious problems I finally found your post which aloud me to succesfully install the latest ATI drivers.

I did have a problem however when using the aticonfig initial command as after restarting my pc my display was completly scrambled, I could hear it logging in but all I could see was a white screen with verious black squares, so to fix it I reconfigured the xserver and changed the xorg.conf file manually as instructed by the wiki which then solved my problem.

I was just curious to know if you have managed to solve the flickering issue as I now notice this when playing a game, the two I've tested being Unreal Tournament 2004 and Open Arena.

Thanks again for your post and hopefully for a future post on the flickering issue.

Edit: Just thought I'd add that I am using an ATI Radeon 9600 for those who have had trouble installing this in the past.

---

### Post by em3raldxiii on 2008-02-28
Well, today is the first day that I have had the chance to see what I can do about the flickering.  So far, no luck ... and I have to head back to work the day after tomorrow (300 km away) for a week.  After that I will have another go at it.

I am glad I could help!  It seems there were a few other threads kinda like this one, but I figure as long as people are getting things to work :D

Cheers!

---

### Post by Yellow Pasque on 2008-02-28
The flickering is a commonly-reported bug inherent to the code. Don't waste time on it.

---

### Post by em3raldxiii on 2008-04-01
It's been some time since I figured out what the problem is, but it's SUPER easy to work around.

Basically, when 3d acceleration (desktop effects) is enabled on the desktop, video overlay and other 3d applications have a hard time reconciling with the desktop.  Net result?  Turn off desktop effects when you want to play video or play 3d applications.

I know it's not the most elegant solution, but it does work.  For now anyway.  I will continue to research this issue when I have a chance to see if there is a way to actually FIX the problem, rather than work around.

---

