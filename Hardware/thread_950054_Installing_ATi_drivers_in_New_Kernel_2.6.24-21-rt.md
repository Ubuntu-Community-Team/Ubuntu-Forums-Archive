---
title: "Installing ATi drivers in New Kernel 2.6.24-21-rt"
date: 2008-10-16
forum: Hardware
---

### Post by KDB9000 on 2008-10-16
I updated 2.6.24-21-rt and found out that all my ATi driver are broken so I decided to reinstall. I keep getting an error saying to run dkms build. well the 8.532 driver of flgrx is all ready added but it keeps giving me errors. What can I do to fix this? Tell me what commands you want me to run and I will post back, will also try and post the errors.

---

### Post by yonkman on 2008-10-16
mine just broke too.

Now, if someone says to switch to nvida I will vote for Mccain/Palin!!!

---

### Post by yonkman on 2008-10-17
fixed by the following

1) uninstall drivers
2) do    aptitude(or apt-gt) full-upgrade
3) check xorg
4) reboot
5) stop swearing ;)

---

### Post by KDB9000 on 2008-10-17
> **yonkman said:**
> fixed by the following

1) uninstall drivers
2) do    aptitude(or apt-gt) full-upgrade
3) check xorg
4) reboot
5) stop swearing ;)

Are you using the built in drivers or the ATi drivers? I am using the ATi drivers, version 8.9.

---

### Post by zeigfried on 2008-10-30
Go to Synaptic and mark for removal > xorg-driver-fglrx; fglrx-kernel-source. Click on apply.

Reinstall fglrx (from ubuntu repositories or ati page) with this guide [Binary Driver How to]("http://https://help.ubuntu.com/community/BinaryDriverHowto/ATI").

Reboot

run > lsmod and see if fglrx is loaded.

Cheers

---

