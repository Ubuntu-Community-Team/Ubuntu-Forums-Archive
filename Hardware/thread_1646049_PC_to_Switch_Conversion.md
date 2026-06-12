---
title: "PC to Switch Conversion"
date: 2010-12-15
forum: Hardware
---

### Post by zmiller965 on 2010-12-15
Hey guys, I recently had a little trouble with hacking on my desktop PC at home, and as a Telecom/Information Security Professional, this is fairly embarrassing to admit :(

However, I reacted quickly and took care of it, but my security vulnerability still bothers me. Basically what I want to do is take an old Pentium core desktop and run a Linux distro (I am more comfortable with Ubuntu, but will settle for any, really) on it as a switch between my modem (from ISP) and my wireless router (personal). The plan was to use a dual NIC and put it between those two physically, and run SNORT as a IDS/IPS, detecting malicious traffic coming in and detecting/preventing certain egress traffic (at my specifications, which I can handle).

My real problem is, I'm not perfectly sure how to go about configuring the linux box to push any and all traffic straight through it. The IPS will kill any traffic I want it to, so I don't need to configure the IP tables/firewall on the box I don't think, but I do need it to simply forward all IP traffic.

Can anyone help? Sorry for the long post. (Also, I have a decent knowledge of Unix/Linux, but you'll probably have to bear with me and elaborate a little on anything very complex)

Thanks gang.

-Z

---

### Post by zmiller965 on 2010-12-15
Actually, nevermind, I believe I've worked it out on my own, if anyone is interested, I'd be happy to detail the process (I'm at work right now, but maybe I'll post it when I get back)

---

