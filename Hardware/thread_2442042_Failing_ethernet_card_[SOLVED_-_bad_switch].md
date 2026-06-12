---
title: "Failing ethernet card? [SOLVED - bad switch]"
date: 2020-04-29
forum: Hardware
---

### Post by jayswenb on 2020-04-29
Hello all,
I'm new to Ubuntu with the new LTS release and fairly new to linux generally. This desktop conversion was my last WIN holdout!!!

Tonight I started getting network connection failures on my wired connection. The wireless connects just fine. The wired MAC isn't receiving an IP address although, to me, the card appears to be active and working. The computer previously received a static IP from router and it had been working fine after the Ubuntu install until this evening.

```
jay@jollymon:~$ ifconfig
        enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::e274:ea7e:1db6:1b5b  prefixlen 64  scopeid 0x20<link>
        ether 98:ee:cb:47:c0:49  txqueuelen 1000  (Ethernet)
        RX packets 252  bytes 62064 (62.0 KB)
        RX errors 0  dropped 39  overruns 0  frame 0
        TX packets 196  bytes 51960 (51.9 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 5649  bytes 496142 (496.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5649  bytes 496142 (496.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.115  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::5c48:9d78:79ac:257  prefixlen 64  scopeid 0x20<link>
        ether 84:ef:18:09:2c:d4  txqueuelen 1000  (Ethernet)
        RX packets 27701  bytes 23154383 (23.1 MB)
        RX errors 0  dropped 1  overruns 0  frame 0
        TX packets 25729  bytes 3716761 (3.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



```

The link light on the NIC is blinking and the switch indicates a 1Gb link to the NIC

```
jay@jollymon:~$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 98:ee:cb:47:c0:49 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP mode DORMANT group default qlen 1000
    link/ether 84:ef:18:09:2c:d4 brd ff:ff:ff:ff:ff:ff



```

```
jay@jollymon:~$ inxi -Fz
  System:
  Kernel: 5.4.0-28-generic x86_64 bits: 64 Desktop: Gnome 3.36.1 
  Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Desktop System: Acer product: Aspire TC-780 v: N/A serial: <filter> 
  Mobo: Acer model: Aspire TC-780 serial: <filter> UEFI: American Megatrends 
  v: R01-A1 date: 06/22/2016 
CPU:
  Topology: Quad Core model: Intel Core i5-6400 bits: 64 type: MCP 
  L2 cache: 6144 KiB 
  Speed: 1000 MHz min/max: 800/3300 MHz Core speeds (MHz): 1: 1039 2: 1071 
  3: 1074 4: 1092 
Graphics:
  Device-1: Intel HD Graphics 530 driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.8 driver: i915 resolution: 1920x1080~60Hz 
  OpenGL: renderer: Mesa Intel HD Graphics 530 (SKL GT2) v: 4.6 Mesa 20.0.4 
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k5.4.0-28-generic 
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet 
  driver: r8169 
  IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter> 
  Device-2: Intel Wireless 3165 driver: iwlwifi 
  IF: wlp2s0 state: up mac: <filter> 
Drives:
  Local Storage: total: 2.07 TiB used: 18.10 GiB (0.9%) 
  ID-1: /dev/sda vendor: Crucial model: CT275MX300SSD4 size: 256.17 GiB 
  ID-2: /dev/sdb vendor: Seagate model: ST2000DM001-1ER164 size: 1.82 TiB 
Partition:
  ID-1: / size: 250.66 GiB used: 18.09 GiB (7.2%) fs: ext4 dev: /dev/sda2 
Sensors:
  System Temperatures: cpu: 45.5 C mobo: 29.8 C 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 253 Uptime: 39m Memory: 23.29 GiB used: 1.42 GiB (6.1%) 
  Shell: bash inxi: 3.0.38 



```

Is there anything I can do other than replacing the NIC? This computer is only 2-3 years old I believe.

Thanks for any help,
Jay

---

### Post by webaake on 2020-04-29
Did you try to set a static IP to the NIC manually? It could be a nuisance  if your moving around different networks, but it would show if your network card is working. In my experience threaded NIC's doesn't break that often, I've had maybe one go bad in 15 years.

---

### Post by jayswenb on 2020-04-29
I am able to manually assign a static IP from the computer and ifconfig confirms the address. However, the computer is not seen by the router. If the wired connection is active, it also appears to block the ability of the wireless connection to work as well. I have to turn off the wired to get any connectivity back.

---

### Post by jayswenb on 2020-04-29
There may be another solution. I tested my wife's computer on ethernet but that worked fine. She printed a document and that worked as well (it could have been directly wireless but I'm not sure). I hadn't been able to see the NAS from any other device despite it obviously running. I replaced the 8 port switch that all these connected with and my wired connection instantly returned. For the past 8 hours, it still runs as it did before.

I'm not quite done testing yet but there is definite progress.  Thanks for the help. You were right...the NIC wasn't the likely source but I didn't initially notice the NAS issue as well. I'll make sure to mark this thread [SOLVED] after a bit more successfully testing.

Jay

---

### Post by jayswenb on 2020-05-02
No problems over the past 2 days, no reboots of the router required, wired connection remains intact....SOLVED!!!!

---

