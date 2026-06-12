---
title: "Brother MFC-J4410DW Printer"
date: 2014-02-28
forum: Hardware
---

### Post by rayj00 on 2014-02-28
The printer is hooked up to my network via Wi-Fi.
My Windows 7 box can print just fine from the LAN via an ethernet connection.

My Ubuntu 12.04 host OS cannot print to it.

I see this in the cups admin error.log:  Unable to bind socket for address 192.168.1.4:631 - Cannot assign requested address.

And here is the rest of the troubleshooting info.  Ideas?

Ray


**rayj@ubuntu12:/etc/cups$ ping 192.168.1.4**
PING 192.168.1.4 (192.168.1.4) 56(84) bytes of data.
64 bytes from 192.168.1.4: icmp_req=1 ttl=255 time=11.6 ms
64 bytes from 192.168.1.4: icmp_req=2 ttl=255 time=10.0 ms
64 bytes from 192.168.1.4: icmp_req=3 ttl=255 time=5.45 ms
64 bytes from 192.168.1.4: icmp_req=4 ttl=255 time=9.50 ms
^C
--- 192.168.1.4 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 5.455/9.177/11.683/2.293 ms
rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ /usr/lib/cups/backend/snmp**
network lpd://BRW844BF578E7AE/BINARY_P1 "Brother MFC-J4410DW" "Brother MFC-J4410DW" "MFG:Brother;CMD:HBP,BRPJL,URF;MDL:MFC-J4410DW;CLS:PRINTER;CID:Brother IJ Type3;URF:SRGB24,W8,CP1,IS1-13,MT1-8-11,OB9,PQ4-5,RS300,OFU0,DM4;" ""
rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ sudo /usr/lib/cups/backend/dnssd**
DEBUG: Found "Brother MFC-J4410DW._ipp._tcplocal"...
DEBUG: Found "Brother MFC-J4410DW._pdl-datastream._tcplocal"...
DEBUG: Found "Brother MFC-J4410DW._printer._tcplocal"...
network dnssd://Brother%20MFC-J4410DW._pdl-datastream._tcp.local/ "Brother MFC-J4410DW" "Brother MFC-J4410DW" "MFG:Brother;MDL:MFC-J4410DW;CMD:HBP,BRPJL,URF;" ""
network dnssd://Brother%20MFC-J4410DW._printer._tcp.local/ "Brother MFC-J4410DW" "Brother MFC-J4410DW" "MFG:Brother;MDL:MFC-J4410DW;CMD:HBP,BRPJL,URF;" ""
network dnssd://Brother%20MFC-J4410DW._ipp._tcp.local/ "Brother MFC-J4410DW" "Brother MFC-J4410DW" "MFG:Brother;MDL:MFC-J4410DW;CMD:HBP,BRPJL,URF;" ""
**rayj@ubuntu12:/etc/cups$ /usr/lib/cups/backend/snmp 192.168.1.4**
network lpd://BRW844BF578E7AE/BINARY_P1 "Brother MFC-J4410DW" "Brother MFC-J4410DW" "MFG:Brother;CMD:HBP,BRPJL,URF;MDL:MFC-J4410DW;CLS:PRINTER;CID:Brother IJ Type3;URF:SRGB24,W8,CP1,IS1-13,MT1-8-11,OB9,PQ4-5,RS300,OFU0,DM4;" ""
rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ lpinfo -v**
network lpd
network ipps
network ipp
network https
network socket
network smb
network http
network beh
network ipp14
network dnssd://Brother%20MFC-J4410DW._ipp._tcp.local/
network dnssd://Brother%20MFC-J4410DW._pdl-datastream._tcp.local/
network dnssd://Brother%20MFC-J4410DW._printer._tcp.local/
direct hpfax
direct hp
network lpd://BRW844BF578E7AE/BINARY_P1
rayj@ubuntu12:/etc/cups$ 
rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ avahi-browse -a -v -t -r **
Server version: avahi 0.6.30; Host name: ubuntu12.local
E Ifce Prot Name                                          Type                 Domain
+  vnet2 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+  vnet1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+  vnet0 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+ virbr0 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
+   eth1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+   eth1 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
+  vnet2 IPv6 ubuntu12 [96:1d:64:75:12:b2]                  Workstation          local
+  vnet1 IPv6 ubuntu12 [56:89:50:fd:20:04]                  Workstation          local
+  vnet0 IPv6 ubuntu12 [16:b6:5f:a8:36:47]                  Workstation          local
+ virbr0 IPv4 ubuntu12 [82:01:1e:e9:e5:2d]                  Workstation          local
+   eth1 IPv6 ubuntu12 [90:2a:35:de:ca:9e]                  Workstation          local
+   eth1 IPv4 WNDR4500 [94:1b:cf:c0:d4:c6]                  Workstation          local
+   eth1 IPv4 ubuntu12 [76:2b:34:ce:d3:2e]                  Workstation          local
+  vnet2 IPv6 ubuntu12                                      Remote Disk Management local
+  vnet1 IPv6 ubuntu12                                      Remote Disk Management local
+  vnet0 IPv6 ubuntu12                                      Remote Disk Management local
+ virbr0 IPv4 ubuntu12                                      Remote Disk Management local
+   eth1 IPv6 ubuntu12                                      Remote Disk Management local
+   eth1 IPv4 ubuntu12                                      Remote Disk Management local
+   eth1 IPv4 Brother MFC-J4410DW                           Internet Printer     local
+   eth1 IPv4 Brother MFC-J4410DW                           UNIX Printer         local
+   eth1 IPv4 Brother MFC-J4410DW                           PDL Printer          local
+   eth1 IPv4 WNDR4500                                      Microsoft Windows Network local
+   eth1 IPv4 Brother MFC-J4410DW                           Web Site             local
+   eth1 IPv4 Web Server on WNDR4500                        Web Site             local
+   eth1 IPv4 WNDR4500                                      _device-info._tcp    local
=   eth1 IPv4 Brother MFC-J4410DW                           Internet Printer     local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [631]
   txt = ["UUID=e3248000-80ce-11db-8000-001ba9cb25e2" "URF=SRGB24,W8,CP1,IS1-13,MT1-8-11,OB9,PQ4-5,RS300,OFU0,DM4" "TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=T" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J4410DW" "usb_MFG=Brother" "priority=25" "adminurl=http://BRW844BF578E7AE.local./net/net/airprint.html" "product=(Brother MFC-J4410DW)" "ty=Brother MFC-J4410DW" "note=" "rp=ipp/printer" "pdl=application/octet-stream,application/vnd.brother-hbp,image/urf" "qtotal=1" "txtvers=1"]
=   eth1 IPv4 Brother MFC-J4410DW                           UNIX Printer         local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [515]
   txt = ["UUID=e3248000-80ce-11db-8000-001ba9cb25e2" "TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=T" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J4410DW" "usb_MFG=Brother" "priority=50" "adminurl=http://BRW844BF578E7AE.local./net/net/airprint.html" "product=(Brother MFC-J4410DW)" "ty=Brother MFC-J4410DW" "note=" "rp=duerqxesz5090" "pdl=application/octet-stream,application/vnd.brother-hbp,image/urf" "qtotal=1" "txtvers=1"]
=   eth1 IPv4 Brother MFC-J4410DW                           Web Site             local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [80]
   txt = []
=  vnet2 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fe0e:f4e]
   port = [65535]
   txt = []
=  vnet2 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fe0e:f4e]
   port = [22]
   txt = []
