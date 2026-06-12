---
title: "Interpid Ibex Asus eee pc 701 wifi problems"
date: 2008-11-30
forum: Hardware
---

### Post by lefty_kreouzis on 2008-11-30
Hi to all,

I have an ASUS eee pc 701, I have installed Ubuntu 8.10 with the Ricey scripts and the linux-backports modules. I have black listed the ath_pci module and use the ath5k module. When I connect to the Wifi at home it connects immediately and the DHCP configuration works, however the actual connection is very flaky, e.g when pinging the eee I get times like the following:

64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1169 ttl=64 time=517 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1170 ttl=64 time=745 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1171 ttl=64 time=155 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1172 ttl=64 time=72.7 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1173 ttl=64 time=26.3 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1174 ttl=64 time=122 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1175 ttl=64 time=58.1 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1176 ttl=64 time=455 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1177 ttl=64 time=162 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1178 ttl=64 time=597 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1179 ttl=64 time=137 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1180 ttl=64 time=26.9 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1181 ttl=64 time=182 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1182 ttl=64 time=66.8 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1184 ttl=64 time=42208 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1185 ttl=64 time=53983 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1188 ttl=64 time=59153 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1189 ttl=64 time=58726 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1191 ttl=64 time=57404 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1192 ttl=64 time=56893 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1194 ttl=64 time=55775 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1197 ttl=64 time=54200 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1198 ttl=64 time=53379 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1249 ttl=64 time=9117 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1250 ttl=64 time=8115 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1251 ttl=64 time=7116 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1252 ttl=64 time=6113 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1253 ttl=64 time=5115 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1254 ttl=64 time=4118 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1255 ttl=64 time=3119 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1256 ttl=64 time=2119 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1257 ttl=64 time=1122 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1258 ttl=64 time=125 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1259 ttl=64 time=3.08 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1260 ttl=64 time=22.5 ms
64 bytes from leftys-toy.home.rtfm.gr (10.3.0.109): icmp_seq=1261 ttl=64 time=5.89 ms

When I had 8.04 installed with the madwifi drivers I didn't have any problems with wifi.

The above happens with 2.6.27-7-generic and 2.6.27-9-generic kernels. 

Thanks

Lefty

---

