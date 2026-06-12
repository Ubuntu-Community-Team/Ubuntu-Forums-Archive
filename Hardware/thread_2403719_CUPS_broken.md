---
title: "CUPS broken"
date: 2018-10-15
forum: Hardware
---

### Post by agb32 on 2018-10-15
Hi,
At some point, my cups installation has become broken, and after a lot of digging around, I've no idea how to solve.  18.04.

I've tried things like purging all cups packages, dpkg, etc.

 systemctl status cups.service
&#9679; cups.service - CUPS Scheduler
   Loaded: loaded (/etc/systemd/system/cups.service; enabled; vendor preset: enabled)
   Active: failed (Result: timeout) since Mon 2018-10-15 15:53:33 BST; 26s ago
     Docs: man:cupsd(8)
  Process: 4652 ExecStart=/usr/sbin/cupsd -l (code=exited, status=0/SUCCESS)
 Main PID: 4652 (code=exited, status=0/SUCCESS)

Oct 15 15:52:03 xps13 systemd[1]: Starting CUPS Scheduler...
Oct 15 15:53:33 xps13 systemd[1]: cups.service: Start operation timed out. Terminating.
Oct 15 15:53:33 xps13 systemd[1]: cups.service: Failed with result 'timeout'.
Oct 15 15:53:33 xps13 systemd[1]: Failed to start CUPS Scheduler.




journalctl -xe:

Oct 15 15:52:03 xps13 systemd[1]: Starting CUPS Scheduler...
-- Subject: Unit cups.service has begun start-up
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit cups.service has begun starting up.
Oct 15 15:53:33 xps13 systemd[1]: cups.service: Start operation timed out. Terminating.
Oct 15 15:53:33 xps13 systemd[1]: cups.service: Failed with result 'timeout'.
Oct 15 15:53:33 xps13 systemd[1]: Failed to start CUPS Scheduler.
-- Subject: Unit cups.service has failed
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit cups.service has failed.
-- 
-- The result is RESULT.
Oct 15 15:53:33 xps13 polkitd(authority=local)[1070]: Unregistered Authentication Agent for unix-process:4606:174094 (system bus name :1.207, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)


If anyone can help, please let me know!

Thanks.

---

### Post by angelo16 on 2018-10-16
The same here... i thought it was the hplip update, but I remember that 3 days ago my system offered me to upgraded ubuntu to 18.04. Now I think the problem was the ubuntu upgrade.

---

### Post by braznyc on 2018-10-16
My Brother HL printer stopped working after I upgraded to Ubuntu 18.04. Is there any connection?

**Update: these 2 commands worked for my printer:**

sudo rmdir /usr/share/ghostscript/9.25/iccprofiles
sudo apt-get install --reinstall libgs9-common

---

### Post by krabelle on 2018-10-22
hi. solved my problem too. many users have this
Is it a bug relating to this package "libgs9-common" in general or more Ubuntu 18.04 bug?

Has someone add this to the Ubuntu-bugtracker?

---

