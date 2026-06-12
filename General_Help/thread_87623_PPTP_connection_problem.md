---
title: "PPTP connection problem"
date: 2005-11-08
forum: General Help
---

### Post by michux on 2005-11-08
Hello... 
I'm having problem connecting to my company's VPN via PPTP
I used this howto: [http://pptpclient.sourceforge.net/howto-debian.phtml](http://pptpclient.sourceforge.net/howto-debian.phtml)
But i'm getting errors: 

# pon empolis debug dump logfd 2 nodetach
pppd options in effect:
debug           # (from command line)
nodetach                # (from command line)
logfd 2         # (from command line)
dump            # (from command line)
noauth          # (from /etc/ppp/options.pptp)
name EMPOLIS\\musie01           # (from /etc/ppp/peers/empolis)
remotename PPTP         # (from /etc/ppp/peers/empolis)
                # (from /etc/ppp/options.pptp)
pty pptp 62.52.27.138 --nolaunchpppd            # (from /etc/ppp/peers/empolis)
crtscts         # (from /etc/ppp/options)
                # (from /etc/ppp/options)
asyncmap 0              # (from /etc/ppp/options)
lcp-echo-failure 4              # (from /etc/ppp/options)
lcp-echo-interval 30            # (from /etc/ppp/options)
hide-password           # (from /etc/ppp/options)
ipparam empolis         # (from /etc/ppp/peers/empolis)
proxyarp                # (from /etc/ppp/options)
nobsdcomp               # (from /etc/ppp/options.pptp)
nodeflate               # (from /etc/ppp/options.pptp)
require-mppe-128                # (from /etc/ppp/peers/empolis)
noipx           # (from /etc/ppp/options)
using channel 3
Using interface ppp0

Connect: ppp0 <--> /dev/pts/2
[...]
Sent control packet type is 7 'Outgoing-Call-Request'
Nov  8 19:43:40 localhost pptp[8846]: anon log[ctrlp_disp:pptp_ctrl.c:841]: Received Outgoing Call Reply.
Nov  8 19:43:40 localhost pptp[8846]: anon log[ctrlp_disp:pptp_ctrl.c:880]: Outgoing call established (call ID 0, peer's call ID 12192).
Nov  8 19:43:41 localhost pptp[8846]: anon log[ctrlp_disp:pptp_ctrl.c:933]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov  8 19:43:41 localhost pptp[8846]: anon warn[ctrlp_disp:pptp_ctrl.c:939]: Non-zero Async Control Character Maps are not supported!
Nov  8 19:43:42 localhost pptp[8846]: anon log[ctrlp_disp:pptp_ctrl.c:933]: PPTP_SET_LINK_INFO received from peer_callid 0
Nov  8 19:43:42 localhost pptp[8846]: anon warn[ctrlp_disp:pptp_ctrl.c:939]: Non-zero Async Control Character Maps are not supported!
Nov  8 19:43:42 localhost pppd[8832]: LCP terminated by peer (VM-uEM-}
[...]
Nov  8 19:43:50 localhost pptp[8846]: anon log[ctrlp_rep:pptp_ctrl.c:243]: Sent control packet type is 12 'Call-Clear-Request


I cannot find much info about those errors on Google. ANy help would be appreciated.

---

