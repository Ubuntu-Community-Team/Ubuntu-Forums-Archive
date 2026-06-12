---
title: "Printer sharing"
date: 2011-04-05
forum: Hardware
---

### Post by DrBob89 on 2011-04-05
I have a desktop pc running Ubuntu 10.10 with a Canon MF4150 printer. I have set the printer to be shared. My laptop is connected through a wireless modem.  It has the MF4150 drivers installed and will print with the printer connected directly.

However, it will not "see" the printer when it is connected to the desktop unit when I try to set it up to share the printer.

Error message: "There were no printshares found.  Please check that the Samba service is marked as trusted in you firewall configuration."

I don't have a firewall installed on either machine.

---

### Post by gzarkadas on 2011-04-07
Ubuntu ships with a firewall (ufw) enabled by default, if I am not wrong. To see for yourself whether this is the case for you, open a terminal window (from Applications|Accessories menu) and type this command to show all your active iptables rules:

```
sudo iptables --list-rules
```

In order to not have a firewall enabled, the output should essentially be empty.  If you see considerable output, then the firewall is enabled and you'll need to open the samba-related ports.

---

### Post by ryounkin on 2011-04-07
According to Firestarter, the firewall is disabled on both machines. Indeed, I get an error message when I try to enable the firewall to the effect that I don't have an internet connection.

Bob

---

### Post by gzarkadas on 2011-04-08
All firewalls are front-ends to iptables, so please post the output of the command in my previous post to acquire a feeling on what's going on at your machine. 

You can try to run the command ```
sudo iptables -F
``` to remove all your rules (this effectively disables the firewall untill the next reboot) and see if printer is accessible.

If you do not have a network connection this is another problem than the one stated in the initial post. If you want to pursue a solution here, please post -in addition to `sudo iptables --list-rules` - the output of the commands below (all run from inside a terminal window):
```

sudo ifconfig
sudo netstat -tuape

```and also a brief explanation of how you (should) connect: with a modem, with a DSL router, with ...

---

### Post by DrBob89 on 2011-04-08
Obviously, I have an internet connection.  I'm using it right now.  Firestarter refuses to enable the firewall giving an error message that I DON't have a connection. Further inquiry along that path revealed that Firestarter is apparently not the best graphical front end for the firewall.  I downloaded gufw which did allow me to enable the firewall, with the SAMBA exceptions and it still didn't work.  So I disabled the firewall, again.  

I have a cable internet connection running through a Linksys wireless router, which is firewalled, hence I didn't feel the need to enable the Ubuntu Firewall.  The "office" machine is hard wired to the router and is the "server" with the printer attached.  The "laptop" has a wireless connection. Both Machines run ubuntu 10.10.  I have, in the past, been able to print in this configuration when "office" was running XP and "laptop" was running Vista. Which suggests to me that the problem is not with the router. 

Here is the output you requested.

Thanks

bob@office:~$ sudo iptables --list-rules
[sudo] password for bob: 
-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT

bob@office:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:22:3f:ec:c8:86  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:3fff:feec:c886/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:189871 errors:0 dropped:0 overruns:0 frame:0
          TX packets:185878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:132624471 (132.6 MB)  TX bytes:47478456 (47.4 MB)
          Interrupt:16 Base address:0x8600 

eth1      Link encap:Ethernet  HWaddr 00:14:22:5a:34:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1680 (1.6 KB)  TX bytes:1680 (1.6 KB)

