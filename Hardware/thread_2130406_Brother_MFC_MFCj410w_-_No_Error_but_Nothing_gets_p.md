---
title: "Brother MFC MFCj410w - No Error but Nothing gets printed."
date: 2013-03-29
forum: Hardware
---

### Post by rajd03 on 2013-03-29
Hello,

I am trying to install Network Brother MFCj410w and MFC465CN Printers on Ubuntu 12.1 desktop and not able to print anything.

The printer is discovered with correct name in the Network Printer settings using either Cups browser version or Settings > Printer utility. I dont see any error in the printing but nothing gets print on the printer. I see /var/spool/cups/d... files in the queue.

I have install brother LPD and Cups driver from the following link and installed as per directions.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html)

Some things that I have tried.

root@ubuntu:~# lpstat -a
Brother_MFC-J410W accepting requests since Fri 29 Mar 2013 07:04:45 AM PDT

root@ubuntu:~# nmap 192.168.1.13


Starting Nmap 6.00 ( [http://nmap.org](http://nmap.org) ) at 2013-03-29 07:39 PDT
Nmap scan report for BRW0022585C348F.home (192.168.1.13)
Host is up (0.0078s latency).
Not shown: 995 closed ports
PORT     STATE SERVICE
21/tcp   open  ftp
23/tcp   open  telnet
80/tcp   open  http
515/tcp  open  printer
9100/tcp open  jetdirect
MAC Address: 00:22:58:5C:34:8F (Taiyo Yuden Co.)


Nmap done: 1 IP address (1 host up) scanned in 4.82 seconds

root@ubuntu:~# lpinfo -v
network https
network lpd
network ipp
network ipp14
direct hp
direct parallel:/dev/lp0
network http
network socket
network ipps
network beh
network smb
network tpvmgp
network tpvmlp
direct hpfax
network lpd://MFC-9970CDW/BINARY_P1 (It is my another printer)
network lpd://BRW0022585C348F/BINARY_P1 (This is the MFCj410w)


Can you please point me in a direction where I can troubleshot the issue? Why nothing gets printed?

Thanks,
Raj

---

