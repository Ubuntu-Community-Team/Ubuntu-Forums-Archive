---
title: "recover from synaptic remove lvm?"
date: 2009-09-09
forum: Installation &amp; Upgrades
---

### Post by inghamc on 2009-09-09
I have this friend who runs x64 kubuntu jaunty (upgraded from intrepid) and who discovered ppa a few weeks ago.  Because larger version numbers are always awesomer, he started upgrading to the latest versions of kde, firefox, chromium, etc. etc.

synaptic started complaining that it couldn't upgrade some kde plasma thingamabob because it needed an 8.1 network manager, so off to ppa and adding to sources.list...

Well, synaptic then told me I mean him that it needed to remove lvm2 (and maybe some other scary stuff, but lvm2 is what sticks out in memory right now...), and for some reason he actually said ok!!!  Lo and behold, after the next reboot grub wasn't able to find /dev/mapper/vgblahdeblah.

So now I/he can boot with the excellent Part Magic LiveCD, view and mount the lvm partitions and see all data, but don't know where to go from here:

Should I just copy /etc, /home and /opt off to another drive and reinstall from scratch, or is there a way I can fix the existing Jaunty install, either by putting files in place or somehow getting to a boot state where I can reinstall lvm?

Thanks in advance - my embarrassed friend would really appreciate your help :)

---

