---
title: "Browsing in 8.10"
date: 2008-11-29
forum: General Help
---

### Post by 98springer on 2008-11-29
Forgive me if this has been covered but I can't find it.
I installed 8.10 on my laptop and I got past the wireless problems so I'm pretty pleased so far. The only remaining issue is that I can't connect to another (CentOS) computer via Connect to Server" in "Places". I'm able to do this with 2 other computers running 8.04. With them I can connect via the command line ssh and by going to "Connect to Server", selecting SSH and entering the IP and username. I'm prompted for a password and a browser window opens displaying the folders on the CentOS computer.
On the laptop I can connect via the command line ssh command but not by using "Connect to Server". I get a message stating "Cannot display location "sftp://root@xxx.xxx.xxx.xxx/". Timed out when logging in." This happens whether I use wired or wireless. The laptop uses DHCP and the others have static IPs.
Thanks in advance.

---

### Post by 98springer on 2008-11-29
Aha!!!
If I create an entry for the server in the laptop /etc/hosts, I can connect using the remote computer hostname or IP. Couldn't do either before.

---

