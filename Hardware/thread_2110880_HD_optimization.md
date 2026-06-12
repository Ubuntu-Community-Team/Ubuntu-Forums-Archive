---
title: "HD optimization"
date: 2013-01-31
forum: Hardware
---

### Post by SAngeli on 2013-01-31
Hi,
running ubuntu server on an IBM xSeries 100 server with onboard Sata-I controller I have two identical HD installed being:
- Barracuda ST31500341AS 7200.11 Serial ATA-II
[**Here**]("http://www.seagate.com/staticfiles/support/disc/manuals/desktop/Barracuda%207200.11/100507013e.pdf") you can see the full pdf specs. This server also has 1Gb NIC and it is connected on a Gb LAN

I use this server for NAS and web services. I wish to ask someone expert on this if hdparm test results are correct/satisfactory (as i do not know/think of) and if is there something that could be done to set up the server so that it can use the maximum transfer speed and also read/write. Please note that both HD are on RAID-1 via Mdadm software raid.

**HD summarized specs:**
> Formatted capacity (512 bytes/sector)*: 1500 Gbytes
Guaranteed sectors: 2,930,277,168
Heads: 8
Discs: 4
Bytes per sector: 512
Default sectors per track: 63
Default read/write heads: 16
Default cylinders: 16,383
Recording density: 1462 kbits/in max
Track density: 190 ktracks/in avg
Areal density: 277 Gbits/in2 avg
Spindle speed: 7,200 RPM
Internal data transfer rate: 1709 Mbits/sec max
Sustained data transfer rate OD: 135 Mbytes/sec max
I/O data-transfer rate: 300 Mbytes/sec max
ATA data-transfer modes supported:
  - PIO modes 0–4
  - Multiword DMA modes 0–2
  - Ultra DMA modes 0–6
Cache buffer: 32 Mbytes
Average latency: 4.16 msec
Track-to-track seek time: <0.8 msec typical read;

Average seek, write: <10.0 msec typical

**hdparm tests:**


```
$ hdparm -iv /dev/sda
======================================================================

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 182401/255/63, sectors = 2930277168, start = 0

 Model=ST31500341AS, FwRev=CC1H, SerialNo=9VS4AW5C
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=unknown, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=2930277168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4
 DMA modes:  mdma0 mdma1 mdma2
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode

$ hdparm -Tt /dev/sda
======================================================================
/dev/sda:
 Timing cached reads:   2304 MB in  2.00 seconds = 1151.90 MB/sec
 Timing buffered disk reads: 372 MB in  3.01 seconds = 123.53 MB/sec
```

Thank you,
Spiro

---

### Post by tgalati4 on 2013-01-31
A gigbit/sec network 1000BaseT (Cat6) will give you peak transfers of ~125Megabytes/sec, so your buffered disk read speeds will keep up.  Since this is on a multi-user network, your real transfer speeds will be lower.  Set up iperf on the server and on some linux desktop machines to test your network speed, then compare to your actual transfer speeds with some standard files (for example an Ubuntu DVD ISO at 1 GB.)

On the server:

```
iperf -s
```

On the desktop/laptop:

```
iperf -c 192.168.1.50 -w 1024k -i 2 -t 20 -f M
```

Change the 192.168.1.50 to your server address.

Run from  wired and wireless connections.  Then copy files between the same machines and compare the raw iperf packet speeds with the file transfer speeds.  Note the differences and post some of the results for comment.

Keep the disk drive at default settings unless you have a really good reason to change them.

---

### Post by SAngeli on 2013-02-01
> Note the differences and post some of the results for comment.
I will do so during the day.

Is there a way I can test between linux server and windows 7 x64 so that I can also post results? I ask this as I will not have any linux desktop in my LAN.

Thank you,
Spiro

---

### Post by tgalati4 on 2013-02-01
I don't use windows.  Is there an iperf in the command.com terminal?  If you have a Live CD or DVD of Ubuntu, you can boot any machine, open a terminal and run the tests.

