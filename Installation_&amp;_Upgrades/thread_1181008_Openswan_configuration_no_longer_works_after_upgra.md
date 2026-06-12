---
title: "Openswan configuration no longer works after upgrade to 8.10"
date: 2009-06-07
forum: Installation &amp; Upgrades
---

### Post by jcoles on 2009-06-07
I have been using OpenSwan successfully since Ubuntu 7.04. When I upgraded from 8.04 to 8.10, my VPN stopped working. My  configuration also doesn't work on 9.04. 

Now I get phase 1 established, but cannot get phase 2:

104 "office" #1: STATE_MAIN_I1: initiate
003 "office" #1: received Vendor ID payload [Dead Peer Detection]
003 "office" #1: ignoring unknown Vendor ID payload [afca071368a1f1c96b8696fc77570100]
003 "office" #1: ignoring unknown Vendor ID payload [5062b335bc20db32c0d54465a2f70100]
003 "office" #1: ignoring unknown Vendor ID payload [1d6e178f6c2c0be284985465450fe9d4]
003 "office" #1: received Vendor ID payload [draft-ietf-ipsec-nat-t-ike-03] method set to=108 
106 "office" #1: STATE_MAIN_I2: sent MI2, expecting MR2
003 "office" #1: NAT-Traversal: Result using draft-ietf-ipsec-nat-t-ike-02/03: i am NATed
108 "office" #1: STATE_MAIN_I3: sent MI3, expecting MR3
004 "office" #1: STATE_MAIN_I4: ISAKMP SA established {auth=OAKLEY_PRESHARED_KEY cipher=oakley_3des_cbc_192 prf=oakley_sha group=modp1536}
117 "office" #2: STATE_QUICK_I1: initiate
010 "office" #2: STATE_QUICK_I1: retransmission; will wait 20s for response
010 "office" #2: STATE_QUICK_I1: retransmission; will wait 40s for response

until it gives up.

What do I change in my configuration? 

ipsec.conf: 

config setup
	# Debug-logging controls:  "none" for (almost) none, "all" for lots.
	# klipsdebug=none
	# plutodebug="control parsing"
	nat_traversal=yes
	# interfaces for ipsec %defaultroute is the default
	interfaces=%defaultroute

include /etc/ipsec.d/*.conf
#Disable Opportunistic Encryption
include /etc/ipsec.d/examples/no_oe.conf


connection conf file:

conn office 
 #left side is work
 left=<office gateway>
 leftsubnet=172.20.120.0/24
 #right side is home
 right=%defaultroute
 #IKE parameters
 keyexchange=ike
 #auth=esp
 #auto=start
 authby=secret
 #optionally specify encryption/hash for phase 1 & 2
 esp=3des
 #perfect forward secrecy (default yes)
 #pfs=yes
 #optionally enable compression
 compress=yes

---

### Post by jcoles on 2009-06-07
Here's my revised ipsec.conf, which works well:

# profile: office
# right: remote
# left: local

version 2
config setup
    interfaces="ipsec0=eth0"
    klipsdebug=none
    plutodebug=none
    plutostderrlog=/var/log/ipsec.log
    nat_traversal=yes

conn %default
    authby=secret
    type=tunnel
    keyingtries=1
    #keylife=1200s
    #ikelifetime=1200s

conn office
    keyexchange=ike
    ike=3des-sha1-1536
    esp=3des-md5-1536
    pfs=yes
    left=192.168.0.101
    right=<office_gateway_IP>
    rightsubnet=172.20.120.0/24

# disable opportunistic encryption
conn block
    auto=ignore

conn private
    auto=ignore

conn private-or-clear
    auto=ignore

conn clear-or-private
    auto=ignore
conn clear
    auto=ignore

conn packetdefault
    auto=ignore

I got this configuration from playing with KVpnc. It created a new ipsec.conf when I ran its setup wizard. KVpnc itself is broken. The profile I created is not visible or accessible in the program. But, I was successful when I combined the new configuration file format with my existing ipsec commands:

/usr/sbin/ipsec auto --add office
/usr/sbin/ipsec auto --up office

In ipsec.conf, I had to be more specific with my ike and esp parameters than I was before. Perhaps some defaults have changed.

---

