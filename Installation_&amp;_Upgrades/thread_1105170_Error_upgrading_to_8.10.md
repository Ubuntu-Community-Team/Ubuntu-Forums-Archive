---
title: "Error upgrading to 8.10"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by luckymoonboy1 on 2009-03-24
Ok, i tried to upgrade my computer from 8.4.1 to 8.10 using the alternate CD. I put the disk in and it asked me if i would like to apply the upgrade. i clicked upgrade now and it went threw the process of upgrading then restarted. now i try to login and this happens on both my account and the guest account:

  Your session only lasted less than 10 seconds. If you have not logged out yourself, his could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the failsafe sessions to see if you can fix this problem.
Veiw details (-/.xsession-errors file)
/etc/gdm/xsession: Begining session setup...
Seting IM through im-switch fo locale=en US.
Start IM through /etc/x11/xinit/xinput.d/all_All Linked to /etc/x11/xinit/xinput.d/default.
Couldn't exec /usr/bin/pulse-session: No such file or directory


I really need to fix this this is the only decent computer i own, i will welcome any help possible.

---

### Post by cariboo on 2009-03-24
Did you make sure Hardy was completely upgraded and all ppa's were removed or commented out in your /etc/apt/sources list? I would suggest you start in recovery mode and at the prompt type:

```
dhclient eth0
```

to get networking started, substitute your network device for eth0, then at the prompt type:

```
apt-get install -f
```

to install missing dependencies, then type:

```
apt-get update && apt-get dist-upgrade
```

Jim

---

### Post by luckymoonboy1 on 2009-03-25
I guess i didn't mention this. there is no network for this computer.

---

### Post by luckymoonboy1 on 2009-03-25
Is there a way to reinstall the operating system from the alternate cd using the command prompt and not deleting the hard drive so that i can keep all of my files?

---

