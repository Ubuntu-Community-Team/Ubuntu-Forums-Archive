---
title: "gnome-power-manager is killing my battery!!!"
date: 2009-09-12
forum: Hardware
---

### Post by sandydoull on 2009-09-12
I recently bought a high capacity 9-cell battery for my acer aspire one. Wanting to preserve the battery for as long as possible i wanted it to shutdown the netbook when it reached 15% power. So in gconf-editor
 i set action to shutdown, critical power to 15% and unchecked "use time for policy". This method worked for my old battery, but I can't get it to work and it just runs the battery down until it is completely dead, this is VERY bad for li-ion batteries i have read.

I decided instead to use time for policy and set it to 21600 secs( 1hr5min), which equates to roughly 15% battery reamaining, this time the shutdown worked fine, but when i boot the computer up with the battery fully charged the computer shuts down a minute or so after booting into ubuntu.

I suspect it's something to do with g-p-m not being able to detect the time remaining in time and shutting down accordingly?!

Anyone have any workarounds or alternative programs i can use for power manangement so that my new battery doesnt get completely killed?! Thanks for reading and thanks in advance for any help;)

---

