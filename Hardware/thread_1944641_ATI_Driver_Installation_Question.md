---
title: "ATI Driver Installation Question"
date: 2012-03-21
forum: Hardware
---

### Post by cromat on 2012-03-21
Hi on the ubuntu wiki ([https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)) the follow command is shown as the way to install ati driver is this necessary?

sudo sh amd-driver-installer-12-2-x86.x86_64.run --buildpkg Ubuntu/oneiric

I generally have just been doing
sudo ./amd-driver-installer-12-2-x86.x86_64.run

And using the packaged installer?  Does anyone know if there is a reason for the buildpkg or is it mainly a safeguard to ensure it is building compatible packages?  What about other distro's based on Ubuntu?

I have never had an issue on Linux Mint with

sudo ./amd-driver-installer-12-2-x86.x86_64.run

Thanks...

---

### Post by Yellow Pasque on 2012-03-21
The main advantage of using packages (on any Debian-based distro) is ease of removal and compliance with Debian filesystem hierarchy policy. Using the install script is not recommended, but it works okay for most people going that route from reports I've seen.

---

### Post by cromat on 2012-04-09
I did a 12.04 install and used the packaged drivers, I have had no issues, much better multi-monitor experience compared to gnome 3 shell.

---

