---
title: "HP Mini 1000 Can't Get Network Up"
date: 2009-11-02
forum: Hardware
---

### Post by i4ybrid on 2009-11-02
My friend had some virus problems with her laptop, so I had her install Ubuntu Netbook Remix. I'm pretty sure that they installed Karmic since I linked them to the website yesterday for the Netbook Remix.

I saw the following on the wiki:

Karmic
[LIST]
[*]Karmic Standard has only one major out-of-the-box problem, but sound works immediately (in contrast to Jaunty. 
[*]Wireless does not work immediately. Using "sudo apt-get install bcmwl-kernel-source" in the terminal and rebooting will resolve this issue without further problems. (Kudos to Oscar Kuo.) 
[*]Window movement is sluggish. Karmic seems to incorporate some sort of "friction" whereby a window being dragged drags slower when in contact with another window. This causes problems on the HP Mini 1000's small screen where the window will almos always be in contact with either the upper or lower panel. Unresolved. 
[*]Ethernet is untested (see Jaunty, below).
[/LIST]

Jaunty
Jaunty UNR works on the HPMini, including wireless. However there is a known bug with audio not working at the moment. 

[LIST]
[*]318942 - no sound from speakers on HP Mini 1000 (hda-intel, IDT 92HD75B2X5) 
[*]There is an outstanding bug involving default ethernet configurations 297263 which prevents ethernet from working if the laptop is booted without the ethernet plugged in.
[/LIST]

Now, being that wireless doesn't work out of the box, guess which untested function also doesn't work out of the box? That's right, WIRED! Based on the info from Jaunty, I assumed that restarting with the ethernet jack plugged in would allow her to run "sudo apt-get install bcmwl-kernel-source", but there was still no network connection even when they restarted with the jack plugged in.

How can I get bcmwl-kernel-source onto her laptop without an internet connection? How do I install it once I get the file onto her laptop?

Thanks.

---

### Post by Black Razor on 2009-11-23
> **i4ybrid said:**
> Now, being that wireless doesn't work out of the box, guess which untested function also doesn't work out of the box? That's right, WIRED!

How can I get bcmwl-kernel-source onto her laptop without an internet connection? How do I install it once I get the file onto her laptop?




Yeah, I need an answer to this too please.  Anyone?

Seriously, I would have much preferred to have to unmute my sound in the audio control panel than for me to get screwed and not be able to get onto the internet at all.

---

### Post by Black Razor on 2009-12-07
Seriously, somebody got a fix for this? Without internet access my netbook is basically a brick.  Please help, someone.

---

### Post by brianjolly on 2009-12-07
I was having the same problem. Couldn't do  "sudo apt-get install bcmwl-kernel-source" because the wired connection wan't working. 

A simple restart with the cable plugged in fixed it though. As soon as the computer booted up wired worked, and I was able to apt-get the bcmwl-kernel-source package. 

Both wired and wireless are going good!

Hope this helps.

---

### Post by Ragtop on 2009-12-10
I have the same problem, but my 1030NR Mini has no RJ45 jack for wired net hookup.  Without wireless, it's REALLY a brick!  Gee, and just when I thought I'd found a solution...

BC

---

### Post by spogue on 2009-12-13
I, too, didn't find the Ethernet jack right away.  It's hidden under a rubber tab on the left side towards the front of the unit.  Just now starting the trek to get wired and then wireless working on my mini which was also infected running XP.

---

### Post by Ragtop on 2009-12-15
Well, that's a little embarrassing, but it's found  and with the cable, I have done the terminal mode stuff and the package manager routine, and have a blue light on the front of the mini.  But I am still offline with the wireless system.  My network name is displayed, and shown to have full signal strength and a padlock symbol.  That is expected, as the router has security enabled.  

Where can the info needed to access the secured network be located, please?  Is this what Ubuntu and/or Broadcom call a "hidden network"??

ATB

BC

---

