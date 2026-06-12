---
title: "Driver for Nvidia GL 710 (3D rendering)"
date: 2020-05-19
forum: Hardware
---

### Post by claus on 2020-05-19
Hi all,

I just purchased a new PC, and everything is running fine ( I installed 20.04 on it). The only problem is that I'm not sure which Nvidia driver I should use. I have a Nvidia GT 710 graphics card installed. Is it sufficient to use the 'nvidia-430' driver, or do I have to download a driver from the Nvidia website? I would like to do some 3D rendering with Blender 18.2.

Thanks,

Claus

---

### Post by Bashing-om on 2020-05-19
claus; Hello -

Welcome to ubuntu - Not Windows :P

We have an easy peasy method to install the proprietary driver.
Either GIUI: additional driver tool in the software updater
or
Terminal:
```

sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```
Where for the 710 card the system will choose the 440 version driver.

[INDENT][INDENT]my bit to try and help[/INDENT][/INDENT]

---

### Post by claus on 2020-05-20
Thanks!

Claus

---

### Post by Yellow Pasque on 2020-05-20
> **claus said:**
> Is it sufficient to use the 'nvidia-430' driver

Note: In Ubuntu 20.04, the nvidia-430 package simply installs nvidia-440 (i.e. it's a transitional package for people upgrading from earlier Ubuntu version).

---

### Post by mastablasta on 2020-05-22
isn't the 710 series in legacy driver?

---

### Post by CelticWarrior on 2020-05-22
> **mastablasta said:**
> isn't the 710 series in legacy driver?

Not yet: [https://www.nvidia.co.uk/Download/driverResults.aspx/159370/en-uk](https://www.nvidia.co.uk/Download/driverResults.aspx/159370/en-uk)

---

