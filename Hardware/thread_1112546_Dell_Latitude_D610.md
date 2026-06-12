---
title: "Dell Latitude D610"
date: 2009-03-31
forum: Hardware
---

### Post by LobeRoni on 2009-03-31
I recently loaded Ubuntu 8.10 (tonight) and my wireless, as well as my Ethernet controller aren't working. I can't connect either to the internet, looked around on the forum and found a few "Dell Latitude D610" posts but nothing to help me. Can anyone help me?

---

### Post by kvn290 on 2009-04-08
I had the similar problem where wired connection worked, but the wireless didn't.  For me, running 'sudo lshw -C network' would show my wireless lan as DISABLED.

I in now way can take credit for a solution, but the following links worked like a charm...


This one was helpful...
[HTML]http://ubuntuforums.org/showthread.php?t=766560&highlight=wireless+d610[/HTML]


But this one actually provided a specific solution for my hardware...

[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#Step%201:%20All%20BCM43xx%20-%20Install%20NDISWrapper%20and%20Blacklist%20Native%20Driver[/HTML]

I hope this helps!

---

