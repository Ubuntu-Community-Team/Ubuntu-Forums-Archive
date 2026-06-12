---
title: "Internet Stopped working when changed IP"
date: 2008-11-07
forum: General Help
---

### Post by m3sSh3aD on 2008-11-07
Hi again,

Done something silly and dont know how to correct what i have done. Seem's a very strange one.

I have a belkin cable router (54Mb G) connected to a cable modem (virgin uk) and i wanted to set my laptop to 192.168.2.5 away from any other possible connections.

I followed this guide:
[http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html](http://www.cyberciti.biz/tips/ubuntu-linux-creating-ethernet-alias-for-eth0-network-device.html)

and changed the settings to:

auto eth0:0
iface eth0:0 inet static
name Ethernet alias LAN card
address 192.168.2.5
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.1

I didnt relise it said eth0:0 and when i checked 'network tool' it came up with both eth0 & eth0:0, with eth0 set to 192.168.2.2 & eth0:0 set to 192.168.2.5 and it seemed to be connecting with the eth0(192.168.2.2) when i checked the router. But it was working.

I edited the file to:

auto eth0
iface eth0 inet static
name Ethernet alias LAN card
address 192.168.2.5
netmask 255.255.255.0
broadcast 192.168.2.255
network 192.168.2.1

Basically just removing the ':0' on the top 2 lines. Restarted and bam, No internet. But i was able connect to my router (192.168.2.1). I changed it back and still nothing. I even replaced the origional which went along the lines of:

auto eth0
iface eth0 inet dhcp

and still firefox as no connection. I restarted with every change so it wasnt that. But in network tools both eth0 & eth0:0 are still showing with loopback with the settings i said at the beggining of the post.

I've just re-installed with Ubuntu Studio so really dont want be doing it twice in one day cause of a simple problem. Well, I hope is a simple problem.

Also, alot of things tell me goto 'Network' for a GUI version to set things up under system>admin>network but that option isnt there, Just 'network tools'. Why is this

Thanks in advance and sorry for essay but trying get everything i can across with been a Linux begginner as i remember when i was new to DOS way back then :)

EDIT: I just found this on another help section (same site weirdly):


"Task: Define new DNS servers

Open /etc/resolv.conf file
$ sudo vi /etc/resolv.conf

You need to remove old DNS server assigned by DHCP server:

search myisp.com
nameserver 192.168.1.254
nameserver 202.54.1.20
nameserver 202.54.1.30

Save and close the file."

I have a feeling this could be the problem but am not currently at my house presently (friday night :)) Doesnt explain why i still see eth0:0 in network tools, or why Network is missing from admin.

Anyways, again, thanks for any help in advance :)

---

### Post by m3sSh3aD on 2008-11-07
BUMP :KS

Sorry to bump this thread but im desperate for a answer and dont want it getting lost in no mans land :)

---

### Post by LateNiteTV on 2008-11-07
does your isp use dhcp?

---

### Post by m3sSh3aD on 2008-11-07
Sorry to be a real noob but DHCP?

I have had it working in Ubuntu with the what i did but with 'eth0' not 'eth0:0'. I just installed ubuntu Studio and did this mistake and everythings gone bump after trying correct the issue. Weirdly it was working fine until i removed ':0' from the interfaces file. 

Before i changed anything though it said:

auto eth0
iface eth0 inet dhcp

so im guessing my ISP does support DHCP. Sorry again for being a right noob with this, but i am learning fast :) I have alot of experience with computer, just not linux OS's :)

---

### Post by m3sSh3aD on 2008-11-07
bump

---

### Post by m3sSh3aD on 2008-11-07
bump...

---

