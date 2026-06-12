---
title: "How do I enable a network device from Terminal?"
date: 2005-11-15
forum: General Help
---

### Post by pbb on 2005-11-15
Hi, I am really just starting with Linux, and I have a question.

I found that support for my Yukon GIgabit networkcard has to be manually enabled in Ubuntu. This I have managed with

```
modprobe -v sk98lin
```

This also brings up the card in the Applications > System Tools > Network Tools. However, at this point, the device is not yet "enabled". To do this, I thought I have to execute

```
sudo ifconfig -v eth1 192.168.0.1
```

Now, the Network Tools window shows the 192.168.0.1 address connected to the interface, but when clicking the Configure button I see the interface is still disabled! ("Enable this device" is unchecked.)

Can someone tell me how to "enable" the interface through the Terminal?

Thanks, Peter

---

### Post by adwait on 2005-11-15
I think that would be
```
sudo ifup eth0
```

---

### Post by pbb on 2005-11-15
When I do that, I get the reply:

```
Ignoring unknown interface eth1=eth1.
```

(It's eth1, my second ethernet card.)

Any suggestions what is wrong here?

---

### Post by Dr. Nick on 2005-11-15
You try ```
sudo ifup eth1
``` If that doesnt work try to bring down your first card with ```
sudo ifdown eth0
``` and try again

---

### Post by az on 2005-11-15
You can add the "sk98lin" to the end of 
/etc/modules
so that it is autoloaded at boot time.


sudo gedit /etc/modules

---

### Post by metoo on 2005-11-15
Add sk98lin to /etc/modules to have the module automatically load at boot.
(I was just beaten for this one... :-) )

Doesn't solve your configure question so...

You are not mentioning whether you have a static IP of use DHCP for the machine.

The network can be configured in /etc/network/interfaces

The wiki will most likely held an entry what settings to enter there...
The entry for a static IP address will look similar to this:

# The primary network interface
iface eth0 inet static
	address 192.168.0.2
	netmask 255.255.255.0
	network 192.168.0.0
	broadcast 192.168.0.255
	gateway 192.168.0.1
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.0.1
	dns-search your-domain

If you are behind a router with the address 192.168.0.1 and your PC has the static IP 192.168.0.2 
your-domain is the domain if you have set this.

---

### Post by pbb on 2005-11-15
Thanks for the help guys! My girlfriend is currently at the computer, so I cannot try it out at this moment but I will later on.

At bit more background info might be handy:
* I am using the Live CD, since I still haven't really decided on which Linux distro I want to use later on. So I am not yet at the point where I can autoload stuff.
* I've got 2 network cards:
- eth0 is a general PCI card, detected and activated by Ubunty, connected to internet.
- eth1 is an onboard Yukon Gigabit card, connected to the local network.
* The IP addresses of eth0 is 10.0.0.4, assigned by the internet modem. I assigned 192.168.0.1 to eth1.

I found one page on the wiki about DHCP, but couldn't really understand the background of it.

More info coming soon when I get another chance to try Ubuntu again.

---

### Post by pbb on 2005-11-15
Adwait, Dr Nick,

I tried the ifup command, but am not getting any further:

```

# sudo ifup eth1
Ignoring unknown interface eth1=eth1.

# sudo ifdown eth0
<breaks internet connection>

# sudo ifup eth1
Ignoring unknown interface eth1=eth1.

# sudo ifdown eth1
ifdown: interface eth1 not configured

```

So, I don't seem to get any further that way... Any suggestions?

- - - - - - 

Metoo,

Could you explain how I need to configure it in the configuration mentioned in my previous post? Would this make my network card be activated without going through the Network Tools window?

---

### Post by Dr. Nick on 2005-11-15
Are you trying to share the internet connection? Ive done something similar once but it was on mandrake which had a gui for it. the interfaces file needs to have info for both of the network cards. The network card window will write them for you.

