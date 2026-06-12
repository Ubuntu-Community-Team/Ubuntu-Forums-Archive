---
title: "USB not mounting,need help with dmesg understanding"
date: 2011-05-31
forum: Hardware
---

### Post by modulator-demodulator on 2011-05-31
```
[ 4795.540090] usb 1-1: new high speed USB device using ehci_hcd and address 6
[ 4796.100184] usb 1-1: device not accepting address 6, error -71
[ 4796.160243] hub 1-0:1.0: unable to enumerate USB device on port 1
[ 4798.908989] type=1400 audit(1306851889.702:2853): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=20857 comm="apparmor_parser"
[ 4798.910259] type=1400 audit(1306851889.712:2854): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=20857 comm="apparmor_parser"
[ 4798.917301] type=1400 audit(1306851889.712:2855): apparmor="DENIED" operation="file_mmap" parent=1 profile="/usr/sbin/cupsd" name="/usr/local/lib/libz.so.1.2.5" pid=20858 comm="cupsd" requested_mask="m" denied_mask="m" fsuid=0 ouid=0

```
That's what I've got after dmesg.
the point is I want to understand what these lines are about, not just fixing the problem.
It says "error  71". Where can I find list of the error numbers and theris explanations?
man dmesg? or something else?
Thanks.

---

### Post by jerrrys on 2011-05-31
found this

[http://www.google.com/search?client=ubuntu&channel=fs&q=error+71+linux&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=error+71+linux&ie=utf-8&oe=utf-8)

[http://www.google.com/search?client=ubuntu&channel=fs&q=usb+device+not+accepting+address+error+-17&ie=utf-8&oe=utf-8#hl=en&sugexp=ldymls&pq=usb%20device%20not%20accepting%20address&xhr=t&q=usb+device+not+accepting+address+linux&cp=34&pf=p&sclient=psy&client=ubuntu&channel=fs&source=hp&aq=0v&aqi=&aql=&oq=usb+device+not+accepting+address+l&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a34f7f1872f21971&biw=1024&bih=642](http://www.google.com/search?client=ubuntu&channel=fs&q=usb+device+not+accepting+address+error+-17&ie=utf-8&oe=utf-8#hl=en&sugexp=ldymls&pq=usb%20device%20not%20accepting%20address&xhr=t&q=usb+device+not+accepting+address+linux&cp=34&pf=p&sclient=psy&client=ubuntu&channel=fs&source=hp&aq=0v&aqi=&aql=&oq=usb+device+not+accepting+address+l&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=a34f7f1872f21971&biw=1024&bih=642)

---

