---
title: "Best/easiest way to mount NAS windows shares on 9.10?"
date: 2009-11-18
forum: Hardware
---

### Post by Shemp on 2009-11-18
Not sure exactly where to post this but:

I've played with Ubuntu over the years so I'm not a complete novice, but in researching this issue on the net there seems to be many different opinions on how to accomplish this.

I just installed 9.10 on my Inspiron 1520 & everything is fine. My main PC is a desktop running Windows 7 Home Premium & for storage I have a Dlink DNS-323. I believe both are in a Win 7 workgroup, but as I understand it, this only matters to other Win 7 PC's. The dns-323's firmware is 1.07 & other than running Tonkymedia is stock. The Ubuntu install on my laptop is up to date. My second desktop & my laptop – both running 9.10 can see the DNS-323 & it's files fine while the Win 7 PC is running, but not at all if its off. Everything is DHCP from my router.

Is there an “official” way or whats the easiest way to automatically mount the windows shares on start up & not have the Win 7 PC running? All I've been able to garner points to installing some form of Samba, I assume on the DNS, but I thought it already had some type of Samba on it.

This is a major sticking point for me.

Thanks!

Shemp

---

### Post by Boondoklife on 2009-11-18
Check and see if you can install an mDNS server on the NAS, if you can then just put in an entry for its smb share and it should be fine. I see this from time to time and it is generally a samba config problem or maybe a firewall/netfilter issue some where.

---

