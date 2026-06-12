---
title: "Ubuntu 12.04 and 3 monitors with 2 nvidia quadro fx4600 cards"
date: 2013-01-08
forum: Hardware
---

### Post by bshosey on 2013-01-08
I have a Dell Precision T3400 with 2 Nvidia Quatro FX4600 video cards. I have read that both the system and the cards support this. I am trying to do this so I can have 3-4 montitors. I can not get SLI-Mosaic to enable. I have an SLI bridge on the cards. I have tride the following command

```
sudo nvidia-xconfig --multigpu=on --base-mosaic --metamodes="GPU-0.DFP-0: 1440x900+0+0, GPU-0.DFP-1: 1440x900+1440+0, GPU-1.DFP-0: 1440x900+2880+0 GPU-1.DFP-1: 1440x900+4320+0"
```

Does any one know how to get SLI-Mosaic to work with this system?
I can get 3 monitors with xirama but we all no no 3d ecceleration.

Any help would be appriciated. Thanks

---

