---
title: "Speeding up video playback..."
date: 2005-12-05
forum: General Help
---

### Post by Liam on 2005-12-05
...on a really, really old system.

I've got an 800mhz PIII notebook, 384MB RAM, with an onboard Trident Cyberblade video card.

I know, I know.

Is there anything I should be looking at to optimize video playback? mplayer is the only thing I can get to work at all - and it's slow, unsynced, and bitches about the processor speed. I'm talking about maybe .25X on an average divx movie downloaded off of usenet. If I use -framedrop, I get *maybe* .8X.

Everything else, including VLC and xine, blanks out the video because they can't keep up with audio.

Since upgrading this machine directly from Warty to Breezy, I've noticed a subjective heckuva big performance hit in general; could xorg have something to do with it?

I'm willing to try any and all suggestions. Thanks.

---

### Post by newuser111 on 2005-12-05
did you try **sudo dpkg-reconfigure xserver-xorg**

also in mplayer if you go into preferences> video> you can try selecting a different video output plugin

---

### Post by Liam on 2005-12-05
Huh.

I swear to god, I set ao=oss, vo=xv, and double=no in my mplayer.conf, and it didn't do any good (by an eyeball test) on the command line.

Then I opened the same file with gmplayer, and set the same options, and it worked.

And now it works from the command line, too.

Odd.

But thanks for the suggestion - you gave me the notion that I should try it through the GUI.

---

### Post by Liam on 2005-12-06
I take that back.

After a reboot, xv put out multicolored puke that looked like something Jackson Pollock would do.

However, I vo=xvidix works, with only a slight amount of delay, so long as I run it as sudo.

Huh.

---

### Post by Mr. Electric Wizard on 2005-12-06
I just wish MPlayer had DVD menu support...

---

