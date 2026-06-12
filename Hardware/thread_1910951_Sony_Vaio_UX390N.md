---
title: "Sony Vaio UX390N"
date: 2012-01-18
forum: Hardware
---

### Post by Netsurfer_x1 on 2012-01-18
Hi all! Long time lurker, first time poster.

Anyway, I'm about to receive a Sony Vaio UX390N that I got for a very reasonable sum from Ebay. Naturally, I intend to junk the version of WIN (Vista) pre-installed on the unit & install 11.10.

But before I get it, and before I do anything stupid, I would like to know if there are any "Gotchas!" I need to worry about (i.e.: proprietary drivers, hardware not supported by Ubuntu, bugs, glitches, & other oddities, etc.)

Any help at all will be useful.

---

### Post by possumkeys on 2012-01-18
Hi,
Been using it a bit. On my acer, there were brightness issues during install and also during booting that were solved by a simple script in rc.local. Might not be so on your Sony. Who knows.
Otherwise, no complaints from me.

---

### Post by raja.genupula on 2012-01-18
HI man , install it and i am sure it will be fine . If you found any issues , all will be minor and by posting here you can get solution . 

All the best.

---

### Post by Netsurfer_x1 on 2012-01-18
Hmmm...OK. I guess I'll just "cowboy" it & come back here with any issues I have.

With any luck, I'll be able to report no major issues, change the header to [SOLVED] & request the mods to lock the thread.

Wish me luck & I'll be back in a few days.

---

### Post by nipunshakya on 2012-01-18
Well, goodluck. Guess you won't have any problem if u start right. Understand what you do with your linux coz linux thinks the same; that you know what you are doing. 

Regards,WinuxUser

---

### Post by sudodus on 2012-01-18
My little contribution would be to suggest you try not only 'vanilla' Ubuntu but also Kubuntu or some other flavour of Ubuntu. If you have a fairly fast internet connection, it is worthwhile to download another iso file, make a boot CD or USB drive and test it live before installing.

---

### Post by Netsurfer_x1 on 2012-01-27
Okay, testing complete. All things considered, installation went well. I attempted to fix any problems on my own, so anything posted here is stuff I need help resolving.
 
So here's the few remaining niggles to work out:

1. No sound from the built in speaker. It **does** pipe the sound out through the headphone jack, but inexplicably, no activity from the built in speaker.

2. The "VAIO Launcher" button is not recognized by the system. Attempted to map with similar function to the WIN key (opens the Dash), but no dice.

3. Zoom In/Out buttons are not recognized. Attempted to map to perform same activity. Again, no dice.

4. "Capture" button (**not** to be confused with PrtSc) is not recognized. I'd like this to launch a "camera" type program (also, can anyone recommend an app to use as such?). Then, while in the program, have it perform as a shutter release/record start/stop button.

5. Neither (front & rear-facing) "MotionEye" cameras are recognized (as confirmed by Skype).

6. The fingerprint/biometric scanner is not recognized by the system. Which is a bummer, because I'd like to use that to log in/authenticate instead of having to deal with the "thumb-board" style keyboard.

---

### Post by nipunshakya on 2012-01-27
1. Did your built in speaker work when u had vista in it?? did u make sure that not ubuntu but vista would give u sound via your built in speakers?
2. If you press the WIN key in a PC, it will guide you to BASH itself...so thats not a big deal.
3. Maybe you dig in for some drivers so that the keyboard functionality works well.
4. In case of windows, "Print Scrn" button is present. On pressing it, it will let you save the screenshot it takes for you to the destination you want. I don't know about a VAIO though. There is a software called cheese...never tried that out but i guess the release/record and all gan be covered with that software.(see software center and search "cheese" there)
5. First solve this issue with webcam. But using cheese might make things right i guess...
6. Maybe the drivers are still missing.

I suggest you once open software center, search "Additional Drivers" in the searchbox(top-right corner), install the software and run it through bash(type Additional Drivers there too). This software will detect for additional drivers needed by your system and recommend you some..try those, have a restart and see if that works.

Good-luck and Happy Linuxing.
Regards,WinuxUser

---

### Post by critin on 2012-01-28
> Naturally, I intend to junk the version of WIN (Vista) pre-installed on the unit & install 11.10.

Have you used linux before?  I vote for keeping Windows and dual booting until you feel comfortable with it.  But of course, some would rather go 'cold turkey' and not depend on a security blanket. (windows)  :P  
At least make a recovery disk of Windows.

---

### Post by Netsurfer_x1 on 2012-01-28
> **WinuxUser said:**
> 1. Did your built in speaker work when u had vista in it?? did u make sure that not ubuntu but vista would give u sound via your built in speakers?
2. If you press the WIN key in a PC, it will guide you to BASH itself...so thats not a big deal.
3. Maybe you dig in for some drivers so that the keyboard functionality works well.
4. In case of windows, "Print Scrn" button is present. On pressing it, it will let you save the screenshot it takes for you to the destination you want. I don't know about a VAIO though. There is a software called cheese...never tried that out but i guess the release/record and all gan be covered with that software.(see software center and search "cheese" there)
5. First solve this issue with webcam. But using cheese might make things right i guess...
6. Maybe the drivers are still missing.

I suggest you once open software center, search "Additional Drivers" in the searchbox(top-right corner), install the software and run it through bash(type Additional Drivers there too). This software will detect for additional drivers needed by your system and recommend you some..try those, have a restart and see if that works.

