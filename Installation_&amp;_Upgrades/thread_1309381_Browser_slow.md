---
title: "Browser slow"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by willisfang on 2009-11-01
fresh 9.10 install.

i notice that the firefox takes 2-3 seconds to do "look up ..address.." every time I click on something or open a new link. Almost like something wrong with my ISP's DNS is down or something. This never happened with 9.04. This makes browsing internet a lot slower than before. 

Anyone notice that?

(thanks for the following post)

disable ipv6 fixed it:

1. type about:config in address
2. filter by ipv6
3. find network.dns.disableIPv6, toggle it to be true.

restart and fast like light

---

### Post by kerry_s on 2009-11-01
did you disable ipv6 in firefox?

---

### Post by lovinglinux on 2009-11-01
The previous poster is probably right.

See **Solution** [*[COLOR="Red"]**FOT005**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT005).

---

