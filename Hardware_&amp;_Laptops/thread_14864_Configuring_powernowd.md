---
title: "Configuring powernowd"
date: 2005-02-10
forum: Hardware &amp; Laptops
---

### Post by Spif on 2005-02-10
Powernowd is installed on my laptop. My 1,7 Ghz Centrino processor is normally running at 600 Mhz, but it often accelerates to maximum speed at times when it is not needed at all. If I load a new page in Firefox, it immediately goes at full speed even though it does not make the loading faster. 

Is there some way to configure powernowd so it only utilizes the processor fully after a given amount of time?

---

### Post by GilGalad on 2005-02-10
To configure powernowd you can create a file called:

/etc/default/powernowd

with the only line:

OPTIONS="-q -m 2"

Have a look at man powernowd to see the configuration options.
Setting -m 2 and maybe using -u 90 may get you where you want.

---

### Post by Spif on 2005-02-10
[QUOTE=GilGalad]To configure powernowd you can create a file called:

/etc/default/powernowd

with the only line:

OPTIONS="-q -m 2"

Have a look at man powernowd to see the configuration options.
Setting -m 2 and maybe using -u 90 may get you where you want.[/QUOTE]

I tried a lot of combinations and now it only gradually raises the processor speed. This is not quite enough. No matter how little the frequency goes up I can hear the computer working, and this is what really drains the battery. Is there any way to CPU throttle it at 600 Mhz?

Any ideas?

---

