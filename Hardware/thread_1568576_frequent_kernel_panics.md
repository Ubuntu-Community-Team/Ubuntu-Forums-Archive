---
title: "frequent kernel panics"
date: 2010-09-05
forum: Hardware
---

### Post by judepereira on 2010-09-05
Using Ubuntu Lucid Lynx
```
Linux fowlmanor 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:21:58 UTC 2010 x86_64 GNU/Linux
```
Last thing in my /var/log/messages log file before the kernel panic are:
```

Sep  5 22:17:11 fowlmanor pppd[2361]: CHAP authentication succeeded
Sep  5 22:17:12 fowlmanor pppd[2361]: local  IP address 180.215.247.63
Sep  5 22:17:12 fowlmanor pppd[2361]: remote IP address 10.214.192.1
Sep  5 22:17:12 fowlmanor pppd[2361]: primary   DNS address 10.216.254.132
Sep  5 22:17:12 fowlmanor pppd[2361]: secondary DNS address 10.216.254.136
Sep  5 22:18:43 fowlmanor kernel: [  355.930919] lo: Disabled Privacy Extensions
Sep  5 22:18:43 fowlmanor kernel: [  356.096384] [UFW BLOCK] IN=ppp0 OUT= MAC= SRC=180.215.208.170 DST=180.215.247.63 LEN=48 TOS=0x00 PREC=0x00 TTL=127 ID=500
23 DF PROTO=TCP SPT=4741 DPT=135 WINDOW=16384 RES=0x00 SYN URGP=0 

<machine freezes here, no idea why!>

Sep  5 22:26:51 fowlmanor kernel: imklog 4.2.0, log source = /proc/kmsg started.
Sep  5 22:26:51 fowlmanor rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="979" x-info="http://www.rsyslog.com"] (re)start
Sep  5 22:26:51 fowlmanor rsyslogd: rsyslogd's groupid changed to 103
Sep  5 22:26:51 fowlmanor rsyslogd: rsyslogd's userid changed to 101
Sep  5 22:26:51 fowlmanor kernel: [    0.000000] Initializing cgroup subsys cpuset
Sep  5 22:26:51 fowlmanor kernel: [    0.000000] Initializing cgroup subsys cpu

```
It's a kernel panic, sysrq functionality gets compromised, so no Alt+SysRQ+K. The temperatures are:
CPU: 46 C [crit is 95]
HDD: 41 C
GPU: 60 C [crit is 115]

The machine has no hardware defects, RAM passed the memtest, disabled swap too just incase it was a hdd problem, untill this afternoon, all was fine, these crashes started happening early evening. Nothing on the hdd has changed. Everything's the same.

Anyone any ideas?

Here's my lspci output:
```

00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.4 RAM memory: nVidia Corporation Device 0a98 (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:06.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:06.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:0c.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
03:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9300 / nForce 730i] (rev b1)

```
Anyone knows how to figure out this? Logs indicate nothing at all. Applications running don't seem to be a problem, happens with different applications running too. I end up hard rebooting the machine.

---

