---
title: "telling sane to find a scanner"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by sarracenia88 on 2007-03-17
I have a brother mfc 8840d and brother has put out linux drivers for it in sane. after i installed the drivers, sane was not able to find my scanner and gave me an output like this.

[I]raptor22@raptor22-edgy:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
raptor22@raptor22-edgy:~$ 
[/I]

when i run the driver find wizard thing i get 

[I]raptor22@raptor22-edgy:~$ brsaneconfig
USAGE: brsaneconfig [-OPTION]   OPTION:
       -a name=FRIENDLY-NAME model=MODEL-NAME ip=xx.xx.xx.xx    
       -a name=FRIENDLY-NAME model=MODEL-NAME nodename=BRN_xxxxx 
                   : Add network scanner
       -r FRIENDLY-NAME [FRIENDLY-NAME ...]
                   : Remove network scanner
       -q          : Query supported models and available network scanners
       -d          : Diagnosis
       -p          : Ping (for network scanners)  
       -s:[LABEL]  : Save current configuration
       -l:[LABEL]  : Load saved configuration

raptor22@raptor22-edgy:~$ brsaneconfig -q
Devices on network
  0 downstairsbrother   "MFC-8840D"         I:192.168.001.104

raptor22@raptor22-edgy:~$ brsaneconfig -p
test downstairsbrother
ping 192.168.001.104 -w 10

PING 192.168.001.104 (192.168.1.104) 56(84) bytes of data.
64 bytes from 192.168.1.104: icmp_seq=1 ttl=59 time=3.60 ms
64 bytes from 192.168.1.104: icmp_seq=2 ttl=59 time=1.76 ms
64 bytes from 192.168.1.104: icmp_seq=3 ttl=59 time=1.75 ms
64 bytes from 192.168.1.104: icmp_seq=4 ttl=59 time=1.78 ms
64 bytes from 192.168.1.104: icmp_seq=5 ttl=59 time=1.75 ms
64 bytes from 192.168.1.104: icmp_seq=6 ttl=59 time=1.77 ms
64 bytes from 192.168.1.104: icmp_seq=7 ttl=59 time=1.90 ms
64 bytes from 192.168.1.104: icmp_seq=8 ttl=59 time=1.76 ms
64 bytes from 192.168.1.104: icmp_seq=9 ttl=59 time=1.75 ms
64 bytes from 192.168.1.104: icmp_seq=10 ttl=59 time=1.78 ms

--- 192.168.001.104 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9020ms
rtt min/avg/max/mdev = 1.752/1.964/3.606/0.551 ms
[/I]

obviously my computer is sensing that the scanner is on the network, i just need to tell sane where it is at. 

I was wondering what command i put in for it to do this

thanks,

---

