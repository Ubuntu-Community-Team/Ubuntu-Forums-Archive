---
title: "Update errors! can't get ANY updates"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by jcbnavy on 2008-12-18
I think something is corrupt with my software sources but not sure or even how to fix it. When I try to perform updates it cannot connect to any of the repositories to fetch updates.  I know my internet connection is working and I have tried to reset the software sources back to default so now I do not know what to try next.  Please Help

Jeff.

---

### Post by jrusso2 on 2008-12-18
Any error messages?  Please post your sources.list

---

### Post by jcbnavy on 2008-12-19
The only thing I get is when I go to get updates it said it "Could Not Download All Repository Indexes".  It acts like I don't have an internet connection but clearly I do.  I am not running through any proxies either.

Below is my sources.list file

# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
##deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) intrepid partner
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security main restricted multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) intrepid-security universe


Jeff

---

### Post by cariboo on 2008-12-19
Go to System-->Administration-->Software Sources and click the Download From Dropdown and select other. Next click Select Best Server and let it run through the server, once it is finished click Choose Server and you should be able to update.

Jim

---

### Post by jcbnavy on 2008-12-19
Okay just tried that and it said no suitable download server available and to check my Internet connection... but I am connected fine... with no firewall..

Jeff

---

### Post by digitalbrain on 2008-12-19
I have the same problem too. I'm using Hardy Heron.

---

### Post by Partyboi2 on 2008-12-19
Are you using a proxy?

---

### Post by jcbnavy on 2008-12-19
No proxy is used.

---

### Post by treepolitik on 2008-12-19
Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy Release.gpg                            
  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out
Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy/main Translation-en_US
  Unable to connect to akirad.hfbk.net http:
Fetched 1100kB in 2min0s (9090B/s)                  
W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg](http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg)  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out

W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2](http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to akirad.hfbk.net http:

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chris@chris-laptop:~$ 

Please advise, thank you.

---

### Post by Partyboi2 on 2008-12-19
> **treepolitik said:**
> Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy Release.gpg                            
  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out
Err [http://akirad.hfbk.net](http://akirad.hfbk.net) akirad-hardy/main Translation-en_US
  Unable to connect to akirad.hfbk.net http:
Fetched 1100kB in 2min0s (9090B/s)                  
W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg](http://akirad.hfbk.net/dists/akirad-hardy/Release.gpg)  Could not connect to akirad.hfbk.net:80 (193.174.241.68), connection timed out

W: Failed to fetch [http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2](http://akirad.hfbk.net/dists/akirad-hardy/main/i18n/Translation-en_US.bz2)  Unable to connect to akirad.hfbk.net http:

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Some index files failed to download, they have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
chris@chris-laptop:~$ 

Please advise, thank you.
 Try going to Software Sources (System>Admin>Software Sources) and on the first tab untick "Installable from cdrom/dvd" and close. Then open a terminal (Applications>Accessories>Terminal) and type
```
sudo dpkg --configure -a
```
then
```
sudo apt-get update
```

---

### Post by bapoumba on 2008-12-20
@ jcbnavy: please post the output to:
```
sudo apt-get update
```

@ treepolitik: please remove that [http://akirad.hfbk.net/](http://akirad.hfbk.net/) repo, the site looks down (I cannot access it either).

---

### Post by jcbnavy on 2008-12-20
:~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                   
  Connection failed
0% [Waiting for headers] [Waiting for headers]


It was sitting there for about ten minutes and I stopped it.  I tried this the other day and left for a few hours and when it finally finished it had a connection failed for every repository....

Jeff

---

### Post by bapoumba on 2008-12-20
> **jcbnavy said:**
> :~$ sudo apt-get update
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) intrepid Release.gpg
  Connection failed
Err [http://archive.canonical.com](http://archive.canonical.com) intrepid Release.gpg                   
  Connection failed
0% [Waiting for headers] [Waiting for headers]


It was sitting there for about ten minutes and I stopped it.  I tried this the other day and left for a few hours and when it finally finished it had a connection failed for every repository....

Jeff
Hmm. You mentioned you are not using a proxy. Have you ever used one (anon proxy or other)? Did you look at the Settings > Prefs > Network tab in synaptic ? System > Prefs > Network proxy from main menu ?

Please post the output of
```
ifconfig
ping us.archive.ubuntu.com
```

```
bapoumba@SonyBlue:~$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.88.40) 56(84) bytes of data.
64 bytes from 91.189.88.40: icmp_seq=1 ttl=51 time=57.7 ms
64 bytes from 91.189.88.40: icmp_seq=2 ttl=51 time=57.5 ms
64 bytes from 91.189.88.40: icmp_seq=3 ttl=51 time=57.1 ms

--- us.archive.ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 30119ms
rtt min/avg/max/mdev = 57.116/57.451/57.701/0.246 ms

```

---

### Post by jcbnavy on 2008-12-20
I check the places you said to look for the proxy settings and they are all set to direct connection.  

:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:70:ff:5f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:fc:2c:a3:4f  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe2c:a34f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:155617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80661 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114193856 (114.1 MB)  TX bytes:12145384 (12.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-2C-A3-4F-33-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

:~$ ping us.archive.ubuntu.com
PING us.archive.ubuntu.com (91.189.88.40) 56(84) bytes of data.
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=1 ttl=50 time=121 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=2 ttl=50 time=123 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=3 ttl=50 time=125 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=4 ttl=50 time=119 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=5 ttl=50 time=125 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=6 ttl=50 time=125 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=7 ttl=50 time=121 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=8 ttl=50 time=131 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=9 ttl=50 time=131 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=10 ttl=50 time=120 ms
64 bytes from drescher.canonical.com (91.189.88.40): icmp_seq=11 ttl=50 time=119 ms
--- us.archive.ubuntu.com ping statistics ---
13 packets transmitted, 13 received, 0% packet loss, time 12046ms
rtt min/avg/max/mdev = 119.846/123.836/131.508/3.822 ms



jeff

---

### Post by jcbnavy on 2008-12-21
Ok so out of nowhere it pulled updates...but now it won't download the updates it found.  I didn't do anything that I know of that made it pull updates...came home and there they were. So now I have to figure out why they won't download.
Idea's?  

Jeff

---

### Post by jcbnavy on 2008-12-21
I restarted my computer and it downloaded everything fine.  Not sure what the issue was.  Have been having this problem for a month and now out of nowhere it works...

Thanks for all your help.

Jeff

---

### Post by jaxxm on 2009-03-17
> **bapoumba said:**
> Hmm. You mentioned you are not using a proxy. Have you ever used one (anon proxy or other)? Did you look at the Settings > Prefs > Network tab in synaptic ? System > Prefs > Network proxy from main menu ?



when did i set this. I can't remember setting this.:redface:

thanks it worked.

---

### Post by bapoumba on 2009-03-17
Glad to see you got it to work :)
(I am very sorry I did not reply the other time around as you had stated all was fine, and I had no explanation).

---

