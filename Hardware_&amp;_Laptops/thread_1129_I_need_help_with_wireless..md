---
title: "I need help with wireless."
date: 2004-10-18
forum: Hardware &amp; Laptops
---

### Post by Infatuated_iPod on 2004-10-18
My wirelss card is not even detected, how do i coonfigure it. I have absolutely no idea how to do this. So i need someone to tell me how to do it step my step. Thank you. I have a linksys wirelss card.

---

### Post by normnmiles on 2004-10-18
what's the model number of your linksys card?

---

### Post by Infatuated_iPod on 2004-10-19
The model number is WPC11 ver.4

---

### Post by normnmiles on 2004-10-19
Try following these steps.  I am not sure if it will work but this is how I configured my card (netgear wg511).

- Computer--&gt;System Configuration--&gt;Networking
- Add
- Forward
- Select Wireless
- enter information and finish.

Good luck.  Hopefully someone with experience with this card help out.

---

### Post by Infatuated_iPod on 2004-10-19
i did that  but when i hit enable it didnt work, and the configuration is never saved, i think there may be something wrong with the networking configuration on my ubuntu.

---

### Post by Lemuel on 2004-10-19
I have a similiar problem, but I can pin it down to WEP encryption.
When turning encryption off for the router, i can get my ipw2200 to work.

When I turn it on, I can't get a connection. The key is the same for both router and my laptop. 
Strange is, that saving it in the network settings dialog takes minutes. But after that, iwconfig shows me the correct encryption key.  But with ifconfig no inet address is listed and dhclient fails to find the router. The router is a NetGear MR814v2 if that does matter.

Thanks in advance

---

### Post by knappen on 2004-10-19
Lemuel, how did you get your ipw2200 to work? Did you make any changes after the initial install?

In - Computer--&gt;System Configuration--&gt;Networking I can see the ipw2200 but I cannot get it active.

Did you download any specific drivers?

---

### Post by Lemuel on 2004-10-20
I didn't download anything concerning ipw2200. 
What I did was ```
modprobe ipw2200
modprobe firmware_class
``` (the latter is probably unneccessary) which resulted in no displayed errrors. But only without WEP I got the thing working.
I chose my wired eth0 as the main network device during install if that should matter.

---

### Post by knappen on 2004-10-20
Thanks Lemuel.

I will try to switch off the encryption and see if it solves it.

I hope so!

---

### Post by knappen on 2004-10-20
Ahh Lemuel it worked!

It works with WEP as well. Perfect! I have a Netgear ME102 access point.

I havent done anything more than following your instructions, so I am lost regarding your problem with the WEP. Sorry...

---

### Post by gregh on 2004-10-20
I have a Toshiba A70 and had the same WEP issue as shown above. Even though I entered the WEP key into the gnome-system-tools applet, it would not work.
I used iwconfig and saw my encryption: off

So, then I used  (my wireless is ath0, substitute yours):

iwconfig ath0 key YourWEPKeyHERE

then look at iwconfig again, you should see your key in place, and hopefully now access your wireless properly.
I am looking at how to get this to load at startup but am stuck at the moment (I am a n00b for Ubuntu and debian)

-Greg

---

### Post by knappen on 2004-10-20
Have a look under -Computer -System configuration -Networking

Is your card there? If so you can add the WEP key and slect to have it activated at boot.

To change the channel, if you have to do that, I did

```


sudo iwconfig ethx channel xx
```

---

### Post by thetourist on 2004-10-21
Can someone with a working ip2200 setup post their /etc/network/interfaces file?

Can you also confirm that you've got it working with encryption turned on?

ifup eth1 complains about unknown interfaces. The networking dialog hangs or doesn't give any feedback as to why the connection can't be activated!

---

### Post by Jspired on 2004-10-21
I have the same card, but a v.3  I don't believe v.4 is supported by linux, as they changed the chipset along the way.  (Someone please correct me if I'm wrong..)

---

### Post by Rancoras on 2004-10-21
Infatuated_ipod:

I found this after a quick google search:

[http://www.linuxvoodoo.com/resources/howtos/linksysv4/](http://www.linuxvoodoo.com/resources/howtos/linksysv4/)

See if that helps you any.

---

### Post by knappen on 2004-10-21
Here is mine:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth1 inet dhcp
name Ethernet LAN card

iface eth0 inet dhcp
name Wireless LAN card
wireless_essid xxxxxxxx
wireless_key xxxxxxxxxxxxxxxxxxxxxxx
auto eth0

Hope it helps.

---

### Post by knappen on 2004-10-21
Dont know about my revision number but it was manfactured in June 2004.

---

### Post by thetourist on 2004-10-21
Thanks Knappen, I can at least use ifup now. Sadly I still can't get an IP...

```
# ifup eth1
Internet Systems Consortium DHCP Client V3.0.1rc14
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http&#58;//www.isc.org/products/DHCP

sit0&#58; unknown hardware address type 776
sit0&#58; unknown hardware address type 776
Listening on LPF/eth1/00&#58;0e&#58;35&#58;44&#58;80&#58;22
Sending on   LPF/eth1/00&#58;0e&#58;35&#58;44&#58;80&#58;22
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 18
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

Here's the output of ifconfig:

```
# ifconfig
eth1      Link encap&#58;Ethernet  HWaddr 00&#58;0E&#58;35&#58;44&#58;80&#58;22
          inet6 addr&#58; fe80&#58;&#58;20e&#58;35ff&#58;fe44&#58;8022/64 Scope&#58;Link
          UP BROADCAST MULTICAST  MTU&#58;1500  Metric&#58;1
          RX packets&#58;0 errors&#58;0 dropped&#58;0 overruns&#58;0 frame&#58;0
          TX packets&#58;0 errors&#58;0 dropped&#58;0 overruns&#58;0 carrier&#58;1
          collisions&#58;0 txqueuelen&#58;1000
          RX bytes&#58;0 &#40;0.0 b&#41;  TX bytes&#58;0 &#40;0.0 b&#41;
          Interrupt&#58;5 Base address&#58;0x2000 Memory&#58;90000000-90000fff

lo        Link encap&#58;Local Loopback
          inet addr&#58;127.0.0.1  Mask&#58;255.0.0.0
          inet6 addr&#58; &#58;&#58;1/128 Scope&#58;Host
          UP LOOPBACK RUNNING  MTU&#58;16436  Metric&#58;1
          RX packets&#58;32746 errors&#58;0 dropped&#58;0 overruns&#58;0 frame&#58;0
          TX packets&#58;32746 errors&#58;0 dropped&#58;0 overruns&#58;0 carrier&#58;0
          collisions&#58;0 txqueuelen&#58;0
          RX bytes&#58;2415629 &#40;2.3 MiB&#41;  TX bytes&#58;2415629 &#40;2.3 MiB&#41;

```

and finally, the output of iwconfig:

```
# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID&#58;&quot;Muppetry&quot;
          Mode&#58;Managed  Channel=13  Access Point&#58; 00&#58;05&#58;2D&#58;7F&#58;02&#58;1E
          Bit Rate=0kb/s   Tx-Power=20 dBm
          RTS thr&#58;off   Fragment thr&#58;off
          Encryption key&#58;1234-ABCD-EF   Security mode&#58;restricted
          Power Management&#58;off

sit0      no wireless extensions.
```

Unfortunately I don't manage the access point so I can't disable encryption to see if that's the problem. Does it look like that might be the problem?

---

### Post by Lemuel on 2004-10-21
what thetourist wrote could as well be from me.  I have basically the same output and the same problem. No connection to the DHCP server and no connection quality displayed in the top GNOME bar applet.

---

### Post by derjohan on 2004-10-21
I have the same problem. 
My wireless card works fine in Ad-Hoc mode with a static IP and encryption enabled. So I think this is a problem with the DHCP client.

---

### Post by Lemuel on 2004-10-21
I tried a static IP, but that didn't help. I don't get any errors after 'ifup eth1' now, but no connection to the access point too.

---

### Post by thetourist on 2004-10-21
Same thing for me - no errors on ifup but 'destination host unreachable' if i try to ping my gateway.

If I use managed mode iwconfig shows the access point as the MAC of my wi-fi card. If I use ad-hoc it's set to 00-00... I guess that's to be expected.

Can anyone describe what steps I should take to find out whether the wi-fi card can even see my access point? I'm trying to narrow down the source of the problem.

---

### Post by Lemuel on 2004-11-03
Strangely, with a different Access Point, it works. The AP is a LinkSys WRT54G, 128 bit WEP encryption.

---

### Post by mduduzi on 2004-11-03
[QUOTE=Lemuel]Strangely, with a different Access Point, it works. The AP is a LinkSys WRT54G, 128 bit WEP encryption.[/QUOTE]

I've had similar failures trying to connect to Netgear's DG834G from my D-Link DWL-G650 cardbus. For a few days I worked with WEP off. But since last night, I been connecting with WEP. What I did was:
1. Connected to the AP using a cable
2. Changed WEP from Shaked Key to Open.
3. Saved the settings and exited.
4. Disconnected the cable, disabled my eth0 and enabled the WLAN (ath0) -with WEP key.
5. Restarted the networking services by typing: #   /etc/init.d/networking restart  .

I got the signal but I kept lossing it shorly after catching it.
I have not had a problem since and after a reboot.
It's been nearly 24hrs now.

---

