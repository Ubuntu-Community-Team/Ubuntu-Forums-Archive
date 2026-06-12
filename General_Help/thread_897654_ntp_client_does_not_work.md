---
title: "ntp client does not work"
date: 2008-08-22
forum: General Help
---

### Post by joec22 on 2008-08-22
I use the same ntp server for every other device or server that I want to sync with and it works for those devices.  Adding this line to /etc/ntp.conf does nothing on my Ubuntu 8.04.  It constantly drifts and is driving me crazy.  /etc/init.d/ntp is running.

server 192.168.20.75


Does anyone have any ideas about what I can check to troubleshoot?
Thanks

---

### Post by LateNiteTV on 2008-08-22
apt-get install ntpdate
ntpdate serveraddress

---

### Post by joec22 on 2008-08-25
ntpdate works when I manually run it, but the drift puts the server out of sync so often that I can't cron a daily ntpdate job.  I tried putting ntpdate into the cron.hourly, but it doesn't work.  

why doesn't ntp work?

---

### Post by joec22 on 2008-08-26
I've come up with a work-around using crontab and ntpdate.  The catch since ubuntu likes sudo is you have to setup crontab as root.  Now I'm able to run ntpdate every hour.  Seems a little harsh, but I don't know what's wrong with ntp on 8.04 so this will have to do for now.

---

### Post by jigsaws on 2008-08-26
Is something in logs? (cat /var/log/messages | grep ntpd)

---

