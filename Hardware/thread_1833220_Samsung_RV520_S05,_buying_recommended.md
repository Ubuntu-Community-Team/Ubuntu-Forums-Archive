---
title: "Samsung RV520 S05, buying recommended?"
date: 2011-08-25
forum: Hardware
---

### Post by Kiesel on 2011-08-25
Hi,

im thinking about buying the samsung rv520 S05. My concern is the NVIDIA GT 520M, which is an Optimus Card. Does anybody know whether that is a proble on this laptop? i.e. is it possible to switch it off? I do not plan on doing anything that needs the GPU.

Thanks for all answers!
Regards, Kiesel

---

### Post by alistair_mc on 2011-10-13
> **Kiesel said:**
> Hi,

im thinking about buying the samsung rv520 S05. My concern is the NVIDIA GT 520M, which is an Optimus Card. Does anybody know whether that is a proble on this laptop? i.e. is it possible to switch it off? I do not plan on doing anything that needs the GPU.

Thanks for all answers!
Regards, Kiesel

Recently got RV520**-S0A** (core i5-2410M based, nvidia gt 520M). Ubuntu 11.04/amd64 runs fine after the following:

1. Installed **samsung-tools** and **easy-slow-down-manager** packages from [https://launchpad.net/~voria/+archive/ppa]("https://launchpad.net/%7Evoria/+archive/ppa").

2. Installed **Elantech touchpad driver** from [http://people.canonical.com/~sforshee/lp681904/psmouse-elantech-dkms/v0.2/psmouse-elantech-dkms_0.2_all.deb]("http://people.canonical.com/%7Esforshee/lp681904/psmouse-elantech-dkms/v0.2/psmouse-elantech-dkms_0.2_all.deb").

3. Added **nvidiabl** DKMS module from [https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.71_all.deb](https://github.com/downloads/guillaumezin/nvidiabl/nvidiabl-dkms_0.71_all.deb) (don't forget to append **nvidiabl** to **/etc/modules** and **acpi_backlight=vendor **to kernel parameters in **/etc/default/grub**).

Hope this helps (not sure, but it seems -S05 have the same HM65 Express chipset).

---

