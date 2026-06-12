---
title: "Weird Media Problem"
date: 2008-10-26
forum: General Help
---

### Post by PrinceArithon on 2008-10-26
OK, so I seem to have stumbled across a problem that I didn't know was a real problem till almost 6 months later....but here is how it goes.

Ever since I upgraded to Hardy (I thought this problem was because of the upgrade process, not cuz of Hardy) I have had a weird problem.  So recently I've reinstalled Hardy and the problem is still here.  Let me explain it.

OK let's say I'm listening to some mp3's or watching a video, it doesn't matter what the format of the video is.  Then let's say I decide to go to youtube and watch a video or 2 over there.  Then I decide to go back to mp3 or watching a video. 

When I decide to go back to the mp3 or video after being at youtube things don't work.  Like the mp3s freeze up right at the first second and so does the player.  As for the videos they will play, but with no sound, and then after the file is finished the player freezes.

The only fix is to log out and log back, and sometimes I have to completely restart everything.

So it seems there is a problem going from Flash to MP3/AVI or whatever.  Sometimes though there is a problem going from MP3 to Flash.  That's rare though.

Anyway just to spell it out again.  The problem is going from Flash to MP3, AVI, MPEG, or WMV.

Is this a bug??  I couldn't seem to find it as a bug on line...but I may have been looking for it wrong...

Anyway this only happened to me in Hardy.  All the other ones from Dapper to Feisty the only thing that would happen is Flash wouldn't work if any media players were open.

Oh and I know this isn't just my laptop this is happening on.  This has happened on 2 different laptops that I have witnessed.

Also the media players involved are Amarok, VLC, Movie Player, Xine, and Rhythm Box.  Those are the only ones I use.

---

### Post by ragtag on 2008-10-26
I'm guessing it's a problem with PulseAudio.

Search the forums for info on how to either remove PulseAudio and use ALSA, or preferably get PulseAudio working with all your applications.

---

### Post by PrinceArithon on 2008-10-26
Ah thanks.  I'll have to do that.  I think I read somewhere else that Pulse is kinda a ******* when it comes to playing nicely....

I'll have to look around now.  Thank you.


Edit:

OK I found the fix.  It's really simple.  All I had to do was install libflashsupport by doing:

sudo apt-get install libflashsupport

After that all it needed was a logout and log back in.  Now I can go back and forth between flash and the other media files with no problem.

Now if only I could figure out how to fix my logon music problem...

---

