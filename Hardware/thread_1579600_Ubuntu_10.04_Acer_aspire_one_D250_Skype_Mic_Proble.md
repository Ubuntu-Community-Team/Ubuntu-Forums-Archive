---
title: "Ubuntu 10.04: Acer aspire one D250: Skype Mic Problem"
date: 2010-09-22
forum: Hardware
---

### Post by hasanarbab on 2010-09-22
Hi,

I'm totally beginner to ubuntu. few months back I tried ubuntu 9.04 which was really great. Had few issues which I solved with the help provided in ubuntu forums. For some reasons I had to retreat to windows xp and now I'm back again to good stuff. This time, I have burnt all ships to go back to windows and have deleted win xp totally. I've installed ubuntu 10.04 as the only os on my netbook.

I've managed to solve everything (I think), except mic is not working in skype 2.1 beta. I don't know, but I think I have tried almost every help available in google search in this regard. I just can't get it work and really, I'm very tired now. 

Please, as I told u before that I have burnt all the ships back to windows, and really I don't want to swim back to windows either. I'll really really appreciate the person as much as I could for whole of my life who'll get me out of this issue successfully. Really, you have no idea of the bitter taste of defeat.

I'm sure, you guys will make me winner.

Thanks in advance.

---

### Post by mastablasta on 2010-09-22
Instructions for 9.04:
[https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250]("https://help.ubuntu.com/community/AspireOneAOD250?action=show&redirect=AspireOne%2FAOD250")
 
 
The mic doens't work only in skype or in general it doesn't work? did you check the ALSA settings for mic volume? did you check the sound preferences? What kind of input/output  is selected there? on my computer the mic works only if i have analog duplex selected.
 
if the mic works but doesn't work in skype it could be a skype issue. check skype preferences for any mic volume.

---

### Post by hasanarbab on 2010-09-22
Hi all,

At last, I have managed to get it work. In 'Ubuntu Software Center', I installed 'Default Sound Card' and 'Pulse Audio Volume Control'

Then I opened 'Pulse Audio Volume Control' from 'Main Menu' -> 'Sound and Video'

In 'Input Devices', I adjusted 'Front Left' to 75% and 'Front Right' to 'Silence'.

I can't say that it worked perfect but it worked fine anyway.

I'll take as [solved] to my problem, but it is just a work around. :P

---

### Post by &#1058;&#1086;&#1084;&#1080;&#1094;&#1072; on 2012-01-14
Sorry for raising this thread from the dead, just wanted to thank hasanarbab for posting the solution. It finally works.

Edit: it doesn't matter which channel you set to 0% volume, it can be either left or right channel. The result is the same.

I have Acer Aspire TimelineX 5830TG and this problem exists only in Skype. All the other suond recording applications, including the System Test, work okay.

Just wondering, does anyone know why this happens? Apparently, that's an Acer-specific problem, but what I don't get is why I have left and right channel for adjusting the input volume in Pulse Audio Settings, when my laptop has only one built-in microphone? Can someone please explain this in details? Thanks.

---

### Post by thenanodude on 2012-02-26
Just letting everybody know that dropping one of the inputs to 0 also worked on my system:  Aspire One ZG5 running Oneiric (11.11)

---

### Post by joao.taborda on 2012-03-21
it did not work for me...still looking for other solution...

---

