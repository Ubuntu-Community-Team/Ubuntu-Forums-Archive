---
title: "Enable Romaming mode? Static IP issue on brand new installation"
date: 2008-08-20
forum: General Help
---

### Post by milasch on 2008-08-20
Hello,

Yesterday I made a fresh installation of ubuntu 8.041 in my Compaq N610c Laptop. The first thing I did after that was to update every package it found update for...

Then installed the LAMP server, set up, etc.

Finally, since I want to use it as a small web server, I wanted to setup a static IP address so I could nat some ports to the laptop... I used the System->Administration->Network Settings to do that, so I unchecked the "Enable roaming mode" find it the only way to put a manual IP address there... Then I found the DNS/Gateway to be ok, under the other tabs, clicked ok...

The connection is lost immediately after I do that. I don't remember right now if I can ping the router... But when I did ifconfig, I got only an ipv6 address. So I have to do
```

sudo ifdown eth0
sudo ifup eth0

```
then it will work properly.

If i reboot though, the settings will be lost.

when I installed ubuntu in my desktop pc it had same problem. I could fix it by messing with the /etc/networks/interfaces settings, but that was a bit luck since I don't remember exactly what I did there...

right now, in the laptop it has:
```

cat /etc/network/interfaces 
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.0.170
netmask 255.255.255.0
gateway 192.168.0.1

auto eth0

```

My desktop pc has
```

cat /etc/network/interfaces
auto lo
iface lo inet loopback
auto br0
iface eth0 inet static
address 192.168.0.169
netmask 255.255.255.0
gateway 192.168.0.1
auto eth0

```
NOTE: br0 was an interface I used to setup virtual box, I'm no longer using it but I'm afraid if I take it out my desktop's network will stop working smoothly again.

It's no big deal, I can, when I have time, mess again with the /etc/networks/interfaces settings on my laptop... 

But as a matter of curiosity, does anyone know why the heck this happens? Isn't it an issue that should have an update for available? What is the best work around?

Thanks!

---

