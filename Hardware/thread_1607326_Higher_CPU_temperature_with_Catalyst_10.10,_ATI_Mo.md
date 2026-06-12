---
title: "Higher CPU temperature with Catalyst 10.10, ATI Mobility 3400."
date: 2010-10-27
forum: Hardware
---

### Post by radioboy on 2010-10-27
I recently did a fresh install of Maverick (64 bits) in a Dell Studio 1535, with an ATI Mobility 3400.
I updated to the latest kernel, 2.6.35-22-generic.
Before, I was using Mint 9 (which is based in Ubuntu) with Catalyst 10.7, 
and I always got CPU temperatures of nearly 55 °C under normal conditions, let's say, browsing without too much flash content, a text editor, a couple of Terminals and Rhythmbox working, with compositing enabled.

Now the newest Catalyst 10.10 driver was just out when I installed Ubuntu;
I downloaded it from the ATI site, and it built correctly; fglrxinfo shows:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3400 Series
OpenGL version string: 3.3.10243 Compatibility Profile Context
However, now the CPU temperature doesn't go below 60 °C at any time under the same conditions, and sometimes it rises up to 65 °C under the same conditions, for one or two minutes. The fan works more as it should (and as it did before) at those temperatures.

This looks like a driver issue, but I'd like to know: 
1) is anyone else having the same issue with this new driver?
2) is it safe to operate *constantly* in the range 60-65 °C? (Typical uptimes recently have been around 2-3 days.)

---

### Post by glomack on 2010-11-07
Look, I'm not sure about it. I've already installed kubuntu 10.10 and I was about to install the proprietary drivers but before doing that since I was wondering about any possible issues about it, I first did a quick google tour to find out any related issues. Actually I found your post among few others and after that I went to the AMD site. Guess what? I found a bulletin stating severe performance issues that were apparently caused by a recent kernel security patch and it happens that they created a patch to resolve the issues...

Not sure whether this problem is affecting you or whether this patch actually resolve them or not... However I thought that if you haven't already read the AMD bulletin it could be interesting for you. Just in case, this is the URL and if you get any news about it please let me know :-)

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

---

### Post by glomack on 2010-11-07
Actually after reading the detailed release documentation I've found out that the 10.10 version should resolve the issue so no clues about it. I have the same graphic card as you but within a vaio FW139E... I'll install the driver and I'll finally get to know whether this driver works for me or not since the generic driver happens to not be doing a good job although it works decently.

> **glomack said:**
> Look, I'm not sure about it. I've already installed kubuntu 10.10 and I was about to install the proprietary drivers but before doing that since I was wondering about any possible issues about it, I first did a quick google tour to find out any related issues. Actually I found your post among few others and after that I went to the AMD site. Guess what? I found a bulletin stating severe performance issues that were apparently caused by a recent kernel security patch and it happens that they created a patch to resolve the issues...

Not sure whether this problem is affecting you or whether this patch actually resolve them or not... However I thought that if you haven't already read the AMD bulletin it could be interesting for you. Just in case, this is the URL and if you get any news about it please let me know :-)

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

---

### Post by radioboy on 2010-11-07
> **glomack said:**
> 
Not sure whether this problem is affecting you or whether this patch actually resolve them or not... However I thought that if you haven't already read the AMD bulletin it could be interesting for you. Just in case, this is the URL and if you get any news about it please let me know :-)

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)

When I was using the 10.9 driver I applied that patch, and as far as I remember it was ok. However, with Catalyst 10.10 I haven't found anything related to this issue, nor available hotfixes yet.

By the way, I tried using the ATI Catalyst 10.10 driver with Kubuntu 10.10, but I found it unusable either with or without compositing (Kwin), while Compiz only worked using Beryl decorations (which look awful), and was still not even at the level of a Gnome desktop with Compiz. It would be interesting to know if you are able to get a better experience.

---

### Post by glomack on 2010-11-07
Well, so far so good here :-). Actually I decided to install the proprietary drivers because I got the sensation that the fan was over working and now it is quiet which it may be good or bad ;-) So far all animations are working as it seems they should. I guess my hardware configuration may be more "suitable" than yours strictly speaking about this driver, don't know... 

One thing you may have done or not is to get more information about the average/recommended/desired CPU temperature specifications for your processor just to be aware whether you're safe or not... I'm sorry I cannot provide you more info :-(

---

### Post by Billy71 on 2013-02-03
Radioboy is not alone, the same thing with ATI Mobility Radeon HD 2400.
I've tried various powersaving with Catalyst drivers 10.10-12.6 but no luck -- the laptop's fan is almost constantly running, even on idle.

It seems that for Radeon 2xxx-3xxx series there is no good alternative to Catalyst 10.9 :(

---

### Post by nothingspecial on 2013-02-03
Old thread.

Closed.

---

### Post by sffvba[e0rt on 2013-02-03
*Old thread **closed**.*


404

---