=  vnet2 IPv6 ubuntu12 [86:1d:62:75:12:c2]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fe0e:f4e]
   port = [9]
   txt = []
=  vnet1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fef6:50d2]
   port = [65535]
   txt = []
=  vnet1 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fef6:50d2]
   port = [22]
   txt = []
=  vnet1 IPv6 ubuntu12 [56:89:50:fd:20:04]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fef6:50d2]
   port = [9]
   txt = []
=  vnet0 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fefa:e962]
   port = [65535]
   txt = []
=  vnet0 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fefa:e962]
   port = [22]
   txt = []
=  vnet0 IPv6 ubuntu12 [16:b6:5f:a8:36:47]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fefa:e962]
   port = [9]
   txt = []
=   eth1 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::922b:34ff:fede:c19e]
   port = [22]
   txt = []
=   eth1 IPv6 ubuntu12 [90:2b:34:de:c1:9e]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::922b:34ff:fede:c19e]
   port = [9]
   txt = []
=   eth1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::922b:34ff:fede:c19e]
   port = [65535]
   txt = []
= virbr0 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [192.168.122.1]
   port = [65535]
   txt = []
= virbr0 IPv4 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [192.168.122.1]
   port = [22]
   txt = []
= virbr0 IPv4 ubuntu12 [82:01:1e:e9:e5:2d]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [192.168.122.1]
   port = [9]
   txt = []
=   eth1 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [192.168.1.5]
   port = [65535]
   txt = []
