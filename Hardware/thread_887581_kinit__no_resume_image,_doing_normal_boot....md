---
title: "kinit : no resume image, doing normal boot..."
date: 2008-08-12
forum: Hardware
---

### Post by Miklas on 2008-08-12
Since I have updated Ubuntu 8.04, i can't start it up anymore. Seembly, there was a new kernel, perhaps this has something to do with it?

If i boot, i get the normal oragne loading bar, and after its finished, i get : 

kinit: name_to_dev_t(dev/disk/by-uuid/6acc0ad2-cf4d-46d1-9392-3d08db4026ea) = sda5(8,5)   
kinit : no resume image, doing normal boot...

Then my whole screen is black and in white letters, and i can 'login'. After logging in, its like a full screen terminal. 

I have read some forums and tried alot of things, but non of them seem to work. If i press ALT-F3 when the orange bar starts, and wait some time, i get the following error : 

intel_rng: FWH not detected 

I have no idea what it means, but i found this ::
[http://forums.gentoo.org/viewtopic-t-559170-highlight-.html?sid=a7efc65428c708b5d3986e327046a049](http://forums.gentoo.org/viewtopic-t-559170-highlight-.html?sid=a7efc65428c708b5d3986e327046a049)
Don't know if it has anything to do with my problem, and it doesn't say how to fix it. 

But, after the intel_rng... error, it just goes on, and when i get to 'rc.local' it just stops. I checked the rc.local file with a live cd, and the only thing in it is : exit 0 . So basicly, that file should not do anything, trough when loading in ALT-F3, its stuck there. 

I think it has to do with the update I did, and the new kernel, but I'm a linux newbie, so I don't really know.

This are my PC's specs : 
2GHZ intel single core
512 MB ram
ATI mobilty radeon 7500

Booting with a live cd goes perfectly.

I wouldn't like to reinstall ubuntu, since i got alot of stuff on the laptop that i wouldn't like to redownload, and i don't have an external harddrive currently where i can back it on to. 

I hope someone here can help me? :(

---

### Post by Miklas on 2008-08-12
After reading this : 

[http://cinnamonpirate.com/blog/497/](http://cinnamonpirate.com/blog/497/)

(what didn't work, btw) 

I think the problem has to do with partitions. Any idea on how to fix it? :S:confused::confused::confused:

---