---

### Post by SAngeli on 2013-02-03
Hi,
finally I was able to accomplish all tests.

For Microsoft Windows OS you can find Iperf [**at openmaniak.com**]("http://www.iperfwindows.com/").

I will post test results from both Linux and Windows OS. I performed both tests - what was requested from this forum and what is explained on iperf windows website.

Please let me know the interpretation of the results.
Moreover, what I was concerned at first was if the HD is woring at its max speed in read/write. I am glad I was able to perorm network test too but wish to know this as well.


[B]IPERF NETWORK TEST
From Ubuntu Desktop Live-CD to Ubuntu Server
[/B]*using the same NIC*
```
(1) Test requested from ubuntu forum, current Thread

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.119 port 48667
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec  2.19 GBytes   941 Mbits/sec


client side:
$ iperf -c 192.168.0.50 -w 1024k -i 2 -t 20 -f M
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 0.25 MByte (WARNING: requested 1.00 MByte)
------------------------------------------------------------
[  3] local 192.168.0.119 port 48667 connected with 192.168.0.50 port 5001
[  3]  0.0- 2.0 sec    225 MBytes    112 MBytes/sec
[  3]  2.0- 4.0 sec    224 MBytes    112 MBytes/sec
[  3]  4.0- 6.0 sec    224 MBytes    112 MBytes/sec
[  3]  6.0- 8.0 sec    225 MBytes    112 MBytes/sec
[  3]  8.0-10.0 sec    225 MBytes    112 MBytes/sec
[  3] 10.0-12.0 sec    224 MBytes    112 MBytes/sec
[  3] 12.0-14.0 sec    224 MBytes    112 MBytes/sec
[  3] 14.0-16.0 sec    225 MBytes    112 MBytes/sec
[  3] 16.0-18.0 sec    224 MBytes    112 MBytes/sec
[  3] 18.0-20.0 sec    224 MBytes    112 MBytes/sec
[  3]  0.0-20.0 sec   2245 MBytes    112 MBytes/sec


(2) Tests suggested by openmaniak.com

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.119 port 48730
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.10 GBytes   942 Mbits/sec


client side:
iperf -c 192.168.0.50
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 21.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.119 port 48730 connected with 192.168.0.50 port 5001
[  3]  0.0-10.0 sec  1.10 GBytes    944 Mbits/sec


(3) Bi-directional bandwidth measurement: (-r argument)

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.119 port 48731
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec  1.10 GBytes   942 Mbits/sec
------------------------------------------------------------
Client connecting to 192.168.0.119, TCP port 5001
TCP window size:  169 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 60547 connected with 192.168.0.119 port 5001
[  4]  0.0-10.0 sec  1.10 GBytes   944 Mbits/sec


client side:
$ iperf -c 192.168.0.50 -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size:   210 KByte (default)
------------------------------------------------------------
[  5] local 192.168.0.119 port 48731 connected with 192.168.0.50 port 5001
[  5]  0.0-10.0 sec  1.10 GBytes    944 Mbits/sec
[  4] local 192.168.0.119 port 5001 connected with 192.168.0.50 port 60547
[  4]  0.0-10.0 sec  1.10 GBytes    941 Mbits/sec


(4) Simultaneous bi-directional bandwidth measurement: (-d argument)

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.119 port 48732
------------------------------------------------------------
Client connecting to 192.168.0.119, TCP port 5001
TCP window size:  174 KByte (default)
------------------------------------------------------------
[  6] local 192.168.0.50 port 60548 connected with 192.168.0.119 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   927 MBytes   776 Mbits/sec
[  6]  0.0-10.0 sec  1.05 GBytes   902 Mbits/sec


client side:
$ iperf -c 192.168.0.50 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size:   193 KByte (default)
------------------------------------------------------------
[  5] local 192.168.0.119 port 48732 connected with 192.168.0.50 port 5001
[  4] local 192.168.0.119 port 5001 connected with 192.168.0.50 port 60548
[  5]  0.0-10.0 sec    927 MBytes    777 Mbits/sec
[  4]  0.0-10.0 sec  1.05 GBytes    901 Mbits/sec


(5) TCP Window size: (-w argument)

server side:
$ iperf -s -w 4000
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 7.81 KByte (WARNING: requested 3.91 KByte)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.119 port 48736
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   203 MBytes   171 Mbits/sec


client side:
$ iperf -c 192.168.0.50 -w 2000
WARNING: TCP window size set to 2000 bytes. A small window size
will give poor performance. See the Iperf documentation.
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 3.91 KByte (WARNING: requested 1.95 KByte)
------------------------------------------------------------
[  3] local 192.168.0.119 port 48736 connected with 192.168.0.50 port 5001
[  3]  0.0-10.0 sec    203 MBytes    171 Mbits/sec


(6) Communication port (-p), timing (-t) and interval (-i):

server side:
$ iperf -s -p 12000
------------------------------------------------------------
Server listening on TCP port 12000
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 12000 connected with 192.168.0.119 port 40992
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec  2.19 GBytes   941 Mbits/sec

client side:
$ iperf -c 192.168.0.50 -p 12000 -t 20 -i 2
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 12000
TCP window size: 21.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.119 port 40992 connected with 192.168.0.50 port 12000
[  3]  0.0- 2.0 sec    227 MBytes    954 Mbits/sec
[  3]  2.0- 4.0 sec    223 MBytes    937 Mbits/sec
[  3]  4.0- 6.0 sec    224 MBytes    939 Mbits/sec
[  3]  6.0- 8.0 sec    225 MBytes    942 Mbits/sec
[  3]  8.0-10.0 sec    225 MBytes    943 Mbits/sec
[  3] 10.0-12.0 sec    224 MBytes    941 Mbits/sec
[  3] 12.0-14.0 sec    224 MBytes    939 Mbits/sec
[  3] 14.0-16.0 sec    224 MBytes    940 Mbits/sec
[  3] 16.0-18.0 sec    225 MBytes    945 Mbits/sec
[  3] 18.0-20.0 sec    224 MBytes    938 Mbits/sec
[  3]  0.0-20.0 sec  2.19 GBytes    942 Mbits/sec


(7) UDP tests: (-u), bandwidth settings (-b)

server side:
$ iperf -s -u -i 1 
------------------------------------------------------------
Server listening on UDP port 5001
Receiving 1470 byte datagrams
UDP buffer size:  224 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.50 port 5001 connected with 192.168.0.119 port 56239
[ ID] Interval       Transfer     Bandwidth        Jitter   Lost/Total Datagrams
[  3]  0.0- 1.0 sec  1.19 MBytes  10.0 Mbits/sec   0.001 ms    0/  850 (0%)
[  3]  1.0- 2.0 sec  1.19 MBytes  10.0 Mbits/sec   0.002 ms    0/  850 (0%)
[  3]  2.0- 3.0 sec  1.19 MBytes  10.0 Mbits/sec   0.001 ms    0/  851 (0%)
[  3]  3.0- 4.0 sec  1.19 MBytes  10.0 Mbits/sec   0.001 ms    0/  850 (0%)
[  3]  4.0- 5.0 sec  1.19 MBytes  10.0 Mbits/sec   0.001 ms    0/  851 (0%)
[  3]  5.0- 6.0 sec  1.19 MBytes  10.0 Mbits/sec   0.001 ms    0/  850 (0%)
[  3]  6.0- 7.0 sec  1.19 MBytes  10.0 Mbits/sec   0.015 ms    0/  850 (0%)
[  3]  7.0- 8.0 sec  1.19 MBytes  10.0 Mbits/sec   0.001 ms    0/  851 (0%)
[  3]  8.0- 9.0 sec  1.19 MBytes  10.0 Mbits/sec   0.002 ms    0/  850 (0%)
[  3]  9.0-10.0 sec  1.19 MBytes  10.0 Mbits/sec   0.002 ms    0/  851 (0%)
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec   0.002 ms    0/ 8504 (0%)
[  3]  0.0-10.0 sec  1 datagrams received out-of-order


client side:
$ iperf -c 192.168.0.50 -u -b 10m
------------------------------------------------------------
Client connecting to 192.168.0.50, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   160 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.119 port 56239 connected with 192.168.0.50 port 5001
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec
[  3] Sent 8505 datagrams
[  3] Server Report:
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec  0.002 ms    0/ 8504 (0%)
[  3]  0.0-10.0 sec  1 datagrams received out-of-order

```

