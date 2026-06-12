---
title: "Programs hogging sound."
date: 2008-07-22
forum: General Help
---

### Post by Phastor on 2008-07-22
I have a few programs that are very particular on how they want to share sound with others.  The two I am having issues with so far are WoW (through wine) and Second Life (Linux client, not windows through Wine). For example, if WoW is running and I open up a youtube video or music in Banshee, no sound will play.  However the sound in WoW keeps working.  The sound in other apps will not work until I close WoW.  On the other hand, if music is playing or a YouTube video is open and I open up WoW, then the sound in WoW doesn't work and will remain that way until I close all other apps that use sound.  Second Life behaves the same way.  I'm hoping both of these games are behaving like this for the same reason and can be fixed with one solution, as well as any other programs that share the same problem.  In short:

-WoW running first, no other sounds play.
-Close WoW, other sounds play again.
-Apps with sound running first, no sound in WoW.
-Close all apps with sound, WoW sounds play again.

I am assuming that the problem resides in Wine, and not WoW itself.  So I guess this is more of a question about Wine than WoW.  I imagine anything running through Wine would behave the same way, but say I'm wrong if I am.

I'm hoping someone out there may have had an issue like this and knows how to stamp it out.

Thank you!

---

### Post by iaculallad on 2008-07-22
> **Phastor said:**
> I have a few programs that are very particular on how they want to share sound with others.  The two I am having issues with so far are WoW (through wine) and Second Life (Linux client, not windows through Wine). For example, if WoW is running and I open up a youtube video or music in Banshee, no sound will play.  However the sound in WoW keeps working.  The sound in other apps will not work until I close WoW.  On the other hand, if music is playing or a YouTube video is open and I open up WoW, then the sound in WoW doesn't work and will remain that way until I close all other apps that use sound.  Second Life behaves the same way.  I'm hoping both of these games are behaving like this for the same reason and can be fixed with one solution, as well as any other programs that share the same problem.  In short:

-WoW running first, no other sounds play.
-Close WoW, other sounds play again.
-Apps with sound running first, no sound in WoW.
-Close all apps with sound, WoW sounds play again.

I am assuming that the problem resides in Wine, and not WoW itself.  So I guess this is more of a question about Wine than WoW.  I imagine anything running through Wine would behave the same way, but say I'm wrong if I am.

I'm hoping someone out there may have had an issue like this and knows how to stamp it out.

Thank you!

Try to install the audio support wrapper file:

```
sudo apt-get install libflashsupport
```

---

### Post by Phastor on 2008-07-22
What does this do?

---

### Post by iaculallad on 2008-07-22
> **Phastor said:**
> What does this do?

This terminal command will install the wrapper for non-free Flash plugin.

---

### Post by Phastor on 2008-07-22
No effect.  Unfortunately it's not just Flash.  If I have any app open that uses sound in any way before I load WoW, the sound in WoW(wine overall?) will not work until I close those apps and restart WoW.  Same thing if WoW is open before I open up another app using sound.  That app will not play sound until I close WoW and restart that app.

As far as flash goes, all I have to do is close any tabs with a flash video.  Don't have to close Firefox completely.

---

### Post by danwood76 on 2008-07-22
For the sound issue you need to setup pulse correctly to handle the different audio streams.
Check this guide out:
[http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio+setup](http://ubuntuforums.org/showthread.php?t=776739&highlight=pulse+audio+setup)

And flash is a little buggy you just have to live with it.

---

### Post by Phastor on 2008-07-22
I set up Pulse.  Seems to work partially.  Everything works together now except for WoW, but I'm guessing that's some kind of Wine issue?

---

### Post by danwood76 on 2008-07-22
Make sure wine is using alsa if its using OSS then it wornt work with pulse.
Though you can run it through a pulse emulator but its easier just to set wine to use ALSA.
(See the additional info in that guide)

-- edit --

If you read the current issues it does say Wine doesnt work through alsa, esd, or oss.

---

### Post by danwood76 on 2008-07-22
I just found an interesting thread with a solution to wine:
[http://ubuntuforums.org/showthread.php?t=789578&highlight=wine+pulse](http://ubuntuforums.org/showthread.php?t=789578&highlight=wine+pulse)

See 'Appendix A: General Tips'

---

### Post by Phastor on 2008-07-23
Got WoW working now with that article you linked.  However even though Pulse solved my issue, it seems like such a jimmy rigged solution.  I don't know if I can remember and keep track of all those changes I made in configs and such.  However I just ran into another package that, from what I understand, does the same thing called alsa-oss(aoss).  From the looks of it there are no configs to change and all you do is prefix OSS using apps with aoss when you run them and it will channel them through alsa.  Since I think I have a better understanding about OSS and it's the OSS apps that don't like to share sound, wouldn't aoss be a better solution for me, or am I still better off with the Pulse server?

---

### Post by danwood76 on 2008-07-23
The pulse sound server is the default sound server in ubuntu so its a little hard not to use it.
It is a very good system it allows you to do all sorts of things with your sound.

The only problem is it isnt really configured correctly in Ubuntu by default and as so many people have so many different sound configurations you can see why.

The aoss will go through pulse anyway so its probably better to do poss instead.

I would stick with Pulse audio, especially if you have it working now ;)
The pulse audio guides will always be on here if you need to reinstall and there isnt really too much configuration changing when you get to know the system.

---

