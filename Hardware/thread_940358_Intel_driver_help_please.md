---
title: "Intel driver help please"
date: 2008-10-06
forum: Hardware
---

### Post by klemperal on 2008-10-06
This thread had been dead in the absolute beginner discussion for a couple days so I figured maybe the people who look at this forum might be able to help.

Through another thread I was told that I might not have a working driver for my 82945G/GZ Integrated Graphics Controller. I'm still pretty new to Linux and I'm not exactly sure how to install a new driver if that is what I need to do. I would really appreciate any help in showing me how to get things working all the way, so let me know if you need me to post any more information (remember to check in the thread listed above as I posted a bunch of stuff in there that might help). Thanks for your trouble.

 > Re: Intel grapics driver help please
You may check how much memory is shared with the integrated graphics in bios as this may cause some issues.


Ok, in the bios under internal graphics mode it says it's using 8 mb. The only other options are "1 mb," or "disabled." I'm not sure if its relevant but the graphic adapter priority is set to PCI/PCI express. Let me know if I need to post more information and or what I should do from here--thanks for the help.

---

### Post by jocko on 2008-10-07
In none of your previous threads about this is there any evidence that you don't have the correct driver (the people that say so haven't even asked for any information that would give any clue about which driver you use).
In your [first thread]("http://ubuntuforums.org/showthread.php?t=933046") you tried to ask something about a cluttered gui and some problem with window sizes (whatever you meant by that... your description of the problem just referred to a missing screenshot).

Start by providing a screenshot of your problem, then maybe it will be possible to try to find out what the real problem is.

---

### Post by klemperal on 2008-10-07
Alright, sorry for the delayed response.  Here is the screen shot that apparently got left out in the other thread.  See how the buttons and text are on top of each other at the bottom of the window (you might have to zoom in). Besides this another thing that I should mention is that 3D games like scorched3D or Vega Strike crash my computer--the screen freezes and I have to restart via the button on my computer.

---

### Post by jocko on 2008-10-08
I can't see any screenshot there... Your link just takes me to the gmail login page...
Attach it to the post instead of linking to it.

---

### Post by klemperal on 2008-10-08
Ok, I think I got it right this time with the screenshot.  Let me know what you think.

---

### Post by jocko on 2008-10-08
Hmmm... I'm pretty sure that's not caused by your video drivers, looks more like it's something with your theme. Does that happen with all programs, or just some of them?

Open up gnome-appearence-properties (System --> Settings --> Appearence) and try to change some things:
In the theme tab, try switching to another theme (change to the stock "Human" theme, unless that's what you use).
Check your settings in the fonts tab; the standard is (top to bottom) "sans", "sans", "sans", "sans bold", "monospace" (10 p for all). Click the "details" button and check the resolution (standard is 96 pixels per inch).

---

### Post by klemperal on 2008-10-08
I checked the fonts and resolution and everything is already set to what you recommended it be.  Also, changing the theme doesn't help much.  It still ends up being cluttered at the bottom, just in a slightly different way.  By the way, this weird problem only affects certain programs that I have noticed.

---

### Post by jocko on 2008-10-08
> **klemperal said:**
> By the way, this weird problem only affects certain programs that I have noticed.
Which programs would that be?

---

### Post by klemperal on 2008-10-08
Tovid-gui is the one in the shot.  A couple games I can't remember that I have since uninstalled would display odd window sizes that, to me, looked similar to the problems with Tovid.  I should also mention that 3D games don't work right or crash my computer which is another reason I suspect something to do with the driver or similar.

---

### Post by jocko on 2008-10-08
> **klemperal said:**
> Tovid-gui is the one in the shot.

That's a bug in tovid-gui. I just installed it, and see exactly the same as in your screenshot.
Nothing wrong with your computer, just a poorly designed program...

---

