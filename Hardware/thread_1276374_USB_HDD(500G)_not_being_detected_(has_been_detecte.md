---
title: "USB HDD(500G) not being detected (has been detected before"
date: 2009-09-27
forum: Hardware
---

### Post by Phonic_P on 2009-09-27
Hi thanks for all the great work the UC do.
I have this problem with my USB HDD not being detected, it has been detected before as I formated it with the current software and have moved files to it. I used tail -f /var/log/syslog in term,

pp@Lightwave:~/Documents$ tail -f /var/log/syslog
Sep 27 14:38:56 Lightwave kernel: [ 2276.402415] usb 1-5: new high speed USB device using ehci_hcd and address 8
Sep 27 14:38:56 Lightwave kernel: [ 2276.560894] usb 1-5: configuration #1 chosen from 1 choice
Sep 27 14:38:56 Lightwave kernel: [ 2276.601800] scsi9 : SCSI emulation for USB Mass Storage devices
Sep 27 14:38:56 Lightwave kernel: [ 2276.624073] usb-storage: device found at 8
Sep 27 14:38:56 Lightwave kernel: [ 2276.624080] usb-storage: waiting for device to settle before scanning
Sep 27 14:39:01 Lightwave kernel: [ 2281.624256] usb-storage: device scan complete
Sep 27 14:39:01 Lightwave kernel: [ 2281.624966] scsi 9:0:0:0: Direct-Access                                    PQ: 0 ANSI: 2 CCS
Sep 27 14:39:01 Lightwave kernel: [ 2281.678944] sd 9:0:0:0: [sdb] Attached SCSI disk
Sep 27 14:39:01 Lightwave kernel: [ 2281.679055] sd 9:0:0:0: Attached scsi generic sg3 type 0
Sep 27 14:40:01 Lightwave /USR/SBIN/CRON[4427]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Sep 27 14:50:01 Lightwave /USR/SBIN/CRON[4638]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)

please help.
Marc

---

### Post by Phonic_P on 2009-09-27
Look's like my cry for help stired no interest from the community, was my enquiry to simple for snobs to answer, this happened last time too (under a different user name). I see that people whom have only posted minutes ago will get answers while others get nothing.
I fixed my own problem but still don't understand why this is so.
I right clicked on the device notifier on my panel & went to settings and selected input by clicking the button. then I put in a USB memory stick, it was detected, I then selected eject from the device notifier and pluged in my USB HDD... Presto detected.
I don't understand why it would not detect to start off with or how what I did made it work.
I hope this helps someone in the future who also got no response from the community.

---

