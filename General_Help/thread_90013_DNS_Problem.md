---
title: "DNS Problem"
date: 2005-11-14
forum: General Help
---

### Post by Thanatos Silentes on 2005-11-14
I have a bad router that returns bad IP addresses when it get DNS requests, so I want to bypass it on my kubuntu machine, and go directly to my ISP DNS.  I change them, and they seem to work, but when I reset my machine, the DNS are reset to my router.  How can I stop this from happening?  I use DHCP.  I have tried changing it from the control center, and also from resolv.conf.  They both do the same thing.  Can anyone help?

---

### Post by adwait on 2005-11-14
Try installing resolvconf
```
sudo apt-get install resolvconf
```

Edit the /etc/resolvconf/resolv.conf.d/original file to reflect the correct DNS servers.

---

### Post by Thanatos Silentes on 2005-11-14
Ok, I tried that out - It doesn't change /etc/resolvconf/resolv.conf.d/original back, but when I go into /etc/resolv.conf or into the control center, it still says the DNS is my router.

---

### Post by adwait on 2005-11-14
That's odd..........after you install resolvconf, the resolv.conf file is supposed to be a symlink to the /etc/resolvconf/resolv.conf.d/original file. Try making a manual link. Rename the /etc/resolv.conf file to something else. and then execute:
```
sudo ln /etc/resolvconf/resolv.conf.d/original /etc/resolv.conf
```

---

### Post by Thanatos Silentes on 2005-11-14
Yes, that worked.  Thanks a lot.

---

