---
title: "Nautilus Segmentation Fault"
date: 2009-05-14
forum: Installation &amp; Upgrades
---

### Post by slick666 on 2009-05-14
I'm re-installing ubuntu, instead of upgrading from 8.04 to 9.04. When I put in the Live CD and boot nautilus does not load. When I execute nautilus from the command line all I get is "Segmentation fault". I have no idea why this would be a problem in a live environment but this might explain how my 8.04 nautilus stopped working after an upgrade.

I've already run the built in self test on the CD and it checks out fine. Does anyone know why nautilus would fail in the live environment?

Thanks

---

### Post by slick666 on 2009-05-20
I found a work around.

In the live environment if I do a full update
> 
sudo apt-get update
sudo apt-get dist-upgrade


In that update is an update to nautilus. After completing the update simply log out. The system will log you back in automatically after 1 seconds and everything works just fine. It seems like Ubuntu should update there install CD for the inexperienced user.

---

