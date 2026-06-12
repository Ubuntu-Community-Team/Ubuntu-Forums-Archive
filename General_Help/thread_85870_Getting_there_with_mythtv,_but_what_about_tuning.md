---
title: "Getting there with mythtv, but what about tuning?"
date: 2005-11-03
forum: General Help
---

### Post by f0rmula on 2005-11-03
I'm at the stage where I need to scan channels.  Is there a way to automatically do this (ala my windows machines gash hauppauge software)?

From what I can see tunig has to be done by using a special config file for my transmitter.  The SandyHeath transmitter is where I'm at, but this config file seems to be unparsable by 'scan'..  Anyone have any ideas?


root@sofa:/usr/share/doc/dvb-utils/examples # scan channels.conf-dvbt-sandy_heath channels.conf
scanning channels.conf-dvbt-sandy_heath
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot parse'BBC-Choice:641833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:620:621
'
ERROR: cannot parse'BBC-Knowledge:641833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:630:631
'
ERROR: cannot parse'BBC-News24:641833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:640:641
'
ERROR: cannot parse'BBC-1:641833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:600:601
'
ERROR: cannot parse'BBC-Parliament:641833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:0:660
'
ERROR: cannot parse'BBC-2:641833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:610:611
'
ERROR: cannot parse'ITV-1:665833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:513:651
'
ERROR: cannot parse'ITV-2:665833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:2819:2820
'
ERROR: cannot parse'C4:665833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:2823:2824
'
ERROR: cannot parse'E4:665833334:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:2831:2832
'
ERROR: cannot parse'C5:650166666:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:6017:6018
'
ERROR: cannot parse'Shop:650166666:INVERSION_OFF:BANDWIDTH_8_MHZ:FEC_2_3:FEC_NONE:QAM_64:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE:6049:6050
'
ERROR: initial tuning failed
dumping lists (0 services)
Done.


Thanks for any input :)

James

---

### Post by unprinted on 2007-04-24
Same here, but with Crystal Palace

It will do something with 

```
 scan  /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace

```

but it fails to actually tune into anything...

```
scanning /usr/share/doc/dvb-utils/examples/scan/dvb-t/uk-CrystalPalace
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 505833333 0 3 9 1 0 0 0
>>> tune to: 505833333:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE
WARNING: >>> tuning failed!!!
>>> tune to: 505833333:INVERSION_AUTO:BANDWIDTH_8_MHZ:FEC_3_4:FEC_AUTO:QAM_16:TRANSMISSION_MODE_2K:GUARD_INTERVAL_1_32:HIERARCHY_NONE (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

---

