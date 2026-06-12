---
title: "Thinkpad T61/Intel 965GM slow 2D performance: desktop switching and window redraws"
date: 2008-08-27
forum: Hardware
---

### Post by proxc on 2008-08-27
I'm experiencing somewhat slow virtual desktop switches and general window redraws on a newly-installed Thinkpad T61 (Intel 965GM graphics chipset) under Kubuntu 8.04 x86_64.  Before I file a bug report (probably with upstream xorg), I wanted to see what others have experienced, since this is a common laptop.

Basically, I'm used to switching between virtual desktops quite often and quickly (using keyboard shortcuts).  On a less-powerful laptop with the Intel 945 chipset and i810 driver, the desktop switches happen more quickly than on my T61.  On the T61, I can briefly (less than 1 second) see web pages with lots of text or graphics swipe top to bottom when switching to that desktop.  The difference isn't huge, but it's noticeable enough that I'd like to see what I can do about it.

I've spent some time looking at bug reports (like [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/252094")).  The problems they have seem to be more severe - scrolling is extremely slow and unusable under EXA on some setups, for example.  I'm not using compiz, and my problem persists whether I'm using dual screens or just the laptop's native 1440x900.

I've tried just about everything I could find, including setting
```
Option "AccelMethod" "XAA"
```to revert to the older acceleration method and
```
        Option "AccelMethod" "exa"
        Option "MigrationHeuristic" "greedy"
        Option "ExaNoComposite" "false"
```to try to get EXA to have good 2D performance.  I also tried upgrading from xserver-xorg-video-intel 2.2.1 (default in Hardy) to 2.4.0 (from a user-contributed deb).  The 2.4.0 performance under EXA is actually worse.  I've also tried booting from both the 8.04 x86_64 and i386 live CDs to ensure that it's not some configuration mistake on my part.

Running a 2D benchmark (x11perf --aa10text) I get about 200,000 glyphs/second with each of the two settings above (a little more for XAA).  glxgears are very similar at about 1100 fps (though I realize this is not a benchmarking utility).  Strangely, this glyph performance is actually about twice as fast as that on my older 945 chipset laptop.

So my questions are:
1.) Has anybody noticed the performance of virtual desktop switching with 8.04 and an Intel 965 chipset (intel driver)?  Like I said, this isn't such a huge slowdown that it would drive most people crazy, but it's fairly easy to tell if you've got two laptops right next to each other.
2.) Is anyone familiar enough with x11perf to have a good idea of which benchmarks I should be running?  I used --aa10text from [http://cworth.org/tag/exa/]("http://cworth.org/tag/exa/"), from a developer who works on 2D performance of EXA acceleration on the intel driver.  I'd like to have some quantitative result if I'm to file a bug with the upstream developers, not just a general notion that things are faster under an older chipset with the i810 driver.

Thanks for any suggestions.

---

### Post by sparks13 on 2008-08-28
I haven't had any problems for quite a while. That being said, when I first put Ubuntu on my laptop about a year ago, I remember having some issues with trying to switch between the different desktops/workspaces. I initially started on Gutsy alpha tribe 5, but I remember the problem persisting until I got that whole compiz cube thing working. Once I had all the special effect type things working, I didn't have a problem. That being said, I'm guessing it's something different handling the workspace switching by that point. However, right now (I just noticed this now), it seems I turned it off somehow in the last couple of days. Anyways, it still seems to be switching just fine for me. I will say, when I had problems, they were bad. They were bad enough that it really just wasn't usable. I'm talking at least 2 seconds minimum to change. I'd rather just find the window I want out of the 15 open on a single desktop than spend 2+ seconds trying to change workspaces. Hope this helps. Send me a private message if you want more info from me.

---

### Post by proxc on 2008-08-29
The redraw issue I see is more than just virtual desktop switching, though it is most visible there.

More digging reveals that I am affected by this bug:
[https://bugs.launchpad.net/linux/+bug/210780/](https://bugs.launchpad.net/linux/+bug/210780/) since I have 4GB of RAM in this system.  There are scripts out there which appear to help, but I haven't found one specific to the T61 (one for the X61 appears to at least get rid of the error and improve performance slightly).

Aside from that, forcing speedstep off (by making the CPU policy "performance") yields the performance I'm used to on other systems.  My old Intel 945GM chipset laptop with a slower (Intel Core) processor has the same slowest speed - 800 Mhz, yet it does not need to be forced into a higher performance mode to work well, as I noted above.  I'm not sure whether forcing the processor speed up is masking another underlying issue or whether speedstep itself doesn't work as well with my T61 processor (2.4 Ghz Intel Core 2 Duo).

The good news is that I think this is fixed at the kernel level in the upcoming 2.6.27 release (which will be in Intrepid).  I'll try the Alpha5 liveCD when it's released to see if it really is fixed.

---

