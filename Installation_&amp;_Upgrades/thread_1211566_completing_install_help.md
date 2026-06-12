---
title: "completing install help"
date: 2009-07-12
forum: Installation &amp; Upgrades
---

### Post by Biceptoid on 2009-07-12
ok i am on a asus g50 and i have an atheros wireless card. i just finished install and i cant get the wireless to connect. all my internet options are greyed out. i duel boot with windows and my windows wireless works fine. so im nto sure if it is a compatalibty issue and what i can do about it. please help

---

### Post by earthpigg on 2009-07-12
> **Biceptoid said:**
> _***all***_ my internet options are greyed out. 

it doesn't work even if plugged into a wired internet connection?

---

### Post by Rocket2DMn on 2009-07-12
Atheros cards are notorious for having problems under linux, so it's not surprising that you're having troubles.  What is your exact model card?  You can check by running
```
lspci
```
or more specifically one of the following (this should work):
```
lspci | grep Wireless
lspci | grep Atheros
```
We can see if there is a bug report currently open for your card, and if not, I can help you file one.

Can you also please post the output of
```
ifconfig
```

---

### Post by Biceptoid on 2009-07-13
when i entered lspci | grep athertos it said.
 
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
 
thanks for the help
 
also when i type ifconfig it says
 
[FONT=Courier New][SIZE=3]kevin@kevin-laptop:~$ lspci | grep Atheros
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
kevin@kevin-laptop:~$ lspci | grep wireless
kevin@kevin-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:15:3a:37:cb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:247 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:15:af:ce:be:1e  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::215:afff:fece:be1e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3579 (3.5 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-CE-BE-1E-65-31-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

 [/SIZE][/FONT]

---

### Post by Rocket2DMn on 2009-07-13
It says you have an IP on the card - are you able to connect to your local wireless network at all?  Can you see any wireless networks when you click on the network manager applet in the taskbar?
Are there proprietary drivers listed for your card under System->Administration->Hardware Drivers?

I see a couple of bug reports related to your card
Bug [lpbug]379096[/lpbug] has already been triaged, and bugs [lpbug]324213[/lpbug] and [lpbug]370185[/lpbug] are older, but incomplete.  Do any of those accurately describe your problem?  Please elaborate on exactly what the problem is, what you have tried, and what behavior you are seeing.

---

### Post by Biceptoid on 2009-07-13
when i get on unbuntu 9.04 everything runs fine. not issues there. my problem is that i cant get any internet connection. Under internet options everything is greyed out so that i cant even click to see other wireless networks at all. i tired some connection comand prompts to no avail.. yet. when i manuely enter my router and modem into the internet connections it says connection established but it never picks up any signal. 
 
i intially tired to run ubuntu 8.04 but had many issues just getting that installed and when i did had issues running the program.
 
also i just plugged a hardwire into my laptop and the internet runs on my comptuer it just cant track my wireless for some reason

---

### Post by Rocket2DMn on 2009-07-14
What do you mean by "internet options"?  Where are you doing this manual entry?  Can you please provide a screenshot?

---