=   eth1 IPv4 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [192.168.1.5]
   port = [22]
   txt = []
=   eth1 IPv4 ubuntu12 [90:2b:34:de:c1:9e]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [192.168.1.5]
   port = [9]
   txt = []
=   eth1 IPv4 WNDR4500 [84:1b:5e:d0:d2:c6]                  Workstation          local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [9]
   txt = []
=   eth1 IPv4 WNDR4500                                      _device-info._tcp    local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [0]
   txt = ["model=Xserve"]
=   eth1 IPv4 Web Server on WNDR4500                        Web Site             local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [80]
   txt = ["path=/index.html"]
=   eth1 IPv4 WNDR4500                                      Microsoft Windows Network local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [445]
   txt = []
=   eth1 IPv4 Brother MFC-J4410DW                           PDL Printer          local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [9100]
   txt = ["UUID=e3248000-80ce-11db-8000-001ba9cb25e2" "TBCP=T" "Transparent=F" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=T" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J4410DW" "usb_MFG=Brother" "priority=75" "adminurl=http://BRW844BF578E7AE.local./net/net/airprint.html" "product=(Brother MFC-J4410DW)" "ty=Brother MFC-J4410DW" "note=" "pdl=application/octet-stream,application/vnd.brother-hbp,image/urf" "qtotal=1" "txtvers=1"]
: Cache exhausted
: All for now
rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ avahi-browse -a -v -c -r **
Server version: avahi 0.6.30; Host name: ubuntu12.local
E Ifce Prot Name                                          Type                 Domain
+  vnet2 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+  vnet1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+  vnet0 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+ virbr0 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
+   eth1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
+   eth1 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
+  vnet2 IPv6 ubuntu12 [86:1d:62:75:12:c2]                  Workstation          local
+  vnet1 IPv6 ubuntu12 [56:89:50:fd:20:04]                  Workstation          local
+  vnet0 IPv6 ubuntu12 [16:b6:5f:a8:36:47]                  Workstation          local
+ virbr0 IPv4 ubuntu12 [82:01:1e:e9:e5:2d]                  Workstation          local
+   eth1 IPv6 ubuntu12 [90:2b:34:de:c1:9e]                  Workstation          local
+   eth1 IPv4 WNDR4500 [84:1b:5e:d0:d2:c6]                  Workstation          local
+   eth1 IPv4 ubuntu12 [90:2b:34:de:c1:9e]                  Workstation          local
+  vnet2 IPv6 ubuntu12                                      Remote Disk Management local
+  vnet1 IPv6 ubuntu12                                      Remote Disk Management local
+  vnet0 IPv6 ubuntu12                                      Remote Disk Management local
+ virbr0 IPv4 ubuntu12                                      Remote Disk Management local
+   eth1 IPv6 ubuntu12                                      Remote Disk Management local
+   eth1 IPv4 ubuntu12                                      Remote Disk Management local
+   eth1 IPv4 Brother MFC-J4410DW                           Internet Printer     local
+   eth1 IPv4 Brother MFC-J4410DW                           UNIX Printer         local
+   eth1 IPv4 Brother MFC-J4410DW                           PDL Printer          local
+   eth1 IPv4 WNDR4500                                      Microsoft Windows Network local
+   eth1 IPv4 Brother MFC-J4410DW                           Web Site             local
+   eth1 IPv4 Web Server on WNDR4500                        Web Site             local
+   eth1 IPv4 WNDR4500                                      _device-info._tcp    local
=  vnet2 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fe0e:f4e]
   port = [65535]
   txt = []
=  vnet1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fef6:50d2]
   port = [65535]
   txt = []
=  vnet0 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fefa:e962]
   port = [65535]
   txt = []
= virbr0 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [192.168.122.1]
   port = [65535]
   txt = []
=   eth1 IPv6 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [fe80::922b:34ff:fede:c19e]
   port = [65535]
   txt = []
=   eth1 IPv4 Virtualization Host ubuntu12                  Virtual Machine Manager local
   hostname = [ubuntu12.local]
   address = [192.168.1.5]
   port = [65535]
   txt = []
=  vnet2 IPv6 ubuntu12 [86:1d:62:75:12:c2]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fe0e:f4e]
   port = [9]
   txt = []
=  vnet1 IPv6 ubuntu12 [56:89:50:fd:20:04]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fef6:50d2]
   port = [9]
   txt = []
=  vnet0 IPv6 ubuntu12 [16:b6:5f:a8:36:47]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fefa:e962]
   port = [9]
   txt = []
