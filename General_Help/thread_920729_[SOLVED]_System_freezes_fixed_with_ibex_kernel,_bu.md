---
title: "[SOLVED] System freezes fixed with ibex kernel, but new problems (sound, shutdown...)"
date: 2008-09-15
forum: General Help
---

### Post by shane19174 on 2008-09-15
I was having total system freezes, requiring me to do hard resets under Hardy 2.6.24-19, simultaneous with network traffic (over my wireless USB stick), so I updated first to 2.6.24-21. I thought it might be Nvidia-related, but no graphics drivers made a difference (repositories, Nvidia website, even beta drivers). The kernel update also made no difference. One day the problem stopped, but a few weeks later it started again. The only thing that had happened shortly beforehand was a virtualbox (PUEL) update. Unable to solve the problem, I restored a backup of my system (made with Acronis True Image in the period when my system wasn't freezing up), and the problem was fixed, even after doing the vbox update. So I thought it must not be vbox, but I didn't know what was to blame.

Anyway, the problem started again the other day, right after vbox 2.02 came out. Again, I don't know if there's any connection. Purging vbox and reinstalling didn't help any. Desparate, I installed the Ibex kernel and kernel headers (2.6.27-3), and what do you know? No more freezes!

But...

New problems have appeared: Sound is all messed up. When the logon screen appears, the familiar drum sound (question.wav) is missing. No big deal, once logged in, all system sounds are there. But if I start up a game, e.g. Supertux kart, the sound can just barely be heard coming not from my speakers but from the internal speaker that usually just emits the "system beep" (for example. when BIOS starts loading).

Moreover, my Belkin Wireless G USB Network Adapter, which had worked out of the box, no longer functions under the new kernel. I had bought this stick because my Rtl8187B was notoriously unsupported by Ubuntu. But now the Rtl8187B works fine! WTF?

Finally, shutdown and restart don't work reliably. That is, they work, but I often see a lot of text on the screen instead of the pretty Ubuntu bar indicating progress.

I have a sneaking suspicion that these problems might be more than coincidentally related. The sound problem announces itself in the GDM logon screen, and GDM is responsible for the smooth shutdown process, right? And sometimes I see errors concerning Network Manager in that text.

Probably I need to add some other packages from the Ibex repository, but which ones? Doing a full upgrade is not possible right now. I tried it briefly but it broke too much of my system. (I then restored from an Acronis backup, so there's no trace of that causing my problems). And going back to Hardy's kernel gives me the system freezes that make Ubuntu virtually unusable.

Sorry about the long post, but I wanted to give as much background as possible to enable a diagnosis.

Does anyone have any ideas?

A few more specs: AMD 5000+, running 32-bit Hardy, 2 GB RAM.

Thanks in advance,
Shane

---

### Post by shane19174 on 2008-09-16
Update:

For some reason the shutdown/restart problem seems to have fixed itself. I don't know why... Or maybe it only happens if I try to use my Belkin wireless stick. I'll have to check... (But right now I'm happy to use the Rtl8187B)

As for sound, I've found that the drum roll at the login screen is not completely missing but, like supertuxkart and other programs, faintly sounding through the PC's internal speaker, which I have found has been defined as the OSS sound device. I think fixing Pukseaudio will be the answer, and the how-to (thanks to psyke83) is either here ([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)) or here ([http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)). But which one? The first is for Hardy (which I'm running), while the second is for Ibex (whose kernel I have)? Or do I need to combine aspects of each?

Any help is appreciated,
Shane

---

### Post by shane19174 on 2008-09-17
OK, I tried the instructions for repairing Pulseaudio in Ibex, and it didn't work: too many unmet dependencies and broken packages for it to work under a Hardy installation, with or without Ibex kernel.

So I rolled back (restored again from an Acronis image) and tried the Hardy instructions. At first, this seemed to solve the problem. I tried the programs that I had noticed were missing sound, and it was back. But then I noticed other programs missing sound (e.g. Gridwars 2), and on the next reboot the computer was again playing selected sounds through the PC speaker (again starting with the login screen drum roll).

Can anyone please help me with this? I'm even willing to try a different kernel; I'd just like for everything to work. It did in the past, and I got used to Ubuntu. I don't want to go back to Vista... Please help if you can,

Shane

---

### Post by shane19174 on 2008-09-17
One last followup: Everything is fixed!

1. System freezes disappeared with the installation of the Ibex kernel.

2. Most audio problems were resolved by following psyke83's "HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)"
([http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)).

3. The rest was fixed with the help of markbuntu's equally impressive "Multiple Sound Solution (ALSA w Pulseaudio)" ([http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)).

I hope this helps someone else.

Shane

---

### Post by Trebaruna on 2008-09-17
Great that your problems are fixed! However, intrepid is still in alpha. This means that your system may well break again, or intrepid may leave dirty dishes in the sink. If you have problems, please see if there's a bug report filed, and otherwise consider filing it yourself: this way developers have a chance to fix your problems and you won't have to jump through hoops to get your system working come October when 8.10 launches.

Also, please realize that because intrepid is still in alpha, support cannot really be given. Please try launchpad instead.

---

### Post by shane19174 on 2008-09-17
Trebaruna,

Thanks for the reply. Please note, though, that I am not running 8.10. Instead, my initial problems (random and total system freezes, usually coinciding with network traffic, even just loading web pages) were with a standard Hardy installation. There are lots of threads here dealing with such freezes in 8.04. My solution (my desparate attempt at a solution) was to install the Ibex kernel in Hardy, but without changing the rest of the system to 8.10. So this really is still a Hardy issue.

Shane

---

