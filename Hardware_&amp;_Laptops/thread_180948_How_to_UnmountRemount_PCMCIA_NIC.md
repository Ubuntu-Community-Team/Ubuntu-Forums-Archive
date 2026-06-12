---
title: "How to Unmount/Remount PCMCIA NIC"
date: 2006-05-23
forum: Hardware &amp; Laptops
---

### Post by Mortuis on 2006-05-23
I have an old Thinkpad 770 running Ubuntu Server. It's connected to my LAN via a PCMCIA 802.11b Ethernet card. I've been having a problem where the ethernet card will just stop working (the light on the card isn't on, and the computer doesn't respond to network connections), there are error messages on the screen but I can't find the log file that they're in.

I am able to solve the problem easily by physically reseating the card, just pop it out and plug it back in and the computer beeps and a few seconds later the light is blinking and when I get to work I'm able to SSH in. Since this happens ever couple days, I was thinking I might be able to avoid this problem if I were to add unmount and remount jobs to the chrontab. I know how to use the chrontab, but I don't know how to unmount and remount an NIC. Could someone please help me with this?

---

### Post by joft on 2006-05-23
Hi,

what you are looking for is - I think: ```
cardctl eject
``` and ```
cardctl insert
```

There is also a ```
cardctl reset
``` but I prefer the first combination, because reset didn't work for me that reliable.

---

### Post by Mortuis on 2006-05-23
Thanks, I'll give that a shot manually next time it goes down.  Yesterday it was working while I was at work, and went down in the time it took me to get home!  I'm thinking maybe I should run an hourly script to try pinging google or something, and remount the card if it can't.

---

