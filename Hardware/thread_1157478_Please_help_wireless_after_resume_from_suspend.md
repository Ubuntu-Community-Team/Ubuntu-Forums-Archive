---
title: "Please help: wireless after resume from suspend"
date: 2009-05-12
forum: Hardware
---

### Post by cartes on 2009-05-12
Can anyone help me to get my wireless light to come back on after suspend? 

I have a Fujitsu Amilo Pro V2000 but the special button to turn the wireless radio on and off doesn't work with Ubuntu 9.04. The following worked to turn wireless on at startup but after resume from suspend no wireless so I have to restart the laptop:

edit /etc/modules and add: fsam7400 on a new line;
created /etc/modprobe.d/options with the line: options fsam7400 radio=1

Any help would be appreciated.

---

