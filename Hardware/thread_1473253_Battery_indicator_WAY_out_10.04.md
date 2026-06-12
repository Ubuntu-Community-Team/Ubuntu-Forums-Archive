---
title: "Battery indicator WAY out 10.04"
date: 2010-05-05
forum: Hardware
---

### Post by JavaNut13 on 2010-05-05
Its all in the title. The battery indicator in the notification area often says that the 'battery is critically low' and messages will pop up telling me that my computer is going to hibernate (which it never does)

It will then flick back to showing 6 hours & 20 minutes remaining... which is similar to what it showed in previous versions.

I am running an Acer Aspire One (1.6Ghz, 1GB, 10.1", 250GB, 1.3MegaPixel, 6 cell, Blue)

Any ideas why its doing this??

Cheers, 
Will

---

### Post by Fire-Eyes on 2010-05-16
I have the same problem...
But my computer tends to go to the lock out screen and then flickers.
It is extremely annoying.
If anyone has any ideas I would also like to hear them.

Thank You

---

### Post by JavaNut13 on 2010-05-17
Mine just shows the wrong battery watt/hourage for the design or for the amount when fully charged.

---

### Post by juniper1982 on 2010-05-17
me too.  my problem is that it doesn't display the percentage, and only the time left.  it then jumps back in forth around some average that steadily drops.

---

### Post by birdtoe on 2010-06-20
I have a similar problem on my Toshiba Satellite L455. Whenever I unplug it I get a warning that says I only have 4 minutes left and that it will go into hibernation soon. After it does that it works fine, but on the battery indicator it only shows the time left, not the percent and the time jumps around a little, approximately where it should be.

---

### Post by HyperFlexed on 2010-07-14
I was testing the "hibernate when critically low" feature. Sure enough, it didn't work and the laptop just died. Not even a soft shutdown.

The laptop was also running far past the point where the battery read as 0%

Now all the charge profiles and correction factor graphs have been wiped, which I assume will mean I have to go through more charge cycles to get that information back. It's outrageous to think that that information would be completely wiped in a hard reset. It should be backed up in /var/ or something.

Idiotic design. I can appreciate that it's difficult to reverse engineer this stuff, but to be so careless with what you can reverse engineer is just unfortunate.

Now my battery is charging, and it claims it's at 100% instead of telling me how long till the charge is complete. *pulls hair out*

Dell Mini 1012, Ubuntu 10.04, XFCE 4.6.1

---

### Post by JavaNut13 on 2010-07-17
I have had it a few times when Im charging, it will say its fully charged and then when you unplug it, it will zoom down to something like 30%

---

