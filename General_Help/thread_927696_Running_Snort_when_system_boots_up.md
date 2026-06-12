---
title: "Running Snort when system boots up"
date: 2008-09-23
forum: General Help
---

### Post by danuk88 on 2008-09-23
I have used the following tutorial to install Snort Mysql Base

[http://ubuntuforums.org/showthread.php?t=145641](http://ubuntuforums.org/showthread.php?t=145641)

when I re-boot I can put the following command in the terminal -

sudo snort -c /etc/snort/snort.conf

and snort will start with no problems but is there a way to get snort to start up automatic or do you have to issue the above command every time you boot up / re-boot?

I am using Ubuntu 8.04 LTS

Thank You

Dan

---

### Post by MoonPhoenix on 2008-10-01
I also have this problem.
Snort starts up fine when launched after boot by 'sudo service snort start'

Could it possibly be starting up and dying because my DHCP is not being allocated fast enough, or the interface has not come up yet.

I'm usually ok with debugging things, but not sure how to log its output at that stage of startup.

---

