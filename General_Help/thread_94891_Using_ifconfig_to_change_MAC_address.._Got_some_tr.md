---
title: "Using ifconfig to change MAC address.. Got some troubles.. Help?"
date: 2005-11-25
forum: General Help
---

### Post by TmP on 2005-11-25
Edit-> Since it worked, you can use it as a how to!

Hi!
My Ip provider restricts the number of network cards that can access the net through my local lan->router. And since i like to plug my laptop in once in a while, its a bit of a pain in the ... I found a way around it, changing the MAC address of my ethernet card.

After the Linux starts up, i deactvate the card through 
system>preferences>network settings

than i run the console and use the following command

sudo ifconfig eth0 hw ether 00:a0:WH:AT:EV:ER

and than activate it back.

It works like a charm. Another way to do it would be using the MacChanger programme. I dont see the point, cause it probably does the same. 

Now my question would be..

1. Which console command would do the same thing as clicking the activate button?
2. How do I put all of this into startup? 
3. Or at least how do i make it easyer?


Untill now, I've tried using a small script wchich went like this:

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:a0:WH:AT:EV:ER
sudo ifconfig eth0 up

It did chgange the MAC address and deactivate the card, but didin't activate the card correctly. And it went awfully fast, like it wasn't waiting for a responce from the DHCP. And in fact it isn't recognised.

As I look at the ifconfig printout, it says:

eth0      Link encap:Ethernet  HWaddr 00:A0:WH:AT:EV:ER
          inet addr:62.xx.XX.x  Bcast:62.xx.XX.xx  Mask:255.xx.xx.x
          inet6 addr: fe80::2a0:d1ff:fed8:b58d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:698068 (681.7 KiB)  TX bytes:149976 (146.4 KiB)
          Interrupt:11 Base address:0xec00

The addres gets changed fine, and everything looks the same as when I ask for the printout after using the activate button. 

When I thy to acces the net, it says that i should check my connection. 
Everything runs ok when I activate the cart through the network settings.

Help? Please?

---

### Post by suRoot on 2005-11-25
sudo ifdown eth0
sudo ifup eth0

---

### Post by odin on 2005-11-25
[QUOTE=TmP]Hi!

My Ip provider restricts the number of network cards that can access the net through my local lan->router. And since i like to plug my laptop in once in a while, its a bit of a pain in the ... I found a way around it, changing the MAC address of my ethernet card.

After the Linux starts up, i deactvate the card through 
system>preferences>network settings

than i run the console and use the following command

sudo ifconfig eth0 hw ether 00:a0:WH:AT:EV:ER

and than activate it back.

It works like a charm. Another way to do it would be using the MacChanger programme. I dont see the point, cause it probably does the same. 

Now my question would be..

1. Which console command would do the same thing as clicking the activate button?
2. How do I put all of this into startup? 
3. Or at least how do i make it easyer?


Untill now, I've tried using a small script wchich went like this:

sudo ifconfig eth0 down
sudo ifconfig eth0 hw ether 00:a0:WH:AT:EV:ER
sudo ifconfig eth0 up

It did chgange the MAC address and deactivate the card, but didin't activate the card correctly. And it went awfully fast, like it wasn't waiting for a responce from the DHCP. And in fact it isn't recognised.

As I look at the ifconfig printout, it says:

eth0      Link encap:Ethernet  HWaddr 00:A0:WH:AT:EV:ER
          inet addr:62.xx.XX.x  Bcast:62.xx.XX.xx  Mask:255.xx.xx.x
          inet6 addr: fe80::2a0:d1ff:fed8:b58d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1122 errors:0 dropped:0 overruns:0 frame:0
          TX packets:966 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:698068 (681.7 KiB)  TX bytes:149976 (146.4 KiB)
          Interrupt:11 Base address:0xec00

The addres gets changed fine, and everything looks the same as when I ask for the printout after using the activate button. 

When I thy to acces the net, it says that i should check my connection. 
Everything runs ok when I activate the cart through the network settings.

Help? Please?[/QUOTE]


