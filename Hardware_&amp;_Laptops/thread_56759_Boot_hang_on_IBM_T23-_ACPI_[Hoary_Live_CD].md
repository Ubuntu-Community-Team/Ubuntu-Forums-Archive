---
title: "Boot hang on IBM T23- ACPI? [Hoary Live CD]"
date: 2005-08-13
forum: Hardware &amp; Laptops
---

### Post by TedETGbiz on 2005-08-13
After a month, I have no replies.  Am I doing something  wrong?  Could someone suggest how I could have done this differently so as to get a response?  I have a client who is thinking about Ubuntu on a laptop, but I need more information to help her...

Thanks.
---------------------------------------------------------------------------------------------
After posting the text below in the wrong place (Warty) I decided to try something I read about in another post.  For those who might be having a similar problem, I typed the following at the boot prompt:

live acpi=off

Using this switch I have now booted successfully twice, and the following works fine:
-network and wireless (and switching between them when I disconnect from the docking station)
-screen and desktop
-sleep and wakeup, either by function key or closing the top
-battery and AC indicators, including time left on battery, charge percentage, etc.

What doesn't work is undocking the laptop, opening and closing the lid and then redocking.  The reason seems to be that the T23 temporarily shows weird garbage, then switches back to the desktop, and my external monitor (Samsung SyncMaster 174v) chokes on it.  Or is it because I turned off ACPI?

Questions:
1. If ACPI is off, is it using APM now?  How do I tell?
2. Is there a boot switch to set the screen resolution correctly at 1280x1024? (it incorrectly detects a higher resolution)
3. Is there an easy way to save the current profile so that when I boot back in from the CD the next time it is all there and doesn't have to go thru all the auto detect, etc?  I believe Knoppix does something like this with a "scan" boot switch...

Great distro!  Love it so far...  :grin: 
---------------------------------------------------------------------------------------------
Ubuntu looks great on my laptop; unfortunately, in about 15 tries, it only booted up once.  The rest of the time it stops with a line beginning "ACPI:"  Since I am doing the live CD, I don't think I can change anything to use APM, and I don't think I can get/keep a log file either.  The CD itself is OK because it boots and runs on an IBM A50 I have on the bench.

Several posts suggest adding "noacpi" to the boot prompt, but that doesn't seem to make a difference.  I assume an APM prompt switch won't work because the module isn't loaded on the live CD.  Is that right?

Ubuntu appears to be an elegant and powerful dist., so I would very much like to get it to work.  Can I create a boot log or change some BIOS settings to try to nail this problem down?

Thanks much!

---