[B]IPERF NETWORK TEST
From Windows 7 Pro x64 to Ubuntu Server[/B]
*using the same NIC*

```
(1) Test requested from ubuntu forum, current Thread

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 50543
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec   983 MBytes   412 Mbits/sec


client side:
c:\>iperf -c 192.168.0.50 -w 1024k -i 2 -t 20 -f M
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 1.00 MByte
------------------------------------------------------------
[156] local 127.0.0.1 port 50542 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0- 2.0 sec  96.1 MBytes  48.0 MBytes/sec
[156]  2.0- 4.0 sec  99.4 MBytes  49.7 MBytes/sec
[156]  4.0- 6.0 sec  99.5 MBytes  49.8 MBytes/sec
[156]  6.0- 8.0 sec  98.5 MBytes  49.2 MBytes/sec
[156]  8.0-10.0 sec   101 MBytes  50.6 MBytes/sec
[156] 10.0-12.0 sec  95.7 MBytes  47.8 MBytes/sec
[156] 12.0-14.0 sec  98.5 MBytes  49.2 MBytes/sec
[156] 14.0-16.0 sec  96.8 MBytes  48.4 MBytes/sec
[156] 16.0-18.0 sec  99.4 MBytes  49.7 MBytes/sec
[156] 18.0-20.0 sec  98.0 MBytes  49.0 MBytes/sec
[156]  0.0-20.0 sec   983 MBytes  49.1 MBytes/sec


(2) Tests suggested by openmaniak.com

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 50554
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   440 MBytes   369 Mbits/sec


client side:
c:\>iperf -c 192.168.0.50
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[156] local 127.0.0.1 port 50553 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0-10.0 sec   440 MBytes   369 Mbits/sec


(3) Bi-directional bandwidth measurement: (-r argument)

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 50613
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   435 MBytes   364 Mbits/sec
------------------------------------------------------------
Client connecting to 192.168.0.110, TCP port 5001
TCP window size:  108 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 34401 connected with 192.168.0.110 port 5001
[  4]  0.0-10.0 sec   496 MBytes   416 Mbits/sec


client side:
c:\>iperf -c 192.168.0.50 -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[180] local 127.0.0.1 port 50612 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[180]  0.0-10.0 sec   435 MBytes   364 Mbits/sec
[180] local 192.168.0.110 port 5001 connected with 192.168.0.50 port 34401
[ ID] Interval       Transfer     Bandwidth
[180]  0.0-10.0 sec   496 MBytes   416 Mbits/sec


(4) Simultaneous bi-directional bandwidth measurement: (-d argument)

server side:
$ iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 50618
------------------------------------------------------------
Client connecting to 192.168.0.110, TCP port 5001
TCP window size:  131 KByte (default)
------------------------------------------------------------
[  6] local 192.168.0.50 port 34402 connected with 192.168.0.110 port 5001
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   132 MBytes   111 Mbits/sec
[  6]  0.0-10.0 sec   422 MBytes   354 Mbits/sec


client side:
c:\>iperf -c 192.168.0.50 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[180] local 127.0.0.1 port 50617 connected with 192.168.0.50 port 5001
[196] local 192.168.0.110 port 5001 connected with 192.168.0.50 port 34402
[ ID] Interval       Transfer     Bandwidth
[196]  0.0-10.0 sec   422 MBytes   353 Mbits/sec
[180]  0.0-10.0 sec   132 MBytes   111 Mbits/sec


(5) TCP Window size: (-w argument)

server side:
$ iperf -s -w 4000
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 7.81 KByte (WARNING: requested 3.91 KByte)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 50621
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   173 MBytes   145 Mbits/sec


client side:
c:\>iperf -c 192.168.0.50 -w 2000
WARNING: TCP window size set to 2000 bytes. A small window size
will give poor performance. See the Iperf documentation.
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 1.95 KByte
------------------------------------------------------------
[156] local 127.0.0.1 port 50620 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0-10.0 sec   173 MBytes   145 Mbits/sec


(6) Communication port (-p), timing (-t) and interval (-i):

server side:
$ iperf -s -p 12000
------------------------------------------------------------
Server listening on TCP port 12000
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 12000 connected with 192.168.0.110 port 50623
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec  1.10 GBytes   474 Mbits/sec


client side:
c:\>iperf -c 192.168.0.50 -p 12000 -t 20 -i 2
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 12000
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[156] local 192.168.0.110 port 50623 connected with 192.168.0.50 port 12000
[ ID] Interval       Transfer     Bandwidth
[156]  0.0- 2.0 sec   111 MBytes   464 Mbits/sec
[156]  2.0- 4.0 sec   107 MBytes   447 Mbits/sec
[156]  4.0- 6.0 sec   111 MBytes   465 Mbits/sec
[156]  6.0- 8.0 sec   115 MBytes   483 Mbits/sec
[156]  8.0-10.0 sec   116 MBytes   487 Mbits/sec
[156] 10.0-12.0 sec   116 MBytes   486 Mbits/sec
[156] 12.0-14.0 sec   114 MBytes   476 Mbits/sec
[156] 14.0-16.0 sec   115 MBytes   481 Mbits/sec
[156] 16.0-18.0 sec   114 MBytes   477 Mbits/sec
[156] 18.0-20.0 sec   113 MBytes   473 Mbits/sec
[156]  0.0-20.0 sec  1.10 GBytes   474 Mbits/sec


(7) UDP tests: (-u), bandwidth settings (-b)

server side:
$ iperf -s -u -i 1
------------------------------------------------------------
Server listening on UDP port 5001
Receiving 1470 byte datagrams
UDP buffer size:  224 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 50070
[ ID] Interval       Transfer     Bandwidth        Jitter   Lost/Total Datagrams
[  3]  0.0- 1.0 sec  1.19 MBytes  10.0 Mbits/sec   0.033 ms    0/  850 (0%)
[  3]  1.0- 2.0 sec  1.19 MBytes  10.0 Mbits/sec   0.046 ms    0/  850 (0%)
[  3]  2.0- 3.0 sec  1.19 MBytes  10.0 Mbits/sec   0.042 ms    0/  851 (0%)
[  3]  3.0- 4.0 sec  1.19 MBytes  10.0 Mbits/sec   0.039 ms    0/  850 (0%)
[  3]  4.0- 5.0 sec  1.19 MBytes  10.0 Mbits/sec   0.066 ms    0/  850 (0%)
[  3]  5.0- 6.0 sec  1.19 MBytes  10.0 Mbits/sec   0.048 ms    0/  851 (0%)
[  3]  6.0- 7.0 sec  1.19 MBytes  10.0 Mbits/sec   0.030 ms    0/  850 (0%)
[  3]  7.0- 8.0 sec  1.19 MBytes  10.0 Mbits/sec   0.033 ms    0/  850 (0%)
[  3]  8.0- 9.0 sec  1.19 MBytes  10.0 Mbits/sec   0.043 ms    0/  851 (0%)
[  3]  9.0-10.0 sec  1.19 MBytes  10.0 Mbits/sec   0.034 ms    0/  850 (0%)
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec   0.049 ms    0/ 8505 (0%)


client side:
c:\>iperf -c 192.168.0.50 -u -b 10m
------------------------------------------------------------
Client connecting to 192.168.0.50, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size: 8.00 KByte (default)
------------------------------------------------------------
[156] local 192.168.0.110 port 50070 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec
[156] Server Report:
[156]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec  0.049 ms    0/ 8505 (0%)
[156] Sent 8505 datagrams

```

