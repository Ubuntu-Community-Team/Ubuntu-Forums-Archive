---
title: "fried nvidia GPU"
date: 2010-06-12
forum: Hardware
---

### Post by Mauri72 on 2010-06-12
Hi all, I am in a spot of trouble right now.
Yesterday the Nvidia (I think 8400m gt) on my Vaio laptop started playing up, overheating and the starting to work again once it cooled down. I thought it was simply overheating so I hooverd a bit of dust and dog's hair from my laptop vents and it seemed to be working fine for a while. Today however it packed up completely. I get funny vertical lines even on the Vaio boot screen and the card is not working on both Ubuntu and Vista. In Ubuntu I had the chance of using the computer anyway because, failing to find a working nvidia GPU it started the low resolution mode. Great!!! but me being me, I couldn't leave well enough (or bad enough) alone and I uninstalled the nvidia drivers, to check if that would make things better. Well, you may already have guessed it, now I cannot get to the low resolution mode, not even in recovery mode (which complains about nouveau and then hangs).
In your infinite collective wisdom, are you aware of any way I could reinstall the nvidia drivers and get access to the laptop at least in low res mode? Not easy simply by looking at a completely black screen. :lolflag:

---

### Post by dino99 on 2010-06-12
boot with video=vesa on the grub boot line (e)

right click on top panel and install icons for temperatures, be sure fans are working, and remove overclocked settings if any.

then open synaptic and check that: nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings are installed

clean your system: install gconf-cleaner and run it (yes to all)

---

### Post by yossell on 2010-06-12
As far as the chip goes, I'm afraid  this is bad news -

Those vertical lines are the classic symptoms of a known issue with the nvidia 8400 graphic chips. Basically, there appeared to a flaw with the manufacturing process for those chips where, over a period of heating and cooling cycles, flaws in (I think) the chip's solder would appear causing those symptoms. This issue affected a number of notebook makers and nvidia eventually stumped up for repairs.

If the computer is under warranty, you should be able to get it replaced. I had the same issue with my Dell m1330 - and Dell fortunately extended the warranty for a year for those models. I don't know what Sony's policy is but you should check, as this is a well known issue. 

There's one trick that will bring your gpu back to life - but it's temporary and requires  bravery: bake your motherboard. No, really. It works - apparently!  200 degrees for 10 min, they say. Make sure you've removed all plastic from the motherboard. Alternatively, if you have a heat gun, you can heat around the nvidia chip - apparently, the solder melts slightly, and reflows, extending life for a week or two. This will at least give you a chance to change to low graphics model - though I don't know whether that will still work if the graphics chip is broken.

[http://forum.notebookreview.com/dell-xps-studio-xps/454864-xps-m1330-faulty-gpu-options-cost-please-help.html](http://forum.notebookreview.com/dell-xps-studio-xps/454864-xps-m1330-faulty-gpu-options-cost-please-help.html)

has a discussion of this issue for the Dell, and includes a link to a video showing the heating procedure plus there are some other discussions round there for the oven trick.

---

### Post by Mauri72 on 2010-06-13
Thanks for your replies guys. I got the nvidia drivers back on, and, as expected, I can use the computer in low resolution mode. Not great, but enough to keep me going for the time being. 
Is there a way to have the laptop just start in low resolution mode without warning me first?

If I really get fed up with it I may really give the baking option a go. 
Cheers

---

