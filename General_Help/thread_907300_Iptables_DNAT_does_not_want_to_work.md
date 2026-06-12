---
title: "Iptables DNAT does not want to work"
date: 2008-09-01
forum: General Help
---

### Post by descentspb on 2008-09-01
I am here for some professional help for iptables.

I am connected to a firewall computer via VPN (ppp0 interface). 
The ip of the client, from which i am connecting is **$MY_IP**. 
The ppp0 IP of the firewall is **$PPP_IP**. 
The LAN IP of the firewall is **$LAN_IP**. 

I want the firewall to forward the 80 port to another machine on the firewall's LAN, which is **$HTTP_IP**, but the firewall is not a gateway for $HTTP_IP. 
I've followed the guide about DNAT'ing ([http://iptables-tutorial.frozentux.net/chunkyhtml/x4033.html](http://iptables-tutorial.frozentux.net/chunkyhtml/x4033.html)) and it worked well, when i tried to connect to to $LAN_IP, from the firewall's LAN. But it does not work when i am connecting from $MY_IP through ppp0, and i can't find the reason. 

Can you please show me my error? 
> iptables -A PREROUTING -t nat --dst $PPP_IP -p tcp --dport 80 -i ppp0 -j DNAT --to $HTTP_IP:80
iptables -t nat -A POSTROUTING -p tcp --dport 80 -j MASQUERADE

---

