---
title: "internet stability issues."
date: 2024-12-03
forum: Hardware
---

### Post by cryofreeze666 on 2024-12-03
last month they used 3 modems to fix my speed issue that me wired never noticed until it was extremely bad.

this month i'm having speeds in my normal range, but it takes a few seconds to load a page.  packetstats.com says my load speeds RIGHT NOW are min 42 ms, max 34389ms with an avg. ping of 912.9 ms

what i am asking is this, is there anything in snap, or via the web that will load test my local network and identify if i have equipment beginning to fail.  not leaning toward that since the wireless is effected as well, my "office" network cables are all gold plated cat8's.  even still  i just want to rule that out, or replace, whatever, ethernet cards, routers, ram, etc. if there is a problem on my end.

oh by the way, i'm a dum ass noob to ubuntu.  any recomendations (if there are any) will have me chasing through reading material, you tube, and maybe asking questions back here

thanks for whatever help i can get.  including, whether or not there even is any such thing as what i'm looking for.

---

### Post by TheFu on 2024-12-06
If both wifi and wire connections are problematic from multiple different devices then it is either the WAN router or upstream inside the ISP. 

Nothing you can do except waste their time until they fix it.  

If your WAN router isn't in support or hasn't been patched in the last 3 months, it is probably time to replace it ... or get off the consumer router forced upgrade train and setup a more generic x86-64 router that can run dd-wrt, openwrt, opnsense or pfsense. By going with x86-64, you'll have the most options and the most likely support periods.  Also, stick with Intel NICs, since some of those router OS options don't support realtek at all - at least not well and not the last time I looked.  There are some low power x86-64 systems out there, so 35W of power isn't required.  I have a 12W single-board-computer, SBC, from AMD running an x86-64 CPU as my router with OpnSense/BSD. Bought it in 2015. Air cooled. Very stable.  

In my config, it can't hit 1 Gbps, but since my internet connection is 10x less than that, I'm not worried. It meets my needs.  The same hardware using a Linux-based OS should easily get to 920Mbps - linux drivers are better on my hardware.  I happen to prefer OpnSense and the trade-off in slower throughput is fine for my needs.

---

### Post by him610 on 2024-12-07
> WAN router or upstream inside the ISP.
A neighbor of mine had issues with flaky internet (Comcast) service; called Comcast several times about poor service. 

Finally, discovered original installer, some independent contractor, had skimped on the coax cable running from distribution box to the house - there were two shorter cables connected in series together with connection inside conduit pipe that filled with water during rain. 
Comcast corrected problem by running one length of coax cable from distribution box to the home.

---

### Post by TheFu on 2024-12-07
I have 3 different coax lines from "the box" to my demarcation point (side of the house) from Comcast.  2 take the long way around and 1 goes under the driveway. 2 are RJ-6 and 1 is the thinner RJ-59. The RJ-59 worked for about 2 yrs.  The RJ-6 cables work about 10 yrs each.  Of course, the demarcation point is exactly on the opposite side of the house from where most internet equipment is located, so the runs are about 3x longer than actually needed.  "The box" to my home office is in the same corner of the property. The run would be direct, then up the side of the house into the room, if grounding wasn't needed.

About once a month, I run and save the results from a speedtest-cli test. Just did another, 
```
Testing download speed................................................................................
Download: 29.40 Mbit/s
Testing upload speed......................................................................................................
Upload: 6.04 Mbit/s

```
I pay for 30/6, so the numbers track to what I'm supposed to get. It is a business connection, not residential.  For 50% less, I could get a residential connection for 300/20, I think, but not with the same SLA or stability and never with a static IP or 5.

Anyway, insist on an RJ-6 Coax, if you are using cable/DOCSIS for internet connectivity.  Every few years, I have to contact Comcast to get the cable re-buried. They don't dig deep enough - guess they don't like digging in clay soil.  I've found the trick is to say that kids play in the yard and are tripping over the exposed cable. That always gets a digging crew sent in a week or so.

---

### Post by him610 on 2024-12-07
> They don't dig deep enough - guess they don't like digging in clay soil.
Yes, clay. We have clay soil up here; when it dries out, it is hard as concrete. 

When I grew up in Georgia, (Cedartown in Polk County)  the soil was really easy to dig in. My mother used to pay me 75 cents an hour to plant her flowers - really easy digging.

---

