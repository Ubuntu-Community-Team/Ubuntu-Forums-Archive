---
title: "VPN connection to Windows (NT/2003)"
date: 2005-02-11
forum: Hardware &amp; Laptops
---

### Post by fenix03 on 2005-02-11
I've been trying to setup a VPN connection to my workplace using PPTP (installed pptp and pptpconfig) but I cannot seem to get it working. Domain name, user and password are all correct but it still says that it cannot authenticate.

Am I missing something here? I'm using dhcp to my ISP with an ADSL modem, default gateway is setup automatically. Do I need to fiddle with route? Any suggestions?

Log below. 
--
athome:/etc/ppp/# pon company debug dump logfd 2 nodetach

pppd options in effect:
debug # (from command line)
nodetach # (from command line)
logfd 2 # (from command line)
dump # (from command line)
noauth # (from /etc/ppp/options.pptp)
user XX.XXX.XX\\user # (from /etc/ppp/peers/company)
remotename PPTP # (from /etc/ppp/peers/company)
# (from /etc/ppp/options.pptp)
pty pptp XXX.XXX.XXX.XXX --nolaunchpppd # (from /etc/ppp/peers/company)
crtscts # (from /etc/ppp/options)
# (from /etc/ppp/options)
asyncmap 0 # (from /etc/ppp/options)
lcp-echo-failure 4 # (from /etc/ppp/options)
lcp-echo-interval 30 # (from /etc/ppp/options)
hide-password # (from /etc/ppp/peers/company)
ipparam iprobe # (from /etc/ppp/peers/company)
noipdefault # (from /etc/ppp/peers/company)
proxyarp # (from /etc/ppp/options)
nobsdcomp # (from /etc/ppp/options.pptp)
nodeflate # (from /etc/ppp/options.pptp)
require-mppe # (from /etc/ppp/peers/company)
noipx # (from /etc/ppp/options)
using channel 62
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x77d046ae> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x77d046ae> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 338> <auth chap MS-v2> <magic 0x9c52b7a2> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 338> <auth chap MS-v2> <magic 0x9c52b7a2> <pcomp> <accomp>]
rcvd [LCP ConfRej id=0x1 <asyncmap 0x0>]
sent [LCP ConfReq id=0x2 <magic 0x77d046ae> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <magic 0x77d046ae> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x77d046ae]
rcvd [CHAP Challenge id=0x1 <8032d3d178a26f9a0945601847992846>, name = "watchguard"]
sent [CHAP Response id=0x1 < 777d286118fe13a2544637ed640f52fd00000000000000002fdd6c5a28e3
7b0a59924015bff341f3e738a7a8eb57f07d00>, name = "XX.XXX.XX\\user"]
rcvd [LCP EchoRep id=0x0 magic=0x9c52b7a2]
rcvd [CHAP Success id=0x1 "S=f956ca36800197d4c645e1adae8fae28f8d6bfd2"]
MS-CHAPv2 mutual authentication failed.
sent [LCP TermReq id=0x3 "Failed to authenticate ourselves to peer"]
rcvd [IPCP ConfReq id=0x1 <addr 192.168.111.1>]
Discarded non-LCP packet when LCP not open
rcvd [LCP TermAck id=0x3]
Connection terminated.

---

### Post by xristos on 2005-05-04
[QUOTE=fenix03]I've been trying to setup a VPN connection to my workplace using PPTP (installed pptp and pptpconfig) but I cannot seem to get it working. Domain name, user and password are all correct but it still says that it cannot authenticate.

Am I missing something here? I'm using dhcp to my ISP with an ADSL modem, default gateway is setup automatically. Do I need to fiddle with route? Any suggestions?

Log below. 
--
athome:/etc/ppp/# pon company debug dump logfd 2 nodetach

pppd options in effect:
debug # (from command line)
nodetach # (from command line)
logfd 2 # (from command line)
dump # (from command line)
noauth # (from /etc/ppp/options.pptp)
user XX.XXX.XX\\user # (from /etc/ppp/peers/company)
remotename PPTP # (from /etc/ppp/peers/company)
# (from /etc/ppp/options.pptp)
pty pptp XXX.XXX.XXX.XXX --nolaunchpppd # (from /etc/ppp/peers/company)
crtscts # (from /etc/ppp/options)
# (from /etc/ppp/options)
asyncmap 0 # (from /etc/ppp/options)
lcp-echo-failure 4 # (from /etc/ppp/options)
lcp-echo-interval 30 # (from /etc/ppp/options)
hide-password # (from /etc/ppp/peers/company)
ipparam iprobe # (from /etc/ppp/peers/company)
noipdefault # (from /etc/ppp/peers/company)
proxyarp # (from /etc/ppp/options)
nobsdcomp # (from /etc/ppp/options.pptp)
nodeflate # (from /etc/ppp/options.pptp)
require-mppe # (from /etc/ppp/peers/company)
noipx # (from /etc/ppp/options)
using channel 62
Using interface ppp0
Connect: ppp0 <--> /dev/pts/2
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x77d046ae> <pcomp> <accomp>]
sent [LCP ConfReq id=0x1 <asyncmap 0x0> <magic 0x77d046ae> <pcomp> <accomp>]
rcvd [LCP ConfReq id=0x1 <mru 338> <auth chap MS-v2> <magic 0x9c52b7a2> <pcomp> <accomp>]
sent [LCP ConfAck id=0x1 <mru 338> <auth chap MS-v2> <magic 0x9c52b7a2> <pcomp> <accomp>]
rcvd [LCP ConfRej id=0x1 <asyncmap 0x0>]
sent [LCP ConfReq id=0x2 <magic 0x77d046ae> <pcomp> <accomp>]
rcvd [LCP ConfAck id=0x2 <magic 0x77d046ae> <pcomp> <accomp>]
sent [LCP EchoReq id=0x0 magic=0x77d046ae]
rcvd [CHAP Challenge id=0x1 <8032d3d178a26f9a0945601847992846>, name = "watchguard"]
sent [CHAP Response id=0x1 < 777d286118fe13a2544637ed640f52fd00000000000000002fdd6c5a28e3
7b0a59924015bff341f3e738a7a8eb57f07d00>, name = "XX.XXX.XX\\user"]
rcvd [LCP EchoRep id=0x0 magic=0x9c52b7a2]
rcvd [CHAP Success id=0x1 "S=f956ca36800197d4c645e1adae8fae28f8d6bfd2"]
MS-CHAPv2 mutual authentication failed.
sent [LCP TermReq id=0x3 "Failed to authenticate ourselves to peer"]
rcvd [IPCP ConfReq id=0x1 <addr 192.168.111.1>]
Discarded non-LCP packet when LCP not open
rcvd [LCP TermAck id=0x3]
Connection terminated.[/QUOTE]
 Not sure but here's an idea :
Go to your /etc/ppp/options file and find a line that says something about "authentication" and comment it out ( put # in front of it ) .
 That should be the same as adding noauth in /etc/ppp/options.pptp but for some unknown reason it is not .

Hoped  I helped

---

