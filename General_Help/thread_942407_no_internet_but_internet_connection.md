---
title: "no internet but internet connection"
date: 2008-10-09
forum: General Help
---

### Post by Achilles124 on 2008-10-09
Yesterday I installed the firewall guarddog. Because this was not done with administrator rights I had no full access to guarddog. So, I removed it.

But now I encounter problems with my internet. I cannot go online. But I do have an internet connection. I am working with Puppy Linux Live Cd now. Why can't I get online when using Ubuntu?

I have run some terminalcommands:
> eth0      Link encap:Ethernet  HWaddr 00:1d:92:70:97:77  
          inet addr:83.189.228.68  Bcast:83.189.255.255  Mask:255.255.224.0
          inet6 addr: fe80::21d:92ff:fe70:9777/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:338 (338.0 B)  TX bytes:342 (342.0 B)
          Interrupt:220 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2054 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96696 (94.4 KB)  TX bytes:96696 (94.4 KB)


 and netstat

---

### Post by Achilles124 on 2008-10-09
Auth log says:

Oct  9 18:18:53 ecmpeek-desktop guarddog: Configuring iptables firewall now.
Oct  9 18:18:56 ecmpeek-desktop guarddog: Finished configuring firewall

How is it possible that guarddog configures iptables. I have deinstalled the program?

thanks in advance

---

### Post by cariboo on 2008-10-09
To see if you have any rules blocking you access in a terminal type:

```
sudo iptables -L
```

This will list all the rules that gaurddog applied. To get rid of the rules in a terminal type:

```
sudo iptables -F
```

If you need a firewall, I would suggest using ufw to control it. There is a gui version of ufw called gufw, it is now in the Intrepid  (v. 8.10) repositories. You can download it here:

