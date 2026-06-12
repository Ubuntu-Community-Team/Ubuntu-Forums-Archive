---
title: "Hardware monitor? HWiNFO32 equivalent?"
date: 2010-10-20
forum: Hardware
---

### Post by adummy on 2010-10-20
Is there a hardware monitoring utility similar to the HWiNFO32 in Windows that monitor and log hardware info such as CPU clock rate, CPU and hard drive temperature etc.? Thanks!

---

### Post by IcarusR on 2010-10-20
Not familiar with HWiNFO32 but I use the following to achieve what I believe you want.

Install 'lm-sensors' it's in the repositories.

To setup run the following in a terminal

```
sudo sensors-detect
```

Then to get info displayed on top Pannel

Right click on top pannel
Select "add to pannel"
High lite "hardware sensors mo0nitor"
Click "add"

Can also add "frequency scaling monitor" which will show cpu frequency

To see hdd temp install 'hddtemp' & can display on pannel as above.

GKrellM will also display this info, and alot more, in a different way...

[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html")

Hope this helps.

---

