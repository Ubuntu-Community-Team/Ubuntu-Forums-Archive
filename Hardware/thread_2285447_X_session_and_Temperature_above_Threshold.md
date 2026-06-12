---
title: "X session and Temperature above Threshold"
date: 2015-07-06
forum: Hardware
---

### Post by ganesh11 on 2015-07-06
[FONT=&quot]We are using Ubuntu 10.4 & 14.04 and getting error of X session and Temperature above threshold & CPU clock Throttled on Intel core i3 2100t/Chipset Q67 Fanless Industrial Embedded PC. we are Video Application (Traffic Signal Video Camera Data) on it .What will be the cause to getting this error and [/FONT]

  [FONT=&quot] [/FONT]
  [FONT=&quot]Why “( root ) cmd (rm.rf / root / .xsession-errors*” this error is coming?[/FONT]
  [FONT=&quot]OS is UBUNTU 10.04 or 14 64 BIT, does this error will halt CPU”[/FONT]
  [FONT=&quot] [/FONT]

---

### Post by dino99 on 2015-07-06
note: 10.04 is no more maintained since a while; so its vulnerable now & you should use an active release instead
as its an embedded pc, pay attention to let some fresh air to the mobo/chipsets; maybe remove dust and everything blocking the air in/out flow

---

### Post by Yellow Pasque on 2015-07-06
> Why &#8220;( root ) cmd (rm.rf / root / .xsession-errors*&#8221; this error is coming?
You or someone else has a cron job set to delete /root/.xsession-errors every two minutes. I don't think it is a standard cron job. I can only speculate that something was/is "spamming" the .xsession-errors file, causing its size to grow rapidly, so someone worked around the problem by creating a cron job to delete the file every two minutes.

---

### Post by ganesh11 on 2015-07-06
HI , THANKS

SO HOW TO  cron job set to delete /root/.xsession-errors

[HR][/HR]

---

### Post by Yellow Pasque on 2015-07-06
Not sure what you're asking?? Look for the cronjob that is causing those messages:
```
cd /etc
ls cron*
cat crontab
```

---

### Post by ganesh11 on 2015-07-06
Thanks,

we are accessing remotely pc through (ultra vnc) lan for  video data monitoring, so as per your suggestion we have to set default cronjob. And why cpu temp shows threshold may be due this.

---