bob@office:~$ sudo netstat -taupe
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       User       Inode       PID/Program name
tcp        0      0 *:ipp                   *:*                     LISTEN      root       23843       1141/cupsd      
tcp        0      0 localhost.:microsoft-ds *:*                     LISTEN      root       8064        791/smbd        
tcp        0      0 localhost.l:netbios-ssn *:*                     LISTEN      root       8065        791/smbd        
tcp        0      0 office:57715            a184-84-222-43.depl:www ESTABLISHED bob        50340       1801/chromium-brows
tcp        0      0 office:44915            74.125.224.56:https     ESTABLISHED bob        14215       1801/chromium-brows
tcp        0      0 office:35955            a184-84-222-139.dep:www ESTABLISHED bob        168751      1801/chromium-brows
tcp        0      0 office:53638            a184-84-222-65.depl:www ESTABLISHED bob        168924      1801/chromium-brows
tcp        0      0 office:33136            a184-84-222-98.depl:www ESTABLISHED bob        170769      1801/chromium-brows
tcp        0      0 office:39069            a184-84-222-112.dep:www ESTABLISHED bob        173615      1801/chromium-brows
tcp        0      0 office:48250            ec2-174-129-245-200:www ESTABLISHED bob        173628      1801/chromium-brows
tcp        0      0 office:48320            66.77.124.48:www        ESTABLISHED bob        169480      1801/chromium-brows
tcp        0      0 office:41261            a184-84-222-66.depl:www ESTABLISHED bob        158205      1801/chromium-brows
tcp        0      0 office:54489            a96-17-127-139.depl:www ESTABLISHED bob        168762      1801/chromium-brows
tcp        0      0 office:56109            a184-84-222-120.dep:www ESTABLISHED bob        168885      1801/chromium-brows
tcp        0      0 office:53436            66.77.124.48:www        ESTABLISHED bob        165535      1801/chromium-brows
tcp        0      0 office:57545            a96-17-124-20.deplo:www ESTABLISHED bob        149493      1801/chromium-brows
tcp        0      0 office:35956            a184-84-222-139.dep:www ESTABLISHED bob        168752      1801/chromium-brows
tcp        0      0 office:52650            a184-84-222-66.depl:www ESTABLISHED bob        165554      1801/chromium-brows
tcp        0      0 office:35957            a184-84-222-139.dep:www ESTABLISHED bob        168753      1801/chromium-brows
tcp        0      0 office:51375            a184-84-222-8.deplo:www ESTABLISHED bob        149375      1801/chromium-brows
tcp        0      0 office:40979            74.125.224.59:www       ESTABLISHED bob        173573      1801/chromium-brows
tcp        0      0 office:38567            www-10-04-snc4.face:www ESTABLISHED bob        168748      1801/chromium-brows
tcp        0      0 office:51373            a184-84-222-8.deplo:www ESTABLISHED bob        149373      1801/chromium-brows
tcp        0      0 office:45475            207.46.119.234:www      ESTABLISHED bob        173629      1801/chromium-brows
tcp        0      0 office:36819            74.125.224.57:www       ESTABLISHED bob        173586      1801/chromium-brows
tcp        0      0 office:57148            a184-84-222-130.dep:www ESTABLISHED bob        168942      1801/chromium-brows
tcp        0      0 office:44033            ox-173-241-242-20.x:www TIME_WAIT   root       0           -               
tcp        0      0 office:50052            a184-84-222-43.depl:www ESTABLISHED bob        52544       1801/chromium-brows
tcp        0      0 office:33933            a184-84-222-40.depl:www ESTABLISHED bob        117542      1801/chromium-brows
tcp        0      0 office:37305            a184-84-222-66.depl:www ESTABLISHED bob        169485      1801/chromium-brows
tcp        0      0 office:45389            a184-51-159-51.depl:www ESTABLISHED bob        169604      1801/chromium-brows
tcp        0      0 office:48318            66.77.124.48:www        ESTABLISHED bob        169478      1801/chromium-brows
tcp        1      0 office:35032            74.125.224.66:www       CLOSE_WAIT  bob        173106      1801/chromium-brows
tcp        0      0 office:43058            a184-51-159-16.depl:www ESTABLISHED bob        168773      1801/chromium-brows
tcp        0      0 office:34661            a96-17-117-115.depl:www ESTABLISHED bob        169022      1801/chromium-brows
tcp        0      0 office:40980            74.125.224.59:www       ESTABLISHED bob        173577      1801/chromium-brows
tcp        0      0 office:56290            a96-17-109-24.deplo:www TIME_WAIT   root       0           -               
tcp        0      0 office:36077            a184-84-222-43.depl:www ESTABLISHED bob        48774       1801/chromium-brows
tcp        0      0 office:48322            66.77.124.48:www        ESTABLISHED bob        169482      1801/chromium-brows
tcp        0      0 office:57717            a184-84-222-43.depl:www ESTABLISHED bob        50342       1801/chromium-brows
tcp        0      0 office:37649            a184-84-222-105.dep:www ESTABLISHED bob        173604      1801/chromium-brows
tcp      415      0 office:42240            a96-17-109-106.depl:www CLOSE_WAIT  bob        173561      1801/chromium-brows
tcp        0      0 office:48319            66.77.124.48:www        ESTABLISHED bob        169479      1801/chromium-brows
tcp        0      0 office:34103            a184-84-222-104.dep:www ESTABLISHED bob        170612      1801/chromium-brows
tcp        0      0 office:45061            sn2ldc2.ac3.msn.com:www ESTABLISHED bob        168909      1801/chromium-brows
tcp        0      0 office:38597            www-10-04-snc4.face:www ESTABLISHED bob        168954      1801/chromium-brows
tcp        0      0 office:44034            ox-173-241-242-20.x:www TIME_WAIT   root       0           -               
tcp        1      0 office:48886            px-in-f138.1e100.ne:www CLOSE_WAIT  bob        173110      1801/chromium-brows
tcp        0      0 office:53418            a184-84-222-130.dep:www ESTABLISHED bob        153354      1801/chromium-brows
tcp        0      0 office:38461            pz-in-f125.:xmpp-client ESTABLISHED bob        14848       1801/chromium-brows
tcp        0      0 office:33932            a184-84-222-40.depl:www ESTABLISHED bob        117541      1801/chromium-brows
tcp        0      0 office:33237            65.55.5.232:www         ESTABLISHED bob        168757      1801/chromium-brows
tcp        0      0 office:35954            a184-84-222-139.dep:www ESTABLISHED bob        168750      1801/chromium-brows
tcp6       0      0 [::]:ipp                [::]:*                  LISTEN      root       23845       1141/cupsd      
udp        0      0 *:56859                 *:*                                 avahi      8198        1017/avahi-daemon: 
udp        0      0 *:bootpc                *:*                                 root       8566        1147/dhclient   
udp   114624      0 *:ipp                   *:*                                 root       23848       1141/cupsd      
udp        0      0 *:netbios-ns            *:*                                 root       9196        1335/nmbd       
udp    53312      0 *:netbios-dgm           *:*                                 root       9197        1335/nmbd       
udp        0      0 *:mdns                  *:*                                 avahi      8196        1017/avahi-daemon: 
udp6       0      0 [::]:mdns               [::]:*                              avahi      8197        1017/avahi-daemon: 
udp6       0      0 [::]:55056              [::]:*                              avahi      8199        1017/avahi-daemon:

