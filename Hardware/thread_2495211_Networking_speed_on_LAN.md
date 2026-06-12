---
title: "Networking speed on LAN"
date: 2024-02-11
forum: Hardware
---

### Post by d3ntin on 2024-02-11
Good afternoon everyone!
I'm in the middle of setting up a small home LAN, using a router provided by my ISP. By now I have my desktop and a Raspberry Pi 4 connected; I'll configure the Pi as a NAS and with PiHole.
Not a networking pro at all, I'm learning on my way.
Current problem is networking speed.
I am sure that my pc has a Gigabit ethernet port, and also the Pi and the router has one. Here is the output of *ethtool* on both my desktop:

```

[FONT=monospace][COLOR=#000000]Settings for enp7s0: [/COLOR]
        Supported ports: [ TP ] 
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supported pause frame use: Symmetric Receive-only 
        Supports auto-negotiation: Yes 
        Supported FEC modes: Not reported 
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: Symmetric 
        Advertised auto-negotiation: Yes 
        Advertised FEC modes: Not reported 
        Speed: 100Mb/s 
        Duplex: Full 
        Auto-negotiation: on 
        Port: Twisted Pair 
        PHYAD: 0 
        Transceiver: internal 
        MDI-X: Unknown 
netlink error: Operation not permitted 
        Current message level: 0x000060e4 (24804) 
                               link ifup rx_err tx_err hw wol 
        Link detected: yes
[/FONT]
```[FONT=monospace]

and my Pi:

[/FONT]```
[FONT=monospace][COLOR=#000000]
Settings for eth0: [/COLOR]
        Supported ports: [ TP    MII ] 
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Supported pause frame use: Symmetric Receive-only 
        Supports auto-negotiation: Yes 
        Supported FEC modes: Not reported 
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Half 1000baseT/Full 
        Advertised pause frame use: Symmetric Receive-only 
        Advertised auto-negotiation: Yes 
        Advertised FEC modes: Not reported 
        Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                             100baseT/Half 100baseT/Full 
                                             1000baseT/Full 
        Link partner advertised pause frame use: Symmetric 
        Link partner advertised auto-negotiation: Yes 
        Link partner advertised FEC modes: Not reported 
        Speed: 1000Mb/s 
        Duplex: Full 
        Auto-negotiation: on 
        master-slave cfg: preferred slave 
        master-slave status: slave 
        Port: Twisted Pair 
        PHYAD: 1 
        Transceiver: external 
        MDI-X: Unknown 
netlink error: Operation not permitted 
        Current message level: 0x00000007 (7) 
                               drv probe link 
        Link detected: yes
[/FONT]
```[FONT=monospace]

Why is my pc working at only 100Mb/s? My desktop is connected through a cable running through the wall, but it is a CAT5e cable, while teh Pi is connected using a pre-made cable directly to the router...[/FONT][FONT=monospace]by now, 100Mb/s is ok for regular internet navigation, but since I'm setting up a NAS, it would be good to have a Gigabit connection...

[/FONT]

---

### Post by TheFu on 2024-02-11
Everything between the Pi and the desktop need to support GigE networking.

For testing performance, I use iperf3.  Run 1 side as the server and the other side as the client.  Let me go turn on my Pi4 .... it is in another room.  It didn't have iperf3 installed, so I installed it:
```
$ sudo apt install iperf3
```
My Pi runs
```
$ lsb_release -d
Description:    Debian GNU/Linux 11 (bullseye)

```
My pi doesn't have a firewall enabled, so it will be the "server" ... on the pi, 
```
$ iperf3 -s
-----------------------------------------------------------
Server listening on 5201
-----------------------------------------------------------

```
**The connectivity**
The pi4 connects through a GigE switch (sb) in that room, back to a patch panel in a wiring closet, then to a GigE switch (sa) on my rack. That GigE switch connects to a specific port on a GigE router (r0).  My "client" workstation connects to the GigE switch (sa), so the router won't be involved in any traffic.  The workstation uses CAT6 cables into the different switches.  The other connections use CAT5e. They are both over 30 ft, so about 60 ft (20m) of ethernet cable is involved between the 2 systems.

Ok, the client runs:
```
$ iperf3 -c pi4
Connecting to host pi4, port 5201
[  5] local 172.22.22.20 port 42768 connected to 172.22.22.17 port 5201
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd
[  5]   0.00-1.00   sec   114 MBytes   958 Mbits/sec    0    382 KBytes       
[  5]   1.00-2.00   sec   112 MBytes   939 Mbits/sec    0    382 KBytes       
[  5]   2.00-3.00   sec   113 MBytes   948 Mbits/sec    0    455 KBytes       
[  5]   3.00-4.00   sec   112 MBytes   940 Mbits/sec    0    475 KBytes       
[  5]   4.00-5.00   sec   113 MBytes   945 Mbits/sec    0    527 KBytes       
[  5]   5.00-6.00   sec   112 MBytes   941 Mbits/sec    0    551 KBytes       
[  5]   6.00-7.00   sec   112 MBytes   938 Mbits/sec    0    551 KBytes       
[  5]   7.00-8.00   sec   113 MBytes   948 Mbits/sec    0    551 KBytes       
[  5]   8.00-9.00   sec   112 MBytes   938 Mbits/sec    0    551 KBytes       
[  5]   9.00-10.00  sec   112 MBytes   938 Mbits/sec    0    551 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bitrate         Retr
[  5]   0.00-10.00  sec  1.10 GBytes   943 Mbits/sec    0             sender
[  5]   0.00-10.04  sec  1.10 GBytes   937 Mbits/sec                  receiver

iperf Done.

```
So, the raspberry pi v4 definitely supports GigE networking.  I can only say that you need to check all the switches, routers, and cables support GigE.

