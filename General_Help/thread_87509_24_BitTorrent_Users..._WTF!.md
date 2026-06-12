---
title: "24 BitTorrent Users... WTF?!?"
date: 2005-11-08
forum: General Help
---

### Post by drummer on 2005-11-08
I upgraded to breezy last week and since then, Azureus isn't working properly. I only ever get 20 to a couple hundred users listed as connected in the status bar, usually there's over 600,000.. so my torrents aren't downloading. I installed Azureus in Hoary, so it's just stayed with me through the upgrade. Is there anything that it needs to run in breezy that's different from hoary? My torrents are more than half done and I don't want to have to start them over (DVD ISOs ;) )

Any ideas / similar problems??

---

### Post by Samuel on 2005-11-08
did you install java RE 1.5? if not there is a howto here--> [link]("http://www.ubuntuforums.org/showthread.php?t=70428")

also dont forget to tell ubuntu to use suns java as default, i had the same problem as you until i did this...
```
 sudo update-alternatives --config java 
```

---

### Post by drummer on 2005-11-08
WOW! over a million users I can see now, thanks a lot. I had Sun's java installed in hoary, would breezy have gotten rid of it? After installing java, the output of that command was this:```
There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
*+    2        /usr/lib/jvm/java-gcj/bin/java
      3        /usr/lib/j2re1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 
```
the last option is the one i just installed, is the selected one breezy's version? what happened to the version I installed in hoary (1.5.0_r3 I think)?

---

