---
title: "DVB tv tuner card disappeared"
date: 2011-01-18
forum: Hardware
---

### Post by dunskii on 2011-01-18
Hey all,

Well been going around in circles for half a day so thought i was time for some help.

I installed a Twinhan VisionPlus DVB tuner card into my media server running Ubuntu Server 10.04.1 LTS, as I want to add mythtv backend.

Once installed I did a lspci and it show 
> 
Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)


So it was time to install mythtv-backend, which I have done successfully before, unfortunately this time when setting up mythtv it couldn't see my tuner card.

When I checked lspci again the expected was no longer there.

So started the googling and did a lsmod and the required modules bttv,  bt878, dvb_core, dst, dvb_bt8xx were no longer present.

Just incase I was imagining that I saw it installed I did grep -i dvb /var/log/messages which displayed
> 
Jan 18 15:21:00 mozart kernel: [    8.907096] bttv0: detected: Twinhan VisionPlus DVB [card=113], PCI subsystem ID is 1822:0001
Jan 18 15:21:00 mozart kernel: [    8.907269] bttv0: add subdevice "dvb0"
Jan 18 15:21:00 mozart kernel: [    9.121500] bt878_probe: card id=[0x11822],[ Twinhan VisionPlus DVB ] has DVB functions.
Jan 18 15:21:00 mozart kernel: [    9.346051] DVB: registering new adapter (bttv0)
Jan 18 15:21:00 mozart kernel: [    9.866926] DVB: registering adapter 0 frontend 0 (DST DVB-T)...


So I know I'm not imagining it. I've done, restarts and shutdown with now luck. 

Its a new server build so I'm happy to reinstall the os and see if that helps, but before I do something that drastic I thought I would ask first.

Thanks in advance 
D

---

