---
title: "Slow typing"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by wyth on 2007-07-08
For some time now, when I type any text, there is a little bit of a lag that's becoming a real problem.  Even typing this I get almost a word ahead before I see the word appear on the screen.  When I'm doing actual work, say in OpenOffice, I'll get one or two words ahead, and keys struck for one word appear in the middle of another word. (So the previous clause would read something like: 'and keys strone ofr word appthe middle of anoword').  This means every two or three words are misspelled and need to be fixed.  I'm a fast typer, but not that fast, and frankly  it's not acceptable.   I have work to do.

I didn't have this problem with the proprietary ATI drivers, but with Xorg 7.2 the proprietary drivers won't work with my card (Radeon R250).  I've used K/Ubuntu happily and productively for three years.  Now with Feisty the old proprietary drivers don't won't, ATI *says* they'll start to offer some real support (uh, yeah...), and nothing is happening except lowered performance for us lucky ones without a one-year-old laptop.  

I've complained about this in the past, but I just started summer teaching, and the lag is not just an annoyance, it's a real show-stopper.  I hate to say it, but if this keeps up, I'm going to have to go back to windows just to get work done, because I can't stop to correct every three words I type.

So I'm writing to see if anyone might know of a fix.  I've tweaked out my xorg.conf file to squeeze every ounce of performance I can, but maybe not enough (or not correctly).  So I've attached that.  

Any insight would be appreciated.

---

### Post by easoukenka on 2007-07-08
off hand can't remember exact thing i clicked but i had the same problem show up suddenly.  i use kubuntu so it may be  a bit different anyways goto accessibility then youll see an option relevent to your problem

---

### Post by wyth on 2007-07-09
I'm on Kubuntu as well, and went to that because it was snappier on my system than Gnome.  But are you talking about "Use slow keys" in the Accessibility tab under the System Settings?  Because that's not checked.  It must be something else.

---

### Post by wyth on 2007-07-11
Bumping this... it's an irritating problem that *has* to have a fix.

---

### Post by Wutzl on 2007-08-14
I got this problem when installing Beryl/Compiz/CompizFusion. Luckily for me, this happened only temporarily and when I completed the installation process, typing was back to normal.

However, I can still produce this annoying behavior - with the current Ubuntu version and an ATI with XGL, I have this phenomenon when I log into an XGL session with gdm, but DON'T start compiz automatically. Typing is painfully slow until is press Alt-F2 and run "compiz --replace".

So if you urgently have to get work done, just log into a regular or failsafe Gnome session (no XGL/AXGL etc) - then things are fine (at least in my case).
If you have time to play around, try the free or proprietary drivers and try running them with or without compiz fusion.

---

### Post by wyth on 2007-08-14
Thanks for the reply, Wutzl.  I ended up ditching Gnome and compiz all together.  For one, my old ATI card just doesn't play well with them.  I've always had a snappier response on KDE.  I'm still getting some lag, but I think that has to do with the open source Radeon driver, to be honest (I've been testing things out). The proprietary driver for my card won't work on Xorg 7.2, so I'm kinda stuck with this laggy performance.  It's not *too* bad, but is still annoying.  Just writing this message, I've gotten a word and a half ahead of myself three times.  There, it just happened again with the word "times,"

I can understand that with better hardware I wouldn't have this problem, but if you were trying to convince someone to convert to linux, you don't want to explain the whole proprietary vs. open source gfx drivers issue.

---

