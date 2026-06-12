---
title: "Network Manager is not running"
date: 2009-06-23
forum: Hardware
---

### Post by cool_ubunt on 2009-06-23
Hi everyone,

I have a Dell XPS 1330 laptop with Ubuntu 9.0.4 version(latest) on it.
I am not able to connect any wireless network today.
Since yesterday it was running great till I did a stupid mistake of running that command:

**sudo chmod -x /usr/sbin/NetworkManager**

After that I got the new updates from update manager.

Previously I was using the kernel 2.6.28-11 and now my kernel version is 2.6.28-13.

Internet was working fine till I switched off my laptop. When I switched on it again, thats where the problem began.

I read lot of forums and tried the following commands:

sudo /etc/init.d/NetworkManager restart
sudo /etc/init.d/NetworkManager start
sudo /etc/init.d/NetworkManager status

but there is nothing happening. When I ran the command there is no output showing whether the command ran successfully or not.

When I click on the Signal Strength icon on the task bar it shows Network Manager is not running. 

Please help me on that issue. I have dual boot on my system so I have to use Windows now everything looks great but I only want to use one and only one UBUNTU.

Thanks for looking at my post.

---

### Post by lswb on 2009-06-23
Try running this command:

sudo chmod +x /usr/sbin/NetworkManager

That should restore proper execute permissions to NetworkManager. 

Then try the command:

sudo /etc/init.d/NetworkManager start

or just reboot your system.

---

### Post by cool_ubunt on 2009-06-23
Thanks dude. It really worked. 

I really appreciate it.

---

### Post by ken5 on 2009-07-09
Thanks lswb!!! this worked for me as well...

---

