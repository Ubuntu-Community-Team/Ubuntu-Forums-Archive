---
title: "Asus Xonar DX"
date: 2008-05-03
forum: Hardware
---

### Post by symbiont on 2008-05-03
Just bought this card a few days ago.  Anyone have any luck gettin one running in Ubuntu?  and if so how? I'm sortof noobie  :)

---

### Post by YogiPaolo on 2008-05-28
I have had zero luck getting this card to work. I've tried every step in the comprehensive guide (twice) and a from-scratch install. No dice. 

This is strange, considering ALSA reports the card fully functional...

I am considering dual booting with another distro to see if things work...

---

### Post by IceDigger on 2008-05-30
I have this card also and can't get it to work on 8 64bit version.  Forced to use onboard sound which sucks hardcore.

---

### Post by in0v8 on 2008-05-30
Have tried loads of different ways to deal with this card.  It will work under 32 bit, but not on my 64 bit install!  Card appears with lspci -v, but not aplay -l after full compile and install using latest ALSA drivers, including the pre-release driver by Clemens Ladisch.  alsaconf detects it and claims configuration but afterwards alsamixer can't find it.

Have also tried the OSS route on 64 bit.  This installs, identifies the sound chip but will not allow sound output.  ossinfo says it's there, ossxmix will allow adjustment of volume levels, osstest appears to do just that - but still no output!

The 32 bit install creates a file /etc/asound.state with details of the card - this hasn't yet happened on my 64 bit efforts.  

Suggestions would be welcome!

---

### Post by YogiPaolo on 2008-05-30
I have seen reports on this forum that people have used the xonar D1/2/U2 cards with no problems out of the box. There must be some electronic difference between the DX and other cards....

I have had very weird results installing alsa from source.

alsaconf will detect the card and say that it is configuring. It will complete with no complaints, then when I re-initialize the sound system using /etc/init.d/asound restart, the system complains that there is no card.

Also, asoundconf will not detect the card.

This might be a problem with using the "pure" alsa driver vs the ubuntufied alsa system.

I'm not finding any clear description of how the sound system works and the differences between the ubuntu implementation and the way alsa is set up. I'll have to do more reading.

---

### Post by in0v8 on 2008-05-31
Are you on 32 or 64 bit, YogiPaolo?  I have the card working on 32 bit Gutsy but no go on 64 bit Hardy.  You are right that there are differences between the cards you mention: nobody appears to report difficulties with the D2, which is a PCI card.  

The DX has an extra chip to overcome the fact that the soundchip itself isn't PCIe compatible: 'The Xonar's Oxygen HD audio chip wasn't designed for PCI Express, so Asus uses a bridge chip from PLX to adapt it to the PCIe interface' (from the review here: [http://techreport.com/articles.x/14500](http://techreport.com/articles.x/14500)).  This chip is identified with lspci -v, where it is reported as 'PCI bridge: PLX technology' on both my 32 and 64 bit installs.

