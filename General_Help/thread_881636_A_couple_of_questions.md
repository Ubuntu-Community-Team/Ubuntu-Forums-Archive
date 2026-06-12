---
title: "A couple of questions"
date: 2008-08-06
forum: General Help
---

### Post by /////// on 2008-08-06
I want an NTFS partition to be automatically mounted as soon as the system starts up. How do I do this?

Also is there anyway to get Ubuntu to do something at a particular time? Say I wanted to load Pidgin or something at 1AM in the morning how do I get Ubuntu to load it for me? Is there anything like the windows 'at' command which I can utilize in Ubuntu or is there a GUI for this?

---

### Post by hermes0710 on 2008-08-06
For the first question, yes you can do it. You must edit your /etc/fstab file and in the column next to the partition's type add the option "auto". Values are comma separated.

For the second one check these:

[http://www.willmaster.com/library/web-development/Scheduling_with_Cron.php]("http://www.willmaster.com/library/web-development/Scheduling_with_Cron.php")

[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/3877-cron-tutorial-cron-linux-event-scheduler.html]("http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/3877-cron-tutorial-cron-linux-event-scheduler.html")

---

### Post by kpkeerthi on 2008-08-06
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)
[https://help.ubuntu.com/community/CronHowto](https://help.ubuntu.com/community/CronHowto)

---

