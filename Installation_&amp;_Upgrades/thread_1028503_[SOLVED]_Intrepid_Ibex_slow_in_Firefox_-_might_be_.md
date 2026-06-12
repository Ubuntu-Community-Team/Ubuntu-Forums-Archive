---
title: "[SOLVED] Intrepid Ibex slow in Firefox - might be caused by Flash"
date: 2009-01-02
forum: Installation &amp; Upgrades
---

### Post by leffect on 2009-01-02
I think this is probably the right place to post...

I have just done a fresh install of Intrepid Ibex in order to fix some problems I was having before, however it hasn't worked. When in normal use (Firefox, XChat, Psi), the computer regularly slows to a crawl, and starts greying out Firefox and Psi. The programs do eventually start working again (typically 30 seconds or so later), but as soon as I try to do anything with them, the grey out again. This means that it's very very slow to do anything, making the computer more or less useless.

The interesting part is that when I first installed it, I wasn't having any of these problems, the computer was running fine. Since then, I've installed all the available updates (apt-get update && apt-get upgrade) and also installed the software I want for general use 
```
sudo apt-get install mplayer ssh psi synergy imagemagick amsn portmap vlc inkscape scribus xchat flashplugin-nonfree galeon compizconfig-settings-manager msttcorefonts randomize-lines awn-applets-* awn-manager unrar recordmydesktop camorama aircrack-ng kismet
```
plus virtualbox and the W32codecs from the Medibuntu repository.

That's about it. I do have a number of extensions installed in Firefox, but they were all fine under Hardy (and Mint Elyssa), so I think they should be OK!

There have been a couple of other problems I'll mention as well, just in case they're related and give any clues! Firstly, every so often when I boot (roughly 50% of the time) X won't start properly, and I get what I assume is Bullet Proof X saying it hasn't started and offering to rebuild my config file. The first few times this happened, I eventually managed to get X to start, through some combination of using the rebuild wizard and rebooting (I'm not sure exactly what I did - I just kept trying things until it worked), but the last time, I made a backup of my xorg.conf just before I rebooted, then when it failed to come up I copied the backup over the current one, pressed ctrl+alt+bksp to restart X. It got stuck at the terminal view, so I did a startx from tty1, and it came up as usual.

The second problem is a minor one, but it's still annoying. I've set the keyboard shortcut to open a terminal in system/preferences/keyboard shortcuts to be ctrl+alt+T, however when I press this, nothing happens. I set home folder to be ctrl+alt+H at the same time, and this works as it should.

If anyone can shed any light on these problems (especially the first one!) I would be most appreciative!

Thanks!

---

### Post by leffect on 2009-01-02
Oh, and as an additional point, I've just tried removing Flash (apt-get remove --purge flash-plugin-nonfree) and then rebooted. I think the computer's now running slightly better, but it's hard to tell. It's still having essentially the same problems.

---

### Post by sendblink23 on 2009-01-02
> **leffect said:**
> Oh, and as an additional point, I've just tried removing Flash (apt-get remove --purge flash-plugin-nonfree) and then rebooted. I think the computer's now running slightly better, but it's hard to tell. It's still having essentially the same problems.

As for me I haven't had a problem as in a Fresh Install of Ubuntu 8.10

I have installed all the programs you have, on your Sudo get

But I installed them through normal *Applications *Add/Remove *All Available Applications

And its all being perfectly really Fast .. being a 4 year old computer

As for the *Commands for the Keyboard I have no clue there.. never tried them.

---

### Post by Dauron on 2009-01-04
I've just solved problem with slow flash in ubuntu (30% CPU used by Xorg).
You have to remove libswfdec* package (which causes slowdowns) and instead use the flashplugin-nonfree.
:D

---

### Post by leffect on 2009-01-08
I've solved the problem! Turns out it wasn't related to Flash or networking at all!

It was caused by a bad connection in my power supply, which I presume was either causing the power to cut in and out rapidly, or to be a lower voltage than was expected, confusing the ACPI manager. This presumably was creating lots of interrupts to switch between battery and mains mode and thereby slowing the system down.

So, now I've fixed the power supply, all is well again! I thought I should just post here in case someone else ever has the same problem.

---

