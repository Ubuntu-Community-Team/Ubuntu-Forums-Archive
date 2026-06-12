---
title: "Upgraded to 9.04 (beta): now the display goes blank"
date: 2009-04-01
forum: Installation &amp; Upgrades
---

### Post by yankeeDDL on 2009-04-01
Hello,

I've upgraded my 8.10 installation (in a Virtaualbox) to 9.04 to see how it worked.
It didn't :)
The installation went fine: everything seemed to be taken care of (I was informed that some repositories were being disabled, I was asked if I wanted to maintain my menu.lst and other files which I had modified).
I have chosen the "replace" option whenever possible, to have an installation as "clean" as possible.
Well, now when X starts the screen goes totally blank.
Can somebody help debugging this?
How do I stop X from starting?
And once I make it to a terminal, how do I debug the problem?

Thanks in advance ...

---

### Post by WilliamJenningsBryan on 2009-04-01
Boot using the recovery option in Grub, and this will take you to a terminal without X starting. 

Deleting /etc/X11/xorg.conf might help the problem.
Also, if you have an older version xorg.conf that worked in the past, maybe try using it instead of the current version.

---

### Post by yankeeDDL on 2009-04-01
I tried it.
I got to the console via Grub and modified xorg.conf.
There was a .bak file (matching a .vbox file) which were the ones I used. 
Didn't help ... still the screen goes totally black when X starts.

I also saw a "try to repair the graphics automatically" (or something like that) in Grub's recovery option. Tried that too but still no progress ...

---

