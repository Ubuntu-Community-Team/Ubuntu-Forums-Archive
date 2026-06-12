---
title: "Linux newbie needing help w/ display"
date: 2009-11-29
forum: Hardware
---

### Post by jazzyeagle on 2009-11-29
Hello -

I've been scouring the forums for the past two days trying to find a thread that can help me get my display working correctly w/ Ubuntu, but either the threads I find are too technical that I can't figure out what I need to do, or the suggestions didn't work.  I have very limited past experience with Linux (tried Slackware & Red Hat about 8 years ago, but never could get it to network), and most of what I knew I've forgotten since then.

Here's what I'm working with:  I've got a Dell Latitude D420 laptop which uses Intel GMA 950.  I'm having wireless network issues as well, but I have the internet connected via wire right now, and I'm not even going to try to overcome that issue until I can see the screen clearly.

The issue I'm having is hard to explain.  The closest I can come to describing it is that it looks blurry.  There's a diagonal line of pixels that should be there, and it appears that the pixels for text is not lining up as they should. 

I've seen the recommendation to set the Visual Effects to none, which I've done several times (it seems to reset itself every restart?), and it helps immensely, but there's still some "blur" on the screen.

I saw another recommendation about appending "i915modeset=0" to a specific line in etc/default/grub, and I did this and restarted the computer, and there was no change.  My brother, who works with Ubuntu a little, also recommended adding "VGA=865" to this file, and it had no effect iether.

I've seen several mentions of xorg.conf, but I can't find it, so I can't check it, nor do I know if there's any settings in there that could help (NOACCEL perhaps?)

I've also seen numerous mentions about drivers.  I believe the one suggestion I understood was a command, which (going off of memory) was something along the lines of "sudo apt-get install xorg-???-video-intel" (the ??? is the part I don't remember).  The response from this was that I already had the most up to date driver.

I'm not sure what else to try or what other information to provide (or how to get it for you), so I'm open to whatever suggestions you can provide.  Thank you!!!

---

### Post by beloved88 on 2009-11-29
I'm also fairly new, so i know what it's like especially when things don't seem to work right off the bat.  Most of my solutions will be increadibly low-tech, nothing really with the cli or anything like that.  Some simple suggestions are to try a few different releases, and see how it works.  I had some trouble with 9.10 so i stuck to 9.04 instead and had a lot less problems.  You can also try installing using different methods, ie LiveCD verses LiveUSB, and try different utilities to make the live USB, the only one that really worked for me was ImageWriter.  You can also try some of the remix versions, such as Easy Peasy Ubuntu, which really was easy for me (although the size of the image requires a USB as opposed to a CD, and again, i only had luck with ImageWriter, the standard USB startup disk creater didn't work for me for some reason).  If it works for you, but you still have wireless issues, you may have a broadcom wireless device, which may require the installation of a proprietary driver, which i can guide you though, but try that other stuff first.  If it does, but you get no wireless, put the following into a terminal and paste the stuff you see here.
```
lspci
```

---

### Post by jazzyeagle on 2009-11-30
Thanks for the reply.  Yes, it's a Broadcom wireless card.  I saw something about an B43 cutter utility, but I'm not ready for that step yet.  I want to be able to read my screen properly first.

Now that you mention it, I did recall seeing a Dell-specific ISO for 9.04 that's said to include the proprietary drivers for most Dell machines.  Has anyone tried this ISO?  Does it really work?  I hesitate to spend another 2 hours downloading and installing a new ISO if it's not going to work.  Also, is there any programs missing from that ISO?  Also, could I then upgrade from 9.04 to 9.10 and still have those proprietary drivers?  I just don't know what comes with it.  I guess it's worth a shot if no one has any answers this.

Thanks!!

---

### Post by RochJer on 2009-11-30
> **jazzyeagle said:**
> Thanks for the reply.  Yes, it's a Broadcom wireless card.  I saw something about an B43 cutter utility, but I'm not ready for that step yet.  I want to be able to read my screen properly first.

Now that you mention it, I did recall seeing a Dell-specific ISO for 9.04 that's said to include the proprietary drivers for most Dell machines.  Has anyone tried this ISO?  Does it really work?  I hesitate to spend another 2 hours downloading and installing a new ISO if it's not going to work.  Also, is there any programs missing from that ISO?  Also, could I then upgrade from 9.04 to 9.10 and still have those proprietary drivers?  I just don't know what comes with it.  I guess it's worth a shot if no one has any answers this.

Thanks!!

You can use the ISO file and use it with CD-Rom drive only without installing Ubuntu OS itself and test 9.10 to see if your proprietary drivers will be compatible with Karmic release. If you feel up to the peak that you can install 9.10, you can go ahead. If it doesn't work out, you can always downgrade. Just keep the 9.04 CD handy.

---

### Post by jazzyeagle on 2009-11-30
> You can use the ISO file and use it with CD-Rom drive only without installing Ubuntu OS itself and test 9.10 to see if your proprietary drivers will be compatible with Karmic release. If you feel up to the peak that you can install 9.10, you can go ahead. If it doesn't work out, you can always downgrade. Just keep the 9.04 CD handy.Ok, I went to go download the Dell ISO, and it's a 1.8GB file.  Unfortunately, I don't have a DVD burner I can use, so unless there's a way for me to run it straight from laptop somehow, I'm not going to be able to use this option.

Maybe a screen shot would help.  I at first didn't try it, because I assumed it was the video card and therefore believed the screen shot would not capture what I'm seeing, but I just noticed that the images are in fact printing clearly, it's just the fonts that seem to be all blurred.  For the heck of it, I went ahead and tried a screen shot, and sure enough this  shows you what I'm seeing.

