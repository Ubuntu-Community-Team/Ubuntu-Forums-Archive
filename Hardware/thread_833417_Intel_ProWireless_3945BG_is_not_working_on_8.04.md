---
title: "Intel Pro\Wireless 3945BG is not working on 8.04"
date: 2008-06-18
forum: Hardware
---

### Post by nabeelfa on 2008-06-18
I downloaded the Ubuntu Wubi while using a windows Vista Notbook which is: 
Toshiba Satellite M100-180
the wireless is not working!! I made the update for it but no solution up-till date!
Please let me enjoy the power of mobility on Ubuntu!!
Thanks.

---

### Post by nabeelfa on 2008-06-18
nabeel@nabeel-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d4:27:2e:35  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5780 errors:2 dropped:0 overruns:0 frame:2
          TX packets:5997 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5671783 (5.4 MB)  TX bytes:643733 (628.6 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.1 KB)  TX bytes:1200 (1.1 KB)

---

### Post by nabeelfa on 2008-06-18
sorry that one was wireless disabled this is the results of #ifconfig -a while it is enabled:

nabeel@nabeel-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:d4:27:2e:35  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10271 errors:5 dropped:0 overruns:0 frame:5
          TX packets:10500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10646759 (10.1 MB)  TX bytes:950869 (928.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.1 KB)  TX bytes:1200 (1.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:18:de:0f:68:8e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-18-DE-0F-68-8E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

nabeel@nabeel-laptop:~$

the roaming is enabled, I tried the #sudo ifconfig wlan0 down then I tried #sudo ifconfig wlan0 up and its still not working!!

---

### Post by stchman on 2008-06-18
> **nabeelfa said:**
> I downloaded the Ubuntu Wubi while using a windows Vista Notbook which is: 
Toshiba Satellite M100-180
the wireless is not working!! I made the update for it but no solution up-till date!
Please let me enjoy the power of mobility on Ubuntu!!
Thanks.

I experienced a similar problem on a Toshiba laptop with a 3945 card.  I returned the laptop and bought an A205 model with a 4965 that works much better.  The 3945 would sometimes see the WAP and then took FOREVER to connect if at all.

---

### Post by nabeelfa on 2008-06-18
> **stchman said:**
> I experienced a similar problem on a Toshiba laptop with a 3945 card.  I returned the laptop and bought an A205 model with a 4965 that works much better.  The 3945 would sometimes see the WAP and then took FOREVER to connect if at all.

Well the issue that I am facing is only with Ubuntu! 
Its working very well with the Windows Vista!
No solution??

---

### Post by nabeelfa on 2008-06-26
No responds??

---

### Post by Azmodanino on 2008-06-26
well, i got the same card on an HP 530 and it's working with no problems, maybe you should download the firmwares manually?

---

### Post by Nepherte on 2008-06-26
There should certainly be a way to get that card to work. I have the same wireless card as you and it worked out of the box

---

### Post by timcredible on 2008-06-26
that card works out of the box on a dell latitude.  have you accidently turned off the wireless by pressing Fn+<some button>?

---

### Post by nabeelfa on 2008-06-30
Nepherte: its a built-in hardware!! and still not working!!
timcredible: I am aware of turning on and off the wireless option, its on..
Guys I thing I know what is wrong here, its because its not known in the restricted hardware!!! before on the Fiesty distro it was within the restricted hardwares, how can I do it like this???

---

### Post by starcannon on 2008-06-30
It must be a Toshiba thing, I have that card on this HP dv2600, I have it on a couple Dell 1420n's and they all work flawlessly out of the box.

Stupid question time, don't throw things at me, and if its the case, don't throw things at yourself... If theres a little wifi switch on the front did you turn it on? If its on did you turn it off and then turn it back on? Those lil' buggers can be a pita sometimes.

---

### Post by bored_shiva on 2008-06-30
> **starcannon said:**
> It must be a Toshiba thing, I have that card on this HP dv2600, I have it on a couple Dell 1420n's and they all work flawlessly out of the box.

It definitely is not a Toshiba thing. I have the problems with this same card on an Acer Aspire 5610. and so far I've not found a solution. (There are several threads here about the 5610, but they relate to the Broadcom card) I've tried using ndiswrapper to use the windows drivers, but no go. 

Very quickly, my problem is that the card works out of the box, but within a few minutes of start, it would drop the connection (though it stills shows as connected) manually stopping and starting the card (by the little switch on the front of the laptop) brings it back up, but again only for a few minutes.  (The card works flawlessly in Vista, BTW)

Any help out there would be most welcome. Just be the virtue of it taking a few minutes to drop I'd hazard a guess that this is some sort of time out. But where it is, I haven't the foggiest.  :-k

---

### Post by leandromartinez98 on 2008-06-30
Have you tried Wicd? I have the same card in a Vaio NR laptop, I had several problems with network manager (generally I could see the networks, but not connect to them). My problems were solved changing to wicd.

---

### Post by sagivegh on 2008-06-30
Hi,

I had the same problem,
try this one:

```
sudo echo "options iwl3954 disable_hw_scan=1" > /etc/modprobe.d/iwl3945
```

And reboot, or reload the iwl3954 module:
Code:

```
sudo modprobe -r iwl3945 && sudo modprobe iwl3945
```

---

### Post by bored_shiva on 2008-06-30
> **leandromartinez98 said:**
> Have you tried Wicd? 

I'm not sure I know what wicd is? How do you use it?

---

### Post by bored_shiva on 2008-06-30
> **sagivegh said:**
> Hi,

I had the same problem,
try this one:

```
sudo echo "options iwl3954 disable_hw_scan=1" > /etc/modprobe.d/iwl3945
```

And reboot, or reload the iwl3954 module:
Code:

```
sudo modprobe -r iwl3945 && sudo modprobe iwl3945
```

At present I have the iwl39xx drivers blacklisted in modprobe and am using ndiswrapper (not that it helps...) Should I undo all that first? What's the hw_scan setting for? (I'm assuming it's to modify the hardware signal scan on the card, but why?)

Thanks

---

### Post by leandromartinez98 on 2008-06-30
> **bored_shiva said:**
> I'm not sure I know what wicd is? How do you use it?

Wicd is a different network manager (the thing that is on top right
of your screen with the little bars, which controls your network
connections). It is another package, which works sometimes better
than the default one:

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

You can try it, if you don't like it you must only re-install the
network-manager (one you install one the other gets uninstalled).

Concerning the loading of the iwl3945 module, I have it on my
/etc/modules file. (Add a line containing "iwl3945" to that file). It was
not me who added it, I think, but it is there. 

Just to say, I have already tryied to change from the default driver to ndiswrapper, and it was not good. I think the bugs here are not related to the driver, but the the network managers.

---

### Post by bored_shiva on 2008-06-30
Well there appears to be some improvement with the hw_scan switch - it seems to take longer for the card to disconnect, and occasionally wicd will actually reconnect it. But so far, nothing earth-shattering.
I should mention a couple of things, in case they are important:
1. I am running an Edimax home router with 802.11b/g capability and wpa security based on pre-shared key. 
2. The card is running in DHCP mode. I did try static but it doesn't seem to make any difference.
3. I am primarily testing this by using add/remove manager to download software package. Though when the package download gets "stuck" so do firefox and ping.
4. Usually, the first sign of trouble is that the mouse freezes for a few seconds while the package is downloading. It will then unfreeze, and the download will continue, but it disconnects shortly after. I don't know if this is connected, but it is reproducible.

Again, any help would be most welcome. If anyone needs me to post anything (settings, logs, whatever) just say so. 

Thanks

---

### Post by nabeelfa on 2008-06-30
on the Fiesty distro it was working as a restricted hardware!!!
but on the 8.04 its not consider it as a restricted hardware!
how can I place it as on fiesty?

---

### Post by bored_shiva on 2008-06-30
As this is a new install, and I've already blown it away twice trying to get the wireless card to work, I decided that I didn't mind experimenting and replaced the install with Kubuntu 8.04. 

Turns out that is works much better. The MCO (mean-time to crap out) for the connection is much longer - up to an hour sometimes, and it usually recovers itself without my having to manually reset. 

Since Ubunutu and Kubuntu are, supposedly, the same O.S. with a different UI, it makes me wonder if the problem isn't somehow related to Gnome? 

Any thoughts?

---

### Post by tsu3000 on 2008-10-23
Hi

Did anyone got the wi-fi working in the end? I am thinking of installing ubuntu on my Toshiba M100.

Thanks.

---

