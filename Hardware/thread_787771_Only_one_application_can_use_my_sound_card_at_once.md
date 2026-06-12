---
title: "Only one application can use my sound card at once"
date: 2008-05-09
forum: Hardware
---

### Post by hallgeirl on 2008-05-09
Hi!
This is a problem that appeared after Ubuntu 8.04. In 7.10 everything worked perfectly. Here's the problem:
If I open, let's say, Rhythmbox, and starts playing some song, and then open some application that also use the sound card, the second application is unable to play any sounds. I find this very strange. Also, even stranger, is that for instance Totem and Rhythmbox can use the sound simultaneously, but every other combination of applications failed to do that. Here's what I've tried so far:
- Changed the Sound playback in System->Preferences->Sound to both Autodetect, Alsa, OSS, and PulseAudio, plus changing the mixer to every possible device there was.
- Installing Alsa-oss (I tried searching, and that was one suggested solution that didn't work). 
- Changing the playback device in the applications that supports that to something else than the Sound playback settings in Preferences->Sound.

My soundcard is a built-in realtek AC'97 on my A8N32 Deluxe motherboard. I also had these problems while running the 8.04 beta, and it persisted after I formatted and reinstalled when the retail arrived.

I'm pretty much out of ideas...
Any suggestions to fixes, or any tips is very much appreciated. :) Also, what logs can I check out to get an idea of what's failing? I'm pretty new to troubleshooting stuff like this in Linux, so I'm not sure where to look. :)

Kind regards, 
Hallgeir

---

### Post by mindracer on 2008-05-09
I had the same problem yesterday, just installed 8.04 (ive been using mostly windows lately), and I was playing Rythmbox yesterday on low volume then decided to make a Skype call, when skype said there is a audio problem.  I thought my Skype wasnt working until I closed Rythmbox, then Skype worked fine.

So is it Rythmbox or a bug?

---

### Post by hallgeirl on 2008-05-09
> **mindracer said:**
> I had the same problem yesterday, just installed 8.04 (ive been using mostly windows lately), and I was playing Rythmbox yesterday on low volume then decided to make a Skype call, when skype said there is a audio problem.  I thought my Skype wasnt working until I closed Rythmbox, then Skype worked fine.

So is it Rythmbox or a bug?

Hi. It's not a Rhythmbox bug - I have the same problem whatever application I use. If I for instance play something in Totem, sound is disabled for every other application. This is weird. Even weirder is that Rhythmbox and Totem can play sounds simultaneously, but no other combination of applications (that I've found at least.

---

### Post by nahtura on 2009-04-27
I have the same problem, Any help on this would be much appreciated!

I have spent quite a bit of time trawling through forums trying to find an answer to no avail.

Surely there is something i have missed!

---

### Post by hallgeirl on 2009-04-27
> **nahtura said:**
> I have the same problem, Any help on this would be much appreciated!

I have spent quite a bit of time trawling through forums trying to find an answer to no avail.

Surely there is something i have missed!

Hi,
I only had this problem in 8.04. 8.10 and higher was working fine for me. I did find a solution though, and that was to uninstall PulseAudio completely and switch to using ALSA.

Hope this helps.

-Hallgeir

---

### Post by mousethief on 2011-01-16
I uninstalled PulseAudio but it still has the problem. 

Have you ever noticed on these forums if your problem isn't a simple one, the line goes dead? Lots of people have the obvious answer but if the obvious answer doesn't fit, you're on your own.

---