My pi4 doesn't have any storage that is suitable for backups. It just has MicroSD with the OS.  
```
$ dft    # <---- that's an alias that only shows "real" storage.
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/mmcblk0p2 ext4   29G  2.0G   26G   7% /
/dev/mmcblk0p1 vfat  316M   62M  254M  20% /boot

```

I have an NTFS USB3-SATA-SSD drive handy. Let's see how well it works for storage ... I'll just push large TV recording using rsync (ssh overhead) and see what I can do to make it faster, assuming it mounts easily.  Ok, it did.  Here's the command:
```
$ rsync -avz --stats --progress  Two_and_a_Half_Men-S8E08.ts osmc@pi4:/media/Recordings/
sending incremental file list
Two_and_a_Half_Men-S8E08.ts
  1,755,502,264 100%   **18.50MB/s**    0:01:30 (xfr#1, to-chk=0/1)
,,,
sent 1,668,351,780 bytes  received 35 bytes  18,434,826.69 bytes/sec
total size is 1,755,502,264  speedup is 1.05
```

So, 18.50MB/s is 148Mbps.  Networking and files like to use bits vs bytes, so we need to ensure apples-to-apples.  That SATA-SSD-USB storage should do better.  I'd expect 100+Mbps even with the ssh encryption overhead.

Let's try **scp** instead of **rsync**.
```
$ scp Two_and_a_Half_Men-S8E08.ts  osmc@pi4:/media/Recordings/
Two_and_a_Half_Men-S8E08.ts                                              100% 1674MB  32.6MB/s   00:51
```
That's faster. Interesting.  Let me try to use **ncat**. I have to use a little math and I'll use "time" to get the transfer duration.
```
$ time ncat --send-only pi4 < Two_and_a_Half_Men-S8E08.ts

real    0m58.298s
user    0m0.338s
sys     0m0.825s
```
So that's slower than scp. Unexpected. 
1,755,502,264 / 58.298s = 28.72 MB/sec.

I felt that wasn't showing the expected results, so I tested with ncat between a VM and the VM host.
```
$ time ncat --send-only deneb  < Two_and_a_Half_Men-S8E08.ts

real    0m2.881s
user    0m0.252s
sys     0m0.557s
```
That's more what I'd expect.
1,755,502,264 / 2.881 = **581.12 MB/sec**. That feels slow.  What's the iperf3 between those systems?  Ok, iperf3 says **26.0 Gbits/sec** today between those systems.  Storage performance matters. That's probably the most important take-away from my runs.  But I'm certain that my systems are GigE or faster.

BTW, I use rdiff-backup for my nightly backups. The backup target storage runs on the VM host above, but on a dedicated HDD - an 8GB WD Black HDD.  While I don't get "MB/sec" information from the backups, I do see:
```
INFO: Backup Start:	2024-02-11-00:03:01
....
INFO:   Backup End:	2024-02-11-00:09:36

```
That's for 9 systems.  6:36 isn't all that much time, is it?
```
TotalDestinationSizeChange 1418 (1.38 KB)
TotalDestinationSizeChange 4745367 (4.53 MB)
TotalDestinationSizeChange 1289 (1.26 KB)
TotalDestinationSizeChange 1593 (1.56 KB)
TotalDestinationSizeChange 96320327 (91.9 MB)
TotalDestinationSizeChange 1035517 (1011 KB)
TotalDestinationSizeChange 665777 (650 KB)
TotalDestinationSizeChange 25359761 (24.2 MB)
TotalDestinationSizeChange 1877 (1.83 KB)
```
Not all that much changed yesterday on each system.

Hope that I've shown enough examples, commands, to help you figure out the issue on your side.

---

### Post by MAFoElffen on 2024-02-12
Both Microsoft and Intel, note that if everything is rated at 1000Base/T and evrything tests okay with them (PC, switches, router) then check your cabling, put into other ports, etc. That just stepping on a cable, or rolling it over with a chair can damage & degrade a cable enough to drop down to 100Base/T. 
> 
You need to check if the switch, router your computer is connected to supports Gigabit connection, if positive, the problem is in the cabling, even if the cable tester shows no problem, noise and poor signal strength in the cable make it authenticates the 100mpbs connection but not the Gigabit connection.


---

