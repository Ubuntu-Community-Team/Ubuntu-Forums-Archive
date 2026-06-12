---
title: "Is laptop mode fixed in 8.10 now?"
date: 2010-04-07
forum: Hardware
---

### Post by RFXCasey on 2010-04-07
Acer aspire 5100, I read about laptop mode issues remaining present from 8.04 to 8.10. I also found a proposed solution here [http://www.theusefulblog.com/post/ubuntu-hdparm-apm-and-laptop-mode-tools/](http://www.theusefulblog.com/post/ubuntu-hdparm-apm-and-laptop-mode-tools/) my 90-hdparm.sh files, all 3 or so of them are a little different then the one shown in the workaround method. Here's how mine look:

if [ -e /usr/sbin/laptop_mode ] ; then
   LMT_CONTROL_HD_POWERMGMT=$(. /etc/laptop-mode/laptop-mode.conf && echo "$CONTROL_HD_POWERMGMT")
   if [ "$LMT_CONTROL_HD_POWERMGMT" !=0 ] \
      && [ -e /var/run/laptop-mode-tools/enabled ]
   then
      #Laptop mode controls hdparm -B settings, we don't.
      DO_HDPARM=n

Seeing as this workaround previously mentioned was posted back in 2008, I was wondering if the issue had been fixed in a later update, hence the variation in my 90-hdparm.sh files or is there still an issue?

---

