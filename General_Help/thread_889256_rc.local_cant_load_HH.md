---
title: "rc.local cant load HH"
date: 2008-08-13
forum: General Help
---

### Post by badm4n on 2008-08-13
this is my /etc/rc.local ( ip edited for security reason )
---
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "1" > /proc/sys/net/ipv4/ip_forward

#-----------------------------------------------------
# eth0 = WAN1 = 202.xxx.xxx.119
# eth1 = DMZ = 192.168.222.1 ( Konek ke MAILSERVER & WEBSERVER - sementara simulai hanya mailserver )
# eth2 = LAN = 192.168.222.2 ( Konek ke PROXY SERVER - sementara di simulai PROXY SERVER = CLIENT )
#------------------------------------------------------

# Tukang sapu
/sbin/iptables --flush
/sbin/iptables --table nat --flush
/sbin/iptables --delete-chain
/sbin/iptables --table nat --delete-chain
/sbin/iptables -F -t nat

# Jembatan gantung DMZ <=> LAN
/sbin/iptables -A FORWARD -i eth2 -o eth1 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -i eth1 -o eth2 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Jembatan gantung DMZ <=> Mail Server & Webserver
/sbin/iptables -A FORWARD -i eth1 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth1 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

# Jembatan gantung WAN1 <=> LAN
/sbin/iptables -A FORWARD -i eth2 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -i eth0 -o eth2 -m state --state NEW,ESTABLISHED,RELATED -j ACCEPT

## Forward port 25 ke mail server
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d 202.xxx.xxx.119 --dport 25 -j DNAT --to-destination 172.16.0.2

## Forward port 80 ke mail server
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d 202.xxx.xxx.119 --dport 80 -j DNAT --to-destination 172.16.0.2

## Forward port 110 ke mail server
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d 202.xxx.xxx.119 --dport 110 -j DNAT --to-destination 172.16.0.2

## Forward port 2810 ke mail server
/sbin/iptables -t nat -A PREROUTING -p tcp -i eth0 -d 202.xxx.xxx.119 --dport 2810 -j DNAT --to-destination 172.16.0.2

# masqurade
/sbin/iptables --table nat --append POSTROUTING --out-interface eth0 -j MASQUERADE
/sbin/iptables --append FORWARD --in-interface  eth0 -j ACCEPT

## REDIRECT
# iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 8080

#transparant proxy - WARNING INI SEMENTARA - LIHAT eth2 -- pake dansguard port 2211
/sbin/iptables -t nat -A PREROUTING -i eth2 -p tcp -s 192.168.222.0/255.255.255.0 --dport 80 -j DNAT --to 192.168.222.2:2211

exit 0

----
root@simulasi:/home/mirza# ls -al /etc/rc.local
-rwxr-xr-x 1 root root 2604 2008-08-11 13:44 /etc/rc.local
root@simulasi:/home/mirza#
----
my question is

my rc.local not load atomatically everytime server soft reboot or hard reboot, so i must re run rc.local manually :(
when i test using manual rc
using update-rc
it works ( other files )
but rc.local still not works

why that can be happen ?

root@simulasi:/home/mirza# uname -a
Linux simulasi 2.6.24-19-server #1 SMP Sat Jul 12 00:40:01 UTC 2008 i686 GNU/Linux
root@simulasi:/home/mirza#

UBUNTU HH

---

### Post by Vivaldi Gloria on 2008-08-14
How about you change rc.local to a simple one like

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo "rclocal executed successfully" > /home/<your_username>/rclocal_executed 
exit 0
```

With this rc.local do you get a rclocal_executed file in your home folder when you boot up?


If it still doesn't work I suggest you try commands of the sort

```
sudo update-rc.d rc.local defaults 
sudo update-rc.d rc.local multiuser 
```

See

```
man update-rc.d 
```

for more info. First use with the flag

```
-n     Don’t do anything, just show what we would do.
```

---

