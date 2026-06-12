---
title: "Koala 9.10 Adobe Flash Audio Problem"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by alaren on 2009-10-30
I upgraded to 9.10 from 9.04 (Kubuntu, all 64-bit).  My audio appeared to be working fine until I loaded a video from YouTube.

When that didn't work, I loaded up Amarok, which said my audio (Intel HDA Analog) wasn't working.  Closed Firefox, restarted Amarok, sound works fine.  In my multimedia settings, the "test" button works fine.  Videos play back fine--as long as Firefox or Konqueror isn't trying to use audio for Flash videos. 

I've tried both the free and the nonfree plugin installers.  Neither give me sound but in every other respect they work find--I see the content just fine.  There's just no sound.

However, the Flash plugin worked fine in 9.04, the 9.10 upgrade definitely introduced the problem...

I have seen several posts about people lacking sound because audio drivers weren't loaded or similar issues, but obviously my sound is working fine so those don't seem to apply (though some responders do mention Flash as opposed to sound generally).  It's hard to watch Google Wave videos without audio. d^_^b

So, have I narrowed it down to the 64-bit plugins in the 9.10 repos or is there something else I should try to fix this?  I've done everything I can think to do.

---

### Post by Ajat on 2009-10-30
have you tried to use pluseaudio? 
it was happen to me too, but i forget how to fix it.. i think i played around with that pulse-something...

---

### Post by alaren on 2009-10-30
If anyone else encounters this... [this thread]("http://ubuntuforums.org/showthread.php?t=1304783") mentioned launching "alsamixer."

I initially didn't do that because I figured the KDE mixer was basically the same thing.

However, in alsamixer there were a couple extra channels that showed--and were muted.  I unmuted everything and my sound came back.  No idea why the 9.04 -> 9.10 upgrade would mute something that wasn't previously muted, but apparently it did--and it wasn't something I could fix with the KDE mixer for whatever reason.

---

### Post by Andyc709292 on 2009-11-03
So, I've been having the same problem - no sound in Flash in a clean Kubuntu 9.10 install with fresh flash installation. 
I'm a newbie, but game for a laugh and tried all sorts, following the google trail for kubuntu and ubuntu generally ending up making a mess of my nice clean installation.
But, I think I have a solution!

This thread:
[http://ubuntuforums.org/showthread.php?t=649569](http://ubuntuforums.org/showthread.php?t=649569)

Goes on about removing oss, and in doing so, removing all reference to OSS I've got sound in Flash now. Yeay!

Looking around the web I'd say there's no simple solution for everyone though, many things to try I think.

---

### Post by steronius on 2009-11-03
i did a _sudo apt-get purge pulseaudio_ and rebooted.
i have great audio, but no volume control widget.

i don't really understand the pulseaudio issue.

can we downgrade pulse or do we wait for next release?

i started with this thread (others had the issue):
[http://ubuntuforums.org/showthread.php?t=1168194&page=3]("http://ubuntuforums.org/showthread.php?t=1168194&page=3")

but ultimately it was this that told me what to do:
[http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html]("http://www.ubuntumini.com/2009/09/fix-most-audio-problems-remove.html")

---

### Post by Zoot7 on 2009-11-03
> **steronius said:**
> i did a _sudo apt-get purge pulseaudio_ and rebooted.
i have great audio, but no volume control widget.

i don't really understand the pulseaudio issue.
Ditto.

What sorted sound from flash for me and letting me get sound from flash and banshee at the same time was installing the package 
flashplugin-nonfree-extrasound through synaptic.

TBH I'd much rather a no frills ALSA setup, Pulse isn't really ready get. Of course there's a lot of potential, paving the way to features like a system wide equalizer etc. But Alsa alone has always been much better for me.

---

### Post by BlackXIII on 2009-11-05
To fix it i just had to run alsamixer in the console and use the arrows to move the pcm slider up. ('m' toggles mute and ESC exits alsamixer)

---

### Post by magikx21 on 2009-12-09
> **BlackXIII said:**
> To fix it i just had to run alsamixer in the console and use the arrows to move the pcm slider up. ('m' toggles mute and ESC exits alsamixer)

Had the same issue in Kubuntu 9.10 NBR and this worked for me. Wish I would have saw this before removing and manually installing Flash.

---

### Post by Mustache Villain on 2010-01-31
> **BlackXIII said:**
> To fix it i just had to run alsamixer in the console and use the arrows to move the pcm slider up. ('m' toggles mute and ESC exits alsamixer)

Thank you so much, this worked for me. I think Kubuntu developers should do this during installation. It's a minor issue but very non-user friendly at the same time.

---

### Post by amr2205 on 2010-02-27
> **magikx21 said:**
> Had the same issue in Kubuntu 9.10 NBR and this worked for me. Wish I would have saw this before removing and manually installing Flash.

Strange, but it's true... it worked for me too :P

---

### Post by SFaulken on 2010-03-21
firing up alsamixer and turning PCM all the way up fixed the issue in the Kubuntu Lucid Alpha 3 as well.

I love easy fixes.  Finding them seems to be the problem.

---

### Post by ascara on 2010-04-24
Verified fix in Kubuntu 10.04-rc Lucid Lynx.

Sound working fine in all cases except for when Firefox is open and Flashplayer is engaged.  Opened alsamixer in a terminal, right arrow over to PCM, turn it up to max, escape to exit.  After that, without reboot, opened YouTube and played a flash video, complete with sound.  Perfect and simple.

---

### Post by scorpion_gr on 2010-04-28
My audio in flash has been dead too for a long while and I don't remember when it happened, but I do seem to remember initially all was working fine. After reading a bit around in this and a few other threads I decided to start with the simple stuff:

I installed alsamixer and turned up the volume level for PCM (which was down to 0). Now I have sound in flash again. Simple as that. Thanks everyone!

---

### Post by volodymyr on 2010-06-25
Hello everyone,

I have the same problem in Kubuntu 10.04 x64 - I have sound in Amarok and in Skype, but in FireFox when playing youtube video I hear nothing.

I tried increasing PCM via alsamixer. It does not help. Firefox still can't play sound :(

What else could go wrong?

---

### Post by volodymyr on 2010-06-26
OK, I've found the solution: [http://www.shcherbyna.com/?p=866](http://www.shcherbyna.com/?p=866)

---