**If you want to have internet sharing:**
Load the module for your 2nd card and try to activate them both in the networking tool, one should be eth0 the other eth1, then install and run firestarter which has a wizard to set up sharing. Firestarter will configure your 2nd card so it gives out IP addresses out to the computer connected to it.

I really dont see the use for 2 ethernet cards at once unless you have internet sharing.

**Ignoring unknown interface eth1=eth1.** is due to an error in your interfaces file. according to this site [http://www.differentpla.net/node/view/157](http://www.differentpla.net/node/view/157)
Im not the best with networking but hopefully something above helps.

---

### Post by pbb on 2005-11-21
Hi Dr. Nick,

**Internet Sharing**
Thank you very much for your reply. You are right, I am trying to enable internet sharing. However, your reply does not answer my original question, how to enable eth1 without going through the "Network Tools" dialog. I still need to go there to enable eth1.

**eth1=eth1**
I've tried reading up a bit on "eth1=eth1", but don't really understand what is being said. Maybe someone can help? Following is the contents of my /etc/network/interfaces:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1

auto eth0
```

**Firestarter**
I've tried installing Firestarter. First I installed DHCP this way:

```
sudo apt-get install dhcp
```

Next I installed and started Firestarter. This gives me the following message: Failed to start the firewall - An unknown error occurred. However, the Firestarter window does state that the firewall is Active ?!?!

I am actually getting a bit dizzy from the endless line of problems that are showing up! Are you going to tell me that I am the first person in the world to try to do internet sharing? Why does this cause so many problems?

---

### Post by Dr. Nick on 2005-11-21
Ive done connection sharing before just not on Ubuntu

This link may be of help [http://users.pandora.be/mydotcom/howto/lanconnect/router/linux.htm](http://users.pandora.be/mydotcom/howto/lanconnect/router/linux.htm)

The sudo ifup command should bring interfaces up from the terminal, but wont work if your interfaces file is misconfigured. Which it may be according to that site, It looks like you need an "iface eth1" line.

The firestarter error is also most likely due to a bad interfaces file.

I hope that link helps some and sorry in advance if it doesnt

---

### Post by pbb on 2005-11-21
Here is (again) the contents of my interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1

auto eth0
```

As you can see, there is a "iface eth1" line in it. Can you see anything that is wrong there? Should the "auto eth1" line be before the "iface eth1" line for example? I don't understand what is wrong...

---

### Post by pbb on 2005-11-21
Here is (again) the contents of my interfaces file:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth0

# The primary network interface
iface eth0 inet dhcp

iface eth1 inet static
address 192.168.0.1
netmask 255.255.255.0

auto eth1

auto eth0
```

As you can see, there is a "iface eth1" line in it. Can you see anything that is wrong there? Should the "auto eth1" line be before the "iface eth1" line for example? I don't understand what is wrong...

---

### Post by Dr. Nick on 2005-11-21
Oops sorry didnt see the line before.

You can try to move the auto up like in the example on the website. Not sure if that will help. 

Are you still on the live CD? If so once you edit your interfaces run this command ```
sudo /etc/init.d/networking restart
``` after loading the modules with modprobe. Then try the ifup commands. The /etc/init.d/netowrking command restarts the network which may be needed for it to use the updated interface file.

I hope someone who has done this in ubuntu recently can help here as I am out of ideas.

---

### Post by pbb on 2005-11-24
Okay.... With the help of a friend that know a bit more about Linux, we found the solution.
Turns out the GUI interface of Network Tools is buggy! The network adapter was initialized properly the whole time, it was just the GUI talking nonsense...
Also, we decided to drop the DHCP part, and just entered all IP and DNS info manually on the other pc. So, internet sharing is working properly now! :D

Thanks for all the help everybody!

---

### Post by Dr. Nick on 2005-11-26
Glad you got it, Sometimes its easier to solve in person opposed to online.
Ive have noticed some oddities in the GUI aswell just like you. I ran the ifup commands on my wireless and the gui kept it deactivated until I hit activate. This is a recent occurance so I guess the network GUi is just moody as it is hard to recreate.

Im glad you got it as I was running out of ideas :)

---

