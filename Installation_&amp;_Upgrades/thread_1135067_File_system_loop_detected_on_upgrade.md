---
title: "File system loop detected on upgrade"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by elyobelyob on 2009-04-24
Upgrading my server edition to 9.04 using "sudo do-release-upgrade".

I have managed to get it upgraded, however, when I had a load of infinite loop problems. I am now trying "sudo apt-get upgrade" and getting the following type of messages galore ... 

find: File system loop detected; 
`/etc/openvpn/easy-rsa/sys/bus/pci/drivers/ohci1394/0000:01:08.0/fw-host0/irm_id/subsystem/drivers/nodemgr/module/drivers/ieee1394:nodemgr' 
is part of the same file system loop as 
`/etc/openvpn/easy-rsa/sys/bus/pci/drivers/ohci1394/0000:01:08.0/fw-host0/irm_id/subsystem/drivers/nodemgr'.

I am totally stuck on this, but have managed to get my apache up and running again, at least ...

---

### Post by elyobelyob on 2009-04-28
*bump*

---

### Post by k7k0 on 2010-05-28
Been late, but I've this problem in a box. I finally managed to upgrade killing the find process

---

### Post by mmm4m5m on 2010-06-25
Upgrading 8.04 to 10.04...
few minutes after upgrade started, I have 500 MB log file:
/var/log/dist-upgrade/apt-term.log
All because of this "find" command and "loop detected" errors.

(can't wait upgrade to complete, so I can remove/uninstall/delete few things which are the reason for these errors/warnings)

---

