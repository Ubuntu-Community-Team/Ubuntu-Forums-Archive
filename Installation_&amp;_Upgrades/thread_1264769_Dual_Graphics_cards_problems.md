---
title: "Dual Graphics cards problems"
date: 2009-09-12
forum: Installation &amp; Upgrades
---

### Post by EclipseOTO on 2009-09-12
Hey,

So, I just did a fresh install of ubuntu on my other desktop which has two graphics cards, 9800 GT's to be precise.  It wouldn't work unless I took one out, so I did so and everything was grand.  I then decided that I had two cards and by god I wanted to use both of them, so I did some research and found this article on how to put in both:

[URL="https://webmail.williams.edu/wm/mail/fetch.html?urlid=g6cba536acb876b0c944472d365f5ecfcckijgplh5l&url=http%3A%2F%2Frmarcus.wordpress.com%2F2009%2F02%2F02%2Fubuntu-with-two-graphics-cards%2F"]http://rmarcus.wordpress.com/2009/02/02/ubuntu-with-two-graphics-cards/
[/URL]


[FONT=Verdana]The system doesn't make it to the log in screen.  Instead it just boots to a blank screen where the mouse is a black X.  I tried taking one of the cards out again, didn't help.  Any ideas?

Thanks,
Pete
[/FONT]

---

### Post by khelben1979 on 2009-09-12
I think the problem is that your x server configuration is configured to only use one graphic card. Attach your /etc/X11/xorg.conf to this thread.

I assume the cards are linked using S.L.I. Have you tried this functionality with Windows just so you know there's not a conflict in hardware?

---

### Post by EclipseOTO on 2009-09-12
Yeah, I'm positive the SLI works, I'd been using it with windows for near 4 months when my windows 7 beta expired.  Attached is my xorg.conf

---

### Post by EclipseOTO on 2009-09-13
I forgot to mention, when I boot the computer, I can't get into the terminal either.  When I press ctrl+alt+f1 theres just a flashing underscore in the upper left corner of the screen.

Thanks,
Pete

---

### Post by dagrump on 2009-09-13
Well it would appear that you are running 3 monitors from your xorg file, is that the case?
Looks like Device0 is an on-board chip or something.
This is the xorg.conf from my machine w/ 9.04 & a pair of 9800s in SLI.
That would be xorg1, the xorg.txt is from a box running 9.04 w/ a pair of 9600s in SLI.
Now I'm only running a single monitor on the boxes, so you need to modify your file to reflect multiple monitors, if that is the case.

---

### Post by EclipseOTO on 2009-09-13
I'm only running a single monitor, so I replaced my xorg with the xorg1 file, renaming it to xorg and putting it in the appropriate spot.  This didn't help however.  Is there something else I should add?

Thanks,
Pete

---

### Post by dagrump on 2009-09-13
Oh, well I'm not sure if that's the way to do it but, if it's no worse.
I think I'd try "lspci" to check the BusID of your graphics cards. I don't have any idea where the xorg file you were using came from, but I think you need to allow the installed drivers to create one.
Then you will need to edit it to designate your primary card, using the BusID line & Option "SLI" "SFR" line.
There are other render options, but I don't remember what they all are.

---

### Post by EclipseOTO on 2009-09-16
So, I fixed up some things, and now I don't get an error of any sort, but all that shows up is a black screen.  No mouse, no underscore, so I'm not sure what that means.  I tried the other monitor ports on the graphics cards too and that didn't work, they just said "no signal" when not in the original.  I can still access the ctrl + alt + F1 though.  Sigh...

---

### Post by EclipseOTO on 2009-09-16
Actually I lied, I get an "(EE) NVIDIA(GPU-1): Failed to initialize the NVIDIA graphics device!" when I change back to the terminal.  Interesting.

---

### Post by EclipseOTO on 2009-09-16
'nother update:

According to the log file, it's not running SLI because it picks up three gpus and doesn't like that, 2 being the 9800 GT's and the third being the one on the motherboard.  How can I work around this problem?

---