Spiro

---

### Post by tgalati4 on 2013-02-07
That is an interesting result.  My understanding is that Windows used Open Source networking code (TCP/IP stack) early in Windows development (Windows 3.0 perhaps) and so rarely do folks complain about Windows networking performance.

Your results are showing 44% reduction in Windows speed.  It could be Windows firewall, spyware or Windows defender or some other anti-virus running.

To answer your original post, your network speeds at 112 MB/sec are the theoretical maximums, so you are good there--no more improvement to be made.  And your disks are fast enough to keep up with those network speeds.

I don't use Windows anymore (and haven't for 10 years) so my guess that Windows had iperf was based on the TCP/IP stack that windows uses is similar to Unix and Linux.

Also, you are running a Live DVD in RAMdisk.  A real installation to hard disk will have syslog running, writing log files and system activity to hard disk, which may slow things down.  Also, you will have several services running on the linux machine eventually, and that may slow down performance.

Bring up task manager and delete all of those 100 useless services in Windows.  Bring it down to a basic minimum:  Probaby explorer.exe, systray.exe, and a few others.  Then rerun your tests as a comparison.

Another strange difference:

TCP window size: 0.25 MByte (WARNING: requested 1.00 MByte)

For some reason, running the Live DVD doesn't allow you to change the TCP window size.  So Linux is running 0.25 MB, or 250,000 Byte window versus 1MB with Windows.  The other difference is the payload size 225MB vs 96MB.  I don't know why there is this difference either.  I don't have a Win7 machine handy or booted at the moment to test against my machines.

