---
title: "Problems after network config change"
date: 2008-09-04
forum: General Help
---

### Post by 5circles on 2008-09-04
I've been making pretty good progress after my latest install a few days ago (to create a single boot system with the entire disk for Ubuntu), but have just run into some odd problems.

I discovered that the network card was configured as DHCP rather than static as I'd intended.  I also changed the hostname.  And I edited /etc/hosts.

Now I'm unable to ping anything on the LAN from the Ubuntu box or vice versa - I'm getting destination host unreachable addresses.  It doesn't matter whether I ping by name or by IP address.  

The network settings look OK to me, but I'm pretty clueless on how to tackle the problem, so any ideas would be most appreciated.  I'm going to try returning to DHCP to see if static is the problem but that seems odd.

Is there a way to rebuild the network configuration from scratch easily?

The only other thing I can think of is a problem that I ran into a couple of months ago where I had to downgrade the driver for the Realtek NIC, but when I reinstalled Ubuntu the problem didn't show up so I assumed I was installing the latest (and fixed) drivers.

[Update - just returned to DHCP and it worked OK. Then tried redoing the changes one at a time.  The only problem was changing the domain name, but then when I changed that AFTER the host name it worked.  Maybe there was some conflict earlier, but I can't figure it out]

Thanks!
Mike

---

### Post by zvacet on 2008-09-04
After you choose between dhcp and static go to the DNS tab and put your nameservers there.After that go to the general tab and check the box on the left of your modem.

---

### Post by 5circles on 2008-09-04
The nameservers were already setup, and the connection enabled.  But thanks

---

