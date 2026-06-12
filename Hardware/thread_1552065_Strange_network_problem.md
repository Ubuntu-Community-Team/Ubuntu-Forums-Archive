---
title: "Strange network problem"
date: 2010-08-13
forum: Hardware
---

### Post by worik on 2010-08-13
I have struck a strange problem on my laptop running Ubuntu 10.04

My wireless connects but does not get an address.  From syslog...

Aug 13 15:56:21 emily NetworkManager: <info>    address 0.0.0.0

I have a static wired network and for a while it ran slow, but later I can access some sites no problem, and others not at all.  I can access my local network (I have two headless servers) and they work fine.

In the same room as me are two other laptops running windows that are connected perfectly through wireless and DHCP.

From those servers I can access all sites I cannot access from my laptop.

This morning it was all working perfectly.

I have tried shutting the machine down completely to no avail.

Later I got the wireless working by using a static address.  The
windows laptops here are using DHCP wireless, working perfectly.

I can access some websites:  google.com, telecom.co.nz, launchpad.net

I cannot access slashdot.org, bankdirect.co.nz, ihug.co.nz

The windows laptops in the room can access them.

My windows running in virtual box on my laptop can and cannot access the same sites I can access from the underlying ubuntu.  (Which is a relief)

I am very frustrated.

Worik

---

### Post by Fafler on 2010-08-13
What hardware are you using? Use lspci and post a complete list if you are unsure. What about using a wired network?

It sounds somewhat like the Broadcom card i had in my Dell Inspiron 6400. I changed it for a Intel 5100 i got of eBay for almost nothing.

---

### Post by worik on 2010-08-13
[QUOTE=Fafler;9714793]What hardware are you using? Use lspci and post a complete list if you are unsure. What about using a wired network?

10:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
30:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4357 (rev 10)

Both netwoks, wired and wireless have the same problems.

There are no iptables rules in force (iptables-save produces no output).

I can access some sites but not others, still, 12 hours later.

I can reach facebook.com, telecom.co.nz  but not slashdot.org and scoop.co.nz

I can and cannot ping them also, it is not a browser fault.

Worik

---

### Post by Iowan on 2010-08-13
[MTU]("http://ubuntuforums.org/showthread.php?t=1376506") has caused similar problems - though it's unlikely to change mid-day...
DNS server OK? (check /etc/resolv.conf)

---

### Post by worik on 2010-08-14
> **Iowan said:**
> [MTU]("http://ubuntuforums.org/showthread.php?t=1376506") has caused similar problems - though it's unlikely to change mid-day...
DNS server OK? (check /etc/resolv.conf)

Nothing I can see useful there.  The wierdest thing is I can access some but not all sites.  (I can access this one).

Whilst the windows laptops on the same network have no problems.

W

---

### Post by worik on 2010-08-14
> **worik said:**
> Nothing I can see useful there.  The wierdest thing is I can access some but not all sites.  (I can access this one).

Whilst the windows laptops on the same network have no problems.

W

It was my route.  Contained the line...

192.0.0.0       *               192.0.0.0       U     2      0        0 wlan0


I adjusted it in nm-connection-editor and the problem disappeared.  I have no idea how that route got in there and I have no idea why my DHCP stopped working in the first place. 

Once I changed the static routes I switched back to DHCP and there was no problem.

Worik

---

