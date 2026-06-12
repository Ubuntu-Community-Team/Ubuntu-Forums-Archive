---
title: "Alt Gr no longer works after upgrade to 9.10"
date: 2009-11-08
forum: Hardware
---

### Post by Román on 2009-11-08
Since updating to Karmic, my keyboard's AltGr key (the right one) no longer works.  It's supposed to enable the 3rd level of keys on my international layout (I use an english keyboard, but my first language is spanish).  What I find stranger is that now when I press AltGr+/ (it's supposed to write the opening question mark '¿') and then another letter it prints some strange and letters with marks I 've never seen: &#672; &#11379; &#7867; &#429; &#7927; &#7911; &#7881; &#7887;&#777; &#421; &#7843; &#642; &#599; ƒ &#608; &#614; &#549; &#392; &#651; &#595; &#626; &#625; 

This is a rather vanilla ubuntu karmic, updated from a jaunty updated from.... up to an 7.10 at least.  The keyboard is a rather generic one and I tried with another even more generic and it didn't work either.

Any ideas?

---

### Post by knowname on 2009-11-10
I have the same problem on a Danish keyboard, after updating from jaunty to karmic.

---

### Post by Román on 2009-11-10
I've been able to fix it by changing the layout from "USA Alternative International (former us_intl)" to "USA International (with dead Keys)"

---

### Post by knowname on 2009-11-11
Mine (Danish keyboard) works now. Two things were changed so I'm not sure which fixed it: the update manager installed a bunch of new updates, and while that was going on I opened the Keyboard Preferences, and switched the "Alt/Win key behavior" setting, but then switched it back to Default. After a reboot I have my normal AltGr behavior.

---

### Post by OliverN on 2009-11-18
if the problem persists you might want to look [here]("http://ubuntuforums.org/showthread.php?t=1311272&highlight=altgr") as well.

---

