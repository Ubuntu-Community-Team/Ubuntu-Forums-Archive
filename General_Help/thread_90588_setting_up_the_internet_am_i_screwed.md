---
title: "setting up the internet: am i screwed?"
date: 2005-11-15
forum: General Help
---

### Post by Specialsauce on 2005-11-15
ok, before i go on, let me explain my networking situation (im no networking expert so bear with me).

So, we have a big linksys wireless g broadband router connected to my moms computer. then we have a little mini router thing on my computer that connects to the big router to hook my up to the internet. My box is ubuntu, my moms in windows XP.

I need to hook up the internet on my ubuntu box, but i beleive i need my IP adress and subnet mask and other things. the only thing is, i have no clue how to find that out. the only hope seems to be that it will only work out if my mom has the same ip and subnet mask as me. (wich is possible, i suppose).

i need to get this figured out, can you help me out here? please feel free to ask me any questions at all..... i'll answer them to the best of my ability.....

---

### Post by Sheco on 2005-11-15
Set the netmask and gateway just the same as your mom's PC, and set your IP to another number next to your mom's IP (in a normal net (netmask 255.255.255.0) if her IP is 192.168.1.10, set yours to 192.168.1.11)

if you ping the gateway, and it replies, then the network is ok, try pinging the outside world.

---

### Post by Specialsauce on 2005-11-15
how do i find out my moms ip, netmask and gateway? i know theres a site that tells your ip, is there a site that tells your netmask and gateway?

---

### Post by Sheco on 2005-11-15
there are plenty of ways, if you have a network status icon on the system tray... double click on it and switch to the second tab there, it tells you all you need to know.

another way is using the command line, run the command line (you can click start menu->run.. then type cmd) there, you can run:
```
ipconfig
```

another way is in the control panel, network connections, double click on the network icon (or you can click propierties in the first tab from the first method I explained) then find "TCP/IP" and click propierties, the info's right there, that's the place where you set the ip/gateway/dns.

I might have messed up with the names and stuff, I'm not on windows right now and I havent memorized them by heart :)

---

### Post by [2]BoxingFiend on 2005-11-15
on your mom's machine, go to start and run, cmd 

ipconfig /all 

this will list all the ip info you need to use with your ubuntu config

---

### Post by Specialsauce on 2005-11-15
wow, thank you, all of you. you reply so fast! im going to try this out..... i'll update on if it works or not....

---

### Post by Specialsauce on 2005-11-15
ok, so when i boot up firefox, it did not connect..... nothing. any further help would be greatly appreciated....

---

### Post by suRoot on 2005-11-15
run

```
ifconfig
```

on your ubuntu box & post the info here.  also post the output from

```
ipconfig /all
```

on your mom's pc.

---

### Post by Dr. Nick on 2005-11-15
If you have a wireless router hooked to to a wired router using ethernet cable, and your box is connected to the wired box via a wire then you can forget about the wireless router as it shouldnt have any effect as long as it is hooked up to the wireless properly.

I assume you have a wired ethernet card hooked up to your wired router. If thats the case check on ubuntu and go to system-administration-networking and see if your ethernet card is listed, If so click properties and set it to dhcp and hit ok and make sure the default gateway is eth0. 

Considering the above assumptions on the wired part are correct and your not doing wireless, run an ubuntu terminal and type ```
sudo dhclient eth0
``` and it will try to get your IP, subnet etc. If that diesnt work post that output aswell.

Also open firefox and type 192.168.0.1 into the address bar and see if you get into your router

---

### Post by sitka on 2005-11-16
I'm having the same problem.   It said the following after i tried that command


sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/etho/my address
Sending on LPF/etho/my address
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS recieved 
No working leases in persistent database - sleeping.

[QUOTE=Dr. Nick]If you have a wireless router hooked to to a wired router using ethernet cable, and your box is connected to the wired box via a wire then you can forget about the wireless router as it shouldnt have any effect as long as it is hooked up to the wireless properly.

I assume you have a wired ethernet card hooked up to your wired router. If thats the case check on ubuntu and go to system-administration-networking and see if your ethernet card is listed, If so click properties and set it to dhcp and hit ok and make sure the default gateway is eth0. 

