---
title: "Ubuntu support for high resolution monitors"
date: 2015-03-07
forum: Hardware
---

### Post by andrew_waite2 on 2015-03-07
Hi!

I'm looking at getting an external monitor for my Dell XPS 13 Developer edition (model 9333).

Current favourites are:
[LIST]
[*][http://www1.euro.dell.com/content/products/productdetails.aspx/dell-u3415w-monitor?c=uk&cs=ukdhs1&l=en&s=dhs](http://www1.euro.dell.com/content/products/productdetails.aspx/dell-u3415w-monitor?c=uk&cs=ukdhs1&l=en&s=dhs)
[*][http://www.kitguru.net/peripherals/monitors/zardon/aoc-u3477pqu-34-inch-3440x1440-ips-review/](http://www.kitguru.net/peripherals/monitors/zardon/aoc-u3477pqu-34-inch-3440x1440-ips-review/)
[/LIST]

Both of these have a resolution of 3440x1440.  Can anyone tell me if I'll have any hardware or software issues going that high?

I'm running 14.10 if that makes a difference, and the laptop has one mini display port as an output.

---

### Post by TheFu on 2015-03-07
I had dell laptop in 2005 with 1920x1440 resolution (4:3).  Worked fine.  X/Windows has supported very high resolutions for decades probably thanks to SGI, but I don't know exactly who did the work.  If the video card driver supports the resolution, there shouldn't be any issue. All the other software is ready.

It has Intel® HD 4400 integrated graphics - intel GPUs have been working with Linux more than the others.

I wouldn't worry.

OTOH, $1300 for a laptop seems expensive to me (typing on a $200 chromebook). Most of us can remote into a faster system and don't need to carry that power around any more.  But if I were still a high-end consultant, I wouldn't think twice about spending $2K on a laptop.  BTW, my chromebook can run KVM/virtualbox and the hdmi out drives to a 1920x1200 monitor fine thanks to the Haswell CPU/GPU.

---

### Post by andrew_waite2 on 2015-03-07
Thanks for the info. :)

It probably wasn't clear from my original message, but I already have the XPS 13.  I just want to know if I'll be able to use it to drive 3440 x 1440.  I've heard some of the 4k monitors require DisplayPort dual stream technology which I don't think Ubuntu supports yet without hacks?

I'm pretty lucky as my company buys us high-end hardware of our choosing (and considering almost everyone else opts for Macs, my Dell is actually cheap by comparison!).

---

### Post by tokyobadger on 2015-03-08
> **andrew_waite2 said:**
> Hi!

I'm looking at getting an external monitor for my Dell XPS 13 Developer edition (model 9333).

Current favourites are:
[LIST]
[*][http://www1.euro.dell.com/content/products/productdetails.aspx/dell-u3415w-monitor?c=uk&cs=ukdhs1&l=en&s=dhs](http://www1.euro.dell.com/content/products/productdetails.aspx/dell-u3415w-monitor?c=uk&cs=ukdhs1&l=en&s=dhs) 
[*][http://www.kitguru.net/peripherals/monitors/zardon/aoc-u3477pqu-34-inch-3440x1440-ips-review/](http://www.kitguru.net/peripherals/monitors/zardon/aoc-u3477pqu-34-inch-3440x1440-ips-review/) 
[/LIST]

Both of these have a resolution of 3440x1440.  Can anyone tell me if I'll have any hardware or software issues going that high?

I'm running 14.10 if that makes a difference, and the laptop has one mini display port as an output.
It's not a question of Ubuntu support - what does your IGPU (Intel's integrated GPU) support? Are there drivers for it? Are they in the xorg package for linux?

**edit**: can't find the specs for your laptop online but if you have [Intel HD 550/5600/6100 or 6200 (the latter if you have a time machine)](https://software.intel.com/en-us/articles/quick-reference-guide-to-intel-processor-graphics) then from the hardware perspective you should be fine

---

### Post by andrew_waite2 on 2015-03-13
Thanks for that, my laptop does indeed have Intel integrated graphics.  The processor is a mobile Haswell i7.  I couldn't find which actual model number though?

I've just been able to try a colleague's monitor which has this resolution (3440 x 1440) using a display port connection.  It was detected correctly in the display control panel, but nothing was displayed on the monitor itself.  Lower resolutions worked fine, but at 3440 x 1440 the monitor just wouldn't display anything at all.

---

### Post by andrew_waite2 on 2015-03-13
Update: tried a HDMI cable and that is able to drive the monitor at 3440x1440 @ 30Hz.

As it's only office work I do (programming/web) I think that should be fine?

---

### Post by andrew_waite2 on 2015-03-17
Update 2: I ended up going for a the Dell u3415w, prepared to accept running it over HDMI @30Hz.  When it arrived, I tried it using mini DP to DP cable and to my surprise, it worked perfectly at native res @ 60Hz.

I have no idea why, but as above my colleague's AOC u3477pqu did not work at the same resolution with my Ubuntu laptop over display port.  I have no idea why that might be (could be ubuntu, my laptop's hardware, a fault with the monitor or cable, perhaps?).

I hope that helps any Ubuntu users that are considering a 34" ultra-wide panel - it may be best to steer clear of the AOC.

---

### Post by daniel-schwiperich on 2015-10-21
I only got this working with my X1 Carbon after disabling DP 1.2 in the monitor menu. 
And only with the internal Mini DP, not with the Docking Station.

---

### Post by Bucky Ball on 2015-10-21
Off-topic: 14.10 reached end-of-life sometime ago and is no longer supported. You should upgrade to a newer, supported release as you currently have no updates/upgrades, including security so not good online machine.

Just throwing that in. Good luck. :)

---