Based on this revelation, I tried changing to different fonts, and all of the various settings under the font tab of System -> Preferences -> Appearances, but it's still blurry.

Given this information, does anyone have any other ideas?  Thanks!!

---

### Post by RochJer on 2009-11-30
Ubuntu 9.10 ISO doesn't tend to be at around 1.8 gb. It tend to be up to 700 MB at least or less than 700 MB. Dell ISO may have complete Ubuntu package but ubuntu site have the download link to get ubuntu CD for this MB usage. 

For the graphic blurry issue, have you received the message or anything about the restricted drivers for your graphic card? You may want to check on this out and look for the video card for Restricted Drivers and update to the recommended version. It may fix this blurry issue you are experiencing at this time.

---

### Post by beloved88 on 2009-12-01
Disclaimer: I know next to nothing
My thought, looks like a font rendering issue, maybe you could try going into System>Preferences>Appearence>Fonts and under rendering there's a ton of stuff.  I know my fonts look horrible with the monochrome option selected, although not quite as bad as yours.  Also you hit that details button and there's a bunch more options too, from smoothing to subpixel RBG order and all kinds of stuff.
Other than that, what the other said seems far more likely to work.  I'm pretty dumb when it comes to this stuff, but i seem to have gotten pretty far on my own.

---

### Post by beloved88 on 2009-12-01
> **jazzyeagle said:**
> Ok, I went to go download the Dell ISO, and it's a 1.8GB file.  Unfortunately, I don't have a DVD burner I can use, so unless there's a way for me to run it straight from laptop somehow, I'm not going to be able to use this option.

Maybe a screen shot would help.  I at first didn't try it, because I assumed it was the video card and therefore believed the screen shot would not capture what I'm seeing, but I just noticed that the images are in fact printing clearly, it's just the fonts that seem to be all blurred.  For the heck of it, I went ahead and tried a screen shot, and sure enough this  shows you what I'm seeing.

Based on this revelation, I tried changing to different fonts, and all of the various settings under the font tab of System -> Preferences -> Appearances, but it's still blurry.

Given this information, does anyone have any other ideas?  Thanks!!

That's so weird!!! it doesn't affect the actual desktop environment at all!  The windows and desktop look pristene, but all text and icons in your launcher and what not look horrible.  wow, there's so much i don't know about how stuff works.

hmmm... maybe you could rule some issues out.  Have you tried hooking up an external monitor to your VGA output (assuming you have a VGA output, not an HDMI) and see how it works out on that?

---

### Post by jazzyeagle on 2009-12-01
[RochJer]("http://ubuntuforums.org/member.php?u=557921") - I did try the standard ISO's for Ubuntu and Kubuntu, and I JUST tried 9.04 Ubuntu this morning, with the same issue.  I read that there needs to be a proprietary driver, but when I check Intel's website, it talks about using the standard Intel drivers that come with the distro.  I tried upgrading that, but I got a reply that I have the most current version.  I also checked for Hardware Drivers, and the only thing I found were my wireless network drivers (and now I have wireless!!  yay!!)  There appears to be ways to download something via git, which I'm not sure exactly how that works, but I'll look into that when I have a chance.  If you have any advise on how those work, I would greatly appreciate it!!

beloved88 - I tried messing with ALL of the different font settings.  I even downloaded ccsm and tried disabling as many settings on there as I could.  Still no change.  I do agree that it's bizarre that the Dell ISO is twice the size as the standard one when the only difference is supposedly proprietary drivers and a simple flash install, but there's nothing I can do about that.  In regards to the monitor, unfortunately, I threw away the only monitor I had last year, since it was one of those old heavy CRT monitors and my desktop died eons ago (the only remaining memory I have of it are its hard drives and sound card.  May it Rest In Pieces).

---

### Post by Grenage on 2009-12-01
Is it not possible that the display seems blurry because it's not using it's native resolution?

---

### Post by jazzyeagle on 2009-12-01
> **Grenage said:**
> Is it not possible that the display seems blurry because it's not using it's native resolution?
 
That's actually one of the first things I tried, and I tried again last night.  I tried four different resolutions (including the lesser 640x480 & 800x600) at all different refresh rates offered for each resolution, and it still didn't improve.

---

### Post by Grenage on 2009-12-01
It looks like 1280x800 is the native resolution, is that an option?

---

### Post by RochJer on 2009-12-01
Try to test all the resolutions to see if the blur decreases. Did you try to use it in previous Ubuntu versions? If all have same results, it may be your monitor issue or video card. If so, refer to your manufacturer for this issue via monitor or video card. Test first, evaluate the resolutions and if it doesn't work out, contact them and see what comes up.

---

### Post by jazzyeagle on 2009-12-01
<quote>[Grenage]("http://ubuntuforums.org/member.php?u=263074"): It looks like 1280x800 is the native resolution, is that an option?</quote>

That is the default option.  This is what it was set to when it installed.  It only has one option for refresh rate:  60 hz.

<quote>[RochJer]("http://ubuntuforums.org/member.php?u=557921"):  Try to test all the resolutions to see if the blur decreases. Did you try to use it in previous Ubuntu versions? If all have same results, it may be your monitor issue or video card. If so, refer to your manufacturer for this issue via monitor or video card. Test first, evaluate the resolutions and if it doesn't work out, contact them and see what comes up.</quote>

I tried 9.04 on here, and had the same result.  The weird thing is that the person who gave me this laptop had 9.04 on here, took off the display effects, and the picture was nice and clear.  I'm assuming he downloaded some proprietary drivers for the Intel GMA 950.  I only wish I could get ahold of him to find out what he did.  I only hesitate to do so, because I'm such a newbie at Linux and don't know what the heck I'm doing.  I guess I'm going to have to dive in and figure it out.

---

