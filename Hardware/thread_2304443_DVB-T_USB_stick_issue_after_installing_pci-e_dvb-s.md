---
title: "DVB-T USB stick issue after installing pci-e dvb-s2 TBS card"
date: 2015-11-26
forum: Hardware
---

### Post by lukasz15 on 2015-11-26
Dear All!

I've experienced issue with my DVB-T card for which I cannot google any answer :( Please advise, here it is:

I have USB DVB-T stick on IT9135 - dual tuner. It worked fine on lubuntu 15.10 with tvheadend. 
Then I added PCI-E dvb-s2 card - also dual - TBS 6982. And it works fine too but with it dvb-t stop working. 
It looks like it is removed and added in loop, dmesg returns:



[ 1695.360847] DVB: registering adapter 2 frontend 0 (ITE 9135(9006) Generic_2)...
[ 1696.218322] DVB: registering adapter 0 frontend 0 (ITE 9135(9006) Generic_1)...
[ 1697.100650] DVB: registering adapter 2 frontend 0 (ITE 9135(9006) Generic_2)...
[ 1697.939457] DVB: registering adapter 0 frontend 0 (ITE 9135(9006) Generic_1)...
[ 1698.805432] DVB: registering adapter 2 frontend 0 (ITE 9135(9006) Generic_2)...
[ 1699.666551] DVB: registering adapter 0 frontend 0 (ITE 9135(9006) Generic_1)...
[ 1700.516487] DVB: registering adapter 2 frontend 0 (ITE 9135(9006) Generic_2).

when log in tvheadend:

[COLOR=#000000][FONT=courier]**2015-11-26 22:14:54.677 linuxdvb: adapter removed /dev/dvb/adapter0**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:54.681 linuxdvb: adapter removed /dev/dvb/adapter2**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:55.266 linuxdvb: adapter added /dev/dvb/adapter0**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:56.351 linuxdvb: adapter added /dev/dvb/adapter2**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:56.407 linuxdvb: adapter removed /dev/dvb/adapter0**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:56.413 linuxdvb: adapter removed /dev/dvb/adapter2**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:56.952 linuxdvb: adapter added /dev/dvb/adapter0**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier]**2015-11-26 22:14:57.883 linuxdvb: adapter added /dev/dvb/adapter2**[/FONT][/COLOR]
[COLOR=#000000][FONT=courier][B]2015-11-26 22:14:58.133 linuxdvb: adapter removed /dev/dvb/adapter0

[/B][/FONT][/COLOR]

Adapter 0 and 2 are adapters for dvb-t. 1 and 3 are assigned to dvb-s and they work fine.

As I mentioned before installing dvb-s dvb-t worked fine on adapter 0 and 1. But they don't seem to be in conflict now, different number are assigned to particular tuner.

Could you please advise how can I handle that?

Many thanks!

---

