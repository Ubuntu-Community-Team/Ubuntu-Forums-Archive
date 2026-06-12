---
title: "eeepc 701 eeebuntu &quot;unable to mount...superuser&quot; 4g sd  ---gparted mounted it but..."
date: 2008-12-07
forum: Hardware
---

### Post by Jaymeister on 2008-12-07
eeepc 701 eeebuntu
 "unable to mount...superuser" 4g sd

tried this...
 ( [http://www.eeepc.it/en/ubuntu-eee-8041-supporto-completo-per-leeepc/](http://www.eeepc.it/en/ubuntu-eee-8041-supporto-completo-per-leeepc/) )
from terminal...
sudo mkdir /media/MMCSD
sudo gedit /etc/fstab
...overwrote last line with...
/dev/sdb1 /media/MMCSD auto user,auto,exec,rw 0 0
...saved reboot reinsert card - same problem

...so i installed gparted from terminal...
sudo apt-get install gparted
sudo gparted
...selected sd card from drop down list on top right
...right clicked the partition on list
...selected mount to 
...selected /media/MMCSD

WORKED! except its mounted as root - for my user read only
...im almost there...

---

### Post by Jaymeister on 2008-12-07
gksudo nautilus
...get to media folder
...right click on MMCSD
...select properties

change permissions to read write
click OK

...didn't work
but at least i can cut from desktop and paste using nautilus to sd card

there has to be another way!
any ideas?

---

