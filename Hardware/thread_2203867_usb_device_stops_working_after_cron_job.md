---
title: "usb device stops working after cron job"
date: 2014-02-05
forum: Hardware
---

### Post by Richard_Snepvanger on 2014-02-05
I'm using a USB cardreader for decoding DVB-C streams. The device is working correct, untill the hourly cron job is run. I have checked it several times. After the cron job the device can not be addressed with /dev/ttyUSB0. When the device is removed en reinserted, the issue is, temperarly, resolved.

The strange thing is that there are no hourly cron jobs configured?? I checked this with: run-parts -v --test /etc/cron.hourly/

Can anyone point me in the right direction? Thank you in advance!

syslog:
[FONT=&amp]Feb  4 21:17:01 homeserver CRON[13649]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  4 21:18:00 homeserver tvheadend[1007]: cwc: Can not descramble service "RTL 4 HD", access denied (seqno: 5630 Req delay: 2100 ms)
[snip] 
Feb  4 22:17:01 homeserver CRON[16322]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Feb  4 22:17:10 homeserver tvheadend[1007]: cwc: Can not descramble service "RTL 5 HD", access denied (seqno: 6968 Req delay: 2104 ms)

Ubuntu version:
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:        12.04
Codename:       precise
kernel:   Linux homeserver 3.8.0-35-generic #52~precise1-Ubuntu SMP Thu Jan 30 17:24:40 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



[/FONT]

---

