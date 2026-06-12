---
title: "Horrid video performance on laptop with integrated Via graphics"
date: 2009-12-05
forum: Hardware
---

### Post by Syntax42 on 2009-12-05
I was tired of using Windows XP on a laptop I only use for web browsing and travel.  It was performing a bit sluggishly, probably from having a cluttered registry. After seeing how well Ubuntu performed on my dad's 486 computer, I decided to give it a try.

One of the things I use the laptop for is watching streaming TV shows I've missed.  Fox.com doesn't support Linux yet, so I went to Hulu.com to watch Fringe.  Unfortunately, the video playback is choppy and has tearing issues in normal viewing mode.  In full screen, the frame rate is so bad I can't even bear it.

The other application I want to run well is 3d Java games, specifically Runescape.  Even on the lowest detail settings and resolution size, the game is choppy.  It is nearly unplayable when I increase the size of the 3d rendering area through the game's options.

In both situations, Windows had smooth frame rates.  After reading the forums for a few hours on relevant topics, I am suspecting the reason for my performance problems is the openchrome graphics driver not being as good as whatever Windows used.  Here is some hardware information if it helps:

```
syntax42@syntax42-laptop:~$ sudo lshw -class video
[sudo] password for syntax42: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 bus_master cap_list
       configuration: latency=64 mingnt=2
       resources: memory:f4000000-f7ffffff(prefetchable) memory:fd000000-fdffffff memory:fe2f0000-fe2fffff(prefetchable)

```Is there a video driver that would run my aforementioned applications better?  Am I out of luck with Linux?  Should I just wait a year or more for someone to make a better driver?

---

