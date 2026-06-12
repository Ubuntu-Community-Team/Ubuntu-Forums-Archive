---
title: "[resolved] Recommended Display Adapter?"
date: 2004-12-23
forum: Hardware &amp; Laptops
---

### Post by mark on 2004-12-23
As I've posted elsewhere at length, I'm not able to configure my preferred resolution (1152x864) in Warty, using the on-board video from my Intel D865GLC main board.  I'm now considering buying an AGP display adapter that will do the trick.  What I need:

[INDENT]An adapter that will support 1152x864@85Hz
An adapter that is reasonably fast
An adapter that doesn't break the bank (I'm cheap, OK?)
Preferably an adapter that's supported "out-of-the-box" by Ubuntu/Warty[/INDENT]
I'm not a gamer; I tried fiddling with the GIMP once & gave it up in horror<g>; nor am I trying to turn my PC into a home entertainment center.  My primary usages are Web surfing, email, text editing/word processing and some spreadsheet work.

I've seen some of the horror stories and/or "holy wars" regarding ATI vs. nVidia (kernel recompiles, proprietary binary-only drivers, etc.) and I'd rather avoid all that.  I'm completely agnostic as to which GPU an adapter uses - I just want the bloody thing to work to my modest specifications.  If anybody has a suggestion for a suitable adapter, I'd love to hear about it.  Conversely, if you have a "whatever you do, DON'T get..." story, that would be appreciated, as well.

*Thanks!* 

Mark

---

### Post by hardcandy on 2004-12-24
Nvidia 5600, 5700 or 5900 Geforce. Follow the tips in the Howto, FAQ forun for configuring it and no problem. I believe the price range is from around $90 to $200 depending on the how much RAM is on the video board and the size of the pipeline. 
Nvidia drivers are always good for any distro.
[http://www.newegg.com/app/SearchProductResult.asp?Submit=Go&Range=1&InnerCata=48&DEPA=0&bop=and&order=PRICE&description=nvidia&page=10&listStyle=2](http://www.newegg.com/app/SearchProductResult.asp?Submit=Go&Range=1&InnerCata=48&DEPA=0&bop=and&order=PRICE&description=nvidia&page=10&listStyle=2)

---

### Post by thors_hammer123 on 2004-12-27
I don't know how helpful this may be, but before running off to buy a new adaptor, perhaps you may still be able to weasel out higher resolutions from your current one even if the gnome screen resolution menu does not currently list them:
After installing Ubuntu, I only had 3 options, the highest being 1024x768. I was certain that my card was able to provide higher resolutions because on my just wiped out Windows partition I could get up to 1600x1200. So first if you also have Windows installed, check what is the max resolution that you can get on your card.
Now, the reason that I could not get higher resolutions was that the Ubuntu installer had misconfigured my monitor: It had set me up with a "Generic Monitor", instead of using my specific monitor. Here Knoppix came to my rescue. I have found that Knoppix's hardware detection capabilities are superior to most distributions and it may work for you too. Burn a Knoppix CD, and boot from it. Now open both the Knoppix /etc/X11/XF86Config-4 and the Ubuntu one. In my case, Knoppix had correctly configured me with my specific monitor plus all the resolutions it supported. If this works for you also, replace the Ubuntu configuration with the Knoppix one. Then go to the screen section of the Ubuntu file and add the resolutions that you want supported.
Hope this helps,

---

### Post by mark on 2004-12-29
[QUOTE=thors_hammer123]I don't know how helpful this may be, but before running off to buy a new adaptor, perhaps you may still be able to weasel out higher resolutions from your current one even if the gnome screen resolution menu does not currently list them: <snip>[/QUOTE] Thanks, thors, but I've already done the drill with providing *very* specific adapter & monitor specs to *XF86Config-4* & I can get higher resolutions (up to & including 1600x1200) - it just doesn't "like" my beloved 1152x864.  So, I'm looking for some (relatively cheap) hardware that will.

Mark

---

### Post by mark on 2005-01-01
I finally picked up a PNY dispaly adapter (nVida FX-5500-based) that has nicely resolved this issue.

---

### Post by spe69017 on 2007-05-15
> **mark said:**
> As I've posted elsewhere at length, I'm not able to configure my preferred resolution (1152x864) in Warty, using the on-board video from my Intel D865GLC main board.  I'm now considering buying an AGP display adapter that will do the trick.  What I need:

[INDENT]An adapter that will support 1152x864@85Hz
An adapter that is reasonably fast
An adapter that doesn't break the bank (I'm cheap, OK?)
Preferably an adapter that's supported &quot;out-of-the-box&quot; by Ubuntu/Warty[/INDENT]
I'm not a gamer; I tried fiddling with the GIMP once &amp; gave it up in horror&lt;g&gt;; nor am I trying to turn my PC into a home entertainment center.  My primary usages are Web surfing, email, text editing/word processing and some spreadsheet work.

I've seen some of the horror stories and/or &quot;holy wars&quot; regarding ATI vs. nVidia (kernel recompiles, proprietary binary-only drivers, etc.) and I'd rather avoid all that.  I'm completely agnostic as to which GPU an adapter uses - I just want the bloody thing to work to my modest specifications.  If anybody has a suggestion for a suitable adapter, I'd love to hear about it.  Conversely, if you have a &quot;whatever you do, DON'T get...&quot; story, that would be appreciated, as well.

*Thanks!* 

Mark


[Equity Line Credit Skin care Bankruptcy build Britney Spears](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

