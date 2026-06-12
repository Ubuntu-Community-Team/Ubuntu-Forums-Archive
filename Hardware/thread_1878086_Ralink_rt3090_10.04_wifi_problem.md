---
title: "Ralink rt3090 10.04 wifi problem"
date: 2011-11-09
forum: Hardware
---

### Post by dverrier on 2011-11-09
Hi,
Using 10.04 LTS, after the upgrade from kernel from 2.6.32-33 to 2.6.32-34 I found my ralink rt3090 was not working. I had previously got it working with a trick like including a directory and empty file /etc/Wireless/RT2860STA/RT2860.dat which I got from a forum posting. I avoided problems by removing the 2.6.32-34 packages and staying happily on -33.

I just upgraded 2.6.32-35 and found the wifi was still not woking... I upgraded to the latest drivers downloaded from the ralinktech.com web site, but still no joy. I saw a message in syslog  that
```
rt2860 0000:05:00.0: firmware file rt3090.bin request failed 
```

I deleted the  /etc/Wireless/RT2860STA/ directory and hoped to find a proper solution.

I copied the /lib/firmware/rt2860.bin to rt3090.bin
I got the message
```
rt2860 0000:05:00.0: firmware file rt3090.bin is too old; driver requires v19 or later
```

This gave me the hint to go back to the ralinktech website and download new firmware v26. I did this, and found that it only contained a file  rt2860.bin. I now see I could have tried to copy that file to lib/firmware, but I wasn't switched on, so I copied it to /lib/firmware/rt3090.bin instead.

Everything now works for me. It wasn't difficult or clever, but I hope this helps.

David

---

