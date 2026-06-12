---
title: "Autostart  canon printer daemon  10.10"
date: 2010-12-09
forum: Hardware
---

### Post by HighSide on 2010-12-09
Hi 

I have been following this[https://help.ubuntu.com/community/CanonCaptDrv190]("https://help.ubuntu.com/community/CanonCaptDrv190")
to install my canon printer. The printer works fine however I have to manually start the ccpd script each time I boot.

As it suggests, I have tried the command.. 
sudo update-rc.d ccpd defaults 50  

but it returns this..
update-rc.d: warning: ccpd start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (2 3)
update-rc.d: warning: ccpd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (0 1 4 5 6)
System start/stop links for /etc/init.d/ccpd already exist

I'm not sure what the arguments mean or should be?

---

