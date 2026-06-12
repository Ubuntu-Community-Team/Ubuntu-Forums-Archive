---
title: "Gutsy: Toshiba A105-S2071 hda-intel; no sound; no soundcard found"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by vagranted on 2008-01-22
So I'm brand new to Ubuntu. When I first installed it, I had three major issues: my ati xpress 200m video card, my atheros wireless card, and my hda-intel sound card. Well, the first two have been fixed, but the sound card is giving me plenty of trouble.

At first, doing the aplay -l command gave me my soundcard, the hda-intel (a861 I believe). The alsamixer was fine, but sound still would not come out. So I tried all the things I could find on the forums and online. After my last attempt, I found out that my sound card cannot be detected.

I've tried the steps on the troubleshooting guide on the Ubuntu Help, so I'm looking for someone to at least help me get my sound card to be detected again. (And maybe for the sound to work too!) Since I'm pretty new to this and I'm still getting used to Terminal, I apologize and thank anyone who helps in advance.
-Danielle

---

### Post by linuxwizard on 2008-01-22
Check this see if your computer is affected by bug reported
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

Or try this
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by vagranted on 2008-01-22
My card doesn't fit under that bug. (it's a 1002:437b PCI id)
As for the second link, that's the steps that I was following last night. I went through the whole thing without errors, and that's when I noticed that my sound card was not being detected.

I just had to reboot for a different reason, and now my sound card is showing up, and when I click on the volume control button I do not receive an error.

However, trying the steps over on the hda-intel-howto page doesn't help fix the problem.
-Danielle

---

