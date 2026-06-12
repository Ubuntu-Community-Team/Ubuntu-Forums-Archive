---
title: "Wireless BCM4322 kernel panic"
date: 2009-03-04
forum: Hardware
---

### Post by urbn on 2009-03-04
Hi folks.

I was able too find a work around for this issue a few weeks ago and have spent the last several hours trying too find it again.

Basically the issue is with the wireless card broadcom BCM4322 causing kernel panic's.  For me the card works fine until I connect using my VPN (Kvpnc).  After connecting too the vpn the system will run for a few minutes until a kernel panic occurs.

I am using the Broadcom STA proprietary drivers now but I thought the fix was too use different drivers?

So too clarify
Wireless works until using the VPN
VPN works with wired network
I know there was a fix though apt-get I just can't remember what it was.
I am pretty sure the fix was related too using different wireless drivers

Thanks for the help in advance!

---

### Post by urbn on 2009-03-05
No one has experienced this problem or know how too resolve this issue?

---

### Post by iceman_ch on 2009-03-05
Do a search on installing ndiswrapper.  I was having problems connecting to encrypted networks and this fixed my problem.  I'm not sure if it will fix yours or not but because everything works when you plug in to the network I would assume it was the drivers for the wireless card that need tweaking.

---

