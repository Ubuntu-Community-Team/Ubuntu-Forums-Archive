---
title: "USB suddenly dies"
date: 2008-08-25
forum: General Help
---

### Post by TheTank on 2008-08-25
Hello All.
I am hoping you all might be able to help me with a weird problem I am having with my USB devices.

The problem is that they just suddenly die on me. All at once.
When this happens and I am on the pc (it happened once right in the middle of surfing) all the lights flashed up and then died.

Sometimes I have the feeling it has something to do with Firefox (more exact when I am watching videos on tube) but I find that a little far fetched.

Anyone have any ideas?

---

### Post by Sycron on 2008-08-25
It may be from your motherboard. Did this happen on other OS ?

---

### Post by TheTank on 2008-08-25
> **Sycron said:**
> It may be from your motherboard. Did this happen on other OS ?
I hardly ever use anything else any more and when I last did, about 2-3 months ago, I noticed nothing.

---

### Post by Sycron on 2008-08-26
> **TheTank said:**
> I hardly ever use anything else any more and when I last did, about 2-3 months ago, I noticed nothing.

It is strange them, very.

---

### Post by TheTank on 2008-09-15
Well I can confirm that it was not my system as I now have a new one and also have the same problems.

Today 'only' my two external drives and my wlan usb dongle died.

syslog contains these:
```

Sep 15 23:25:55 mypc kernel: [ 7537.109989] rt73: - BBP write: Retry count exhausted or device removed!!!
...
Sep 15 23:26:27 mypc kernel: [ 7562.356599] usb 6-3: reset high speed USB device using ehci_hcd and address 4
...
Sep 15 23:26:42 mypc kernel: [ 7573.251165] usb 6-3: device descriptor read/64, error -110
...
Sep 15 23:27:49 mypc kernel: [ 7612.700182] usb 6-3: USB disconnect, address 4
Sep 15 23:27:49 mypc kernel: [ 7612.700500] sd 4:0:0:0: Device offlined - not ready after error recovery
Sep 15 23:27:49 mypc kernel: [ 7612.703049] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Sep 15 23:27:49 mypc kernel: [ 7612.703053] end_request: I/O error, dev sdb, sector 369445033

```

---

### Post by TheTank on 2008-11-21
Changed my mouse from USB to PS2 via adapter as I feared it could just be a case of too many devices at once, but again it happend.

Anyone have any ideas?

Still running 8.04 btw.

Edit:
I looked into the various syslog files and did notice something strange:
All the problems started happening shortly after a cron job!
```

Nov 21 19:56:09 mainframe anacron[6447]: Job `cron.daily' started
Nov 21 19:56:09 mainframe anacron[8979]: Updated timestamp for job `cron.daily' to 2008-11-21
Nov 21 20:03:24 mainframe kernel: [  593.434529] rt73: - BBP write: Retry count exhausted or device removed!!!

Nov  1 20:17:01 mainframe /USR/SBIN/CRON[17019]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  1 20:17:42 mainframe kernel: [ 1270.025922] rt73: - BBP write: Retry count exhausted or device removed!!!

Nov 11 20:09:01 mainframe /USR/SBIN/CRON[13544]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -type f -cmin +$(/usr/lib/php5/maxlifetime) -print0 | xargs -r -0 rm)
Nov 11 20:11:52 mainframe kernel: [  714.071039] rt73: - BBP write: Retry count exhausted or device removed!!!

```

---