= virbr0 IPv4 ubuntu12 [82:01:1e:e9:e5:2d]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [192.168.122.1]
   port = [9]
   txt = []
=   eth1 IPv6 ubuntu12 [90:2b:34:de:c1:9e]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [fe80::922b:34ff:fede:c19e]
   port = [9]
   txt = []
=   eth1 IPv4 WNDR4500 [84:1b:5e:d0:d2:c6]                  Workstation          local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [9]
   txt = []
=   eth1 IPv4 ubuntu12 [90:2b:34:de:c1:9e]                  Workstation          local
   hostname = [ubuntu12.local]
   address = [192.168.1.5]
   port = [9]
   txt = []
=  vnet2 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fe0e:f4e]
   port = [22]
   txt = []
=  vnet1 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fef6:50d2]
   port = [22]
   txt = []
=  vnet0 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::fc54:ff:fefa:e962]
   port = [22]
   txt = []
= virbr0 IPv4 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [192.168.122.1]
   port = [22]
   txt = []
=   eth1 IPv6 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [fe80::922b:34ff:fede:c19e]
   port = [22]
   txt = []
=   eth1 IPv4 ubuntu12                                      Remote Disk Management local
   hostname = [ubuntu12.local]
   address = [192.168.1.5]
   port = [22]
   txt = []
=   eth1 IPv4 Brother MFC-J4410DW                           Internet Printer     local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [631]
   txt = ["UUID=e3248000-80ce-11db-8000-001ba9cb25e2" "URF=SRGB24,W8,CP1,IS1-13,MT1-8-11,OB9,PQ4-5,RS300,OFU0,DM4" "TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=T" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J4410DW" "usb_MFG=Brother" "priority=25" "adminurl=http://BRW844BF578E7AE.local./net/net/airprint.html" "product=(Brother MFC-J4410DW)" "ty=Brother MFC-J4410DW" "note=" "rp=ipp/printer" "pdl=application/octet-stream,application/vnd.brother-hbp,image/urf" "qtotal=1" "txtvers=1"]
=   eth1 IPv4 Brother MFC-J4410DW                           UNIX Printer         local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [515]
   txt = ["UUID=e3248000-80ce-11db-8000-001ba9cb25e2" "TBCP=F" "Transparent=T" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=T" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J4410DW" "usb_MFG=Brother" "priority=50" "adminurl=http://BRW844BF578E7AE.local./net/net/airprint.html" "product=(Brother MFC-J4410DW)" "ty=Brother MFC-J4410DW" "note=" "rp=duerqxesz5090" "pdl=application/octet-stream,application/vnd.brother-hbp,image/urf" "qtotal=1" "txtvers=1"]
=   eth1 IPv4 Brother MFC-J4410DW                           PDL Printer          local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [9100]
   txt = ["UUID=e3248000-80ce-11db-8000-001ba9cb25e2" "TBCP=T" "Transparent=F" "Binary=T" "PaperCustom=T" "Scan=T" "Duplex=T" "Copies=F" "Color=T" "usb_CMD=HBP,BRPJL,URF" "usb_MDL=MFC-J4410DW" "usb_MFG=Brother" "priority=75" "adminurl=http://BRW844BF578E7AE.local./net/net/airprint.html" "product=(Brother MFC-J4410DW)" "ty=Brother MFC-J4410DW" "note=" "pdl=application/octet-stream,application/vnd.brother-hbp,image/urf" "qtotal=1" "txtvers=1"]
=   eth1 IPv4 WNDR4500                                      Microsoft Windows Network local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [445]
   txt = []
=   eth1 IPv4 Brother MFC-J4410DW                           Web Site             local
   hostname = [BRW844BF578E7AE.local]
   address = [192.168.1.4]
   port = [80]
   txt = []
=   eth1 IPv4 Web Server on WNDR4500                        Web Site             local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [80]
   txt = ["path=/index.html"]
=   eth1 IPv4 WNDR4500                                      _device-info._tcp    local
   hostname = [WNDR4500.local]
   address = [192.168.1.1]
   port = [0]
   txt = ["model=Xserve"]
: Cache exhausted
rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ ifconfig**
eth0      Link encap:Ethernet  HWaddr 90:2b:34:de:c1:a0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 90:2b:34:de:c1:9e  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::922b:34ff:fede:c19e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2491239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2079064 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1900199833 (1.9 GB)  TX bytes:524073747 (524.0 MB)
          Interrupt:20 Memory:f7c00000-f7c20000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4441307 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4441307 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1082154831 (1.0 GB)  TX bytes:1082154831 (1.0 GB)

virbr0    Link encap:Ethernet  HWaddr fe:54:00:0e:0f:4e  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:237289 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234142 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:31541440 (31.5 MB)  TX bytes:327689773 (327.6 MB)

vnet0     Link encap:Ethernet  HWaddr fe:54:00:fa:e9:62  
          inet6 addr: fe80::fc54:ff:fefa:e962/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63576 errors:0 dropped:0 overruns:0 frame:0
          TX packets:439982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:5547222 (5.5 MB)  TX bytes:181856030 (181.8 MB)

vnet1     Link encap:Ethernet  HWaddr fe:54:00:f6:50:d2  
          inet6 addr: fe80::fc54:ff:fef6:50d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44075 errors:0 dropped:0 overruns:0 frame:0
          TX packets:317702 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:3173412 (3.1 MB)  TX bytes:144903738 (144.9 MB)

vnet2     Link encap:Ethernet  HWaddr fe:54:00:0e:0f:4e  
          inet6 addr: fe80::fc54:ff:fe0e:f4e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:76698 errors:0 dropped:0 overruns:0 frame:0
          TX packets:95066 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:19637462 (19.6 MB)  TX bytes:16131944 (16.1 MB)

rayj@ubuntu12:/etc/cups$ 
**rayj@ubuntu12:/etc/cups$ route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         WNDR4500.local  0.0.0.0         UG    100    0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
192.168.122.0   *               255.255.255.0   U     0      0        0 virbr0
rayj@ubuntu12:/etc/cups$

---

### Post by Ubi_one_2014 on 2014-03-01
did you install the drivers for your printer?

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J4410DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J4410DW)

