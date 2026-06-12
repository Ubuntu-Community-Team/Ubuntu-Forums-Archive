---
title: "find and repair sound card"
date: 2005-06-07
forum: Hardware &amp; Laptops
---

### Post by veritas366 on 2005-06-07
Hello,

I have two questions.  First, what command can I use to determine what sound card I have.  I know it's a crappy one, but I'll need that for the second question, which is:

I have sound. and when I put in an audio cd it plays fine...considering the poor quality of my speakers and sound card (does anyone else pick up local radio stations on their computer speakers when the speakers are on but they aren't playing sounds...but I digress).  Anyway, when playing games such as Battle for Wesnoth (at which I suck, even on the easiest level) and Neverwinter nights (their Linux client, not thru wine) the sound is staticy.  It plays, but it sounds EXACTLY as if an old vinyl cd were playing with small skips and hisses and pops.  Kind of a nostalgic sound, actually, but not one I'd like to keep.  Anyone have any ideas what could be going on.  For the heck of it, I went thru the ubuntu guide to "fixing" the sound, though the guide doesn't say what problems are being fixed.  In any event, it didn't work.  

Thanks!

---

### Post by PryGuy on 2005-06-07
The best way to find out what card do you have is to open the PC and look what's inside :) But you may also look it up in the Windows' Control Panel if you have dual boot.

I have noticed that there's some mess with the Volume Control sliders. You should play with them, 'cause in my case i had "Line in" and "Mic" not muted for instance, and they produced a great noise spoiling all sounds. Guess your problem might be here in your case as well.

---

### Post by veritas366 on 2005-06-07
Thanks!  Actually I saw that "video" wasn't muted in "capture" so I muted that and it helped.  Still a few pops.  I don't know if this is the first time I've messed with sound since I went from fc3 to Ubuntu, but I notice it's using OSS and not ALSA.  I have very little knowledge of the difference or which is best to use when.  Do you or anyone have a link to someplace that explains the difference. Right now, I guess I will go with "if it ain't broke, don't fix it," but I was curious.

---

