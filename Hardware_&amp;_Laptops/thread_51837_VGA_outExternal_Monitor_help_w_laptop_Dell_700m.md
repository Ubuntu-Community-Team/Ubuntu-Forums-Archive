---
title: "VGA out/External Monitor help w/ laptop? Dell 700m"
date: 2005-07-25
forum: Hardware &amp; Laptops
---

### Post by naked on 2005-07-25
Well this is my first post here.  I've had my laptop for about a month now.  I ran debian unstable for a wekk or two, but then decided to try ubuntu.  I LOVE IT!  I have just about everything configured how I want it.  Except having support for external video.  I'd like to hook up an extra LCD when I'm at home, and a projector sometimes when I am doing presentations.

I've found several sites that have basic HOWTO type info for getting this to work.  But I have no results.  

[http://www.celifornia.com/documents/dell700m.html#Video-out](http://www.celifornia.com/documents/dell700m.html#Video-out) 

I've tried working through that, but it is far to comlicated of a setup.

Attached is my xorg.conf that I have tried to setup video out on.  This config works fine, but no video out.

Any help is GREATLY appreciated!

Luke

I had trouble uploading my xorg.log, so here is a link to it.  [xorg.log](http://enterlife.net/xorg.log.txt)

---

### Post by damonw5 on 2005-07-25
[QUOTE=naked]Well this is my first post here.  I've had my laptop for about a month now.  I ran debian unstable for a wekk or two, but then decided to try ubuntu.  I LOVE IT!  I have just about everything configured how I want it.  Except having support for external video.  I'd like to hook up an extra LCD when I'm at home, and a projector sometimes when I am doing presentations.

I've found several sites that have basic HOWTO type info for getting this to work.  But I have no results.  

[http://www.celifornia.com/documents/dell700m.html#Video-out](http://www.celifornia.com/documents/dell700m.html#Video-out) 

I've tried working through that, but it is far to comlicated of a setup.

Attached is my xorg.conf that I have tried to setup video out on.  This config works fine, but no video out.

Any help is GREATLY appreciated!

Luke

I had trouble uploading my xorg.log, so here is a link to it.  [xorg.log](http://enterlife.net/xorg.log.txt)[/QUOTE]
 Silly question, but have you used the Fn key combination on your laptop to enable video-out? Usually it's the Function key plus something else (for example, Fn+F10.) Often it is turned off by default. There are three modes: Laptop display only, both displays, and external display only. You can also set these defaults in your BIOS.

If you've tried this already, I apologize. Any other ideas?

---

### Post by naked on 2005-07-25
[QUOTE=damonw5]Silly question, but have you used the Fn key combination on your laptop to enable video-out? Usually it's the Function key plus something else (for example, Fn+F10.) Often it is turned off by default. There are three modes: Laptop display only, both displays, and external display only. You can also set these defaults in your BIOS.

If you've tried this already, I apologize. Any other ideas?[/QUOTE]
 I have tried that.  But nothing happens at all.  I don't think that ubuntu supports that?  Or maybe my laptop has some issues with that.

I got dual display working with the aove config.  But it just stretches my desktop across the two displays.  I want to be able to mirror my current display to the video out.

Are there any programs or scripts that can make changes on the fly?  Like once I get my xorg configs figured out will I be able to switch between spanning and mirroring without having to kill X and reconfigure my config?

Luke

---

### Post by WhoDoYouBunTu on 2006-02-11
hey there ... can u pls explain how you got it to span across 2 monitors with "aove config" ... i just need to extend my desktop, not mirror it ... thank you.

---