Considering the above assumptions on the wired part are correct and your not doing wireless, run an ubuntu terminal and type ```
sudo dhclient eth0
``` and it will try to get your IP, subnet etc. If that diesnt work post that output aswell.

Also open firefox and type 192.168.0.1 into the address bar and see if you get into your router[/QUOTE]

---

### Post by Dr. Nick on 2005-11-17
@sitka Is your netowrk card listed under System-Admistration-Networking? Not usre exactly what that means but looks like it doesnt see your card

---

### Post by Specialsauce on 2005-11-17
[http://xs.to/xs.php?f=262626.PNG&h=xs55&d=05464](http://xs.to/xs.php?f=262626.PNG&h=xs55&d=05464)

theres what i get when i type in "ipconfig /all" on my mom's pc..... its gonna be hard to show you what mine says when i type "ifconfig" like you said i should....

---

### Post by Specialsauce on 2005-11-17
can someone pleeease help me, this really is important to me..... *sniffle*

---

### Post by Yoda_Oz on 2005-11-17
it looks like the address to your router is:
192.168.1.1

why have you got another router connected in the first place?
all you need is another ethernet cable to go from your big linksys router to your computer. then in ubuntu you need to configure your ethernet card. thats if it is recognised by your ubuntu. what comes up when you go to the system menu in gnome at the top and then in the administration section and the clicking on networking (System/Administration/Networking)? Hopefully, you'll have something up there saying "Ethernet Connection". tell me what it says below that in the small writing about the interface. is it eth0?
you need to set up that card:
1. click on Ethernet Connection and then click properties.
2. Enable the device.
3. You should have the configuration set to dhcp (for the moment, just so we can get the internet working). Click OK.
4. Now you need to set up your DNS server. Click on DNS tab at the top of the main network settings control panel thing. you need to add a new one which says (according to the info on that screenshot) 192.168.1.1. click ok to go back to the main network control panel thingie.
5. Now make eth0 the default gateway device (its down the bottom). click ok and exit.
6. now open up a terminal and tell me what "ifconfig -a" says about eth0 (or whatever one you jst set up).
7. if it doesnt work, you might want to try restarting your computer again. (sorry advanced linux users, im new to linux too so i dont really know much about restarting services and stuff yet so bear with me!)

after restart it might work. tell me what ifconfig -a says after a restart making sure to include everything that comes up.

---

### Post by Specialsauce on 2005-11-18
okay, so i reinstqalled, and typed in my ip at the installer prompt. the netmask default was right, so i kept it. the gateway was one number different from my IP. i kept it, and now when i go into firefox and try to go somewhere it constinually says its loading.... weird....

---

### Post by Yoda_Oz on 2005-11-18
you should set it to dhcp.

what comes up when you type into a terminal:

sudo ifconfig -a

???

also, what happens when you type into the address bar of firefox:

192.168.1.1

???

---

### Post by Specialsauce on 2005-11-22
this is what comes up..... [http://img457.imageshack.us/img457/7035/screenshot5ff.png](http://img457.imageshack.us/img457/7035/screenshot5ff.png)
ive been seeing stuff about 'ndiswrapper'.... only i have no clue what it is.... could that help me?

---

### Post by SickTwist on 2005-11-24
No, ndiswrapper is a tool meant to use a Windows driver for an ethernet adapter when a Linux driver is not available. Fortunately your card seems to be detected so you don't need to worry about that.

Try doing this from your Linux box:
System --> Administration --> Networking
select "Ethernet Connection" and click "Properties"
Make sure "Enable this connection" is checked
Change the configuration to "Static IP address"
IP address: 192.168.1.110
Subnet mask: 255.255.255.0
Gateway address: 192.168.1.1
Click "OK"
Select "Ethernet Connection" and click "Activate" if it is not active
Click "OK"

To test, open a terminal (Applications --> Accessories --> Terminal) and type this:
**ping -c 1 192.168.1.1**

That should send a packet to the "big router" and see if it comes back. The output should look similiar to this:
```
jconte@kunto:~ $ ping -c 1 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=150 time=0.415 ms

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 0.415/0.415/0.415/0.000 ms
```

Let us know how it goes.

---