Thing is, the card works on 32 bit Gutsy, using the pre-release driver from the ALSA project website: [http://www.alsa-project.org/~clemens/alsa-driver-20080415.tar.bz2](http://www.alsa-project.org/~clemens/alsa-driver-20080415.tar.bz2) - so is this a Hardy problem?

---

### Post by YogiPaolo on 2008-06-01
That is a great deal of help. Thank you so much! I love excellent clues like that.

I am running 64 bit Hardy. Here is the output of lspci -v 

```

02:00.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=02, secondary=03, subordinate=03, sec-latency=32
	I/O behind bridge: 00009000-00009fff
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [60] Express PCI/PCI-X Bridge IRQ 0

03:04.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
	Subsystem: ASUSTeK Computer Inc. Unknown device 8275
	Flags: bus master, medium devsel, latency 2, IRQ 11
	I/O ports at 9c00 [size=256]
	Capabilities: [c0] Power Management version 2

```

I'm not sure how one might answer the question about where the problem is. I guess the critical question is: what is the difference (if any) between 32 bit and 64 bit drivers in this case? Would this be a problem with the kernel identifying and working with the bridge or the alsa driver?

I have checked launchpad (keyword xonar) and have found no specific reference to the bridge. Do you think it would help to file a report in launchpad? I've never done that. Is it a bug?

I'm about to return the card to newegg or sell it on craigslist if they won't take it back....

---

### Post by in0v8 on 2008-06-02
So, next effort: reinstall 64 bit Hardy, cleanly from CD. modprobe soundcore is now fine. Recompile Alsa from source, including the most recent snapshot. All source compiles without error and installs likewise. alsamixer, however, returns:

ALSA lib control.c:874:(snd_ctl_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_ctl_pulse.so

alsamixer: function snd_ctl_open failed for default: No such file or directory

This despite reinstalling libasound2 (purge reinstall). The directory /alsa-lib/, not surprisingly, does not contain the libasound module.

lspci still finds the card, so does alsaconf, but not aplay -- in other words, Ubuntu knows the card is there, has the drivers available to run it, but for some reason, cannot connect the two.

I have filed a bug on launchpad: #234804... would really like to solve this one - the sound under 32 bit Gutsy is great, better to my ears than the X-Fi I was using before!

---

### Post by YogiPaolo on 2008-06-03
Once again, thanks in0v8.

I'd really love to see this one solved too. I'll be checking launchpad...

---

### Post by in0v8 on 2008-06-10
As the card will work on 32 bit Gutsy, I wondered whether there might be some 32bit/64bit issue, so yesterday, as a long shot, tried installing the ia32-libs, together with a purge of all previous alsa and a fresh compile and install of the 1.0.17rc1 ALSA.  Still no go.

I've also tried OSS4.0, which detects the soundchip and agrees to test the card, only there is no output at all from the speakers (and, yes, I've raised all the volume levels in ossxmix).

I'm more and more convinced that this is an issue with the PLX Technology PCI Express-to-PCI Bridge which allows the Oxygen audio chip to communicate over PCIe.  The result of hours of Googling on this topic is that those people who have successfully installed Xonar soundcards on 64-bit Linux systems have been using the D2, which is a PCI card.  So far I haven't turned up a successful 64-bit install of either the DX or the D2X (the PCIe equivalent of the D2).  Of course, I'd be glad to hear otherwise, with a guide to succeeding!

---

### Post by gmjs on 2008-10-23
If it's any help (probably not!) I;m trying to get this card to run under Ubuntu 8.04 32-bit and am having exactly the same problems.

I've tried alsa-1.0.18r3 as suggested on their site.  The drivers compile and install, lspci can find the card, but /proc/asound/modules only ever lists the onboard sound (which I have switched off in the BIOS as I dual boot with Windows - and the card works in that of course ;)!

This would suggest that it's not a 64-bit issue.

I'm very interested if someone can get this to work.  I'm clean out of ideas!

Thanks.

---

### Post by SaddaGocaraRupa on 2009-01-07
I built a new rig in July and installed Intrepid via Wubi in Vista Ultimate and while there are now proper drivers for it it works very well with the supplied alsa ones. When I select the digital Asus Virtuoso drivers, i get nothing at all, with the analog ones I get a weird crackling noise whenever I pla anything but very smooth sound afterwards, but I basically just have everything set to Autodetect and it works a charm :)

---

### Post by Francewhoa on 2009-05-22
If your Asus Xonar DX sound card isn't automatically detected by Ubuntu 8.04.2 Desktop 32bits the below installation script is the **easiest way that I know of** to install & configure any sound card. It's a script made by *soundcheck*. It does all the hard manual setup process for you. ** [Click here to open the post]("http://ubuntuforums.org/showthread.php?t=1167232&highlight=xonar"), then find the latest installation script attached at the bottom. **Current installation script is title *AlsaUpgrade-1.0.x-rev-1.17.tar*.


If the script works for you please add your results here:

[LIST]
[*][https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards](https://wiki.ubuntu.com/HardwareSupportComponentsSoundCards)
[*][http://www.ubuntuhcl.org/browse/search+sound-cards?category=27](http://www.ubuntuhcl.org/browse/search+sound-cards?category=27)
[/LIST]

---