But the bottom line:  Your hardware should maximize your current TCP/IP bandwidth on your network.

---

### Post by SAngeli on 2013-02-13
Hi,

finally I was able to perform some test booting in Windows Safe Mode.

Here is the results:
```
(1) Test requested from ubuntu forum, current Thread

server:
root@ubuntu:~# iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 49162
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec  2.21 GBytes   949 Mbits/sec


client:
C:\Temp>iperf -c 192.168.0.50 -w 1024k -i 2 -t 20 -f M
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 1.00 MByte
------------------------------------------------------------
[156] local 192.168.0.110 port 49162 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0- 2.0 sec   228 MBytes   114 MBytes/sec
[156]  2.0- 4.0 sec   226 MBytes   113 MBytes/sec
[156]  4.0- 6.0 sec   226 MBytes   113 MBytes/sec
[156]  6.0- 8.0 sec   226 MBytes   113 MBytes/sec
[156]  8.0-10.0 sec   226 MBytes   113 MBytes/sec
[156] 10.0-12.0 sec   226 MBytes   113 MBytes/sec
[156] 12.0-14.0 sec   226 MBytes   113 MBytes/sec
[156] 14.0-16.0 sec   226 MBytes   113 MBytes/sec
[156] 16.0-18.0 sec   226 MBytes   113 MBytes/sec
[156] 18.0-20.0 sec   226 MBytes   113 MBytes/sec
[156]  0.0-20.0 sec  2264 MBytes   113 MBytes/sec


(2) Tests suggested by openmaniak.com

root@ubuntu:~# iperf -s
server:
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 49165
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   766 MBytes   642 Mbits/sec


client:
C:\Temp>iperf -c 192.168.0.50
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[156] local 192.168.0.110 port 49165 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0-10.0 sec   766 MBytes   641 Mbits/sec


(3) Bi-directional bandwidth measurement: (-r argument)

server:
root@ubuntu:~# iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 49168
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   753 MBytes   631 Mbits/sec
------------------------------------------------------------
Client connecting to 192.168.0.110, TCP port 5001
TCP window size:  254 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 58079 connected with 192.168.0.110 port 5001
[  4]  0.0-10.0 sec  1.10 GBytes   941 Mbits/sec


client:
C:\Temp>iperf -c 192.168.0.50 -r
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[180] local 192.168.0.110 port 49168 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[180]  0.0-10.0 sec   753 MBytes   630 Mbits/sec
[116] local 192.168.0.110 port 5001 connected with 192.168.0.50 port 58079
[ ID] Interval       Transfer     Bandwidth
[116]  0.0-10.0 sec  1.10 GBytes   942 Mbits/sec


(4) Simultaneous bi-directional bandwidth measurement: (-d argument)

server:
root@ubuntu:~# iperf -s
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 49170
------------------------------------------------------------
Client connecting to 192.168.0.110, TCP port 5001
TCP window size:  239 KByte (default)
------------------------------------------------------------
[  6] local 192.168.0.50 port 58080 connected with 192.168.0.110 port 5001
[ ID] Interval       Transfer     Bandwidth
[  6]  0.0-10.0 sec  1.09 GBytes   938 Mbits/sec
[  4]  0.0-10.0 sec   214 MBytes   179 Mbits/sec

client:
C:\Temp>iperf -c 192.168.0.50 -d
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[180] local 192.168.0.110 port 49170 connected with 192.168.0.50 port 5001
[196] local 192.168.0.110 port 5001 connected with 192.168.0.50 port 58080
[ ID] Interval       Transfer     Bandwidth
[196]  0.0-10.0 sec  1.09 GBytes   937 Mbits/sec
[180]  0.0-10.0 sec   214 MBytes   179 Mbits/sec


(5) TCP Window size: (-w argument)

server:
root@ubuntu:~# iperf -s -w 4000
------------------------------------------------------------
Server listening on TCP port 5001
TCP window size: 7.81 KByte (WARNING: requested 3.91 KByte)
------------------------------------------------------------
[  4] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 49181
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-10.0 sec   252 MBytes   211 Mbits/sec


client:
C:\Temp>iperf -c 192.168.0.50 -w 2000
WARNING: TCP window size set to 2000 bytes. A small window size
will give poor performance. See the Iperf documentation.
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 5001
TCP window size: 1.95 KByte
------------------------------------------------------------
[156] local 192.168.0.110 port 49181 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0-10.0 sec   252 MBytes   211 Mbits/sec


(6) Communication port (-p), timing (-t) and interval (-i)

server:
root@ubuntu:~# iperf -s -p 12000
------------------------------------------------------------
Server listening on TCP port 12000
TCP window size: 85.3 KByte (default)
------------------------------------------------------------
[  4] local 192.168.0.50 port 12000 connected with 192.168.0.110 port 49178
[ ID] Interval       Transfer     Bandwidth
[  4]  0.0-20.0 sec  1.51 GBytes   647 Mbits/sec

client:
C:\Temp>iperf -c 192.168.0.50 -p 12000 -t 20 -i 2
------------------------------------------------------------
Client connecting to 192.168.0.50, TCP port 12000
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[156] local 192.168.0.110 port 49178 connected with 192.168.0.50 port 12000
[ ID] Interval       Transfer     Bandwidth
[156]  0.0- 2.0 sec   154 MBytes   647 Mbits/sec
[156]  2.0- 4.0 sec   152 MBytes   636 Mbits/sec
[156]  4.0- 6.0 sec   156 MBytes   655 Mbits/sec
[156]  6.0- 8.0 sec   156 MBytes   654 Mbits/sec
[156]  8.0-10.0 sec   153 MBytes   641 Mbits/sec
[156] 10.0-12.0 sec   154 MBytes   645 Mbits/sec
[156] 12.0-14.0 sec   152 MBytes   638 Mbits/sec
[156] 14.0-16.0 sec   154 MBytes   647 Mbits/sec
[156] 16.0-18.0 sec   156 MBytes   654 Mbits/sec
[156] 18.0-20.0 sec   156 MBytes   655 Mbits/sec
[156]  0.0-20.0 sec  1.51 GBytes   647 Mbits/sec


(7) UDP tests: (-u), bandwidth settings (-b)

server:
root@ubuntu:~# iperf -s -u -i 1
------------------------------------------------------------
Server listening on UDP port 5001
Receiving 1470 byte datagrams
UDP buffer size:  224 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.50 port 5001 connected with 192.168.0.110 port 55247
[ ID] Interval       Transfer     Bandwidth        Jitter   Lost/Total Datagrams
[  3]  0.0- 1.0 sec  1.19 MBytes  10.0 Mbits/sec   0.050 ms    0/  850 (0%)
[  3]  1.0- 2.0 sec  1.19 MBytes  10.0 Mbits/sec   0.050 ms    0/  850 (0%)
[  3]  2.0- 3.0 sec  1.19 MBytes  10.0 Mbits/sec   0.049 ms    0/  851 (0%)
[  3]  3.0- 4.0 sec  1.19 MBytes  10.0 Mbits/sec   0.050 ms    0/  850 (0%)
[  3]  4.0- 5.0 sec  1.19 MBytes  10.0 Mbits/sec   0.047 ms    0/  850 (0%)
[  3]  5.0- 6.0 sec  1.19 MBytes  10.0 Mbits/sec   0.046 ms    0/  851 (0%)
[  3]  6.0- 7.0 sec  1.19 MBytes  10.0 Mbits/sec   0.047 ms    0/  850 (0%)
[  3]  7.0- 8.0 sec  1.19 MBytes  10.0 Mbits/sec   0.047 ms    0/  850 (0%)
[  3]  8.0- 9.0 sec  1.19 MBytes  10.0 Mbits/sec   0.046 ms    0/  851 (0%)
[  3]  9.0-10.0 sec  1.19 MBytes  10.0 Mbits/sec   0.049 ms    0/  850 (0%)
[  3]  0.0-10.0 sec  11.9 MBytes  9.99 Mbits/sec   0.115 ms    0/ 8505 (0%)


client:
C:\Temp>iperf -c 192.168.0.50 -u -b 10m
------------------------------------------------------------
Client connecting to 192.168.0.50, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size: 8.00 KByte (default)
------------------------------------------------------------
[156] local 192.168.0.110 port 55247 connected with 192.168.0.50 port 5001
[ ID] Interval       Transfer     Bandwidth
[156]  0.0-10.0 sec  11.9 MBytes  9.99 Mbits/sec
[156] Server Report:
[156]  0.0-10.0 sec  11.9 MBytes  9.99 Mbits/sec  0.115 ms    0/ 8505 (0%)
[156] Sent 8505 datagrams
```

Here are few pictures for when I copy a large file from Windows to ubuntu server ext4 filesystem:
- [**1 pic**]("http://i.imgur.com/qQ8CVrm.png")
- [**2 pic **]("http://i.imgur.com/kcjZ3xL.png")

Here are 2 pictures for when I copy a large file from Windows to a VHD file hosted in ubuntu server ext4 filesystem:
- **[3 pic]("http://i.imgur.com/fCSx6DV.png")**
- **[4 pic]("http://i.imgur.com/dJWhZII.png")**

I just do not understand why copying to ext4 is way faster than to a VHD.
Moreover, I do not understand why in Safe Mode I am able to reach almost same results as between the Two linux OS.

Please let me know.
Thank you,
Spiro

---