[http://packages.ubuntu.com/search?keywords=gufw&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=gufw&searchon=names&suite=all&section=all)

Jim

---

### Post by Achilles124 on 2008-10-10
I don't have much knowledge about the terminal so maybe you can help me out, cariboo, to see if there is anything wrong in the iptables. Here is the sudo iptables -L:

> Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  83.189.228.68        83.189.255.255      
logaborted  tcp  --  anywhere             anywhere            state RELATED,ESTABLISHED tcp flags:RST/RST 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
nicfilt    all  --  anywhere             anywhere            
srcfilt    all  --  anywhere             anywhere            

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
srcfilt    all  --  anywhere             anywhere            

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 
ACCEPT     icmp --  anywhere             anywhere            icmp destination-unreachable 
ACCEPT     icmp --  anywhere             anywhere            icmp time-exceeded 
ACCEPT     icmp --  anywhere             anywhere            icmp parameter-problem 
s1         all  --  anywhere             anywhere            

Chain f0to1 (3 references)
target     prot opt source               destination         
logdrop    all  --  anywhere             anywhere            

Chain f1to0 (1 references)
target     prot opt source               destination         
logdrop    all  --  anywhere             anywhere            

Chain logaborted (1 references)
target     prot opt source               destination         
logaborted2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 

Chain logaborted2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `ABORTED ' 
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED 

Chain logdrop (4 references)
target     prot opt source               destination         
logdrop2   all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
DROP       all  --  anywhere             anywhere            

Chain logdrop2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `DROPPED ' 
DROP       all  --  anywhere             anywhere            

Chain logreject (0 references)
target     prot opt source               destination         
logreject2  all  --  anywhere             anywhere            limit: avg 1/sec burst 10 
LOG        all  --  anywhere             anywhere            limit: avg 2/min burst 1 LOG level warning prefix `LIMITED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       all  --  anywhere             anywhere            

Chain logreject2 (1 references)
target     prot opt source               destination         
LOG        all  --  anywhere             anywhere            LOG level warning tcp-sequence tcp-options ip-options prefix `REJECTED ' 
REJECT     tcp  --  anywhere             anywhere            reject-with tcp-reset 
REJECT     udp  --  anywhere             anywhere            reject-with icmp-port-unreachable 
DROP       all  --  anywhere             anywhere            

Chain nicfilt (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
RETURN     all  --  anywhere             anywhere            
logdrop    all  --  anywhere             anywhere            

Chain s0 (1 references)
target     prot opt source               destination         
f0to1      all  --  anywhere             83.189.228.68       
f0to1      all  --  anywhere             83.189.255.255      
f0to1      all  --  anywhere             localhost           
logdrop    all  --  anywhere             anywhere            

Chain s1 (1 references)
target     prot opt source               destination         
f1to0      all  --  anywhere             anywhere            

Chain srcfilt (2 references)
target     prot opt source               destination         
s0         all  --  anywhere             anywhere            
ecmpeek@ecmpeek-desktop:~$ 




---

### Post by fragos on 2008-10-11
That is far from a default iptables and your problem is likely there. The following is the default iptables output. There is a command iptables-restore that might fix things for you but I recommend you research it before trying it as this is only a guess.

fragos@Geo:~$ sudo iptables -L
[sudo] password for fragos: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
fragos@Geo:~$

---

### Post by Achilles124 on 2008-10-11
The command iptables restore can one use if one has saved the iptables beforehand. I didn't, so that is not an option. 

I tried the command sudo iptables -F. But to no avail.

I give you more lines:
> Oct  9 12:45:01 ecmpeek-desktop CRON[7746]: pam_unix(cron:session): session opened for user root by (uid=0)
Oct  9 12:45:01 ecmpeek-desktop CRON[7746]: pam_unix(cron:session): session closed for user root
Oct  9 12:45:50 ecmpeek-desktop gnome-keyring-daemon[6423]: removing removable location: volume_uuid_DCC0_02A1
Oct  9 12:58:47 ecmpeek-desktop gdm[5991]: pam_nologin(gdm:auth): cannot determine username
Oct  9 12:58:50 ecmpeek-desktop gdm[5991]: pam_unix(gdm:session): session opened for user ecmpeek by (uid=0)
Oct  9 12:58:52 ecmpeek-desktop gnome-keyring-daemon[6221]: Couldn't unlock login keyring with provided password
Oct  9 12:58:52 ecmpeek-desktop gnome-keyring-daemon[6221]: Failed to unlock login on startup
Oct  9 12:58:57 ecmpeek-desktop guarddog: Configuring iptables firewall now.
Oct  9 12:58:57 ecmpeek-desktop guarddog: Finished configuring firewall

This comes from the auth.log.

Hope this shed some light. Thanks for help in advance.

---

### Post by Achilles124 on 2008-10-11
I run the following command:
sudo locate guarddog

and this was the result:

> 
/etc/init.d/guarddog
/etc/network/if-down.d/50guarddog
/etc/network/if-up.d/50guarddog
/etc/ppp/ip-down.d/50guarddog
/etc/ppp/ip-up.d/50guarddog
/etc/rcS.d/S65guarddog
/home/ecmpeek/.kde/share/config/guarddogrc
/home/ecmpeek/Documenten/Computer/www-simonzone-com_software_guarddog_manual2_using-guarddog-html#id2406392.pdf
/usr/share/app-install/desktop/guarddog.desktop
/usr/share/app-install/icons/guarddog.png
/usr/share/openclipart/png/computer/icons/flat-theme/applications/guarddog.png
/usr/share/openclipart/png/computer/icons/lemon-theme/apps/guarddog.png
/usr/share/openclipart/svg/computer/icons/flat-theme/applications/guarddog.svg
/usr/share/openclipart/svg/computer/icons/lemon-theme/apps/guarddog.svg
/var/cache/apt/archives/guarddog_2.6.0-1ubuntu1_i386.deb
/var/lib/dpkg/info/guarddog.list
/var/lib/dpkg/info/guarddog.postrm

My computer is still filled with guarddog files. Can I safely remove all of them?

---

### Post by Achilles124 on 2008-10-11
See what I have found on the net:
A german fellow had the same problem as I have:
[http://forum.ubuntuusers.de/topic/ich-komme-nicht-mehr-ins-internet./]("http://forum.ubuntuusers.de/topic/ich-komme-nicht-mehr-ins-internet./")

with the solution given there:
sudo rm /etc/rcS.d/S65guarddog /etc/ppp/ip-up.d/50guarddog /etc/ppp/ip-down.d/50guarddog /etc/init.d/guarddog /etc/network/if-down.d/50guarddog /etc/network/if-up.d/50guarddog ~/.kde/share/config/guarddogrc

I will let you know if it works.

---

### Post by Achilles124 on 2008-10-11
It didn't work.

First I give the command locate guarddog and I get this:> /etc/init.d/guarddog

/etc/network/if-up.d/50guarddog
/etc/ppp/ip-down.d/50guarddog
/etc/ppp/ip-up.d/50guarddog
/etc/rcS.d/S65guarddog
/home/ecmpeek/.kde/share/config/guarddogrc
/home/ecmpeek/Documenten/Computer/www-simonzone-com_software_guarddog_manual2_using-guarddog-html#id2406392.pdf
/usr/share/app-install/desktop/guarddog.desktop
/usr/share/app-install/icons/guarddog.png
/usr/share/openclipart/png/computer/icons/flat-theme/applications/guarddog.png
/usr/share/openclipart/png/computer/icons/lemon-theme/apps/guarddog.png
/usr/share/openclipart/svg/computer/icons/flat-theme/applications/guarddog.svg
/usr/share/openclipart/svg/computer/icons/lemon-theme/apps/guarddog.svg
/var/cache/apt/archives/guarddog_2.6.0-1ubuntu1_i386.deb
/var/lib/dpkg/info/guarddog.list
/var/lib/dpkg/info/guarddog.postrm

but when I give the command:
sudo rm /etc/network/if-down.d/50guarddog

I get:
ecmpeek@ecmpeek-desktop:~$ sudo rm /etc/network/if-down.d/50guarddog
rm: cannot remove `/etc/network/if-down.d/50guarddog': **No such file or directory**

Not there? :confused:

I don't understand. I am so close...
Anyone???

---

### Post by Achilles124 on 2008-10-11
anyone? I am so close.

---

### Post by Dr_Willis on 2008-10-11
Note that the locate command, uses a database, that database only gets updated every 24 hrs or so..

You are searching/finding files that are no longer there in some cases.

sudo updatedb 


will take a few min to run, and have updated your locate database.

:lolflag:

---

### Post by Achilles124 on 2008-10-14
Solved it. Run updatedb in terminal and files were gone. Internet is running. Thanks for answering. 

Greetz

---