---

### Post by gzarkadas on 2011-04-09
Your services (samba|cups) seem ok. So you have your firewalls open and the services up and running. The only thing left to look at is service configuration. Either samba or/and cups.

**Big, fat disclaimer:** Since I have *not* significant experience in cups/samba sharing of printers, all of the suggestions below are plausible ways to achieve your goal based on documentation, but I have not personally verified them. Use at your own risk and backup files you edit so that you can restore your previous state. If anything goes wrong, there is a high probability that I will not be able to help. If there are more competent in this subject forum members, please drop in :).

Now, on with the suggestions:

What are the contents of the [printers] section in your server's `/etc/samba/smb.conf' ? Does it have the following lines? (either with 1 or Yes):
```

[printers]
...
 printable = 1
 public = 1
 browsable = 1
...

```If not try to include them and see what happens.

See also the cups documentation at [http://localhost:631/help/sharing.html](http://localhost:631/help/sharing.html) (this assumes you have a web server running on your machine, if not use the online help at [http://cups.org/documentation.php/doc-1.4/sharing.html](http://cups.org/documentation.php/doc-1.4/sharing.html)). 

By reading this, it seems to me that you need to run on the server the command ```
cupsctl 'BrowseLocalProtocols="cups smb"'
``` because smb sharing of printers is not enabled by default.

You may also need to execute ```
cupsctl --share-printers
``` on your server. If however your network contains subnets you need ```
cupsctl --share-printers --remote-any
``` instead. In that later case you 'll need to also execute ```
cupsctl BrowsePoll=server:port
``` on your client (laptop).

Test all the above one at a time, in order to be certain what worked and what has not worked.

---

### Post by DrBob89 on 2011-04-09
Public = no

But I can't edit the samba.conf file directly.  Is there a command line instruction?

This brings up the question of SAMBA documentation, which I find to be lacking. Could you recommend a good reference?

Thanks Bob

---

### Post by IcarusR on 2011-04-10
> But I can't edit the samba.conf file directly. Is there a command line instruction?


In a terminal...

```
sudo gedit /path/to/samba.conf
```

You will be asked for your password.

SWAT is a web admin tool for samba, is in repos.

Samba howto/docs

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/]("http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/")

There are a lot of docs on samba website.

This is my working printers section.

```
[printers]
	path = /var/spoool/samba
	guest ok = Yes
	printable = Yes
	browseable = No

```

Testparm is a samba terminal tool that parses & checks samba.conf

```
testparm
```

Hope this is of help.

---

### Post by DrBob89 on 2011-04-13
I finally went to: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2554221](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/FastStart.html#id2554221) , which has an example of a simple anonymous print server. I swapped out the smb.conf on both machines, with appropriate modifications and it worked.

Thanks Bob

---

