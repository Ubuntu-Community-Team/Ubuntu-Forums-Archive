---
title: "Trying to get my Fujitsu T4220 tablet to work"
date: 2009-12-18
forum: Hardware
---

### Post by raccoonone on 2009-12-18
I have a Fujitsu T4220, tablet laptop (the kind where the screen can fold flat and then you can draw on it). However, I just installed Ubuntu 9.10, and it doesn't recognise the pen at all. I had Intrepid install a while ago, and it at least recognised that I had a pen (and I was able to use it as a mouse).

I was looking at this guide: <https://help.ubuntu.com/community/T4220>, but it doesn't have instruction for Karmic. Does anyone know how I can get this working, or where I would start?

SOLUTION:
1) "sudo apt-get install wacom-tools xserver-xorg-input-wacom"
2) use the .fdi file provided by Favux (see post below). You do not need to install linuxwacom 0.8.4-4
3) run "wacomcpl" to calibrate (this can be frustrating as the mapping for your pen will be *totally* messed up). Instead you can try the .xinitrc that I posted below

---

### Post by Favux on 2009-12-18
Hi raccoonone,

Did you install the 32-bit or 64-bit version?

Be sure to use Update Manager and make sure your system is completely up to date.

Then try one of the two 10-linuxwacom .fdi's attached to the bottom of this [HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  Either should work for you as you have a serial Wacom tablet pc.  Instructions are in Section 2 b).

---

### Post by raccoonone on 2009-12-19
Hi Favux,

I have 32bit, and have installed all the latest updates. I tried both of the .fdi file you suggested, but I'm still having problems. I also followed the guide in section 1 to install linuxwacom.

I can see my stylus in both xinput --list, and xsetwacom list, but when I touch the stylus to the screen the cursor simply disappears. I tried using wacomcpl to calibrate it, but got the same behavior of a disappearing cursor.

I read through a couple of your other posts, and then looked at the output of lshal, which lists pnp_FUJ02e5. So I think my device should work.

Any suggests as to where to go from here? (maybe try the dev version of linuxwacom?)

Thanks!

---

### Post by Favux on 2009-12-19
Hi raccoonone,

So you installed linuxwacom 0.8.4-4?  I wouldn't install 0.8.5-7 because it won't let you restart and besides I don't think linuxwacom is the problem.

That's too bad.  I thought the problem was with 64-bit, but it looks like it affects at least some 32-bit installs too.

Some have reported using 0.8.4-4 fixed it for them.  So that was reasonable to try.

Others say that restarting X fixes it for them.  Something to do with plug and play maybe, at least it's different in Xorg.0.log after a X restart.  To set up X restart in Karmic see:  [http://ubuntuforums.org/showpost.php?p=8424078&postcount=654](http://ubuntuforums.org/showpost.php?p=8424078&postcount=654)

Maybe it's partially a baud rate problem?  If we specified the baud in the .fdi?

---

### Post by raccoonone on 2009-12-19
Yep, I installed 0.8.4-4. I tried restarting X, but that had no effect. One thing I noticed though, is that although my stylus is listed there is no listing for the eraser.
Also, after more testing. The cursor doesn't disappear when I try to use the stylus. It's simply moved to the lower right hand corner. I wonder, if the stylus could be mapping to a screen with different coordinates, or something like that?

---

### Post by Favux on 2009-12-19
Hi raccoonone,

The stylus moving to a corner like that usually indicates X isn't getting input.  I wonder if you managed the linuxwacom compile and install correctly?

---

### Post by raccoonone on 2009-12-19
So, I finally made some progress.

It turns out it was just mapping the coordinates in a super weird way. The very upper left corner of my tablet was some how mapped to the entire screen, so after much hassle I managed to click on the calibration squares in wacomcpl.

I've attached my .xinitrc, in case anyone else has the same problem as me.

Now, the only thing I can't get working is the eraser. Any suggestions there? neither xinput --list or xsetwacom list, will show it.

---

### Post by Favux on 2009-12-19
Hi raccoonone,

Your attachment didn't post.  I think something hinky may be going on.  Could you also post your "xinput --list"?

---

### Post by raccoonone on 2009-12-19
Here we go, I've attached them. (note, this xinput --list is from using the version of linuxwacom in the Karmic repo (0.8.4-1))

I've been playing around a bit more, and discovered that by removing linuxwacom and reinstalling the version in the Karmic repo, I was able to get the eraser to show up in "xinput --list" again. Of course, now "xsetwacom list" doesn't see either the stylus or the eraser.

---

### Post by Favux on 2009-12-19
Hi raccoonone,

That's because you now again have the default 10-linuxwacom.fdi which won't return stylus and eraser.  You have to use one of the modified .fdi's attached to the HOW TO or rec's script.

---

### Post by raccoonone on 2009-12-19
The strange thing is that when I replaced my 10-linuxwacom.fdi with one of the ones from your HOWTO, my eraser disappeared from the output of "xinput --list". So, there's something else going on there.

---

### Post by raccoonone on 2009-12-19
Oh ya, and now that I'm using the .fdi from the Karmic repo. Both my stylus and eraser work in GIMP and have pressure sensitivity (which I didn't even know I had! that never worked in Windows).

The only problem now is that they don't work with wacomcpl (which isn't a big deal for me now that I have them calibrated), but it would be nice to know how to fix that, so I can do it in the future or for other people.

---

### Post by Favux on 2009-12-19
Hi raccoonone,

But wasn't that with the 0.8.4-4 linuxwacom you installed?  Could you try one of my .fdi's now and see how it goes?

---

### Post by raccoonone on 2009-12-19
Good call. I tried your generic .fdi file, and now everything is working great.

Thanks for all your help!

---

### Post by Favux on 2009-12-19
Hi raccoonone,

Outstanding!  You're the third or fourth serial tablet pc to confirm that the new-generic .fdi works for them.  I appreciate it and you're welcome.

---