---

### Post by rayj00 on 2014-03-01
Yes I installed the drivers.

It's weird though.  There is some communications going on between my Ubuntu box and the printer.
If I try to check toner levels, the printer does wake up and the panel lights come on.

Ray

---

### Post by gifford on 2014-03-01
It looks like you are trying to access the printer via ethernet. Is this correct?
Have you tried via wireless?

---

### Post by Ubi_one_2014 on 2014-03-02
are you able to setup the printer from:
127.0.0.1:631

---

### Post by rayj00 on 2014-03-02
> **gifford said:**
> It looks like you are trying to access the printer via ethernet. Is this correct?
Have you tried via wireless?

I can print over WiFi using my Windows 8 Nokia Lumia 521 just fine.
I had to download an app,  but it works.

As I said initially, my wife's Windows 7 box can print just fine also (over ethernet).

The Ubuntu box I am having the issue with does not have WiFi.

Ray

---

### Post by am-clark on 2014-03-21
I'm having similar problems with my MFC-J4410DW, it's printing okay over the USB, although the settings (ie paper sizes, and type) cannot be changed, which I can live with for normal printing, but I use it to print photgraphs via the network. The Ubuntu machine is connected via ethernet to the router and the printer via wireless.

I did notice that my router changed the printer IP address evertime I turned it on, so have had to make it a static IP address.

The settings can be changed, hence why I use this option, but it takes an age to print. Over 1hr for an A4 picture. I belive it's something to do with the drivers as the spooling is what is taking the time. As soon as the spool number increases, the printer moves a fraction.

I appreciate its not an answer to the thread, but I think the drivers are slightly faulty.

---

### Post by rayj00 on 2014-03-21
> **am-clark said:**
> I'm having similar problems with my MFC-J4410DW, it's printing okay over the USB, although the settings (ie paper sizes, and type) cannot be changed, which I can live with for normal printing, but I use it to print photgraphs via the network. The Ubuntu machine is connected via ethernet to the router and the printer via wireless.

I did notice that my router changed the printer IP address evertime I turned it on, so have had to make it a static IP address.

The settings can be changed, hence why I use this option, but it takes an age to print. Over 1hr for an A4 picture. I belive it's something to do with the drivers as the spooling is what is taking the time. As soon as the spool number increases, the printer moves a fraction.

I appreciate its not an answer to the thread, but I think the drivers are slightly faulty.

Well, initially my black ink needed replacement so I got one.   Then it told me that the C and Y need replacement.
So I did.  But then it continued to show the brand new cartridges need replacing and would not print!
So, I have 4 brand new cartridges and it still will not print!  I got my money back for 3 of the 4.
I am going to junk this printer.  I will never buy a Brother again.   I should have known better to stick with
the leaders in printing,  either HP or Epson.   I bought an Epson.  I have not tested out the printing from
my Linux box yet.

---

