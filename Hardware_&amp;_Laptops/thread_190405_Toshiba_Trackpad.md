---
title: "Toshiba Trackpad"
date: 2006-06-06
forum: Hardware &amp; Laptops
---

### Post by kieranjones on 2006-06-06
Hi,

I've just installed Ubuntu on my laptop, and among other problems I've posted elsewhere, I simply cannot use the trackpad as it is at the moment. I'm having to run my finger several times accross it to move from one side of the screen to the other. Is there a way to adjust the trackpad resolution or sensitivity?

In Windows it is setup so that when I touch in the top left corner the mouse goes to that corner, and when I touch in the top right corner it goes there. Absolute positioning I think it's called or something like that, heh.

Help anyone?

---

### Post by HankB on 2006-06-06
There are a lot of configuration options in the xorg.conf file (or there can be.) These probably depend on whether you have an ALPS or Synaptics touch pad. I have Synaptics and use the program qsynaptic to manage settings. I'm not sure if it works with the ALPS pad, but is worth a try since I recall reading that the synaptics driver works with both touch pads.

Once I have my settings configured, I run 
```
qsynaptics -r
```
from the command line after starting up to load the settings. Most of the settings could be migrated to the xorg.conf file to eliminate this need, but I use the option to delay tapping after keyboard activity and that loads a background program syndaemon.

Someday I'll figure out how to get *that* configured in xorg.conf or how to run 'qsynaptics -r' automatically on startup.

HTH,
hank

---

### Post by jphofmann on 2006-06-06
Adjustments to the trackpad sensitivity can be made from the 'System->Preferences->Mouse' menu under a tab called motion. Undser the speed subheading play with Acceleration and Sensitivity untill you find a combination that feels right.

For my track pad i have sensitivity all the way up and acceleration set to a little better then half.  But to each his own.

Sadily if you also use a mouse it will share these settings.  There is a more complicated method that can be used to create prefrences on the device level, but to my knowledge there is no "strightforward" way to do this.

Also, I know of no "officially supported" way to enable what you call 'absolute positioning' but it sounds like a great idea to me.

J

---

### Post by roblef on 2007-06-01
Is there any way to stop the trackpad from accepting my taps as clicks? I hate that "feature" in  laptops, and turn it off when using windows or Mac ones. How do I disable it in Ubuntu, as there's no "trackpad" settings, and the mouse doesn't work that way, hence no settings in the Mouse pref panel.

---

### Post by xs650 on 2007-07-11
Roblef, I followed JPHOfmann's advice
> 'System->Preferences->Mouse' menu under a tab called motion. Under the speed subheading play with Acceleration and Sensitivity until you find a combination that feels right.
and cut the sensitivity all the way down to prevent the touch pad being overly sensitive to taps. It worked like a champ. With the sensitivity as low as it will go, the tap feature is essentially off on my 7 year old Sony Vaio laptop with Alps touch pad running Feisty.

I may add some sensitivity back and see if I can get a reasonable compromise. Fortunately, I have no plans to use a mouse with that computer.

---

