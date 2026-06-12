---
title: "Cisco VPN errors"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by ajsantell on 2009-01-21
I had to switch over to Linux for a class I'm taking, but having trouble getting the VPN to install.

Here's what's happening,
root@andrew-laptop:/home/andrew/vpnclient# rm /opt/cisco-vpnclient
rm: cannot remove `/opt/cisco-vpnclient': Is a directory
root@andrew-laptop:/home/andrew/vpnclient# rm -r /opt/cisco-vpnclient
root@andrew-laptop:/home/andrew/vpnclient# ./vpn_install
Cisco Systems VPN Client Version 4.8.01 (0640) Linux Installer
Copyright (C) 1998-2006 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms. 


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.27-9-generic/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.27-9-generic/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.27-9-generic/build" will be used to build the module.

Is the above correct [y]

Shutting down /opt/cisco-vpnclient/bin/vpnclient: module cisco_ipsec is not running.
Stopped: /etc/init.d/vpnclient_init (VPN init script)
Making module
make -C /lib/modules/2.6.27-9-generic/build SUBDIRS=/home/andrew/.local/share/Trash/files/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic'
  CC [M]  /home/andrew/.local/share/Trash/files/vpnclient/linuxcniapi.o
  CC [M]  /home/andrew/.local/share/Trash/files/vpnclient/frag.o
  CC [M]  /home/andrew/.local/share/Trash/files/vpnclient/IPSecDrvOS_linux.o
  CC [M]  /home/andrew/.local/share/Trash/files/vpnclient/interceptor.o
  CC [M]  /home/andrew/.local/share/Trash/files/vpnclient/linuxkernelapi.o
  LD [M]  /home/andrew/.local/share/Trash/files/vpnclient/cisco_ipsec.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/andrew/.local/share/Trash/files/vpnclient/.libdriver.so.cmd for /home/andrew/.local/share/Trash/files/vpnclient/libdriver.so
  CC      /home/andrew/.local/share/Trash/files/vpnclient/cisco_ipsec.mod.o
  LD [M]  /home/andrew/.local/share/Trash/files/vpnclient/cisco_ipsec.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic'
Copying module to directory "/lib/modules/2.6.27-9-generic/CiscoVPN".
Already have group 'bin'

Creating start/stop script "/etc/init.d/vpnclient_init".
    /etc/init.d/vpnclient_init
Enabling start/stop script for run level 3,4 and 5.

Installing license.txt (VPN Client license) in "/opt/cisco-vpnclient/":
    /opt/cisco-vpnclient/license.txt

Installing bundled user profiles in "/etc/opt/cisco-vpnclient/Profiles/":
* Replaced Profiles: abington altoona beaver behrend berks brandywine COE-from-ISP COE-Wireless dickinson dubois EMS-from-ISP EMS-Wireless fayette greater_allegheny great_valley harrisburg hazleton ISPtoPSU lehigh_valley LIAS-VPN mont_alto new_kensington schuylkill shenango_valley smeal university_park wilkes_barre worthington_scranton york 
cp: cannot stat `vpnclient.ini': No such file or directory

Copying binaries to directory "/opt/cisco-vpnclient/bin".
Adding symlinks to "/usr/local/bin".
    /opt/cisco-vpnclient/bin/vpnclient
cp: cannot stat `vpnclient': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/vpnclient': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/vpnclient': No such file or directory
    /opt/cisco-vpnclient/bin/cisco_cert_mgr
cp: cannot stat `cisco_cert_mgr': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/cisco_cert_mgr': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/cisco_cert_mgr': No such file or directory
    /opt/cisco-vpnclient/bin/ipseclog
cp: cannot stat `ipseclog': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/ipseclog': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/ipseclog': No such file or directory
Copying setuid binaries to directory "/opt/cisco-vpnclient/bin".
    /opt/cisco-vpnclient/bin/cvpnd
cp: cannot stat `cvpnd': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/bin/cvpnd': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/bin/cvpnd': No such file or directory
Copying libraries to directory "/opt/cisco-vpnclient/lib".
    /opt/cisco-vpnclient/lib/libvpnapi.so
cp: cannot stat `libvpnapi.so': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/lib/libvpnapi.so': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/lib/libvpnapi.so': No such file or directory
Copying header files to directory "/opt/cisco-vpnclient/include".
    /opt/cisco-vpnclient/include/vpnapi.h
cp: cannot stat `vpnapi.h': No such file or directory
chown: cannot access `/opt/cisco-vpnclient/include/vpnapi.h': No such file or directory
chmod: cannot access `/opt/cisco-vpnclient/include/vpnapi.h': No such file or directory

Setting permissions.
    /opt/cisco-vpnclient/bin/cvpnd (setuid root)
    /opt/cisco-vpnclient (group bin readable)
    /etc/opt/cisco-vpnclient (permissions not changed)
* You may wish to change these permissions to restrict access to root.
* You must run "/etc/init.d/vpnclient_init start" before using the client.
* This script will be run AUTOMATICALLY every time you reboot your computer.
root@andrew-laptop:/home/andrew/vpnclient# 


Any suggestions?

---

### Post by pytheas22 on 2009-01-21
I'm not sure what's wrong, but you should be able to install a Cisco VPN client much more easily by simply opening a terminal (while you're connected to the Internet) and typing:
```

sudo apt-get install network-manager-vpnc
```

When it finishes, left-click on the Network Manager icon in the top-right corner of your screen and you should see an option for VPN connections.  You can configure a connection, then connect.

If this doesn't work for some reason, we can try to figure out why your text-based installer is broken.  But for various reasons it's a much better idea to use the Network-Manager plugin instead.

---

### Post by ajsantell on 2009-01-22
Thanks, I gave that a try.

I just need to talk to my system admin to find out the gateway and stuff.
Thanks again.

---

