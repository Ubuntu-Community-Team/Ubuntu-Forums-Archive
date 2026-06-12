---
title: "No Connection on an old Dell Latitude"
date: 2010-08-18
forum: Hardware
---

### Post by foralwaysforever430 on 2010-08-18
I have a really old Dell laptop that the windows operating system crashed and I couldn't reinstall it. So a friend of mine said I should try Ubuntu. 
So I burned the ISO to a CD and installed it on the laptop. After what seemed like an eternity and several error messages and having to start over twice, It finally finished installing and I got it to boot up. 
Now my problem is getting on the internet. The laptop is so old, it doesn't have a ethernet port but rather uses PCI cards. I have a 3Com 10/100 ethernet card.
How do I install the hardware for the card?
The computer says I'm connected to a wired connection, but Firefox still displays a server error when I try to visit yahoo or google. 

Do I have to enter all my internet settings manually?? I hate doing this. I would need to be walked through step by step. 

Here are some specs on the computer and please don't laugh. It's super old for a computer but I like playing with old computers, just to see if I can upgrade them or even get them to work at all. It was purchased in May of 1999. 

It's a Dell Latitude CPiA366xt
It originally had 128MB of RAM but has been upgraded to a whole 256MB
The hard drive was originally only 6.4GB but has been upgraded to 12gb I think
The original operating system was Windows NT. It was downgraded to Windows 95 and that was removed and replaced with Ubuntu today. I tried to reinstall windows NT 4.0 from the CD but it kept crashing or having errors, so I gave up. 
All I want to do is go on the internet, check email, maybe use chat services, and use word processing once in a blue moon. 
No fancy 3D games, no making movies, I don't even really want to store music on it since it's got such a small hard drive. 
I just want to do what I said above if it's even remotely possible. 
Can anyone help me out??
Thanks

---

### Post by jarviser on 2010-08-18
Should have started a new thread.

You need to disclose a bit more about the router/modem you have and the ISP. 

It sounds like the PC is connected to the modem, and this is usually automatic with ethernet, but to check, find out the IP address of the router modem. It should be printed on the label, probably 192.168.0.1  or .1.1  

Using firefox connect to that address and see if you can connect to the admin system of the router. If you can, then the problem is most likely in the way the router modem connects to the internet.

Most desktops use PCI cards for ethernet, that is normal. You should only have to enter your cable or ADSL internet settings in the router modem, not in Ubuntu.

---

### Post by Sef on 2010-08-18
> Should have started a new thread.

So moved.

---

### Post by Fafler on 2010-08-18
You should try a lighter version of Ubuntu, like Lubuntu. But this anyway. Open a terminal from Applications -> Accessories -> Terminal. This thing will be your best friend in Linux, if you choose to get to know it. Anyway, enter these commands:

```
ifconfig
```It returns a bunch of info about your network cards. They have names like eth0, wlan1 and lo, which by the way is the loopback device. Always present, you don't use it much directly. Look at for something like this:

```
wlan0     Link encap:Ethernet  HWaddr 00:21:23:76:23:97  
          inet addr:176.16.1.2  Bcast:176.16.255.255  Mask:255.255.0.0
          inet6 addr: fe80::221:5dff:fe56:ef0c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:547484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:282734 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:795540675 (795.5 MB)  TX bytes:27912974 (27.9 MB)

```It says i have the IP address 176.16.1.2, which means the communication between the laptop and the router works. Next do a

```
route
```It returns a list of possible gateways. One of them is called default. Try pinging the address next to it.
```
fafler@oxygen:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
link-local      *               255.255.0.0     U     1000   0        0 wlan0
176.16.0.0      *               255.255.0.0     U     2      0        0 wlan0
default         hydrogen.local  0.0.0.0         UG    0      0        0 wlan0
fafler@oxygen:~$ ping -c 5 hydrogen.local
PING hydrogen.local (176.16.0.1) 56(84) bytes of data.
64 bytes from hydrogen.local (176.16.0.1): icmp_seq=1 ttl=64 time=1.03 ms
64 bytes from hydrogen.local (176.16.0.1): icmp_seq=2 ttl=64 time=0.604 ms
64 bytes from hydrogen.local (176.16.0.1): icmp_seq=3 ttl=64 time=1.04 ms
64 bytes from hydrogen.local (176.16.0.1): icmp_seq=4 ttl=64 time=0.597 ms
64 bytes from hydrogen.local (176.16.0.1): icmp_seq=5 ttl=64 time=0.643 ms

--- hydrogen.local ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 0.597/0.783/1.045/0.210 ms
fafler@oxygen:~$ 
```That proves it still works. The router address could also be a IP address instead of a name. Then try pinging something outside like google. I'll let you figure that one out. That means you're on the internet.

If any of these steps fails, cut'n'paste the output from the terminal here.

Oh yeah, and when you get firefox to work, go visit the lubuntu site at [www.lubuntu.net](www.lubuntu.net) Try going File -> Work Offline

---