Good-luck and Happy Linuxing.
Regards,WinuxUser

> **critin said:**
> Have you used linux before?  I vote for keeping Windows and dual booting until you feel comfortable with it.  But of course, some would rather go 'cold turkey' and not depend on a security blanket. (windows)  :P  
At least make a recovery disk of Windows.

For the both of you: One area of Linux that I'm very weak on is using Bash/Terminal. So I might need a bit of a skilled hand here.


For WinuxUser:

1. Yes, the built in speaker did work when I had Vista (it gave me the standard WIN sounds, i.e.: error beeps, 4 note boot fanfare, et al.). Granted, more often than not, I'll be using headphones with it anyway, but it's a nice option to have.

2. Actually, the WIN key opens up the Dash Home on my install. I can easily re-map that without problem though.

3. Already had a look through the system apps & did what I could with the knowledge I've got & the tools I had.

4. Actually, the "Capture" isn't meant to be used a screencap button. It's meant to serve the same function as camera's shutter release/record start/stop on a camera/camcorder. Perhaps I should clear that up in my original post (Oops! :X )

5. Thanks for the tip with regard to Cheese. I still didn't help. I would seem then, that drivers are missing.

6. That was my thought too.

Misc: Already ran the Additional Drivers app. It turned up no results.


For critin:

Yes, I have been using Linux for a while now. And I absolutely despise WIN, especially Vista! To me, Vista reminds me of that one car that General Motors makes, but that's so bad they can't even give it away.

---

### Post by mörgæs on 2012-01-28
Changed the thread title to a more informative one and moved it to the hardware forum.

When you are through experimenting, please consider a post in 
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006) .

---

### Post by Netsurfer_x1 on 2012-01-28
Cool! Thanks much!

---

### Post by Netsurfer_x1 on 2012-02-01
Bumping because I know someone can help me sort this out & I don't want this one to get lost in the shuffle.

---

### Post by sudodus on 2012-02-02
> **Netsurfer_x1 said:**
> Bumping because I know someone can help me sort this out & I don't want this one to get lost in the shuffle.
Please be more specific and ask direct questions!

---

### Post by Netsurfer_x1 on 2012-02-02
Well, please see posts 7, 8 & 10 in this thread. Those are the questions & problems I'm trying to resolve.

---

### Post by sudodus on 2012-02-02
> **Netsurfer_x1 said:**
> Okay, testing complete. All things considered, installation went well. I attempted to fix any problems on my own, so anything posted here is stuff I need help resolving.
 
So here's the few remaining niggles to work out:

1. No sound from the built in speaker. It **does** pipe the sound out through the headphone jack, but inexplicably, no activity from the built in speaker.

Sometimes you need to reconfigure the audio settings because they might simply be muted after installation. Try the graphical user interface (which looks different depending of version).
> 
2. The "VAIO Launcher" button is not recognized by the system. Attempted to map with similar function to the WIN key (opens the Dash), but no dice.
I don't know, I don't have that computer. **[COLOR="Red"]Let us hope someone with the same kind of computer comes in and helps[/COLOR]**> 
3. Zoom In/Out buttons are not recognized. Attempted to map to perform same activity. Again, no dice.
I don't know ...> 
4. "Capture" button (**not** to be confused with PrtSc) is not recognized. I'd like this to launch a "camera" type program (also, can anyone recommend an app to use as such?). Then, while in the program, have it perform as a shutter release/record start/stop button.I don't know about the button, ... Try Cheese!> 

5. Neither (front & rear-facing) "MotionEye" cameras are recognized (as confirmed by Skype).
I don't know ...> 
6. The fingerprint/biometric scanner is not recognized by the system. Which is a bummer, because I'd like to use that to log in/authenticate instead of having to deal with the "thumb-board" style keyboard. I'm not sure there is such software for Ubuntu. My daughter has a Toshiba with fingerprint, which only works in Vista.

---

### Post by mörgæs on 2012-02-02
Having so many problems with 11.10 it is worth trying a live boot of 12.04.

---

### Post by Netsurfer_x1 on 2012-02-03
An interesting idea. But after having been burned by "alpha" software before (it wasn't Ubuntu), I don't use alpha software, & I avoid using betas as much as possible.

---

### Post by Netsurfer_x1 on 2012-02-03
> **sudodus said:**
> Sometimes you need to reconfigure the audio settings because they might simply be muted after installation. Try the graphical user interface (which looks different depending of version).


I messed around with that (spent a good 15 minutes or so testing all options), no dice.

---

### Post by mörgæs on 2012-02-03
I was thinking of a live boot. It is important to know what is in the pipeline no matter if you install or not.

---

### Post by sudodus on 2012-02-04
> **mörgæs said:**
> I was thinking of a live boot. It is important to know what is in the pipeline no matter if you install or not.

I support that suggestion of *mörgæs *(to try Ubuntu 12.04 alpha *live*). Furthermore, I suggest that you try other distros *live*, for example Linux Mint 12 (based on Ubuntu 11.10). Maybe you can browse the internet searching for *linux Vaio UX390N* and find a success story leading you to a distro, that works well with your hardware. At least you should get the loudspeakers and cameras to work.

---

### Post by mörgæs on 2012-02-04
Maybe this thread helps:
[http://ubuntuforums.org/showthread.php?t=1731232](http://ubuntuforums.org/showthread.php?t=1731232)

---

### Post by Netsurfer_x1 on 2012-02-04
Hmmm...An interesting idea. Might be worth investigating.

---

