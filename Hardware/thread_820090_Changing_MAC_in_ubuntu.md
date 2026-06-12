---
title: "Changing MAC in ubuntu"
date: 2008-06-05
forum: Hardware
---

### Post by heatblazer on 2008-06-05
I was about to ask how to do that operation but I`ve solved it, so I`ll post the solved problem for anyone who`ll need it.

sudo gedit /etc/rc.local

(enter the following in the empty space before exit 0 )

ifconfig eht1 hw ether YO:UR:MA:CH:ER:E!

Save and close, reboot. The next time your system reloads you`ll start with automatically changed MAC. Hope that was helpful!

---

