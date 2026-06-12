---
title: "Nouveau to Nvidia - Which driver????"
date: 2024-03-24
forum: Hardware
---

### Post by LVDave on 2024-03-24
I'm on KUbuntu 22.04 and have an Nvidia Quadro K2200 video card. I'm currently on the
opensource Nvidia driver but need to switch to the proprietary driver. When firing up the
driver manager I'm presented with the following: 

[https://imgur.com/a/42hcFYL](https://imgur.com/a/42hcFYL)


The last time I paid much attention to needing the Nvidia driver via the driver manager
on Ubuntu, probably 16.04 or 18.04, there was like only two version choices. Now?
what a mess!!! What's the difference between a "server driver metapackage" and
a "driver metapackage"??

Help!!

Thanks!!

---

### Post by Yellow Pasque on 2024-03-24
They should all work, but most likely, you want the first option (nvidia-driver-535)

[https://devicetests.com/nvidia-server-driver-ubuntu-differences](https://devicetests.com/nvidia-server-driver-ubuntu-differences)

---

### Post by LVDave on 2024-03-24
Thank you for the link to the explaination of the differences..

---

### Post by MAFoElffen on 2024-03-24
That card is supported by NVidia through current (550).

With mine, I find that 535 is stable, 545 & 550 have some things to work through, but that is with mine. Yours may be different.

Honestly-- What I do, is I go to what the ubuntu system recommends, via either the top of Alternate Drivers app, or via 
```

sudo ubuntu-drivers list
sudo ubuntu-drivers autoinstall

```
And through trial and error, I try each until I find one that works 'best'. I can recommend what I use, but depending on the specific machine and specific GPU, that is the best way I've found.

---

