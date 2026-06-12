---
title: "HP Officejet 6500 Printer"
date: 2011-10-15
forum: Hardware
---

### Post by tb75252 on 2011-10-15
I am using **Ubuntu 11.10**, 32-bit, with **GNOME Classic** as my desktop environment.

I am trying to set up my printer which is an **H-P Officejet 6500**.  I go to **Applications -> System Tools -> System Settings** and select **Printers**.  Upon selecting the **Add New Printer** button, I get the following window:

[SIZE=2][B]     FirewallD is not running. Network printer detection
     needs services mdns, ipp, ipp-client and samba-client
     enabled on firewall.[/B][/SIZE]

I've been trying to find where this FirewallD is located and how to turn it on but I cannot find it anywhere.

Could somebody please give me a hand?  Thanks.

---

### Post by st_allis on 2011-10-16
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871985](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871985)

To add the printer log into another desktop environment, even Unity  works. Once the printer is added it will work in Gnome 3. But as far as I  know you can't do it in Gnome 3 itself.

---

### Post by tb75252 on 2011-10-18
> **st_allis said:**
> [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871985](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/871985)

To add the printer log into another desktop environment, even Unity  works. Once the printer is added it will work in Gnome 3. But as far as I  know you can't do it in Gnome 3 itself.
Thanks for your reply.  I ended up using CUPS by logging in to  [http://127.0.0.1:631]("http://127.0.0.1:631/") with my browser.  I was able to set up my printer that way.

---

