---
title: "I think I broke something"
date: 2008-07-20
forum: General Help
---

### Post by M4rotku on 2008-07-20
Hello all,

I was trying several how-to's to try and improve my systems performance and between them, I somehow messed up something to do with the audio and video stuff.  When I try to use Amarok to play music, it freezes and won't even exit and when I try to access a webpage that uses flash, Firefox dies and quits.

There are several different things that may've caused this problem.  The main thing that I think caused it was trying to upgrade alsa to the newest version in order to get my microphone working.  The mic still doesn't work.  I followed the instructions on the 4th post of this thread:

[Alsa upgrade thread]("http://ubuntuforums.org/showthread.php?t=475013")

Is there anyway to reverse this upgrade and revert back to the old version of alsa?



Other things that may've caused this problem:
[LIST]
[*]Installing and then removing NoScript
[*]Trying to fix my sound using this [link]("http://ubuntuforums.org/showthread.php?t=789578")
[*]Undervolting my laptop with this [link]("http://ubuntuforums.org/showthread.php?t=786402")
[*]Trying to install and configure conky with this [link]("http://ubuntuforums.org/showthread.php?t=205865")
[/LIST]



Chances are that the problem was caused by the alsa upgrade, but I wanted to include everything I'd been up to during this period of time just to be sure.

Can anyone help me get things back to normal?

Much thanks,
M4rotku

---

### Post by M4rotku on 2008-07-20
bump

---

### Post by M4rotku on 2008-07-21
I was driving down the road and hit a BUMP!

---

### Post by steveneddy on 2008-07-21
I suggest you backup and reinstall.

It will save you hours of frustration and you can just start over.

Sometimes it is hard to go back and a total reinstall only takes 30-45 minutes plus the extra time to reinstall of the software you had on there before.

The few times I have had to do that over the last few years saves me my sanity. 

There are others may not agree with the last statement.

---

### Post by rogier.de.groot on 2008-07-21
ALSA? I though Hardy was supposed to use PulseAudio? What version are you using anyway?

---

### Post by M4rotku on 2008-07-21
I'm using Hardy and I"m pretty sure it's supposed to use PulseAudio.  This could be why the stuff I did with alsa messed things up in the first place.  Is there any way that I can go back to using PulseAudio and get rid of the alsa upgrade?

@ Steve:  I have backed up my system before, just not recently at all.  I need to do it more often.

---

### Post by M4rotku on 2008-07-22
bump

---

### Post by M4rotku on 2008-07-23
More info:

My virtual machines on VirtualBox do not work.

The reason Firefox was crashing is because one of my default tabs contained flash content which seems to crash things as well as sound.

---

### Post by jtniehof on 2008-07-23
> **M4rotku said:**
> 
Undervolting my laptop with this [link]("http://ubuntuforums.org/showthread.php?t=786402")
Did you go back to the original voltage? Undervolting can cause system flakiness like this.

---

### Post by M4rotku on 2008-07-23
I have tried things at the original voltage too.  I don't think it's the undervolting that caused the problem.  I think it's the first thing I listed with the alsa thingy.  But I'll try again just to be sure.

---

### Post by M4rotku on 2008-07-23
Ok, the undervolting did not cause the problem.  The laptop is running at it's default voltage right now and the problems remain.

Also:  When I try to view a video (.avi), Totem tells me that the audio device is busy and asks if another application is using it.

---

### Post by jtniehof on 2008-07-23
> **rogier.de.groot said:**
> ALSA? I though Hardy was supposed to use PulseAudio? What version are you using anyway?
PulseAudio is an audio management daemon...ALSA is still the architecture for the drivers.

M4rotku: if you want to try reverting to the ALSA drivers that came with the system, fire up synaptic, search for name including "alsa", and "Mark for reinstallation" anything that's marked as installed (green square). Do the same for any of the following that are marked as installed: linux-sound-base, any linux-restricted-modules packages, any linux-ubuntu-modules packages, any linux-image packages, and any linux-headers packages. Then click on "apply." This is *not* guaranteed to work, but should replace most bits that the ALSA driver upgrade stepped on.

A backup/reinstall, however, may indeed be the way to go. You don't have to wipe out /home...you can keep all your documents, the backup is Just In Case.

---

### Post by M4rotku on 2008-07-23
Rejoice!!!:popcorn:

It worked, thank you so much!

---

### Post by carl_pr on 2008-07-24
i had this issues, i used a guide that is around the forums on how to solve pulseaudio issues. It worked fine now i dont have any problems or random crash like that. Is all running nice.

---

