---
title: "wireless won't reconnect if dropped"
date: 2005-02-22
forum: Hardware &amp; Laptops
---

### Post by lerrup on 2005-02-22
I have a centrino based laptop running Hoary on the 686 kernel.

My problem at present is that if I am connected and for some reason the connection is interrupted eg the router is turned off or the laptop powers down then it will not remake a connection.  I have tried to force it through the various network config tools and they do not have any effect.  The only thing that works is to reboot it, which seems a little extreme.

Below is my /etc/network/interfaces file, is there anything clearly wrong?  It all worked well in Warty, so I know the hardware is fine.

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
 # wireless-* options are implemented by the wireless-tools package
 wireless-mode managed
 wireless-essid any
 wireless_essid home network

auto eth1

iface eth0 inet dhcp

---

### Post by alastair on 2005-02-22
I haven't tried the "router powered down" test, but a laptop (thinkpad) suspend to RAM screws up my wireless and I need to reconnect. A reboot is out of order though.

You could try using the shell to reconnect e.g.

iwconfig eth1 essid <name>
iwconfig eth1 key restricted <key>

etc. I  use :

iwconfig eth1 ap <ap MAC>
iwconfig eth1 key restricted <key>

but I do not broadcast the ESSID (and don't use the "essid" iwconfig command).

---

### Post by poofyhairguy on 2005-02-22
[QUOTE=lerrup]I have a centrino based laptop running Hoary on the 686 kernel.

My problem at present is that if I am connected and for some reason the connection is interrupted eg the router is turned off or the laptop powers down then it will not remake a connection.  I have tried to force it through the various network config tools and they do not have any effect.  The only thing that works is to reboot it, which seems a little extreme.[/QUOTE]


Here is how I do it. First I close everything that uses the internet. Then I open the "networking" tool. Then I select the wireless and I click on the "deavtivate" button (even if it already is). Then I close the network tool and restart it. Then I click "activate" button. Then I close the tool.

After that process anything I start that uses the internet works again. In fact, a few things work even if I didn't close them in the first place (Firefox never does, and its my most used program). Probably is way to do that in like 4 seconds on the command-line but it feels comfortable to me.

---

### Post by soro2005 on 2005-03-09
[QUOTE=lerrup]I have a centrino based laptop running Hoary on the 686 kernel.

My problem at present is that if I am connected and for some reason the connection is interrupted eg the router is turned off or the laptop powers down then it will not remake a connection.  I have tried to force it through the various network config tools and they do not have any effect.  The only thing that works is to reboot it, which seems a little extreme.

Below is my /etc/network/interfaces file, is there anything clearly wrong?  It all worked well in Warty, so I know the hardware is fine.

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
 # wireless-* options are implemented by the wireless-tools package
 wireless-mode managed
 wireless-essid any
 wireless_essid home network

auto eth1

iface eth0 inet dhcp[/QUOTE]
 I seem to be having the same problem, with the "some reason" the connection is interrupted mostly being no apparent reason whatsoever. This is, after a certain while, the connection just gets lost, and I can't get it restored with whatever "iwconfig", "ifdown/up", Network Configuration Tool, Kwifimanager... I try to bring to the task. Warty's wireless connections went down as well, but it mostly connected to some random "any" network at least, of which there are many in the neighbourhood, but I'd actually like to connect to the one I'm paying for. And Hoary doesn't even connect to "any" it seems, just pretends it's tuned in to my essid, but doesn't acquire an IP or a MAC address of the router.

I will try using iwconfig ap next time it happens, as alastair has suggested (my network is also not broadcasting its essid), but may there be some issue with the Centrino wireless adapter and its Linux driver under Hoary? Why does it disconnect all the time in the first place? Any suggestions where and how to tweak so it's not that unstable? (XP stays connected with exactly the same physical setup)

Last, but not least: What exactly is the procedure to bring down the adapter entirely and start it from scratch, just as if it were a reboot? poofyhairguys suggestion doesn't work for me, and I haven't ever had a problem acquiring the network address at boot.

---

### Post by dave9191 on 2005-04-26
Hey guys, 

I recently intstalled kubuntu 5.04. When I suspend or hibernate my wireless sometimes doesnt work again after I wake the computer up. I was searching for a solution and came accross this thread. Although it didnt help me, I found a solution and thought Id share it with you if you still need it. 

First of all shut down the networking interfaces, unload the wirless module from the kernel, load it up again and  run the networking interfaces script again. This essentially restarts the networking like a system restart would, and sure as hell beats a restart. 

Ill be making a script for this later, but I need to dash now. For now have fun with this :) 

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2200 (or whatever your wireless module is, i have intel centrino chipset)
sudo modprobe ipw2200
sudo /etc/init.d/networking start

