---
title: "configuring wired network connection"
date: 2009-09-23
forum: Hardware
---

### Post by manjusrinivas2007 on 2009-09-23
hai

i have installed UBUNTU 8.01.
we have wired internet conncetion.
how to configure network setting (i gave static IP, mas, gateway)

can anybody help in this regard.

Thank you..

---

### Post by fuzzyk.k on 2009-09-23
Right click on the icon that looks like two computers at the top right on the bar, select "Edit Connections..."  A window with the title "Network Connections " will appear with tabs at the top (wired , wireless etc.), from the buttons on the right select "Add" . A second window will appear with the title "Editing wired connection 1". here you can name your connection,if you use ipv4 select the ipv4 tab, you will see a label called method ,from the options beside it select manual, then click the add button on the lower right and input the addresses you need. the ipv6 is similar

helped ?

---

### Post by sirius1 on 2009-09-23
I have a similar problem in that I try and "Add" with the "Edit Connections..." from "Network Connections " I receive a dialogu box that says, "The ubterface does not exist." eth1

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sms       no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:212  Noise level:170
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

I don't no what to do now...I appreciate any help.

---

### Post by fuzzyk.k on 2009-09-23
you default first wired network card is normally eth0 not eth1.
please dump the output of > sudo ifconfig (paste the command in terminal and put your password)

---

### Post by sirius1 on 2009-09-23
Thanks...

~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:e8:91:b9:9a  
          inet addr:192.168.2.140  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::224:e8ff:fe91:b99a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:28790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22884 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25375160 (24.1 MB)  TX bytes:4454627 (4.2 MB)
          Interrupt:220 Base address:0x2000 

eth1      Link encap:Ethernet  HWaddr 00:23:08:6e:ba:2c  
          inet addr:192.168.2.141  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe6e:ba2c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4467 errors:0 dropped:0 overruns:0 frame:2816
          TX packets:9 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1031167 (1006.9 KB)  TX bytes:1613 (1.5 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1686 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1686 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:103288 (100.8 KB)  TX bytes:103288 (100.8 KB)

sms       Link encap:Ethernet  HWaddr 00:53:49:41:4e:4f  
          UP BROADCAST NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by sirius1 on 2009-09-23
If this helps...

~$ /etc/network/interfaces


auto lo
iface lo inet loopback



# iface eth0 inet dhcp

# auto eth0

---

### Post by fuzzyk.k on 2009-09-23
am sorry but according to your dump both your wired interfaces are configured. I am all out sorry , i fail to understand, wish i could help.

---

### Post by fuzzyk.k on 2009-09-23
all i can think of at the moment is assigning your ip manually from the terminal like this

> sudo ifconfig <interface> <ip address>

hope someone can do better, cheers

---

### Post by sirius1 on 2009-09-23
Appreciate your time!

---

### Post by sirius1 on 2009-09-26
I restored from, "Simple Backup Restore" and the problem was gone.

I now have both wired and wireless connection.

---

