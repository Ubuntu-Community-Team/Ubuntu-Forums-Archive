---
title: "Nvidia (Surround) Xinerama ON &amp; OFF Scripts"
date: 2018-08-25
forum: Hardware
---

### Post by BigBig5 on 2018-08-25
I got Nivida Xinerama working on Ubuntu with LightDM. I made two simple scripts that turns Xinerama on and off.

ON
```
#!/bin/bash
#Xinerama on
sudo sed -i 's/"Xinerama" "0"/"Xinerama" "1"/g' /etc/X11/xorg.conf
#lightdm restart
sudo service lightdm restart
```

OFF
```
#!/bin/bash
#Xinerama off
sudo sed -i 's/"Xinerama" "1"/"Xinerama" "0"/g' /etc/X11/xorg.conf
#lightdm restart
sudo service lightdm restart
```

---

