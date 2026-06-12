---
title: "Hauppauge PVR-500 not scanning channels mythbuntu 9.10"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by bcambre on 2009-11-12
Did a fresh install (with latest updates) of mythbuntu 9.10.

However, when trying to scan for channels in the Europe-West region (Belgium); the progress bar does not move...

when i do  
```
ivtv-tune /dev/video0 -t europe-west -c E10
```
and then record via
```
cat /dev/video0 > /tmp/test.mpg
```
it is working just fine and i can see what has been recorded

when switch to this channel while the scan progress is running, it does move.

what could be causing this?

I used to have a Debian myth system (3 years old) that I want to move to this new platform.  Is it possible that i somehow (my memory fails me if I had to do that 3 yrs ago) have to RESET the PVR-500 card?

---

