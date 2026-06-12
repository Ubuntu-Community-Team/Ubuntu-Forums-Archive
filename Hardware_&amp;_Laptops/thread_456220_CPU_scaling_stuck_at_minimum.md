---
title: "CPU scaling stuck at minimum"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by Vivification on 2007-05-27
Sorry that this one is so wordy.  It's kind of unusual for me not to figure this out on my own and I'm not used to posting on forums.  Here goes nothing...

Alright, I reinstalled Ubuntu Feisty yesterday after a clean install and all seems well (after my last bout I now loath Automatix, but that's not part of this story).  I'm running a Dell M140 laptop with a 2Ghz Intel Centrino processor.  The thing runs hot if you let Ubuntu do as it pleases so I've relied on CPU power scaling for the past few distributions.  Now my processor stays locked in the lowest setting of 798 Mhz.  It remains at this setting regardless of what governor I select either via the GNOME CPU Frequency Scaling Monitor applet or via the command prompt.  I don't think this is a Fesity issue since my previous Feisty install didn't have this as the problem.  

I've followed the steps provided in [[COLOR="Red"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=248867") and [[COLOR="Red"]on this blog[/COLOR].]("http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling/")  And I've also entered in:
> $ sudo chmod +s /usr/bin/cpufreq-selector 
That step was taken from O'Reilly's Ubuntu Hacks book and allows for the GNOME applet to change my governor.

I know this has been a bit technical, but I'm pretty sure I screwed this up by being too complicated.  See, I went through all the steps listed and I've determined that the problem is with the cpufrequtils.  Whenever I run cpufreq-info I'm told:
>   current policy: frequency should be within 798 MHz and 798 MHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 798 MHz.

I can change it back to 2Ghz by entering: > sudo cpufreq-set -u 2Ghz

This fixes the problem during that session for me.  However, the second I reboot my system forgets everything I've entered and I'm back at the 798Mhz level on the next boot.  Also, it insist that my selected governor on boot is ondemand when I've actually told it conservative.  Not a big deal, but it isn't listening to me with that either.

How can I force cpufreq-set to remember what I tell it on next boot?  I attempted to have the 2GHZ command enter itself at startup but that didn't work.  This has to be the first time in awhile that I'm really loving Ubuntu and I'd have the perfect setup if I could just this one nagging issue resolved.  Any help would be appreciated, I'm just about out of ideas.

---

### Post by mat_london on 2007-06-04
Hi 

Are you sure?
I've just done a fresh Feisty install and my "CPU Frequency Scaling Monitor" sits there doing precisely nothing or at least the graphic does. They were working fine in Edgy.

However if I hover my mouse over the applets or set them to show text and graphic then the text in GHz is changing as expected.

I think the problem is with the applet on my PC 
 I think the reason the applet always shows the lowest CPU setting is because it gets the MHZ correct and the % wrong. 
That is you can watch it changing between 1 & 1.66 GHz all the time, but it only ever changes between 1% & 2%.

Any ideas ?

Mat

---

