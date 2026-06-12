---
title: "wireless problem  sit0: unknown hardware address type 776"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by caitanya on 2006-03-29
So this is the scenario:

I have a wireless D-Link DWL-G520 card on my desktop.  My AP is a D-Link 2100AP. And my dhcp server is on a windows 2003 server.

The desktop can see the card, and I can configure it fine, but I don't have any network access.

The AP has an open system with encryption enabled.

I have tried setting the AP with no encryption and as the dhcp server but still no luck.

when I run ifup on the interface I get
"sit0: unknown hardware address type 776"

Help please!

---

### Post by caitanya on 2006-03-29
Fixed!

I had to run dhclient

---

