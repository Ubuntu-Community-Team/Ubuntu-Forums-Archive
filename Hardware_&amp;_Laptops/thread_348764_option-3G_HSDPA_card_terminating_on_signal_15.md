---
title: "option-3G HSDPA card: terminating on signal 15"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by martinko01 on 2007-01-29
Trying to get an option-3g HSDPA datacard running, nozomi is installed with patch, /dev/noz0 linked to /dev/modem, I can talk to the modem via AT command, KPPP tries to make connection, but "Terminating on signal 15".
There is definitely no PIN set on this card, that is, it is turned off. 
Anybody seen this problem ? Anybody an idea what "signal 15" is here ?

Jan 25 10:08:09 t41 pppd[3985]: pppd 2.4.4 started by martin, uid 1000
Jan 25 10:08:09 t41 pppd[3985]: using channel 5
Jan 25 10:08:09 t41 pppd[3985]: Using interface ppp0
Jan 25 10:08:09 t41 pppd[3985]: Connect: ppp0 <--> /dev/noz0
Jan 25 10:08:09 t41 pppd[3985]: sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x63b9818e> <pcomp> <accomp>]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [LCP ConfReq id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x10ee4b20> <pcomp> <accomp>]
Jan 25 10:08:09 t41 pppd[3985]: sent [LCP ConfAck id=0x0 <asyncmap 0x0> <auth chap MD5> <magic 0x10ee4b20> <pcomp> <accomp>]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [LCP ConfAck id=0x1 <asyncmap 0x0> <magic 0x63b9818e> <pcomp> <accomp>]
Jan 25 10:08:09 t41 pppd[3985]: sent [LCP EchoReq id=0x0 magic=0x63b9818e]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [LCP DiscReq id=0x1 magic=0x10ee4b20]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [CHAP Challenge id=0x1 <5455f5ccea66b5fe4a0f7837b8df33ab>, name = "UMTS_CHAP_SRVR"]
Jan 25 10:08:09 t41 pppd[3985]: sent [CHAP Response id=0x1 <58d64d55e0e55a21cbe6286850146820>, name = "user"]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [LCP EchoRep id=0x0 magic=0x10ee4b20 63 b9 81 8e]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [CHAP Success id=0x1 ""]
Jan 25 10:08:09 t41 pppd[3985]: CHAP authentication succeeded
Jan 25 10:08:09 t41 pppd[3985]: CHAP authentication succeeded
Jan 25 10:08:09 t41 pppd[3985]: sent [CCP ConfReq id=0x1 <deflate 15> <deflate(old#) 15> <bsd v1 15>]
Jan 25 10:08:09 t41 pppd[3985]: sent [IPCP ConfReq id=0x1 <addr 0.0.0.0> <ms-dns1 0.0.0.0> <ms-dns3 0.0.0.0>]
Jan 25 10:08:09 t41 pppd[3985]: rcvd [LCP ProtRej id=0x2 80 fd 01 01 00 0f 1a 04 78 00 18 04 78 00 15 03 2f]
Jan 25 10:08:09 t41 pppd[3985]: Protocol-Reject for 'Compression Control Protocol' (0x80fd) received
Jan 25 10:08:10 t41 pppd[3985]: rcvd [IPCP ConfNak id=0x1 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jan 25 10:08:10 t41 pppd[3985]: sent [IPCP ConfReq id=0x2 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
Jan 25 10:08:11 t41 pppd[3985]: rcvd [IPCP ConfNak id=0x2 <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14> <ms-wins 10.11.12.13> <ms-wins 10.11.12.14>]
Jan 25 10:08:11 t41 pppd[3985]: sent [IPCP ConfReq id=0x3 <addr 0.0.0.0> <ms-dns1 10.11.12.13> <ms-dns3 10.11.12.14>]
Jan 25 10:08:39 t41 pppd[3985]: Terminating on signal 15
Jan 25 10:08:39 t41 pppd[3985]: sent [LCP TermReq id=0x2 "User request"]
Jan 25 10:08:42 t41 pppd[3985]: sent [LCP TermReq id=0x3 "User request"]
Jan 25 10:08:45 t41 pppd[3985]: Connection terminated.
Jan 25 10:08:45 t41 pppd[3985]: Modem hangup
Jan 25 10:08:45 t41 pppd[3985]: Exit.

---

