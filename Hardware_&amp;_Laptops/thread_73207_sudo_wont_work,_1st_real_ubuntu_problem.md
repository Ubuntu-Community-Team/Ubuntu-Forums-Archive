---
title: "sudo wont work, 1st real ubuntu problem"
date: 2005-10-08
forum: Hardware &amp; Laptops
---

### Post by mjkelly on 2005-10-08
Being an idiot, i installed this wi-fi radar program just to see what it did. I played with it a little and it messed up my internet connection. So i opened up Network-Config through administration and tried restarting the net. Wouldnt work. So i went and erased all the settings in there for eth1 then figured when i restarted the comp it would automatically detect and fill in the settings, such as the hostname.

Well... Now sudo wont work. And with sudo not working i cant run network-config. Heres the error from sudo:
sudo : unable to lookup x1-a0-00-b1-**-**-**-** via gethostbyname()
Where the astericks are alphanumeric combinations that correspond to the alphanumeric combination listed next to eth1 in lspci.
Now i dont have the lspci right here because im in windows... **shutters....
But heres something like it looked like

eth1 : Rhine II Ethernet Controller 10/10Mbps : x1-a1-b5-89-n7-**-**-**

you get the idea. So it took the setting after my ethernet controller listing in lspci and is using it for my hostname(???) Im really not sure. When im at a shell prompt it looks like this:
homeslice@x1-89-c3-s7-lk-43-**-**-** : #
It used to say      homeslice@ubuntu : #

When i log into gnome it tells me that my hostname doesnt match up in /etc/hosts and to place x1-89-v4-********* manually into /etc/hosts/
Well i did that and it didnt work.

Any suggestions? I searched google briefly before coming here and they recommended changing etc/hosts but that didnt work again.

---

### Post by mlomker on 2005-10-08
You could start by checking the contents of these three files.  I'm not sure what exactly you deleted, though.  The entries in iftab should match the hardware addresses that **ifconfig** gives you.

```

mlomker@mlomkernote:/etc$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost       mlomkernote

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
mlomker@mlomkernote:/etc$ cat /etc/hostname
mlomkernote
mlomker@mlomkernote:/etc$ cat /etc/iftab
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:03:0D:D3:CA:F0
wlan0 mac 00:11:F0:CC:5D:05

```

---

### Post by landotter on 2005-10-08
Are you trying to run sudo as the first user created? Any additional users may not use sudo (unless you enable that privledge)

---

### Post by mjkelly on 2005-10-08
im gonna check those files then mount the windows partition and save the outputs on windows then copy and paste em up here.

it is the original user, not an added one. it has something to do with me erasing the contents of the System > Administration > Network Configuration -- Hosts tab

There was something there called shendo which was what i chose to name the host when installing ubuntu. Ya know how it asks that hostname that you can pick, i chose shendo and then i erased that. But now i cant use sudo to get back into network config to readd that, but im not even sure if that would work now or not.

Like it used to say    homeslice@ubuntu : # but now it has that weird alphanumeric address there, why is that? What would cause that?


My etc/hosts is empty, i know that already

---

### Post by mjkelly on 2005-10-08
Ok /etc/hosts/ and /etc/hostname/ are both empty except for # marked off lines.

Heres /etc/iftab:
# This file assigns persistent names to network interfaces.  See iftab(5).
eth0 mac 00:04:5a:50:57:e2
eth1 mac 00:e0:4c:b0:89:a9
Heres ifconfig
eth1      Link encap:Ethernet  HWaddr**_ 00:E0:4C:B0:89:A9 _** 
          inet addr:12.44.226.13  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::2e0:4cff:feb0:89a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2427 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:156649 (152.9 KiB)  TX bytes:5780 (5.6 KiB)
          Interrupt:23 Base address:0xec00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:824 errors:0 dropped:0 overruns:0 frame:0
          TX packets:824 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:252710 (246.7 KiB)  TX bytes:252710 (246.7 KiB)

Heres /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp

auto eth1




## The bold underlined line halfway up there is the number that sits next to homeslice@** : #

Any ideas guys?

---

### Post by mlomker on 2005-10-08
> =mjkelly]Ok /etc/hosts/ and /etc/hostname/ are both empty except for # marked off lines.


You'll need to recreate those to fix that 'getbyhostname' error.  You can use mine as a template--just fill in 'mlomkernote' with whatever you want to name your machine.

I'm not sure how you're getting in right now, but a Knoppix disc will allow you to boot up and edit those files if need be.

---

### Post by mjkelly on 2005-10-08
Nah i can boot in from recovery then use vim to edit the files.
I already did tho. I added a line in my /etc/hosts file like
127.0.01        localhost.localdomain          shendo

and it fixed my sudo problem completely
my prompt is fixed too


However, i cant get my internet up and running. I just cant figure this one out. It connects via dhclient but wont work. Look here at my output
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:04:5a:50:57:e2
Sending on   LPF/eth0/00:04:5a:50:57:e2
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth1/00:e0:4c:b0:89:a9
Sending on   LPF/eth1/00:e0:4c:b0:89:a9
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 10.201.120.1
bound to 12.44.226.13 -- renewal in 33058 seconds.

