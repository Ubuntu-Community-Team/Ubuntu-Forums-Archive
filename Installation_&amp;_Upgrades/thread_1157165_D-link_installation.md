---
title: "D-link installation"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by jonathan F on 2009-05-12
Okay round #2...try again! Need to install a D-link 655 but am not having any glory.

Installed Wine so I could use the CD that comes with D-link but nothing.


How do I get my computer to see the darn thin so I can begin to config?

Any and all help would be helpful.:confused:

---

### Post by lvleph on 2009-05-12
Hook the router up using one of the cabels. Then type in 192.168.0.1 (or 192.168.1.1) to your browser. The book that came with it should tell you the password. The user name is admin and I believe the password is blank or "password". From there you can start setting things up.

---

### Post by jonathan F on 2009-05-12
Thanks for the suggestion...

Tried but received an error message>
can not connect to (either) Ip address.

Is there a configuration on the PC that I should adjust or..anything else you can recommend?

cheers,

J

---

### Post by lvleph on 2009-05-12
With the ethernet cable from your computer connected to the router, open up a terminal and type ```
ifconfig
```
Paste the output here.

---

### Post by jonathan F on 2009-05-12
Here is what I received.

jonathan@jonathan-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bd:7f:16  
          inet6 addr: fe80::230:1bff:febd:7f16/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:748 errors:0 dropped:0 overruns:0 frame:0
          TX packets:681 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:735535 (735.5 KB)  TX bytes:84733 (84.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:209.240.37.6  P-t-P:209.240.47.145  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:714 errors:0 dropped:0 overruns:0 frame:0
          TX packets:641 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:728167 (728.1 KB)  TX bytes:69003 (69.0 KB)

---

### Post by lvleph on 2009-05-12
Hmmm, You have your router plugged in, yes? Then you are plugging your ethernet cable from your computer into your LAN 1 port of the router? If so I am not sure what to tell you.

---

### Post by jonathan F on 2009-05-12
router is plugged in...cable is going from pc to #1 port.

---

### Post by lvleph on 2009-05-12
Is there a light on with a box around a number one? Is it flashing?

---

### Post by jonathan F on 2009-05-12
Just switched cables (thought it might be a bad cable) and yes I see the box around #1

---

### Post by lvleph on 2009-05-12
Okay, with the new cable try the ip address, I gave in, your browser. If you can't get there past the output to ifconfig.

---

### Post by jonathan F on 2009-05-12
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bd:7f:16  
          inet6 addr: fe80::230:1bff:febd:7f16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4656398 (4.6 MB)  TX bytes:1632250 (1.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:209.240.37.6  P-t-P:209.240.47.145  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:358111 (358.1 KB)  TX bytes:58613 (58.6 KB)

---

### Post by Mze on 2009-05-12
Could you try a reset of your router?

As per your manual online:

> To reset the router, locate the reset button (hole) on the rear panel of the unit. With the router powered on, use a paperclip to hold the button down for 10 seconds. Release the button and the router will go through its reboot process. Wait about 30 seconds to access the router. The default IP address is 192.168.0.1. When logging in, the username is 
admin  and leave the password box empty.

---

### Post by jonathan F on 2009-05-12
gave it a whirl but still no luck.

---

### Post by lvleph on 2009-05-12
I am at a loss. Have you had connectivity problems with any other router?

---

### Post by jonathan F on 2009-05-12
no..I have in the passed hooked up the router using window but wanted to use the linux PC as it is stationary and then activate the wireless componet for the laptops.

bloody frustrating! But I have appreciated your help thus far

---

### Post by agathian on 2009-05-12
Maybe the dhcp server is not working ( or disabled) in the router - and that is why you are not getting your config set. ( or you have DHCP disabled in your system )

May be try setting the eth0 interface manually to say 192.168.0.2 and gateway to 192.168.0.1.
System->admin->network will provide a gui interface ( alternately you are comfortable, you can use ifconfig and route commands ).

Also- be aware. 192.168.0.x is the default subnet typically used. I think it is possible to change it - and if someone has used this router before and changed it - this stuff may not work

---

### Post by lvleph on 2009-05-12
I have a similar router and was able to change the subnet.

---

### Post by jonathan F on 2009-05-13
I did try you recomendtion but unfortunatly no luck

I decided to try plugging the net cable into my laptop (windows) and was/am able to get to the router and navigate. I still have the problem of allowing my linux box access. Any thoughts?

---

### Post by ercanizzet on 2009-05-13
Hi all,
I am new user of Linux and Linux Ubuntu. I installed Ubuntu 9.04 today. I have wireless network at home and my desktop has D-Link DWA-110 Wireless adapter. As you guess i could not find the Linux driver of this adapter. Could ony one help me to find related driver or write me in detailed how to Linux detect this adapter? Please do not forget i am realy beginer for Linux.

---

### Post by lvleph on 2009-05-13
It seems to me that your ethernet card on the linux comp is not working. But you said you had it working before, yes?

> **ercanizzet said:**
> Hi all,
I am new user of Linux and Linux Ubuntu. I installed Ubuntu 9.04 today. I have wireless network at home and my desktop has D-Link DWA-110 Wireless adapter. As you guess i could not find the Linux driver of this adapter. Could ony one help me to find related driver or write me in detailed how to Linux detect this adapter? Please do not forget i am realy beginer for Linux.
Don't hijack threads. Start a new thread or better yet search for a thread dealing with your exact issue. Drivers are typically found on the manufacturers website. Windows drivers can be used by using a program called ndiswrapper. Do a search and you will get all the info you need.

---

### Post by jonathan F on 2009-05-13
It has worked. In fact, if I connect my computer directly to the internet (using my network connection) it works okay. Its just the router where things go pear shaped.

---

### Post by lvleph on 2009-05-13
If it is new, you could always return it to get the D-Link DIR-628. This is the exact one I have and it works perfectly. However, I don't believe it is Gigabit ehternet.

EDIT: Have you tried calling them?

---

### Post by Xamiga on 2009-05-13
> **jonathan F said:**
> eth0      Link encap:Ethernet  HWaddr 00:30:1b:bd:7f:16  
          inet6 addr: fe80::230:1bff:febd:7f16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6221 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4656398 (4.6 MB)  TX bytes:1632250 (1.6 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:209.240.37.6  P-t-P:209.240.47.145 Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:333 errors:0 dropped:0 overruns:0 frame:0
          TX packets:350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:358111 (358.1 KB)  TX bytes:58613 (58.6 KB)



This is showing that you do NOT have a connection to your router at least when you are connected to your ppp0 link (no ipv4 address).

Try disconnecting ppp0, rerun ifconfig and then reconnect and post the output.

al

---

### Post by jonathan F on 2009-05-14
sorry but as I am a green horn...can you advise how I disconnect ppo?

thanks

---

### Post by Xamiga on 2009-05-14
> **jonathan F said:**
> sorry but as I am a green horn...can you advise how I disconnect ppo?

thanks

Apparently you are connected to the internet via a modem or aircard of some type.  That is your ppp0 inteface as shown by ifconfig.  Disconnect that hardware, reboot, re-run ifconfig, and see if you then have an ip address showing up on your eth0 section of the ifconfig output.  If so then use the 192.168.0.1:80 address from firefox to connect to your router.  Also, what release version of ubuntu are you using?

---

### Post by jonathan F on 2009-05-15
thanks I will give it a try. Version 8.10

---

### Post by jonathan F on 2009-05-15
Tried no luck...

jonathan@jonathan-desktop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:30:1b:bd:7f:16  
          inet6 addr: fe80::230:1bff:febd:7f16/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1789 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:83622 (83.6 KB)  TX bytes:1204 (1.2 KB) 
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B) 

jonathan@jonathan-desktop:~$

---

### Post by agathian on 2009-05-15
> **jonathan F said:**
> I did try you recomendtion but unfortunatly no luck

I decided to try plugging the net cable into my laptop (windows) and was/am able to get to the router and navigate. I still have the problem of allowing my linux box access. Any thoughts?


Jonathan,

So the router is working fine from windows?

then, i would look at few things...
   - what IP does your windows box get?
   - can you access the router configuration page from the windows box?
          ( look at the gateway address from windows and access it thru browser )
    -   if you can access the config - verify if there are any filters set? like MAC filter for ex.
    -   is the ethernet card in your linux box working?
    -   is the cable you are using from linux box to router good?

I know this sounds a lot - but these are basic troubleshooting 101, sorry :)

BTW - where is this router connected to.. cablemodem? can you directly plugin your linux box to the cablemodem? - that way atleast you can make sure the NIC/cable is working fine.

-A

---

### Post by jonathan F on 2009-05-15
No worries...
Ip 192.168.0.1
I reset the D-link router back to factory deliver...so there asre not Mac filters etc (that I can see)
I beleive the ethernet in my linux box is working as I have to use it to connect to mythe internet.

---

### Post by Xamiga on 2009-05-15
> **jonathan F said:**
> No worries...
Ip 192.168.0.1
I reset the D-link router back to factory deliver...so there asre not Mac filters etc (that I can see)
I beleive the ethernet in my linux box is working as I have to use it to connect to mythe internet.

Jonathan,

I'm sure lost with this thread.

Please tell me exactly the physical setup that you used when you used "ethernet to connect to the internet"
Are you now unable to do that?

---

### Post by corowakid on 2009-05-16
> **jonathan F said:**
> No worries...
Ip 192.168.0.1
I reset the D-link router back to factory deliver...so there asre not Mac filters etc (that I can see)
I beleive the ethernet in my linux box is working as I have to use it to connect to mythe internet.

Hi - I'm no expert, but I'm sure the address of the modem isn't in the 192.168 range. I access mine via 10.1.1. Just a thought.

---

### Post by jonathan F on 2009-05-16
Okay...using a cat5e I connect the linux box to a wireless modem(modem is issue by the phone company and sadly is not configurable). In turn, I am able to be to the internet .

hope this makes sense?

---

### Post by jonathan F on 2009-05-18
All indications are that the linux box is not playing nice....any idea what settings I could adjust that might resolve my issue?

thanks

---

### Post by agathian on 2009-05-19
> **jonathan F said:**
> All indications are that the linux box is not playing nice....any idea what settings I could adjust that might resolve my issue?

thanks



Well- i would agree with this, if not for your previous reply. If it is working correctly when connected directly to the modem, that means ethernet card is fine and it is properly acquiring DHCP address.

Q1.  Are you using the same cable when connecting your linux box to modem and the D-link router?

Q2.  Is there some sort of indicator, at the router end and linux box's ethernet port, green light or something, confirming the physical link is working?

Q3. have you tried manually setting the address to 192.168.0.1 ( and the relevant subnet/gateway/etc, exactly as you are seeing in the windoze box ) ( actually, this is kind of a moot point, bcos it is working fine when you connect directly to the cable/dsl modem)

---

