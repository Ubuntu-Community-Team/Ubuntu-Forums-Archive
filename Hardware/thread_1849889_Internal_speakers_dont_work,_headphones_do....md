---
title: "Internal speakers dont work, headphones do..."
date: 2011-09-25
forum: Hardware
---

### Post by sinncier on 2011-09-25
I installed Ubuntu 10.04 dual booted with Windows 7 on my Lenovo laptop. In windows 7 sound plays fine from speakers and headphones. But in Ubuntu sound only plays through the headphones, not the speakers. I researched and have been troubleshooting with no luck of getting the internal speakers to play. Sound card is recognized, adjusted levels in alsamixer, drivers seem to be loaded, modules, everything. One thing though my headphone jack port is damaged internally. I have to move the wire around and jimmy rig it to get the sound to play. I'm almost positive this is contributing to the problem but if it works in Windows fine then it must be software/configuration related issue. 

Any thoughts on a fix?

---

### Post by Iloru on 2011-09-27
I, too, am able to get sound only through headphones.  The built-in speakers on my Acer Aspire 5830TG will not work in Ubuntu.  Like you, I have gone through all of the suggested solutions from editing alsa-base.conf to checking drivers and adjusting settings in alsamixer.  It seems that there is no fix for this as of yet.

One thing I have noticed, on my system at least, is that my speakers work if I first boot up into Windows, then restart my laptop and boot up Ubuntu.  However, if I close the laptop or it sleeps/hibernates for any reason, then the speakers once again stop working.

From what I've been able to find, it seems that this is a bug in the kernel.  I found a few old posts (from somewhere around January, I think?) where it was suggested that downgrading to an older kernel would fix what seems to have been an identical problem.  I haven't tried this as of yet, as I have been quite busy the past few days, but it might be worth a try.  I will post if there is any success with it.

In the meantime, hopefully someone else can offer some suggestions.  I would love to be able to watch tv and listen to music on my laptop again.  :)

---

### Post by Iloru on 2011-09-27
Ok, possibly some good news.  Some more-targeted searches and a great deal of tinkering later, I finally have sound!  I ran across this link:  [http://ubuntuforums.org/showthread.php?t=1790404&highlight=5830TG]("http://ubuntuforums.org/showthread.php?t=1790404&highlight=5830TG")

Post #5 has a quoted bit with a link to an HDA Analyzer and instructions on which part to enable.  My onboard sound is Intel HDA, so this was relevant in my particular case.  I'm not sure what sound card you have in your HP, but perhaps this will work for you, as well.

---

