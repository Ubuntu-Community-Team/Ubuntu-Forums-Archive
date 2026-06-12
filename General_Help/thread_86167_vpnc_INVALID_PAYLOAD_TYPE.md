---
title: "vpnc INVALID_PAYLOAD_TYPE"
date: 2005-11-04
forum: General Help
---

### Post by flyingman on 2005-11-04
Why do I get this error while connecting to my University using Ubuntu Breezy and VPNC?
 


bjornart@flyingman:/etc/vpnc$ sudo vpnc studentit.conf

Enter password for [email]batron@student.uit.no[/email]@129.242.233.180:

vpnc: quick mode response rejected: INVALID_PAYLOAD_TYPE

this means the concentrator did not like what we had to offer.

Possible reasons are:

  * concentrator configured to require a firewall

     this locks out even Cisco clients on any platform expect windows

     which is an obvious security improvment. There is no workaround (yet).

  * concentrator configured to require IP compression

     this is not yet supported by vpnc.

     Note: the Cisco Concentrator Documentation recommends against using

     compression, expect on low-bandwith (read: ISDN) links, because it

     uses much CPU-resources on the concentrator

 

bjornart@flyingman:/etc/vpnc$










Here's my studentit.conf file:
IPSec gateway 129.242.233.180
IPSec ID student.uit.no
IPSec secret student.uit.no
XAuth username [email]batron@student.uit.no[/email]




The university uses this config file for the Cisco VPN client:
[main]
Description=VPN tilkobling med Student-IT konto.
!Host=129.242.233.180
!AuthType=1
!GroupName=student.uit.no
GroupPwd=
enc_GroupPwd=F992230153F51928672DF6C7B9C61EF8437252CFBE28C1101EF1A119D077E93CCCEEE4FE72E8A2DF5EC384E005F77577CCA7CCCA231FE9D8
EnableISPConnect=0
ISPConnectType=1
ISPConnect=
ISPCommand=
Username=[Erstatt med din fulle epostadresse]
!SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=0
MSLogonType=1
EnableNat=1
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
DHGroup=2
ForceKeepAlives=0
PeerTimeout=90
EnableLocalLAN=1
TunnelingMode=0
TcpTunnelingPort=10000
SendCertChain=0
VerifyCertDN=
EnableSplitDN







Why can't I connect using vpnc? 


I dropped the cisco vpn client because I would get this error every time while installing it:
bjornart@flyingman:~/vpnclient$ ./vpn_install
Sorry, you need super user access to run this script.
bjornart@flyingman:~/vpnclient$ sudo ./vpn_install
Cisco Systems VPN Client Version 4.6.00 (0045) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.12-9-386/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.12-9-386/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.12-9-386/build" will be used to build the module.

Is the above correct [y]y

Making module
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/bjornart/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/bjornart/vpnclient/interceptor.o
/home/bjornart/vpnclient/interceptor.c: In function `add_netdev':
/home/bjornart/vpnclient/interceptor.c:59: sorry, unimplemented: inlining failed in call to 'supported_device': function body not available
/home/bjornart/vpnclient/interceptor.c:245: sorry, unimplemented: called from here
/home/bjornart/vpnclient/interceptor.c: In function `recv_ip_packet_handler':
/home/bjornart/vpnclient/interceptor.c:607: warning: passing arg 1 of `skb_checksum_help' from incompatible pointer type
/home/bjornart/vpnclient/interceptor.c: In function `do_cni_send':
/home/bjornart/vpnclient/interceptor.c:732: warning: passing arg 1 of `skb_checksum_help' from incompatible pointer type
make[2]: *** [/home/bjornart/vpnclient/interceptor.o] Error 1
make[1]: *** [_module_/home/bjornart/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
bjornart@flyingman:~/vpnclient$

---

### Post by hajk on 2005-11-04
The Ubuntu vpnc package should work, but it needs some work if you use a firewall. Are you using Firestarter?

---

