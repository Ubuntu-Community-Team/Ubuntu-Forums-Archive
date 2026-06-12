---
title: "Canon MG3100 issues"
date: 2015-10-30
forum: Hardware
---

### Post by chondromalasia on 2015-10-30
So, I currently run 14.04 on an ACER laptop, which can dual boot into Windows 8.

A couple years ago, my wife got a Canon MG 3100 and it was working great for a while. I can't remember if this coincided with us getting a new router or not, about three months ago, but for about two months, whenever I tried to print in Ubuntu, it would come out all jagged and stuff. Like it was kind of slipping vertically. If this helps, I could print a working UPC code, but not a working QPC code.

I tried everything to find a way to do a printer head alignment. I rebooted into Windows, which I knew had some Canon Tools, and it turns out I can print things out just fine in Windows. I really only have Windows on there for gaming and just for a backup, in reality 99.99% of the printing I will be doing would ideally come from Ubuntu.

This weekend I decided to fix the problem, and it turns out that it doesn't even try to print, it just spits out two piece of blank paper and then has an E and a flashing warning on its maintenance window.

I also just checked, it works just fine in Windows.

So I looked into changing the driver, and it turns out that it's been using the Gutenprint driver for a while, so I went ahead and installed the proprietary driver according to this post:

[http://ubuntuforums.org/showthread.php?t=2265878](http://ubuntuforums.org/showthread.php?t=2265878)

Everything seemed to install fine, in fact there are selections to print test pages and do a printer head alignment. However, when I select any of those options, the printer queue just says 'Pending'. If I try to print anything out, again, it still just prints two blank pages. I just installed a new cartridge, for what it's worth.

I'm kind of out of options at this point, so I thought I would turn to you guys for help. Let me know what information you need from me, I don't really know what to provide for this sort of thing.

Thanks in advance.

---

