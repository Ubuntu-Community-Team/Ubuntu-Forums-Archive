---
title: "Xubuntu 8.04 on LG C1"
date: 2008-03-15
forum: Hardware &amp; Laptops
---

### Post by oc666 on 2008-03-15
Hello everyone
I just upgrade my LG C1 to Xubuntu 8.04 Alpha with the command:[PHP]update-manager -d[/PHP]
First of all, I fix already bug on the iwl3945 new driver, which didn't work in the first place. I create the file /etc/modprobe.d/iwl3945 with the next content:
[PHP]alias wlan0 iwl3945
options iwl3945 disable_hw_scan=1
[/PHP]
Here is a [link]("http://www.ces.clemson.edu/linux/f8-nm-iwl3945.shtml") where I heard about this patch.
Now, I have few little bit problems:
1. The leds of the wireless doesn't work. I read about people know about this problem, but I didn't found a patch for this.
2. My battery monitor of xfce4-battery-plugin doesn't work well with bad estimation or without estimation at all.

---

