---
title: "Samsung 850 EVO SSDs still blacklisted?"
date: 2016-08-20
forum: Hardware
---

### Post by tys3 on 2016-08-20
I remember reading that Samsung 850 EVO SSDs were blacklisted due to issues with TRIM a while ago and that a fixed was found. How can I find out if I currently have the fix, or if TRIM is functioning as intended? I've got Xubuntu 16.04 on a 850 EVO SSD that I have been using the past few months (without any issues) and just want to make sure that my SSD is optimised and running properly. Thanks.

---

### Post by tys3 on 2016-08-25
From [https://github.com/torvalds/linux/blob/master/drivers/ata/libata-core.c ]("https://github.com/torvalds/linux/blob/master/drivers/ata/libata-core.c")

Update: It looks like it is still blacklisted. I thought this issue was fixed (unless I'm reading the code wrong)??

```
/* devices that don't properly handle queued TRIM commands */
    { "Micron_M500_*",        NULL,    ATA_HORKAGE_NO_NCQ_TRIM |
                        ATA_HORKAGE_ZERO_AFTER_TRIM, },
    { "Crucial_CT*M500*",        NULL,    ATA_HORKAGE_NO_NCQ_TRIM |
                        ATA_HORKAGE_ZERO_AFTER_TRIM, },
    { "Micron_M5[15]0_*",        "MU01",    ATA_HORKAGE_NO_NCQ_TRIM |
                        ATA_HORKAGE_ZERO_AFTER_TRIM, },
    { "Crucial_CT*M550*",        "MU01",    ATA_HORKAGE_NO_NCQ_TRIM |
                        ATA_HORKAGE_ZERO_AFTER_TRIM, },
    { "Crucial_CT*MX100*",        "MU01",    ATA_HORKAGE_NO_NCQ_TRIM |
                        ATA_HORKAGE_ZERO_AFTER_TRIM, },
    { **"Samsung SSD 8*"**,        NULL,    ATA_HORKAGE_NO_NCQ_TRIM |
                        ATA_HORKAGE_ZERO_AFTER_TRIM, },
    { "FCCT*M500*",            NULL,    ATA_HORKAGE_NO_NCQ_TRIM |
ATA_HORKAGE_ZERO_AFTER_TRIM, },
```

---

### Post by QIII on 2016-08-25
The blacklist keeps them from attempting NCQ operations (queued commands) such as queued trim.

You can still issue the TRIM command as normal.  I'd recommend against using the "discard" option in fstab.

---

### Post by dannytaki on 2016-08-25
What are TRIM commands?  I just bought the 850 EVO and installed ubuntu on it, wanting to use it.  What's wrong with it?

---

### Post by Bucky Ball on 2016-08-25
I've had one running in my laptop for about two years and no problems to this point. I haven't done anything. Maybe I should before it all come crashing down around me! :-k

---

### Post by Dennis N on 2016-08-25
> **dannytaki said:**
> ...I just bought the 850 EVO and installed ubuntu on it, wanting to use it.  What's wrong with it?

I think it's a good drive. I have one in use since Nov 2015 with no problems. It does have the 'discard' option enabled in its mount entries in /etc/fstab. Those were put there by the installer:

```
UUID=5ab00007-48ec-4aea-8e5f-089ea9defd58 /  ext4    defaults,noatime,discard  0       1
```

---

### Post by QIII on 2016-08-25
My primary machine runs on an 850.

---

### Post by oldfred on 2016-08-25
[https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard)

But I created my own daily trim with log file as per this:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

---

### Post by howefield on 2016-08-25
> **Bucky Ball said:**
> I've had one running in my laptop for about two years and no problems to this point. ..

Probably the Auto Garbage Collection Algorithm that is keeping it in trim...no pun intended :)

---

### Post by tys3 on 2016-08-26
> **QIII said:**
> The blacklist keeps them from attempting NCQ operations (queued commands) such as queued trim.

You can still issue the TRIM command as normal.  I'd recommend against using the "discard" option in fstab.

So it should still be okay to run the TRIM command manually?

> **oldfred said:**
> [https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard](https://sites.google.com/site/easylinuxtipsproject/ssd#TOC-Not-advised:-by-discard)

But I created my own daily trim with log file as per this:
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

Thanks for the links. I'll look into how to use cron to automate TRIM daily on the SSD.

---

