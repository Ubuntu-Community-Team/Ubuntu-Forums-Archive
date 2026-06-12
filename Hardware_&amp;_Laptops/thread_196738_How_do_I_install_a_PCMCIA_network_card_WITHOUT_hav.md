---
title: "How do I install a PCMCIA network card WITHOUT having to reinstall Ubuntu?"
date: 2006-06-14
forum: Hardware &amp; Laptops
---

### Post by Mortuis on 2006-06-14
I installed Ubuntu Server 5.10 on a thinkpad 770 last year and recently upgraded it to 6.06. When I installed it, it recognized my wireless PCMCIA card so I never head to deal with what's involved in linux hardware installation.

A few days ago my wireless router crapped out and I want to get the server up and running again until I can afford a new one. So I pulled a non-wireless NIC out of my windows server (another thinkpad 770) and plugged it into the Ubuntu Server, only to realize I have no idea what to do from here.

I'm a linux newbie, I can't find any guides that pertain to Ubuntu on how to install a PCMCIA network card.  Rebooting didn't work, trying some command called ifconfig says:
lo    Link encap:Local Loopback
      inet addr:127.0.0.1  Mask:255.0.0.0
      inet6 addr: ::1/128 Scope:Host
      UP LOOPBACK RUNNING  MTU:16436 Metric:1
      RX packets:0 errors:0 dropped:0 overruns:0 frame:0
      TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
      collisions:0 txqueuelen:0
      RX bytes:0 (0.0 b) TX bytes:0 (0.0 b) 

I'm not sure what to do or try from here.  I suppose I could reinstall the operating system, but that just seems stupid.  Surely there's a way to install hardware in linux, I just can't seem to find the information anywhere.

Any help would be appreciated, if only what documentation to reference, I really have very little clear idea what I'm doing here.

I don't know what files to look at, what my hardware's particulars are, anything. I've tried googling for about an hour but can't seem to find any information on NIC installation that doesn't involve using some GUI application. Again, this is Ubuntu Server so I have no graphical environment.

Could anyone help me out here? Where do I start looking? What should I be googling for? I don't even know where to begin.

---

### Post by ddumanis on 2006-06-14
I got mine working by installing Ndiswrapper, then going to system>administration>windows wireless drivers and selecting the .inf file for my NIC. (I had to copy it from my Windows system.)

In the Networking control panel, it shows up as a wireless card... but it does show up, and it does work. (I have the password and network ID set to blanks.)

Or, you could just spend $30 bucks at NewEgg and get a NIC that works with Linux out of the box.

---

### Post by hkosturi on 2006-06-15
Go to menu->sytem->administration->Networking see if your card is listed there eth0 or something click propertise and set up the details then activate. Then on the right top corner of your destop click on the network connection  icon and change to the ethx whatever your designated network card is. 
lo means loopback so is not connected anywhere

---

### Post by patrickfromspain on 2006-06-15
Do you people read the posts? Or only half of them?

He tries to install a NON-wireless NIC but a wired one and he HAS NOT A GRAPHICAL ENVIRONMENT, as he is running a server install..

;)

I think you could try to edit /etc/network/interfaces file and add the information you need. For the hardware.. I think you musn't do anything. If the card is detected fine (as it probably is) ubuntu will load the modules it needs.

---

### Post by Mortuis on 2006-06-15
[QUOTE=patrickfromspain]
I think you could try to edit /etc/network/interfaces file and add the information you need. For the hardware.. I think you musn't do anything. If the card is detected fine (as it probably is) ubuntu will load the modules it needs.[/QUOTE]

Thanks Patrick, could you give me any pointers on how to go about figuring out what information I would need to add to /etc/network/interfaces?  I appologise if it's intuitive when in the file, I'm at work right now and obviously can't SSH into my server back home right now. ;-)

---

### Post by patrickfromspain on 2006-06-15
mm sorry for that but I'm afraid I can't help much more, anyway, I'll try.

You would first need to know how the interface is named. I suppose it will be eth0 or eth1, but I'm not sure at all. Then, in the file, you could try to add this:

auto eth0
iface eth0 inet static
address 192.168.0.39
netmask 255.255.255.0
gateway 192.168.0.1

so that the NIC gets the same IP address always, or:

auto eth0
iface eth0 inet dhcp

to get IP adress from the router or whatever.

---

### Post by Mortuis on 2006-06-16
[QUOTE=patrickfromspain]mm sorry for that but I'm afraid I can't help much more, anyway, I'll try.

You would first need to know how the interface is named. I suppose it will be eth0 or eth1, but I'm not sure at all. Then, in the file, you could try to add this:

auto eth0
iface eth0 inet static
address 192.168.0.39
netmask 255.255.255.0
gateway 192.168.0.1

so that the NIC gets the same IP address always, or:

auto eth0
iface eth0 inet dhcp

to get IP adress from the router or whatever.[/QUOTE]
Alright, thanks.  I'll play around with that a bit.  At least I have something I can try.

---

### Post by ozorba on 2006-06-16
PCMCIA sometime does not work. This depends on the PCMCIA card. you may have to edit pcmcia configurations in /etc/pcmcia direcotry. Watch put the IRQ and IO addresses...

OZ

---

