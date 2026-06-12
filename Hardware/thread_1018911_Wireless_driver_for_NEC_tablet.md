---
title: "Wireless driver for NEC tablet"
date: 2008-12-22
forum: Hardware
---

### Post by yard on 2008-12-22
I've just installed 8.10 on an old NEC Versa Litepad tablet.  Three problems: no stylus, no wireless, and wrong screen resolution.  I tried a live version of Dapper and with it, the wireless and the screen were fine.  Copied xorg.conf to 8.10 to fix screen resolution.  How can I "roll back" the driver to what I was using with the Dapper Live disk or at least figure out what it was?  Still working on stylus...

---

### Post by LarrySPS on 2009-03-05
yard,

I've been thinking of breaking out my old NEC tablet and doing the same thing, although I haven't seen anything yet that suggests that it's possible to live in a Linux environment with complete tablet support.

Since my bad old days of doing I.T. work in the Windows world, I've gone back to an Apple environment (OS X is a nice change of pace from the old days of the mid 80's -- I can jump back into Unix whenever I need to get anything serious done).  But, if I were able to run my tablet completely in a Linux environment, it would allow me to take it to class and use for note-taking / word processing / browsing.

How'd the attempt at getting the stylus recognized work out for you?  Any updates?  Did you get it going, or eventually give up on it?

Thanks!

Larry

---

### Post by Favux on 2009-03-05
Hi LarrySPS,

I hope you hear from yard soon.

> Also NEC uses a standard Wacom stylus – the same as the Acer with their Tablet PC so you can use any Wacom stylus that you prefer. The stylus writes comfortably on the screen without requiring additional effort. 
From:  [http://www.tabletpctalk.com/reviews/versalitepad.shtml]("http://www.tabletpctalk.com/reviews/versalitepad.shtml")
If this is right, it most likely has a serial Wacom active digitizer (no battery) in the stylus.

In which case if you're able to install Ubuntu then the linuxwacom drivers and the default HAL .fdi file should handle the stylus.  I noticed that the link showed a stylus with a side-button.  I couldn't tell if there is an eraser.  If there is you may need to configure your xorg.conf.

All in all it should be doable.  The main problem may be ram.  The first model had 256 MB?

---

### Post by casualdays on 2009-06-26
> **yard said:**
> I've just installed 8.10 on an old NEC Versa Litepad tablet. Three problems: no stylus, no wireless, and wrong screen resolution. I tried a live version of Dapper and with it, the wireless and the screen were fine. Copied xorg.conf to 8.10 to fix screen resolution..
 Digging up an old thread..is there anyway I can do this from Ubuntu 9.04?
 
I just got a Litepad, and I love it. I just want to have a full resolution with Ubuntu. I currently only am allowed to go up to 800x600.
 
Also, it seems like the standard Wacom drivers aren't really working. They only work sporradically.
 
Help me Ubuntize my Litepad!!

---

### Post by Favux on 2009-06-27
Hi casualdays,

Welcome to Ubuntu!

You probably ought to address the video problem first.  I probably won't be much help with that.  Do you know what video card you have?

For the Wacom it sounds like the .fdi is "working".  What do you mean by sporadically?  The .fdi controlling things is most likely the 10-wacom.fdi at "/usr/share/hal/fdi/policy/20thirdparty/".  If you look in it you'll see the various subsections.  The serial subsection has a identifier match line near the beginnning.  You'll see the various wacom tablets ID begins with WAC.  So if you do a "lshal>lshal.txt" you should be able to pull up your wacom sections in gedit with find.

---

### Post by casualdays on 2009-06-27
The Versa litepad has a Trident Cyber Aladdin-T 16MB (shared) video card. I believe I have the correct drivers installed- when I open the Synaptic Package Manager I have the xserver-xorg-video-trident package installed, version  !:1.3.0-1ubuntu1. Was an older package better? It tells me under the Display heading that it is an unknown display. I was just curious since the OP was able to achieve the full screen resolution by transferring an older Linux's files to 8.10. 

As for the Wacom part, I need to know where I should calibrate the screen. Essentially what happens is that the touchscreen works sometimes and then after a restart, it won't work.

I just want Ubuntu.

Still stumped..:confused:

---

### Post by Favux on 2009-06-27
Hi casualdays,

I know a little about Trident cards.  If your bios allows you to share more RAM with the video card I'd definitely consider doing that.  I'm going to do a little info. dump on you.  It shouldn't take that long to skim through these threads.

In Jaunty you probably just need the video sections from the xorg.conf in post #13 from the following:  [http://ubuntuforums.org/showthread.php?t=1102194](http://ubuntuforums.org/showthread.php?t=1102194)  Be cautious and back up xorg.conf before you do anything.  Another one is:  [http://ubuntuforums.org/showthread.php?t=1029397&highlight=tablet](http://ubuntuforums.org/showthread.php?t=1029397&highlight=tablet)  And Jaunty has given you nearly the latest driver as you can see from posts #21 and #27 here:  [http://ubuntuforums.org/showthread.php?t=1053210](http://ubuntuforums.org/showthread.php?t=1053210)

To calibrate your tablet you'd want to use wacomcpl described in Section 3 here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  But to do that you need the following command in a terminal:
```
xsetwacom list
```
to return linuxwacom names like stylus and eraser.  If it is blank then wacomcpl won't work.  To see the names HAL is returning in a terminal enter;
```
xinput --list
```
Then you either need to rename things or try rec's script.  3 or 3a in Jaunty Users near the top here:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

So take it slow and read through this stuff until you have a handle on things.

Good luck!

PS:  If you want me to look at any proposed changes to your xorg.conf before you implement them I'd be happy to.

---

