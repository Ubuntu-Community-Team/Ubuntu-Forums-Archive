---
title: "Can´t stablish ethernet connection"
date: 2005-03-28
forum: Hardware &amp; Laptops
---

### Post by #Vizc@ch@ on 2005-03-28
Hi everyone, this is my first post, so I hope I´m posting in the correspondig subforum.

I´ve instaled ubuntu a couple of weeks ago, and no matter how much I tried and asked how, I can´t get online. I´ve used the same configuration, as regarding ip, gateway, subnet mask and dns server, as in my win xp, and still can´t get online.

I phoned my ISP and asked them, which could the problem be, and they told me that it should work just fine  :-k 

The ethernet card I use is:

Realtek RTL8139/810X Family PCI Fast Ethernet NIC

I´ve tried configuring the network, both trough the GUI (Wizard) and the command prompt, and none worked. I mean, it´s configured, but it doesn´t seem to work.

This is the commands I used (the data is false):

# ifconfig eth0 192.168.1.2 broadcast 192.168.255.255 netmask 255.255.0.0 up
# route add default gw 192.168.1.1
# echo "nameserver 80.58.0.33" >/etc/resolv.conf
# echo "nameserver 80.58.32.97" >>/etc/resolv.conf

Well I hope you guys can give me some advice and scuse me If there are too many mistakes in my post, I´m not a native speaker.
Thanks

---

### Post by Whiffle on 2005-03-29
Your english is 100x better than most of what I see on the internet :D 

I have the same network card and it works fine and the whole system worked just fine right from the beginning.  Soo..

Best idea is to start with the basics.  Are the lights on the back of the card lit up and blinking?  If not we have a hardware problem..

Have you been able to make it work with dhcp?

---

### Post by mercurus on 2005-03-29
[QUOTE=#Vizc@ch@]Hi everyone, this is my first post, so I hope I´m posting in the correspondig subforum.

I´ve instaled ubuntu a couple of weeks ago, and no matter how much I tried and asked how, I can´t get online. I´ve used the same configuration, as regarding ip, gateway, subnet mask and dns server, as in my win xp, and still can´t get online.

I phoned my ISP and asked them, which could the problem be, and they told me that it should work just fine  :-k 

The ethernet card I use is:

Realtek RTL8139/810X Family PCI Fast Ethernet NIC

I´ve tried configuring the network, both trough the GUI (Wizard) and the command prompt, and none worked. I mean, it´s configured, but it doesn´t seem to work.

This is the commands I used (the data is false):

# ifconfig eth0 192.168.1.2 broadcast 192.168.255.255 netmask 255.255.0.0 up
# route add default gw 192.168.1.1
# echo "nameserver 80.58.0.33" >/etc/resolv.conf
# echo "nameserver 80.58.32.97" >>/etc/resolv.conf

Well I hope you guys can give me some advice and scuse me If there are too many mistakes in my post, I´m not a native speaker.
Thanks[/QUOTE]
 Is this to connect to the internet or to a LAN ?

You'll need different information for different networks ... Try the other adapter in WinXP for alternative configuration information ...

Cheers
mercurus

---

### Post by Warhammer on 2005-03-29
I have the same problem. Even with the same Eth card, iirc. The cable modem works fine. I think it's something with the configuration...

---

### Post by #Vizc@ch@ on 2005-03-31
I'm simply happy! I'm finally online posting from my Ubuntu-Linux, it´s amazing.

Here's the solution (I hope it helps someone else):

I typed the command "lspci" in the root terminal and I found out that the system didn't recognize my ehternet carde, instead it was trying to use the netcard (I don't know if this is the correct word to describe it) that I use for my private LAN, so I just had to switch the cable from the ethernet card to the card I use for the LAN and .. whala! a smile was drawn in my face when I started to see that the ping I made to google, returned some data  [-o<

---

