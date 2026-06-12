---
title: "[SOLVED] Help with Asus P4P800SE"
date: 2007-09-17
forum: Hardware &amp; Laptops
---

### Post by HOLOGRAPHICpizza on 2007-09-17
First, hello random people of the Ubuntu community! I have used Ubuntu as a secondary OS off and on since 5.10, but have just recently dumped windows entirely as of about a month ago.

Everything is going smoothly, except there are serious problems with switching users, going into sleep, hibernate, and sometimes just leaving it alone too long.
Sometimes I will come to it after a few hours and it will be stuck at a black screen that nothing brings it out of, or a screen filled with random blue, yellow, black, and white character sized chunks.
If you try to switch users, go into sleep, or hibernate, it just goes to a blinking black screen and the monitor turns on and off like crazy.
If you kill X through ctrl-alt-backspace it goes to a franticly blinking purple screen.
Edit: I just found a new error, logging out, (which usually works) resulted in a colourful rainbow screen of death!
I can take colourful pictures if you want.:-D

My system specs:
Mobo: Asus P4P800SE BIOS revision 1011 (I don't really know if it has anything to do with these posts [http://ubuntuforums.org/showthread.php?t=107543](http://ubuntuforums.org/showthread.php?t=107543) and [http://ubuntuforums.org/showthread.php?t=112626&highlight=asus+p4p800+solved](http://ubuntuforums.org/showthread.php?t=112626&highlight=asus+p4p800+solved) )
2 512 mb DDR2 RAM going dual-channel
Pentium 4 2.4 ghz processor
Radeon X700 with 256 mb of ram (my graphics drivers are working fine, or so I think)

Anyone have any ideas?

---

### Post by HOLOGRAPHICpizza on 2007-09-18
Please help, anyone?
I think its getting worse, I have seen like 5 more random screens just from leaving it sit.:cry:

---

### Post by HOLOGRAPHICpizza on 2007-09-19
bump
No one has any ideas?

---

### Post by HOLOGRAPHICpizza on 2007-09-21
None seems to notice this post, so I'm gonna put a link to it in my signature and answer everyone else's questions and hope they will notice this post.

And just to be sure, BUMP!

---

### Post by hessiess on 2007-09-21
have you tryed any outher distros?

---

### Post by HOLOGRAPHICpizza on 2007-09-21
aww.... but I like Ubuntu.:(

Maybe I could just use XDM or something instead of GDM, it seems like a likely cause for the problem. How would I go about doing that, just aptitude remove gdm, aptitude install xdm?

---

### Post by hessiess on 2007-09-21
just to check if it works with anouther distrobution;)

its may be a problem with the ati card, but im just gessing rilly, as nobody was replying to your thred:)

---

### Post by HOLOGRAPHICpizza on 2007-09-21
So should i like check from a live cd, or go through with the installation on another partition? And should I try another Debian distro, or something different entirely?

---

### Post by hessiess on 2007-09-21
live cd should be good enugh, but you can try instaling if you have any problems, maby puppy/ damn small linux. thay are small and dont take ages to download.

do you have a nvidia card? just to rule out graphics isues, and live cd's can be problamatic with ati

edit

P4P800SE  linux problems brings up lots of results, but i dont know if thay are relivent

---

### Post by HOLOGRAPHICpizza on 2007-09-21
Yeah, all I have is an ATI card. I would want to test it on a distro with gdm and gnome, because I think that is what my problem is based around. First i'm just gonna try the ubuntu live boot cd, then if that doesn't work im going to try openSUSE since it has gdm and gnome, yet isn't debian based.

---

### Post by hessiess on 2007-09-21
try a kde distro just to make shore its not a gnome problem;) i know kde is ugly:lolflag:

---

### Post by HOLOGRAPHICpizza on 2007-09-21
Ok I just tested with both the ubuntu and kubuntu live cds, and switching sessions worked fine! Im thinking this might be a problem with the ati drivers. I used kubuntu a while ago as a secondary os, and I remember having a similar problem, and I also had the ati drivers installed! Im going to try removing the ati drivers, and if it still doesn't work then it can't be the drivers. If it does work, I will try using the proprietary ati drives from ati, instead of the open source ones im currently using.

---

### Post by HOLOGRAPHICpizza on 2007-09-22
Ok I think I figured it out, with the ati drivers I get sorta ok 3d acceleration, and my problem is fixed.
With the fglrx drivers, I get amazing 100% 3d acceleration, but my terrible rainbow screen of death problem is back.
CANT THERE BE A HAPPY MEDIUM!?!?!?
Well for now im using the ati drivers and my problem is fixed, but I cant use any 3d screensavers without getting like 3 frames per second.
At first I was sure it was a problem with my motherboard, because this is the only computer I have seen it happen on. But it was the graphics drivers the whole time. I will just have to hope for better ati support in future releases.

---

