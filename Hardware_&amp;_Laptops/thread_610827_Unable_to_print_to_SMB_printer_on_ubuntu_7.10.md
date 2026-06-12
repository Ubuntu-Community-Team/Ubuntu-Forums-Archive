---
title: "Unable to print to SMB printer on ubuntu 7.10"
date: 2007-11-12
forum: Hardware &amp; Laptops
---

### Post by leifwi on 2007-11-12
When I try to print a test page, the following lines are shown in error log (var/log/cups)

E [12/Nov/2007:18:21:28 +0200] [Job 8] No ticket cache found for userid=1000
E [12/Nov/2007:18:21:28 +0200] [Job 8] Can not get the ticket cache for xxxxxx
E [12/Nov/2007:18:21:28 +0200] [Job 8] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [12/Nov/2007:18:21:29 +0200] [Job 8] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [12/Nov/2007:18:21:29 +0200] [Job 8] Unable to connect to CIFS host, will retry in 60 seconds...

What can I do to fix this?

---

### Post by leifwi on 2007-11-17
Retyped my username and password again in the printer configuration tool, and it works. Must have been a typing error in the password.

---

### Post by steveneddy on 2007-11-17
Can we mark this as SOLVED?

---

### Post by leifwi on 2007-11-18
Yes this is solved.

---

