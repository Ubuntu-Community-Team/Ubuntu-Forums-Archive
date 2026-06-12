---
title: "Inspiron 1501 Randomly Freezes"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Cris987 on 2008-01-10
This has very little to do with Ubuntu, but I thought you guys could kindly help me.

I have a Ubuntu-installed Dell Inspiron 1501 that did not itself come with Ubuntu. Wehn I was in Feisty, the laptop would randomly freeze on desktop loading (capslock indicator and scroll lock indicator flashes). I did not know what I could do about it, so I tried to see if a fresh insstall of Gutsy would fix anything. 

Indeed it did - except now my laptop freezes not on desktop loading, but just randomly. I would have firefox, rhythmbox, and pidgin on (not too intensive IMO), and all of a sudden it would freeze - no response whatsoever (ctrl-alt-backspace doesn't work).

Anyone has any clue what could be wrong with my laptop? I bought it this summer, but is its warrantee still in effect with Ubuntu installed on it? 

Thanks.

---

### Post by prx on 2008-01-13
BUMP!

I am experiencing the same issue. It seems to be occurring when the laptop is idle. Have disabled screensaver, power management, and video is set to no 3d, etc.

syslog does not seem to be catching any errors before it dies.

---

### Post by Cris987 on 2008-01-13
I'm suspecting that it's a firefox issue. I've switched to swfitfox to see if that is the case.

---

### Post by sprucegum on 2008-05-04
I am running the same system and also experiencing hard locks; no response from the capslock key; no result from either ctrl-alt-backspace or [Skinny Elephants]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html").  

I turned off powernow in the BIOS, so far, so good with an uptime of 7 minutes!

I have also added pci=nomsided to my kernel options as suggested by [Fosser]("http://fosser.wikispaces.com/Ubuntu+on+Inspiron+1501") 

Ok, so turning off powernow through the BIOS gave me a freezeless system for about 50 minutes until I rebooted intentionally.  I turned powernow back on and am just trying to determine if the pci=nomsided kernel option will make the difference.  I would rather not lose CPU frequency control.  Although I'm not quite sure what pci=nomsided does,  I think it will have less of a negative effect than the powernow setting.  Hopefully it works or I will have no option but to turn off the frequency scaling.

I experienced a lock up using the pci=nomsided option so I turned powernow off through the BIOS.  The system seems stable.  However, I did experience a single lock-up but I was able to safely reboot using [Skinny Elephants]("http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html").  This may be the best solution so far, although I would like to have CPU frequency scaling.

Ok, looks like the workaround is acceptable.  Disabling powernow through the BIOS has given me crash free computing.  I have uptime of over 4 days, however the CPU frequency does not scale when this option is used.  So there is a tradeoff.

---

### Post by redDEADresolve on 2008-05-13
I haven't come across this issue, what BIOS are you guys using?

---