Note that this will stop all networking interfaces on the computer when stopping the networking script. 

Dave

---

### Post by soro2005 on 2005-04-26
Thanks dave9191, will try. Just to make sure: I'm still interested in a good solution. Would really make the difference in terms of usability of Ubuntu. So please post your script once you have it  :)  Cheers!

---

### Post by dave9191 on 2005-04-26
I was in a rush to get out the house ealier, but those 4 lines I scribbled down are basically it. And each scipt will be unique to your setup. 

sudo /etc/init.d/networking stop
sudo modprobe -r ipw2200
sudo modprobe ipw2200
sudo /etc/init.d/networking start

Create a new text file (using gedit or whatever you prefer :)), copy those 4 lines into it, save it somewhere, you home dir should be fine. Name is net_restart.sh. Then open a terminal, navigate to where you saved the file and type

chmod +x net_restart.sh

Then you can run that script when you need to restart your wireless (just type "./net_restart.sh" where ever you saved it). You can also create an icon on your panel or desktop for it. Just give the full path as the command to execute for the shortcut. 

Now just a few more pointers, in my case the wireless module is called ipw2200, if you have another one, then you have to replace that with the name of yours. 

This script assumes that your wireless connection is setup and working when you boot your laptop, in otherwords, set up in the networking script thats called to start and stop the network. If thats not the case you will have to add more commands to set it up (tell me I can help you with that if you want).

I guess that it is possible to have this executed whenever your laptop comes out of suspend or hibernate but I need to look into that another time. 

Im very pressed for time at the moment and this is what Ive done for myself and it seems to do the trick. I might try to make something smoother and nicer when I have more time, so that it does it for you when you suspend or hibernate.

---

### Post by soro2005 on 2005-04-27
Thanks, that's very much appreciated. I have an ipw2200 as well, and as I say, it seems to me it's just not reconnecting once it loses the signal. Which is the case quite frequently in my situation, although I don't really know why that is. Perhaps some jamming devices around, cell phones, electromagnetic pollution, what know I. The router is just about 10 feet away.

In any case, Windows reconnects. Perhaps it's a problem with the Linux driver for the wireless device which, I understand, is still being developed. I'll use your script in the meantime, so thanks again. Didn't get a chance to try it out, but it looks pretty basic once you know you have to stop networking and not some individual device. Newbie problems.  :^o

---

### Post by dave9191 on 2005-04-27
Im learning slowly stuff too. I'm pretty new to Linux too. Took me several months to figure out how to get FN keys working on my laptop. Hope that the script works for you too. I was having a problem with windows where it would keep dropping the connection around every 5 min or so and then reconnecting. I changed the encryption type and it stopped dropping the connection. I changed it to 128bit wep shared. Then I just used the same encryption when i changed over to Linux. 

And the driver is still being developed, so it doesnt reconnect like windows when dropped. And crashes often for me when returning from hibernate or suspend.

---

### Post by soro2005 on 2005-04-28
Thanks again, dave9191. Your script seems to be doing the job for me. I made a little shortcut, and it works like a breeze. Ubuntu seems to have speeded up considerably between Warty and Hoary when it comes to bringing up the networking module. That's why I like it so much: Every day, something works a little better.  :grin:

Is it just me, or is it correct that one has to close and restart applications before they're able to get through over the reinitiated network connection? Golden days for Opera and Firefox's session saver extension!

Re lost network connections. I'm also with 128bit wep, but I've tried with some other setups, and even over my many friendly neigbours' open networks with all beacons out, I get occasional disconnects. (I wish they were as friendly when you meet them in the stairwell as they are when it comes to internet connection sharing.  :?) I guess it's just how it is in Lower Manhattan. Too much traffic in ridiculously small spaces.

---

### Post by dave9191 on 2005-04-28
When I restart the network, most applications still work. Kopete gets very annoying about it. So i usually close that b4 i restart the net. Not sure about other programs, but the news ticker and weather applet dont mind too much the network restart and work. 

And that might be a reason, too many networks in one place. In parts of my flat I can pick up lots of other networks and sometimes my own one gets drowned out. I got a new access point yesterday ( from a b standard to a g). The network driver likes it so much more, and the signal is stronger everywhere. And you cant always pick your neighbours eh :)

---

