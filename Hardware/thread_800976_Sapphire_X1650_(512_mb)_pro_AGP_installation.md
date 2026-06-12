---
title: "Sapphire X1650 (512 mb) pro AGP installation"
date: 2008-05-20
forum: Hardware
---

### Post by KUNI0 on 2008-05-20
After months i finaly installed my driver and all is working perfect(3d Acc, and those desktop effects).
If you just install the drivers from ati and reboot it will end with a black screen so:

Install ubuntu(8.04 tested) and dont update it ,just folow these steps.

1. go to Ati site and download x1600 radeon driver
2. open terminal and write>> "sudo sh "and drag the downloaded driver into the terminal ,hit enter and instal it.
3. write in terminal : sudo aticonfig --initial
4. write in terminal : sudo aticonfig --overlay-type=Xv
5. write in terminal : sudo aticonfig --resolution=0,1024x768
6. reboot
And done.

Donno if this exist,but more is better ,for those who dont know :)
_____________________
TEstED on Ubuntu 8.04

---

