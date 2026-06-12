---
title: "GNOME not loading on bootup"
date: 2006-09-10
forum: Hardware &amp; Laptops
---

### Post by nits_555 on 2006-09-10
Hi All,

I installed ltsp from the [www.ltsp.org](www.ltsp.org) site (all packages). Then I went on to activate eth0 (ethernet port) on my laptop. ltsp could not configure my DHCP as the dhcpd package was absent. So I installed the dhcpd package. After this I tried using "ltspconfig" to reconfigure DHCP and it created a file dhcpd.conf

I rebooted ubuntu and since then, it only boots in "command prompt" mode (nitin@ubuntu). I even tried the recovery mode and it still boots in "command prompt" (root@ubuntu).

I am wondering if there is anyway to get ubuntu to start in GUI-mode. I have no clue what could have gone wrong. Any ideas on how to debug this problem will really be appreciated.

Thanking you in advance,
Nitin.

---

### Post by smelly_sox on 2006-09-10
After bootup, log in as root at your terminal
*nano /etc/inittab* (nano is a text editor)
A couple of lines down should look like:

[I]# The default runlevel.
id:2:initdefault:[/I]

Number needs to be 2 for graphical multiuser boot, i.e. gdm & gnome
*crtl + x* to exit and save (exit nano)

Regards

---