Well I may be wrong but just with ifconfig eth0 up you dont get your ip address via dhcp.try with this after activating your card:

dhclient eth0

When you have changed the MAC that could give some problems cause your real mac is associated to the ip you were using before so you have to get a new IP address for your new MAC.This could be the reason but not sure,just try it.

and about running the script at boot time,first you have to place it in /etc/init.d/ and then make a symbolic lynk to /etc/rcX.d/
Something like this:

ln -s /etc/init.d/your_script /etc/rcX.d/your_script 

where X in the runlevel where you want it to run.I'm not sure about this one but if you lynk it to /etc/rcS.d/ it should work.

No matter what just try it and if there's any problem I'll try to find out.

edit:

Remember to make your script executable:

chmod +x scriptname

This lynk may help you for understanding the run levels and how this thing with the init scripts work:

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit)

---

### Post by xristos on 2005-11-25
You can put a new line in your /etc/network/interfaces file
Something like this 
```
hwaddress ether 00:00:00:00:00:00
```

---

### Post by TmP on 2005-11-26
Thanx Guys!
You'r the best, and so is the whole Ubuntu community!

I found out that all 3 solutions worked fine, but I went for the simplest

I changed my
/etc/network/interfaces
Now it goes like this:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

iface eth0 inet dhcp
hwaddress ether 00:a0:WH:AT:EV:ER
auto eth0

And It works like a charm!

---

### Post by crazy_fox on 2006-10-19
Hi, i am trying to change the MAC address as well.. For my own router..

Once i chagne the mac address, the router gives me a new address, etc, but i cant see the router or the network..

Any ideas why?

---

### Post by ryckmonster on 2007-05-31
> **suRoot said:**
> sudo ifdown eth0
sudo ifup eth0

GENIUS!!!!!!!!!!!!  I think I had been torrenting a little too much, and my connection was blocked.  But its working now, after only two lines. TY

---

### Post by MK3 on 2007-08-21
HI Im a noob when it comes to this new Linux stuff.
anyhow just installed Ubuntu, everything works great, except it will not 
allow me to change my network interface settings.

the file "/etc/network/interface" is read-only

then when i try to change it to write it says i do not have admin wrights

any conclusions?

cheers

:confused::confused:

---

### Post by adamoxx1 on 2007-08-23
Just type:
'su -'    which after typing the right password switches you into administrator mode in the 'root' folder
or only 'su' without the dash which does the same thing but in the current directory you're in
You must remember the admin password to become the root.
This is a way to use on the console.
There is also a possibility of using your file manager with root privileges, eg. Konqueror in KDE. You just have to find the right entry in the KMenu and after clicking it you will also be asked to give the root password.

---

### Post by MK3 on 2007-08-26
cheers for you reply adamoxx1, I will check this out now.

cheers

mk3

---

### Post by MK3 on 2007-08-26
> **adamoxx1 said:**
> Just type:
'su -'    which after typing the right password switches you into administrator mode in the 'root' folder
or only 'su' without the dash which does the same thing but in the current directory you're in
You must remember the admin password to become the root.
This is a way to use on the console.
There is also a possibility of using your file manager with root privileges, eg. Konqueror in KDE. You just have to find the right entry in the KMenu and after clicking it you will also be asked to give the root password.

hi again,
just typed su with and without dash, but it comes up with 

Authentication failure

???

---

### Post by melbourne on 2008-05-02
hi ppl 


  i am like complete newbie to linux   i have somehow managed to install ubuntu on my dell inspiron notebook. now comes the problem , i have  to change my mac address in order to access internet . now i am a kind person who dont know absolutely anything  about linux , example : i dont even know where the commands you are talking about should  be typed .

so plzzzzzzz someone give me a spoonfed(step by step)  details of how to change mac addrress .. this post i am making through my vista partition on my sysytem 

thank u in advance

---

### Post by geci on 2008-05-23
hey
i've changed my mac address like this: 
           [B] ifconfig eth0 down hw ether *new address*
            ifconfig eth0 up[/B]
everything works fine but when i restart the computer the mac address changes back to old address
how can i "save" it after i change it?

---