See it finds and binds eth1, which is correct. In network-admin it is set as the default gateway, has located the DNS servers, and is activated. On the one tab of network-admin, the last one, the farthest to the right, it only lists my current /etc/hosts/ file verbatim. Like it says 127.0.0.1 localhost.localdomain shendo
There used to be alot more in there. Alot more numbers and addresses. I think that might be where the problem was. Those numbers were never manually entered in there so some program wrote them in there.

I dont know what else there is to do? I need to fully configure the network i think? Im really not sure. You guys know any commands here that work or can i get yas any more info?

---

### Post by mlomker on 2005-10-08
> I dont know what else there is to do? I need to fully configure the network i think? Im really not sure. You guys know any commands here that work or can i get yas any more info?

Let's take a look at these after you've run the dhclient:

```

ifconfig eth1
route -n
cat /etc/resolv.conf

```

Can you get to things by number?

```

ping 128.101.101.101

```

---

### Post by mjkelly on 2005-10-08
Ok heres the responses
ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:E0:4C:B0:89:A9  
          inet addr:12.44.226.13  Bcast:255.255.255.255  Mask:255.255.254.0
          inet6 addr: fe80::2e0:4cff:feb0:89a9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1553 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101793 (99.4 KiB)  TX bytes:5310 (5.1 KiB)
          Interrupt:23 Base address:0xec00 

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
12.44.226.0     0.0.0.0         255.255.254.0   U     0      0        0 eth1
0.0.0.0         12.44.226.1     0.0.0.0         UG    0      0        0 eth1

cat /etc/resolv.conf
domain shenhgts.net
nameserver 65.83.241.181
nameserver 67.32.118.46

And ping fails and doesnt return any ms.

Any ideas?

---

### Post by mlomker on 2005-10-08
> And ping fails and doesnt return any ms.


That all looks good to me.  Can you ping the gateway?  This worked before the whole wifi-radar thing?

```

ping 12.44.226.1

```

---

### Post by mjkelly on 2005-10-08
Yes it worked fine and is working now with windows on the same box with the same connection.

Thats what i said, everything looked good to me. Ill try that and post the reply.

---

### Post by mjkelly on 2005-10-08
Ok i pinged the gateway and it came back with a successful ping including a ms count.

What do i do now?

Im gonna try a post over on linuxquestions.org as well.

EDIT:
[http://www.linuxquestions.org/questions/showthread.php?s=&threadid=371056](http://www.linuxquestions.org/questions/showthread.php?s=&threadid=371056)

---

### Post by mlomker on 2005-10-09
I'd probably boot up a Knoppix CD and see if things work.  I'd also compare the output of those diagnostic commands between the two operating systems.

It's usually in situations like this that I end up reloading the box.  If everything looks right then there's probably some key file that got overwritten and the odds of finding it aren't so good.

---

### Post by mjkelly on 2005-10-09
Do you know what files that network-admin writes to?

Like when i started ubuntu, prolly during installation, it ran something to detect my network settings. It filled in all those tabs under network-admin. Including a bunch of settings that arent in there anymore. So i needa know what files network-admin writes to then compare it to someone else. Or id really like to know what program writes to network-admin.

---

### Post by mlomker on 2005-10-09
> Do you know what files that network-admin writes to?

I don't know.  I don't even use gnome on a regular basis.  I know a lot about networking in general because that's what I do for a living, but I don't know how the various graphical programs work because they're all different.

---

### Post by mjkelly on 2005-10-09
Ok new question.

When i run   dnsdomainname   i get the response: localhost
When i run   hostname   i get shendo.
In resolv.conf it lists a couple of nameservers, but they arent the nameservers that my ISP just gave me 5 minutes ago. So another question, how do i look up my DNS servers in windows? Am i gonna have to download some shitty program thats going to give me a 7 day free trial or some such shit?

When i change my nameservers in linux, in resolv.conf, then run dhclient to reconnect, it changes them back to what they were before i changed them. So its obviously connecting and detecting some nameservers. I want to compare them with the ones in windows to see if thats the problem, but apparently somewhere windows got rid of the command   winipcfg   prolly cuz microsoft obviously knows best.

---

### Post by mlomker on 2005-10-09
>  i look up my DNS servers in windows?

Open a command prompt:

```

ipconfig /all

``` 

> changes them back to what they were before i changed them. So its obviously connecting and detecting some nameservers. 

I've had that problem before--your ISP is dishing out addresses that don't work.  What you can do is install the **resolvconf** package.  It allows you to override those settings by adding a couple lines to your /etc/network/interfaces file.  Look at [this post.]("http://www.ubuntuforums.org/showthread.php?p=395480#post395480")

---

### Post by mjkelly on 2005-10-09
Well i checked the windows DNS servers with the Linux DNS servers and both are the same. So... it cant be a DNS problem.

Im trying to rule things out but im not getting anywhere. Like Linux is detecting DNS and IP and the whole thing. The card is set up right and all. I didnt toy with any modules or anything. And everything is enabled. I dont get it.

Besides DNS and everything named above, what else is included in using your connection? Can someone out there tell me what they have listed in the "Hosts" tab in network-admin? I still think its there.

---

