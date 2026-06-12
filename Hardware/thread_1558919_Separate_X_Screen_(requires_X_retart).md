---
title: "Separate X Screen (requires X retart)"
date: 2010-08-22
forum: Hardware
---

### Post by terrywang on 2010-08-22
Hi Guys,

Recently I mistakenly clicked on TwinView in the NVIDIA X Server Settings GUI which I never really use.

Hardware: Dell Latitude D620 + Dell P2210 LCD

Then I found something odd happened.

Normally at work I use only the P2210 monitor and disable the laptop LCD. I used to be able to use Separate X Screens dynamically, in other words, I was able to switch between the LPL - Laptop LCD and P2210 (2 ways) any time I want without restarting X.

But after that, I found it's not possible to do this any more. Symptom:
1. if I set the P2210 as default, want to disable P2210, TwinView and Disable options grayed out.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167268&stc=1&d=1282529596[/IMG]

2. try to enable LPL, TwinView is usable but Separate X Screen requires restart.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167269&stc=1&d=1282529596[/IMG]

I tried to recreate the xorg.conf, reset settings, use nvidia-xconfig to enable --separate-x-screen and all other different things with no luck. 

Just wonder how to revert back to the old way, so that I can still enable/disable separate X screen on different monitors 2 way + dynamically.

Try to see if anyone in Ubuntu Forum know this issue by any chance. 

Any input will be appreciated. Thanks.

Terry

---

### Post by clrg on 2010-08-23
Set both screens to TwinView. If you want to disable one, set the resolution to "off", don't set it to disabled. 

I use the same control panel, and I know it sucks. But that way you should be fine :)

---

### Post by terrywang on 2010-08-24
Well, I finally figured out something.

Once I click TwinView the separate X Screen option won't be available in nvidia-settings again, when trying to enable a previously disabled screen.

Now it works this way:
I can switch between 2 LCDs (means I use 1 of the LCDs at a time) by:

1. Enable TwinView for the external LCD
2. Apply
3. Disable LPL (laptop LCD)
4. Apply

Now I can use the external LCD only.

The only thing different is that now I need to use TwinView instead of Separate X Screen to switch off LCDs.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167366&stc=1&d=1282627164[/IMG]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=167367&stc=1&d=1282627164[/IMG]

---

### Post by terrywang on 2010-08-24
> **clrg said:**
> Set both screens to TwinView. If you want to disable one, set the resolution to "off", don't set it to disabled. 

I use the same control panel, and I know it sucks. But that way you should be fine :)

Thanks for the reply.

Finally I figured out. The nvidia-setting GUI is not that great bug it has worked fine on my D620/D630 since Ubuntu 8.04 Hardy. I can't complain too much about it;-)

In fact, I like the way Intel Driver works under Linux, fully integrated, although Intel GMA graphic chip is crap lol:lolflag:

---

### Post by clrg on 2010-08-24
Glad you found a solution :)

Please mark the thread as solved, for it will help others when searching for a solution to the same problem.

---

