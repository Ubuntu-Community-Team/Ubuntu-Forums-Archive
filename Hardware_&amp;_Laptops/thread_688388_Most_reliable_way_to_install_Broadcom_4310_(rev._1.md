---
title: "Most reliable way to install Broadcom 4310 (rev. 1) drivers?"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by Limbic on 2008-02-05
After a great deal of searching around in the forums and trying all of the solutions posted in the major threads, I still can't get my computer to even detect the wireless card at all.  I've read everything I could find and have tried all the major methods, including fwcutter and compiling the drivers and ndiswrapper from scratch with no luck.

After installing all the drivers and doing the error check where it's supposed to list the driver version as installed along with the hardware, it only lists the driver as installed with no sign of a wireless card at all.  I'd post a printscreen but don't have my computer with me to do so.

At this point, I'm starting to wonder if I've just got too much crap piled onto a fresh installation so I'm going to do a reformat and fresh install of Ubuntu just to play it safe.  Since it's a fresh start, I figured I'd just check in with others to see if they've had any luck.

My computer:
HP dv2715
AMD CPU, 1.9ghz dual core
Broadcom 4310 (rev. 1) wireless card
Ubuntu 7.10 Gutsy Gibbon

So for the people who have this same card and have been able to get it working, which method would you try on a fresh Linux install?

---

### Post by KyleAnderson on 2008-02-05
I helped a friend had a similar problem.
I think it was the same card. We did it with just a few steps after doing a million things.
1. Turn on multiverse / universe
2. Click on the thing in the restricted drivers manager.
That automatically installed fwcutter, and did everything for us, like magic.

Now you don't really have to format, you could just try this in a live cd.  If it works "just like that", then consider reinstalling.

---

### Post by keenwerkz on 2008-02-27
basically we have the same laptop DV2715nr same specs, same wireless card, follow the instruction from this thread (jamesgu's post) and i suggest do so using a freshly installed system cos it worked for me!

[http://ubuntuforums.org/showthread.php?t=650729](http://ubuntuforums.org/showthread.php?t=650729)

---

