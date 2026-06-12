---
title: "Internet won't work"
date: 2008-05-08
forum: Hardware
---

### Post by philipsone on 2008-05-08
I have installed ubuntu 6.06 on a thirteen years old Toshiba Satellite laptop with 256kb ram. Nearly all appears well except....

There is a Network Connection: eth0 to the ADSL router. Firefox can access the router admin at 192.168.1.1

BUT Firefox (or Evolution) cannot connect to the internet. The Toshiba can see other computers connected to the router and the other computers connected to the router and on the network continue to connect to the internet as usual. 

Can anyone please advise ?

With thanks

---

### Post by renzokuken on 2008-05-08
when connected what do you get from the following commands

```
ifconfig
```
```
ping www.google.com
```

---

### Post by philipsone on 2008-05-08
ian@MonOldTosh:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:39:12:56:3B
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:39ff:fe12:563b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:580 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:148180 (144.7 KiB)  TX bytes:60811 (59.3 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:15 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:772 (772.0 b)  TX bytes:772 (772.0 b)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

ian@MonOldTosh:~$ netstat -na
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State
tcp        0      0 127.0.0.1:43465         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:52927         0.0.0.0:*               LISTEN
tcp        0      0 127.0.0.1:43465         127.0.0.1:47683         ESTABLISHED
tcp        0      0 127.0.0.1:47683         127.0.0.1:43465         ESTABLISHED
udp        0      0 0.0.0.0:68              0.0.0.0:*
raw        0      0 0.0.0.0:1               0.0.0.0:*               7
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  3      [ ]         DGRAM                    13323    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     10655    /tmp/.gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     12245    /tmp/mapping-ian
unix  2      [ ]         DGRAM                    4964     @/org/kernel/udev/udevd
unix  2      [ ACC ]     STREAM     LISTENING     10881    /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     10959    @/tmp/hald-runner/dbus-tBOGJeYr4Q
unix  2      [ ACC ]     STREAM     LISTENING     11800    @/tmp/dbus-4iKcgVtFAtunix  2      [ ]         DGRAM                    10967    @/org/freedesktop/hal/udev_event
unix  2      [ ACC ]     STREAM     LISTENING     11420    /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     9632     /var/run/acpid.socketunix  2      [ ACC ]     STREAM     LISTENING     10935    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     10723    /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     11795    /tmp/ssh-EKrbFZ4857/agent.4857
unix  2      [ ACC ]     STREAM     LISTENING     11819    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  2      [ ACC ]     STREAM     LISTENING     11830    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  2      [ ACC ]     STREAM     LISTENING     10958    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  2      [ ACC ]     STREAM     LISTENING     11853    /tmp/.ICE-unix/4857
unix  2      [ ACC ]     STREAM     LISTENING     11863    /tmp/keyring-nL3eUd/socket
unix  2      [ ACC ]     STREAM     LISTENING     11876    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  2      [ ACC ]     STREAM     LISTENING     11905    /tmp/.esd-1000/socketunix  2      [ ACC ]     STREAM     LISTENING     11916    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  2      [ ACC ]     STREAM     LISTENING     11949    /tmp/orbit-ian/linc-133b-0-43c9cb9f27a0d
unix  2      [ ACC ]     STREAM     LISTENING     11978    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  2      [ ACC ]     STREAM     LISTENING     12007    /tmp/orbit-ian/linc-1345-0-4546456775bf9
unix  2      [ ACC ]     STREAM     LISTENING     12017    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  2      [ ACC ]     STREAM     LISTENING     12057    /tmp/orbit-ian/linc-134c-0-3345e5c77184c
unix  2      [ ACC ]     STREAM     LISTENING     12102    /tmp/orbit-ian/linc-134e-0-3345e5c62660b
unix  2      [ ACC ]     STREAM     LISTENING     12120    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  2      [ ACC ]     STREAM     LISTENING     12142    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  2      [ ACC ]     STREAM     LISTENING     12154    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  2      [ ACC ]     STREAM     LISTENING     12273    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  2      [ ACC ]     STREAM     LISTENING     12290    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  2      [ ACC ]     STREAM     LISTENING     12395    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  2      [ ACC ]     STREAM     LISTENING     12455    /tmp/orbit-ian/linc-1391-0-4ee32b326fac
unix  2      [ ACC ]     STREAM     LISTENING     12569    /tmp/orbit-ian/linc-13b7-0-5eca89d0a330b
unix  2      [ ACC ]     STREAM     LISTENING     20963    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20976
unix  3      [ ]         STREAM     CONNECTED     20975
unix  3      [ ]         STREAM     CONNECTED     20973    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     20972
unix  3      [ ]         STREAM     CONNECTED     20970    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20969
unix  3      [ ]         STREAM     CONNECTED     20968    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     20967
unix  3      [ ]         STREAM     CONNECTED     20966    /tmp/orbit-ian/linc-34b2-0-448202b8cd104
unix  3      [ ]         STREAM     CONNECTED     20965
unix  3      [ ]         STREAM     CONNECTED     20962    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     20961
unix  3      [ ]         STREAM     CONNECTED     20958    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     20957
unix  3      [ ]         STREAM     CONNECTED     20953    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     20952
unix  2      [ ]         DGRAM                    16362
unix  3      [ ]         STREAM     CONNECTED     12572    /tmp/orbit-ian/linc-13b7-0-5eca89d0a330b
unix  3      [ ]         STREAM     CONNECTED     12571
unix  3      [ ]         STREAM     CONNECTED     12568    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12567
unix  3      [ ]         STREAM     CONNECTED     12553    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12552
unix  3      [ ]         STREAM     CONNECTED     12462    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12461
unix  3      [ ]         STREAM     CONNECTED     12460    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12459
unix  3      [ ]         STREAM     CONNECTED     12458    /tmp/orbit-ian/linc-1391-0-4ee32b326fac
unix  3      [ ]         STREAM     CONNECTED     12457
unix  3      [ ]         STREAM     CONNECTED     12454    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12453
unix  3      [ ]         STREAM     CONNECTED     12449    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12448
unix  3      [ ]         STREAM     CONNECTED     12433    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12432
unix  3      [ ]         STREAM     CONNECTED     12431    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12430
unix  3      [ ]         STREAM     CONNECTED     12429    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12428
unix  3      [ ]         STREAM     CONNECTED     12423    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12422
unix  3      [ ]         STREAM     CONNECTED     12419    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12418
unix  3      [ ]         STREAM     CONNECTED     12417    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12416
unix  3      [ ]         STREAM     CONNECTED     12407    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12406
unix  3      [ ]         STREAM     CONNECTED     12404    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     12403
unix  3      [ ]         STREAM     CONNECTED     12402    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12401
unix  3      [ ]         STREAM     CONNECTED     12400    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12399
unix  3      [ ]         STREAM     CONNECTED     12398    /tmp/orbit-ian/linc-1376-0-61d60bc7c6e8f
unix  3      [ ]         STREAM     CONNECTED     12397
unix  3      [ ]         STREAM     CONNECTED     12394    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12393
unix  3      [ ]         STREAM     CONNECTED     12389    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12388
unix  3      [ ]         STREAM     CONNECTED     12324    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     12323
unix  3      [ ]         STREAM     CONNECTED     12322    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12321
unix  3      [ ]         STREAM     CONNECTED     12319    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12318
unix  3      [ ]         STREAM     CONNECTED     12317    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12316
unix  3      [ ]         STREAM     CONNECTED     12310    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12309
unix  3      [ ]         STREAM     CONNECTED     12307    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12306
unix  3      [ ]         STREAM     CONNECTED     12297    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12296
unix  3      [ ]         STREAM     CONNECTED     12295    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12294
unix  3      [ ]         STREAM     CONNECTED     12293    /tmp/orbit-ian/linc-137b-0-689c7fb4feec
unix  3      [ ]         STREAM     CONNECTED     12292
unix  3      [ ]         STREAM     CONNECTED     12289    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12288
unix  3      [ ]         STREAM     CONNECTED     12284    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12283
unix  3      [ ]         STREAM     CONNECTED     12280    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12279
unix  3      [ ]         STREAM     CONNECTED     12278    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12277
unix  3      [ ]         STREAM     CONNECTED     12276    /tmp/orbit-ian/linc-1378-0-689c7fb24878
unix  3      [ ]         STREAM     CONNECTED     12275
unix  3      [ ]         STREAM     CONNECTED     12272    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12271
unix  3      [ ]         STREAM     CONNECTED     12267    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12266
unix  3      [ ]         STREAM     CONNECTED     12249    /tmp/mapping-ian
unix  3      [ ]         STREAM     CONNECTED     12241
unix  3      [ ]         STREAM     CONNECTED     12210    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12209
unix  3      [ ]         STREAM     CONNECTED     12208    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12207
unix  3      [ ]         STREAM     CONNECTED     12200    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12199
unix  3      [ ]         STREAM     CONNECTED     12196    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     12195
unix  3      [ ]         STREAM     CONNECTED     12194    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12193
unix  3      [ ]         STREAM     CONNECTED     12186    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12185
unix  3      [ ]         STREAM     CONNECTED     12184    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12183
unix  3      [ ]         STREAM     CONNECTED     12182    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12180
unix  3      [ ]         STREAM     CONNECTED     12181    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12176
unix  3      [ ]         STREAM     CONNECTED     12173    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12172
unix  3      [ ]         STREAM     CONNECTED     12171    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12170
unix  3      [ ]         STREAM     CONNECTED     12163    /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     12162
unix  3      [ ]         STREAM     CONNECTED     12161    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  3      [ ]         STREAM     CONNECTED     12160
unix  3      [ ]         STREAM     CONNECTED     12159    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12158
unix  3      [ ]         STREAM     CONNECTED     12157    /tmp/orbit-ian/linc-1352-0-6099eaace1a76
unix  3      [ ]         STREAM     CONNECTED     12156
unix  3      [ ]         STREAM     CONNECTED     12153    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12152
unix  3      [ ]         STREAM     CONNECTED     12149    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12148
unix  3      [ ]         STREAM     CONNECTED     12147    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12146
unix  3      [ ]         STREAM     CONNECTED     12145    /tmp/orbit-ian/linc-1357-0-260a1733c663b
unix  3      [ ]         STREAM     CONNECTED     12144
unix  3      [ ]         STREAM     CONNECTED     12138    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12137
unix  3      [ ]         STREAM     CONNECTED     12134    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12133
unix  3      [ ]         STREAM     CONNECTED     12127    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12126
unix  3      [ ]         STREAM     CONNECTED     12125    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12124
unix  3      [ ]         STREAM     CONNECTED     12123    /tmp/orbit-ian/linc-1355-0-6099eaac76d40
unix  3      [ ]         STREAM     CONNECTED     12122
unix  3      [ ]         STREAM     CONNECTED     12119    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12118
unix  3      [ ]         STREAM     CONNECTED     12114    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12113
unix  3      [ ]         STREAM     CONNECTED     12110    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12109
unix  3      [ ]         STREAM     CONNECTED     12108    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12107
unix  2      [ ]         DGRAM                    12106
unix  3      [ ]         STREAM     CONNECTED     12105    /tmp/orbit-ian/linc-134e-0-3345e5c62660b
unix  3      [ ]         STREAM     CONNECTED     12104
unix  3      [ ]         STREAM     CONNECTED     12101    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12100
unix  3      [ ]         STREAM     CONNECTED     12094    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12093
unix  3      [ ]         STREAM     CONNECTED     12086    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12085
unix  3      [ ]         STREAM     CONNECTED     12082    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12074
unix  3      [ ]         STREAM     CONNECTED     12073    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     12072
unix  3      [ ]         STREAM     CONNECTED     12067    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12066
unix  3      [ ]         STREAM     CONNECTED     12062    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12061
unix  3      [ ]         STREAM     CONNECTED     12060    /tmp/orbit-ian/linc-134c-0-3345e5c77184c
unix  3      [ ]         STREAM     CONNECTED     12059
unix  3      [ ]         STREAM     CONNECTED     12056    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12055
unix  3      [ ]         STREAM     CONNECTED     12052    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12049
unix  3      [ ]         STREAM     CONNECTED     12045    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12044
unix  3      [ ]         STREAM     CONNECTED     12031    @/tmp/dbus-4iKcgVtFAtunix  3      [ ]         STREAM     CONNECTED     12030
unix  3      [ ]         STREAM     CONNECTED     12026    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12025
unix  3      [ ]         STREAM     CONNECTED     12023    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     12022
unix  3      [ ]         STREAM     CONNECTED     12020    /tmp/orbit-ian/linc-1343-0-45464567872a1
unix  3      [ ]         STREAM     CONNECTED     12019
unix  3      [ ]         STREAM     CONNECTED     12016    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12015
unix  3      [ ]         STREAM     CONNECTED     12012    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12011
unix  3      [ ]         STREAM     CONNECTED     12010    /tmp/orbit-ian/linc-1345-0-4546456775bf9
unix  3      [ ]         STREAM     CONNECTED     12009
unix  3      [ ]         STREAM     CONNECTED     12006    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     12005
unix  3      [ ]         STREAM     CONNECTED     12002    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     12001
unix  3      [ ]         STREAM     CONNECTED     11997    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11996
unix  3      [ ]         STREAM     CONNECTED     11990    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11989
unix  3      [ ]         STREAM     CONNECTED     11985    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     11984
unix  3      [ ]         STREAM     CONNECTED     11983    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     11982
unix  3      [ ]         STREAM     CONNECTED     11981    /tmp/orbit-ian/linc-1341-0-791dcb9943ef8
unix  3      [ ]         STREAM     CONNECTED     11980
unix  3      [ ]         STREAM     CONNECTED     11977    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11976
unix  3      [ ]         STREAM     CONNECTED     11973    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     11970
unix  3      [ ]         STREAM     CONNECTED     11964    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11963
unix  3      [ ]         STREAM     CONNECTED     11956    /tmp/.ICE-unix/4857
unix  3      [ ]         STREAM     CONNECTED     11955
unix  3      [ ]         STREAM     CONNECTED     11954    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11953
unix  3      [ ]         STREAM     CONNECTED     11952    /tmp/orbit-ian/linc-133b-0-43c9cb9f27a0d
unix  3      [ ]         STREAM     CONNECTED     11951
unix  3      [ ]         STREAM     CONNECTED     11948    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11947
unix  3      [ ]         STREAM     CONNECTED     11919    /tmp/orbit-ian/linc-1330-0-2feae26567812
unix  3      [ ]         STREAM     CONNECTED     11918
unix  3      [ ]         STREAM     CONNECTED     11915    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11914
unix  3      [ ]         STREAM     CONNECTED     11912    /tmp/.esd-1000/socketunix  3      [ ]         STREAM     CONNECTED     11910
unix  2      [ ]         STREAM                   11904
unix  3      [ ]         STREAM     CONNECTED     11894    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11893
unix  3      [ ]         STREAM     CONNECTED     11882    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  3      [ ]         STREAM     CONNECTED     11881
unix  3      [ ]         STREAM     CONNECTED     11880    /tmp/orbit-ian/linc-132e-0-721990b1bbec5
unix  3      [ ]         STREAM     CONNECTED     11879
unix  3      [ ]         STREAM     CONNECTED     11834    /tmp/orbit-ian/linc-12f9-0-15d0a1e14a18a
unix  3      [ ]         STREAM     CONNECTED     11833
unix  3      [ ]         STREAM     CONNECTED     11832    /tmp/orbit-ian/linc-1329-0-24f5d0b630232
unix  3      [ ]         STREAM     CONNECTED     11829
unix  2      [ ]         DGRAM                    11814
unix  3      [ ]         STREAM     CONNECTED     11808    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11807
unix  3      [ ]         STREAM     CONNECTED     11804    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11803
unix  3      [ ]         STREAM     CONNECTED     11802
unix  3      [ ]         STREAM     CONNECTED     11801
unix  3      [ ]         STREAM     CONNECTED     11417    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11412
unix  2      [ ]         DGRAM                    11409
unix  2      [ ]         DGRAM                    11390
unix  3      [ ]         STREAM     CONNECTED     11281    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11280
unix  3      [ ]         STREAM     CONNECTED     11263    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11261
unix  3      [ ]         STREAM     CONNECTED     11262    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11255
unix  3      [ ]         STREAM     CONNECTED     11211    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11206
unix  3      [ ]         STREAM     CONNECTED     11085    /var/run/acpid.socketunix  3      [ ]         STREAM     CONNECTED     11084
unix  3      [ ]         STREAM     CONNECTED     11089    @/tmp/hald-local/dbus-kiFDn2Ho3J
unix  3      [ ]         STREAM     CONNECTED     11079
unix  3      [ ]         STREAM     CONNECTED     10962    @/tmp/hald-runner/dbus-tBOGJeYr4Q
unix  3      [ ]         STREAM     CONNECTED     10961
unix  3      [ ]         STREAM     CONNECTED     10938
unix  3      [ ]         STREAM     CONNECTED     10937
unix  2      [ ]         DGRAM                    10758
unix  4      [ ]         STREAM     CONNECTED     10892    /tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10732
unix  2      [ ]         DGRAM                    9833
ian@MonOldTosh:~$ cat /etc/resolv.conf
nameserver 192.168.1.1
ian@MonOldTosh:~$ ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.

---

### Post by renzokuken on 2008-05-08
ok, so you appear to definately be connected to the actual internet. sounds more like a firefox problem to me.

here's a dumb but valid point as i have often overlooked it myself.....is your firefox set to work in Offline mode (File -> Work Offline)? i had a period where firefox always started in offline mode whether i was connected or not. took me a while to figure it out too.... >_<

failing that how do other browsers fair?

---

### Post by philipsone on 2008-05-08
Thanks - it is definitely on-line.
I will check another browser.

---

### Post by philipsone on 2008-05-08
It looks like getting another browser is a bit tricky since I'm not on-line.

---

### Post by renzokuken on 2008-05-08
haha, i didnt think of that......although, if you can ping google, you should be able to download from the repos.

try ```
sudo apt-get install kazehakase
```

this will (might hehe) install the kazehakase browser, try it and see if it works.....

---

### Post by philipsone on 2008-05-08
Thanks again.

E: Couldn't find package kazehakase.

But Evolution will not connect either.

---

### Post by philipsone on 2008-05-12
Hi Again

There is a happy ending (restart).

Summary:
I installed ubuntu 6.06 (from a downloaded Live CD) onto a 7 years old Toshiba Satellite (S2800-500) laptop with 256kb ram.
(Sorry I hastily said before it was 13 years old).
The reason I chose 6.06 was because of my limited RAM. The more recent Live CD versions appeared to require more than 256kb RAM.

6.06 installed OK except I could not get the internet up in spite of all your help. We tried.

I tried openSUSE in various forms and got the internet up with a few tweaks (disable IPv6) but got other problems (including sound).

I downloaded Ubuntu 8.04, yes Hardy Heron. I chose the alternate CD option which said it needed a minimum 256kb ram.
The Live CD needed 384kb RAM.

Result:
IT ALL WORKED straight out of the box. :lolflag:
It's a bit slow (Pentium III) but it all works.

It runs like a dream.
[www.3wiw.com](www.3wiw.com)

Thanks again for your help.

---

