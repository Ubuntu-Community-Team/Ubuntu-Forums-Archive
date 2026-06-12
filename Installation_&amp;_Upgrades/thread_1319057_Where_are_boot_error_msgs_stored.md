---
title: "Where are boot error msgs stored?"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by irishbreakfast on 2009-11-08
When booting, I get some error messages on the splash screen that don't stay around long enough for me to read. I've greped in /var/log but can't find the same text.

Can anyone tell me where those error messages are stored so I can read them?

---

### Post by PRR on 2009-11-08
try /var/log/dmesg

---

### Post by irishbreakfast on 2009-11-08
I have tried "grep <some text that I was able to read> /var/log/*" and found nothing quite right.

I should add that what I can read has to do with difficulties with mounting at least two of my partitions.

---

### Post by irishbreakfast on 2009-11-08
Sorry, I made a mistake (that's what I get for staying up past midnight)

Rereading I found the following, which is repeated for every partition, in messages.1 and user.log.1. These are not exactly the message displayed on screen during a reboot but it fits as what I can read is about 'waiting' and partitions.

So, why is all this debugging going on? I have not seen this before with 8.04 or 9.04. The only difference is that during the clean install on 9.10 I changed all partitions (except Vista's) to ext3. And I just searchd the forums for os-proeber and got a lot of threads for "Foundation Team" but nothing that explains why this is happening.

Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/10freedos on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil 10freedos: debug: /dev/sda5 is not a FAT partition: exiting
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/10qnx on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil 10qnx: debug: /dev/sda5 is not a QNX4 partition: exiting
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/20macosx on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil macosx-prober: debug: /dev/sda5 is not an HFS+ partition: exiting
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/20microsoft on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil 20microsoft: debug: /dev/sda5 is not a MS partition: exiting
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/30utility on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil 30utility: debug: /dev/sda5 is not a FAT partition: exiting
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/40lsb on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/70hurd on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/80minix on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/90linux-distro on mounted /dev/sda5
Nov  6 01:20:24 MinasIthil os-prober: debug: running /usr/lib/os-probes/mounted/90solaris on mounted /dev/sda

---

### Post by irishbreakfast on 2009-11-08
I restarted this with a better title 
Hope that is OK

---

