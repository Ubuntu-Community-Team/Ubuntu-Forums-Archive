---
title: "Network is always in use :("
date: 2008-11-08
forum: General Help
---

### Post by qwe99 on 2008-11-08
When is open the Ubuntu 8.1 the network is always in use. Sometimes about 2%, 6%, 16%  and sometimes 38% (1024 kbps is my internet speed). I close all softwares about network(browser,weather reporter,emesene...) but the network is still using. I looked to system monitor the network is just receiving . (nothing about sending). And it receivs 2-4 KIB/S but in the panel it writes 2%, 6%, 16%  and sometimes 38% .

---

### Post by bobyy on 2008-11-08
Ciao ..
Close all your programs witch ar running and conected to internet(firefox .gaim...)
 $sudo netstat -tupale
and
 $sudo lsof -i
so you can chech what prog is using the network or aree "calling home" :)

---

### Post by bodhi.zazen on 2008-11-08
Or use something like wireshark to capture your packets :)

---

### Post by qwe99 on 2008-11-08
user@user-desktop:~$ sudo netstat -tupale
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 localhost:ipp           *:*                     LISTEN      root       16648       5574/cupsd      
udp        0      0 *:51079                 *:*                                 avahi      16523       5503/avahi-daemon: 
udp        0      0 *:bootpc                *:*                                 root       18296       6182/dhclient   
udp        0      0 *:mdns                  *:*                                 avahi      16522       5503/avahi-daemon: 


user@user-desktop:~$ sudo lsof -i
COMMAND    PID  USER   FD   TYPE DEVICE SIZE NODE NAME
avahi-dae 5503 avahi   14u  IPv4  16522       UDP *:mdns 
avahi-dae 5503 avahi   15u  IPv4  16523       UDP *:51079 
cupsd     5574  root    2u  IPv4  16648       TCP localhost:ipp (LISTEN)
dhclient  6182  root    5w  IPv4  18296       UDP *:bootpc 

I write the commands to terminal after I closed the programs which are use the network. But I didn't understand what those means :confused:

---

### Post by bobyy on 2008-11-08
Ciao again 
So ...from this new point of view nothing is conected from outside or inside..
I think is nothing to be woried about ..
So the netstat command show you the whole listening/conected  ports witch are used by diferit daemons or programs with outside world and viceversa,
Lsof also show you the same stuf.... but with lsof (List Of Open Files) you can see also running programs.
Also always that will be a small amount of trafic because is need for the network to see you machine ....you machine send and receive packets (broadcast , ack )
My box in this moment is download 0,6 k/s and use this pack just to comunicate with the router and the boxes from network.
Also you can use wireshark for deeper investigation
Have fun :)

---

### Post by qwe99 on 2008-11-09
bobyy ; sorry but I didn't understand what did you want to tell me (my english is not so good) . But I think you told me to not worried about it .. So I'm not gonna do anythink ... (But I can't avoid myself still feeling bad :( :( )

---

### Post by bobyy on 2008-11-09
Yes that y want to tell you ..
For further investigation please use Wireshak to capture the packet`s betwen you machine and router ..
so you will see if is some suspicious trafic...

Have a good day.

---

