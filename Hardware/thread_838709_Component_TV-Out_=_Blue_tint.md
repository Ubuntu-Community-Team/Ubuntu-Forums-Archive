---
title: "Component TV-Out = Blue tint"
date: 2008-06-23
forum: Hardware
---

### Post by cyberb0b on 2008-06-23
I'm using the ATI fglrx driver, ubuntu 8.04, mythtv, component tv-out on my new GA-MA69GM-S2H motherboard.  When I turn on the computer the tv-out correctly displays colors on the post screen, before grub starts and it boots up.

When X starts the colors on my monitor look fine, but the component tv-out looks to be blue and white.  See pic.

I've gone thru a lot of options in the "Device" section of my xorg.conf file but nothing fixes the problem.  I tried some options from [this]("http://www.kvaes.be/mythtv/the-unofficial-guide-to-getting-your-tv-out-working-on-an-ati-x1250/") page.

I'm not even sure what to call the problem.  I read some places it might be RGB vs YPrPb setting, but how do I change that?

---

### Post by cyberb0b on 2008-07-05
A little more investigation reveals that plugging the blue cable into composite input gives me the correct colors.  Plugging the green cable into composite gives me black and white.  Plugging in red displays nothing.

So my motherboard is outputting composite instead of component.  I guess.

---

