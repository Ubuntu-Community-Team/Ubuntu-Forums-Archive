---
title: "Issue with driftnet and kismet"
date: 2011-03-18
forum: Hardware
---

### Post by Xeneth on 2011-03-18
I put them in this category because I believe both issues are directly related to my wireless.

Both these tools are not working, in that they cannot seem to use the wireless card.  I run these using sudo so it's not permissions, but neither seems to see any traffic at all.

Kismet get's the error "all sources are in error mode" while driftnet does nothing.   I know the wireless works because I not only can get online with it, but the new wireshark works flawlessly with it, even in monitoring mode.

I thought it could be the drivers, but it appears to have the updated ipw2200 drivers, so I'm a little baffled as to what's up.  I do not know linux well enough to troubleshoot like I can in windows so here I am asking for help.  :)

My laptop is a "Dell Latitude D610"

EDIT: Just thought I would mention this.  I find it off that my wireless is showing up as eth1 instead of wlan0.  May be unrelated, but thought I would throw that in.

Thanks

---

### Post by Xeneth on 2011-03-18
Figured this would get moved if it was in the wrong forums, but I never seem to get these kind of things solved.  

I don't know if this is an issue with Ubuntu or the installation, but any help would be appreciated.

---

### Post by Xeneth on 2011-03-19
Update, Most of the issues where fixed when I updated to Maverick, so it was an OS issue.  From what I have read in the kismet page, the un-fixed things are inherent to my wireless card.

Still having trouble with driftnet though.  Still looking.

---

### Post by jonnyboysmithy on 2012-03-09
I also had a d610, the wireless always worked for me. I got a new computer after the d610 went faulty. so now I run 64bit but driftnet 64bit has a bug so it won't work on 64bit.. :/
Yea I used to run 11.04 with unity. worked nicely. 11.10 was slow as hell on that thing.
EDIT: on the d610 the wireless was always eth1 for me (??)

---

### Post by pr0misc on 2012-09-04
I have this question regarding driftnet:

i can sniff the traffic in my LAN, I can also check what website ips and when a user is gathering images but it allways show "0 bytes transferred" and nothing appears on the window.

how can I solve this?

If I use my local machine it works but other machines on the same network do not :\

---

