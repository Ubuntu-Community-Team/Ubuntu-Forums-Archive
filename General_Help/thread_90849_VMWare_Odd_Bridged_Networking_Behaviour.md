---
title: "VMWare Odd Bridged Networking Behaviour"
date: 2005-11-15
forum: General Help
---

### Post by tosh on 2005-11-15
Hello, 

I've got VMWare 5 (finally) humming along in Kubuntu. I built an XP Pro VM, specified bridged networking, and am observing networking behaviour that I don't understand.

Here are the facts I am aware of:

1. The Kubuntu install has good network access (I'm posting from it!)
2. The XP VM is getting appropriate address and nameserver assignments from dhcp (but is not able to ping the assigned gateway)
3. The XP VM *can* ping the Kubuntu host, and vice versa
4. Other hosts on my network can ping the Kubuntu host, but not the XP VM.
5. Obviously, the XP VM has no access beyond the Kubuntu host.

Is there a configuration for forwarding of some kind that is not apparent? I'd dearly love to see the XP host gain access to the internet! 

Thanks so much for your help!

tosh

---

### Post by lorenco on 2005-11-15
R u using bridged networking ??? 

Try using NAT.  This gives the VM a "local" ip from linux but NAT to the rest.  It is also usefull as it is protected by the linux firewall ;-)
The secondary beneifit is that you can use any network like I have a wireless and ether network and swop seamlessly between them. I can also connect via VPN on linux to my work network and windows is none the wiser ! 

Works Great!

---

### Post by tosh on 2005-11-16
Thanks, Lorenco...that did work. I have internet access on the VM, now...unfortunately, what I'm hoping to do with it isn't working! Actually, I'm trying to do exactly what you mentioned, connect to work using a Cisco VPN client. I think the reason I thought bridged as opposed to NAT was I worried there might be a problem with IPSEC and address translation (but I don't know that for sure). Are you doing anything special to make your VPN connection? Thanks :)

---

### Post by mlomker on 2005-11-17
Each form of VMWare networking has its trade-offs.  I use bridged mode and I've never had any luck networking between host and guest...the guest does behave normally, though.  I'm surprised that you had trouble pinging your gateway...I haven't seen any issue like that.

I use the Cisco client on Ubuntu but I've never had a need to use it from a guest.

---

