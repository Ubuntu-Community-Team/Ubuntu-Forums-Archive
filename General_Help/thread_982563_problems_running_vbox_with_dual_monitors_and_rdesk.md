---
title: "problems running vbox with dual monitors and rdesktop"
date: 2008-11-14
forum: General Help
---

### Post by themusicalduck on 2008-11-14
Hey,

I've been following the tutorial at [http://ubuntuforums.org/showthread.php?t=433359](http://ubuntuforums.org/showthread.php?t=433359) but have got stuck at the last step of actually making windows seamless.

I can start the VM fine but if I run the command like said on the tutorial, using the IP address which is assigned to my windows machine, then nothing happens. If I run the command using the IP address of the host then it lets me see the VM. If I log out and run the command again, like it says to do in the howto, then nothing happens. It only shows me the screen again but stays on the login screen and still isn't seamless.

This is the command it says to use to get to the VM -

```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" <IP recorded from Windows>:3389 -u "<Your Windows Username>" -p <Your Windows Password>
```


This is my rc.local file -

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

tunctl -t tap0 -u theo
 chmod 0666 /dev/net/tun
 /usr/sbin/brctl addbr br0
 /sbin/ifconfig eth1 0.0.0.0 promisc
 /usr/sbin/brctl addif br0 eth1
 /sbin/dhclient br0
 /usr/sbin/brctl addif br0 tap0
 ifconfig tap0 192.168.1.161 up
 bash -c 'echo 1 > /proc/sys/net/ipv4/conf/tap0/proxy_arp'
 route add -host 172.16.73.71 dev tap0
 arp -Ds 172.16.73.71 eth1 pub

exit 0
```


This is the only part I'm unsure about from the tutorial -

'Next, you need to replace <vbox_ip> with an IP that is within your subnet. It doesn't matter what it is, I use 192.168.1.161 simply because it was open. The only requirement is that there isn't another device on your network with this IP. This IP will come in handy when your Windows install is not accessible over the network. Confusing I know, but it will make more sense later.'

Since I'm connected to my university network it's hard to know whether the IP address I chose is actually free or not.. I just used the example he gave anyway.

Any thoughts?

---

### Post by themusicalduck on 2008-11-14
bump

---

### Post by themusicalduck on 2008-11-15
bump

---

