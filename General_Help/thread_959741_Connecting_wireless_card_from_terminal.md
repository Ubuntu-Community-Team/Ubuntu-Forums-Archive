---
title: "Connecting wireless card from terminal"
date: 2008-10-26
forum: General Help
---

### Post by LeboyX on 2008-10-26
I'm trying to find a way to run terminal commands to my Broadcom wireless card to connect to a given wireless network. In the end, this is going to go into a script which will continually try to connect to a specific network until success. (The networks here tend to be difficult to get a connection from at times. It's annoying to manually ask it to connect every time the connection times out). Any suggestions?

---

### Post by ryanhaigh on 2008-10-26
Take a look at the man page from the iwconfig command (open terminal and issue man iwconfig). Alternately go to system>help and search for iwconfig.

---

### Post by LeboyX on 2008-10-28
So far I type the following command:

_$ iwconfig eth1 essid ResnetWireless_

But nothing happens...

---

### Post by tCarls on 2008-10-28
> 
So far I type the following command:

$ iwconfig eth1 essid ResnetWireless

But nothing happens...


If you run iwconfig again you should see the essid has been changed to ResnetWireless. That's not enough to connect; you need to assign an IP. If the IP is assigned via DHCP (likely) then run "sudo dhclient eth1".

Is the network encrypted? If so then you also need to run "sudo iwconfig eth1 key <encryption_key>".

---

### Post by ryanhaigh on 2008-10-28
I used to use the following:
```

iwconfig wlan0 essid mywireless-ap mode managed commit 
dhclient wlan0

```
Note that my network was open and not all of my wireless cards required the commit.

---

### Post by LeboyX on 2008-10-29
@ryan: I tried running your command line, but I have a feeling I wasn't doing it right or something, as I was told I'd given it invalid arguments. 

@tCarls: When I first type "iwconfig eth1 essid ResnetWireless" followed by "iwconfig", there is nothing in the field for essid. However, if I repeat this process again, the essid suddenly changes, and I'm not sure why. When I run "dhclient eth1" it spits out all sorts of IP's and requests, but I still don't connect to the internet. Would this have to do with Wireless being disabling wireless on my nm-applet? Also, I'm guessing that iwconfig won't disconnect me from one network to connect to another, will it?

The network here requires a login through a web browser upon connection before I can officially use the internet. But, I wouldn't think that should stop this method from working...?

---

### Post by ryanhaigh on 2008-10-29
Keep in mind that it may take a while for the connection to be established which may be why the it seemed to connect on the second attempt. After running dhclient eth1 you should have an ip address assigned, you can use ifconfig eth1 to confirm this. It might be worth quitting the nm-applet while you are doing all this as it may interfere.

Once you know you have an ip address try to ping your networks gateway address (generally the one that assigned you the ip address so you can check the output of the dhclient command for something like DHCP ack received from .....) or dns server (use cat /etc/resolv.conf to get the dns servers ip).

---

