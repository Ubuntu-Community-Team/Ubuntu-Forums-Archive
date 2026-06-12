---
title: "Ubuntu 13.04 + Acer Aspire Revo 3610 = problem"
date: 2013-07-03
forum: Hardware
---

### Post by 0911rdmitry on 2013-07-03
Hi,
I'm trying to install 13.04 from LiveCD on Revo 3610 (atom 330 1.6 GHz, nVidia ION, VGA, HDMI, 2GB RAM, 160GB HDD) The booting process starts and at the moment where GNOME interface should appear, the screen becomes black and video signal disappears. I tried x64 and x32 versions, changed VGA and HDMA outputs, changed monitors changed BIOS, nothing helps. The system is alive . I can blindly get into it with ctrl-alt-F2 and sudo reboot works just fine. lightdm restart or stop don't produce any effect. Only restart helps. In the mean time 12.04 and Cent OS 6.4 work just fine. 
The question is obvious: how to get rid of this problem?
I attached lspci -v and DSDT files. May be something's wrong in the configuration parameters? 
Thanks, Dmitry

---

