---
title: "Jaunty, Xorg and ATI-hell..."
date: 2009-05-06
forum: Hardware
---

### Post by odinb on 2009-05-06
Any Xorg experts out there?

I have been fighting this issue ever since I upgraded to Jaunty from intrepid...

I have a Laptop (HP/Compaq NW8440) wit an ATI card (Radeon Mobility X1600), and it seems I have discovered what a bunch of other people has as well, ATI are flipping the bird on us with a GPU older than 2-3 years!!

When at the office I use this machine with 2 external 20 inch monitors (HP LP2065), and used to use ATI BigDesk with Intrepid. Worked beautifully with the proprietary drivers!

Now with Jaunty and when ATI no longer deems me worthy of running this "old" GPU, I am left to the open source drivers. Desktop effects work, but have been unable to get a big desktop again...

xrandr reports the following for my monitors:
[http://pastebin.com/f13d9a52a](http://pastebin.com/f13d9a52a)

xorg.conf looks like this:
[http://pastebin.com/f41f53f9a](http://pastebin.com/f41f53f9a)

xorg.0.log looks like this:
[http://pastebin.com/f6dcd49d0](http://pastebin.com/f6dcd49d0)

Even though I have not defined the laptop LCD in xorg.conf, it seems to be affecting the setup.

When I boot, the machine is 1600x1200 at login screen, and it is not mirrored, the 2 screens differ.

After logging in, I am reduced to 1280x1024 and mirroring.

If I try to use the GUI (under system > preferences) to change resolution, unticking mirroring, and turning laptop LCD off, and then setting resolution to 1600x1200 on the remaining screens, it changes my xorg.conf to 4880x1252 as opposed to the 3200x1200 I put in there, leading to the displays coming up garbled..

Seems even though I do not activate the laptop LCD in xorg, and disable it in the GUI, it still messes up the settings.

I get the feeling it might be gnome that does something here, as the screen is 1600x1200 at login prompt, and not mirrored, but becomes 1280x1024 after logging in, and mirrored.

What am I doing wrong? Is it the internal laptop LCD that haunts me? Can I disable it totally, and if so how? If I can, how do I re-enable it when laptop is undocked?


Thanks for any help!

//Odin

---

### Post by snowboarder13 on 2009-05-06
Have you considered using [EnvyNG]("http://www.albertomilone.com/nvidia_scripts1.html")?  I used the legacy version for multiple monitors on my old desktop (Radeon 9600) in the past and it worked great.  Recently I have upgraded to a single 23" monitor and an HD4670, again flawless installation, giving me full 1920x1200.  I used to spend hours fiddling with my xorg.conf and I no longer need to anymore.  It's not guaranteed to work but it can't hurt to try.  Also, on a side note, I was under the impression that the xorg.conf has been phased out, but I don't know much about this.

---

### Post by odinb on 2009-05-06
As assumed, Envy was not any better than me at finding drivers that does not exist...

[IMG]http://odinb.mypicgallery.com/ubuntu/envyng_large.jpg[/IMG]

It is correct that xorg.conf is mostly not used/needed these days, but for specific setup, I guess you still have to use it.

Thanks for responding, too bad it did not help...

---

### Post by odinb on 2009-05-07
Bump...

..anyone has any ideas, or do I have to roll back to 8.10?:(

---

### Post by polecat409 on 2009-05-09
> **odinb said:**
> Bump...

..anyone has any ideas, or do I have to roll back to 8.10?:(

I'm doing just that right now.  I have a Toshiba A215-S6804 which has an ATI Radeon X1200 Series display adapter.  I love Jaunty, but I can't stand the lack of performance the open source drivers provide.

I actually took out an ATI card from my workstation at work and replaced it with an older Nvidia card just so I could upgrade to 9.04.

---

