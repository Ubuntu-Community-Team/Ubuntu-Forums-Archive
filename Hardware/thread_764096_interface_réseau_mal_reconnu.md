---
title: "interface réseau mal reconnu"
date: 2008-04-23
forum: Hardware
---

### Post by aladion on 2008-04-23
Bonjour
J'utilise Ubuntu LTS Hardy heron avec les modules du generic 24.12
Mais je fais ifconfig et j'ai ce résultat


aladion@aladion-onyx:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:73:37:b4  
          inet addr:192.168.10.2  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:4bff:fe73:37b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8684 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8570812 (8.1 MB)  TX bytes:1416331 (1.3 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:136 errors:0 dropped:0 overruns:0 frame:0
          TX packets:136 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6800 (6.6 KB)  TX bytes:6800 (6.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:73:9d:bb:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-9D-BB-98-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Je voudrais pouvoir faire de mon pc le pc principal pour un partage de connection internet.Mon problème est au niveau de l'interface:

wmaster0  Link encap:UNSPEC  HWaddr 00-1A-73-9D-BB-98-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Qu'est ce à dire et quoi faire .Quand je vais voir mes outils réseau, cette carte est marquée non reconnue.Que faire?Merci d'avance pour l'aide

---

### Post by nathansoz on 2008-04-23
Does this need moved to the French Forums?

---

### Post by aladion on 2008-04-23
yes move it in a french forum if that can help me

---

