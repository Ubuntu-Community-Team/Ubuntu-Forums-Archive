---
title: "Do 9700M/9800M NVIDIA (or latest ATI) drivers exist?"
date: 2008-08-13
forum: Hardware
---

### Post by kcy29581 on 2008-08-13
Hi all,

I am about to buy two laptops that have the NVIDIA 9700M GTS graphics card (I'm thinking about the  [Toshiba]("http://forum.notebookreview.com/autolink.php?id=178&script=showthread&forumid=1029") Qosmio F55). I will install Ubuntu on these machines and World of Warcraft as well.

However, after browsing NVIDIA's site, I cannot seem to find where to download the drivers for the NVIDIA 9M mobile graphics cards! After some googling I have found that ATI also have no drivers on their site for their latest mobile graphics cards, the Mobility 3000 series

Do these drivers exist at all? Is it not possible to get 3D graphics with the latest NVIDIA and ATI mobile graphics cards?

Thanks

---

### Post by sdennie on 2008-08-13
I don't know if the default Ubuntu drivers support those cards but, there usually isn't much lag time between a card release and nvidia releasing a driver that will work for it.  The latest stable drivers are: [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) and the latest beta drivers are: [http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html).  You may also want to ask or look at the nvidia linux forums to see if anyone has any experience with those cards: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

---

### Post by kcy29581 on 2008-08-13
> **vor said:**
> I don't know if the default Ubuntu drivers support those cards but, there usually isn't much lag time between a card release and nvidia releasing a driver that will work for it.  The latest stable drivers are: [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) and the latest beta drivers are: [http://www.nvidia.com/object/linux_display_ia32_177.13.html](http://www.nvidia.com/object/linux_display_ia32_177.13.html).  You may also want to ask or look at the nvidia linux forums to see if anyone has any experience with those cards: [http://www.nvnews.net/vbulletin/forumdisplay.php?f=14](http://www.nvnews.net/vbulletin/forumdisplay.php?f=14)

Those drivers are desktop GPU drivers, not laptop GPU drivers.

Also, [this knowledgebase article]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2085&p_created=1184686348&p_sid=JU3K3fbj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD01OTIsNTkyJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MQ**&p_li=&p_topview=1") does not inspire confidence that NVIDIA laptop drivers will be released again...

---

### Post by sdennie on 2008-08-13
> **kcy29581 said:**
> Those drivers are desktop GPU drivers, not laptop GPU drivers.

Also, [this knowledgebase article]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=2085&p_created=1184686348&p_sid=JU3K3fbj&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPSZwX3NvcnRfYnk9JnBfZ3JpZHNvcnQ9JnBfcm93X2NudD01OTIsNTkyJnBfcHJvZHM9JnBfY2F0cz0mcF9wdj0mcF9jdj0mcF9zZWFyY2hfdHlwZT1hbnN3ZXJzLnNlYXJjaF9ubCZwX3BhZ2U9MQ**&p_li=&p_topview=1") does not inspire confidence that NVIDIA laptop drivers will be released again...

I'm not sure where you are getting your information, but, those are unified drivers for nvidias entire product line.  I am running them right now with a laptop that has an 8400M GS and installed them last week on a desktop that has (I believe) a 7800GTX.

Although nvidia doesn't update its drivers as often as many people would like, they do update them and I assume that they will continue to do so to stay competitive in some of the markets that linux is heavily used in.

---

### Post by kcy29581 on 2008-08-13
> **vor said:**
> I'm not sure where you are getting your information, but, those are unified drivers for nvidias entire product line.  I am running them right now with a laptop that has an 8400M GS and installed them last week on a desktop that has (I believe) a 7800GTX.

Although nvidia doesn't update its drivers as often as many people would like, they do update them and I assume that they will continue to do so to stay competitive in some of the markets that linux is heavily used in.

Weird, when searching specifically for GeForce 8800M GTX drivers on the NVIDIA site, I get the link for the 169.12 drivers. But I see that the link you provided also supports the GeForce 8800M GTX. I apologise for assuming the drivers are different. Then hopefully the next driver update will include the latest mobile GPUs. :)

---

### Post by syberghost on 2008-12-31
Nvidia added drivers for this December 19th:

[http://www.nvidia.com/object/linux_display_ia32_180.17.html](http://www.nvidia.com/object/linux_display_ia32_180.17.html)

---

