---
title: "Atheros network card not working"
date: 2010-08-22
forum: Hardware
---

### Post by SonnyKing on 2010-08-22
Hi,
My atheros network card (AR9287) work well with ath9k driver, 
but for some reasons, i need uninstall it, and install madwifi driver.My OS version is 10.04, and kernel 2.6.32-21-generic;

I followed the HowTo Link: 
[http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi-project.org/wiki/UserDocs/FirstTimeHowTo)
But the command "module-assistant auto-install madwifi-source" return errors, meaned "something missed"

Thereby,I tried manually install, and downloaded madwifi in [http://madwifi-project.org/](http://madwifi-project.org/), (surely, branch version);
make
make install
all is right, and I modprobe ath_pci module, then reboot, but lshw -C network returns "AR9287 unclaimed",

Any suggestions? thank you.
one thing more, system>administrator>hardware drivers, only ATI card included, nothing more, what's wrong.

---

