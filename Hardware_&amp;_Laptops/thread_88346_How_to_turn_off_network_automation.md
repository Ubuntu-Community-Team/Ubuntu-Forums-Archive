---
title: "How to turn off network automation?"
date: 2005-11-10
forum: Hardware &amp; Laptops
---

### Post by Molerat on 2005-11-10
Recently I've discovered the joys of suspending back and forth between Windows and Ubuntu.  At this point, network management is about the only thing Windows seems to have on Linux, for me anyway.

Invariably, whenever I resume Ubuntu, it tries to bring back wireless when I'm actually using an Ethernet cable, or vice-versa.  I use my laptop all over -- wired, wireless, encryption, no encyrption.  The network changes all the time.

What I would like to do is switch networking over to manual mode.  Ideally, both of my network adapters (eth0 and ath0) would stay DOWN until I explicitly bring them up.  Further, I would like hibernation to bring all the network devices down.  Upon resume, I'd like it to stay that way.

I'm sure this is just a matter of editing some configuration scripts somewhere... but where?  I've searched a bit, but the answer isnt' obvious to me.

---

### Post by pear-i on 2005-11-10
edit your /etc/networking/interfaces file -- i believe if you comment out parts of the DHCP / mapping, it shouldn't be a problem --

for manual control for your network cards
try

sudo ifup eth0 -- turns it ON
sudo ifdown eth0 -- turns it DOWN
substitute eth0 with whatever designation for the interface -- (check ifconfig / iwconfig) 

hope that helps

---

### Post by Molerat on 2005-11-10
^ Thanks.  there's mention of eth0 for the hotplug system, but no mention of my wireless adapter, ath0.  Thanks also for ifup/down, but I already use those.

What I want to do is to tell my configuration files, "look, I've got networking.  Don't try to automatically start things for me.  I'll tell you when I need it."

Or, if possible, "I don't trust you, Linux.  Let me tell you when I want networking enabled.  You just be sure to bring all the adapter down when you go to sleep."

Perhaps the hotplug system is a part of this...?

---

### Post by Molerat on 2005-11-11
Anyone?

---

### Post by apjone on 2005-11-11
[QUOTE=Molerat]Anyone?[/QUOTE]
Firstly 
vi /etc/networking/interface
and remove the *auto eth0* at the end 

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
iface eth0 inet static
address 10.7.152.246
netmask 255.255.248.0
gateway 10.7.152.254

**auto eth0** *comment this out and try that*

---

### Post by Molerat on 2005-11-11
^ Thanks for the reply.  Other than lo, I do not have any auto entries in my /etc/network/interface file:

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
        hostname nixon

iface ath0 inet dhcp
wireless-essid polk

```

Should I comment anything out here?  I don't want to break ifup and ifdown, but yes, I do want to disable autoloading.  The comments in that file say those interfaces will be loaded automatically by the hotplug system.  I don't want to go breaking things willy-nilly!

Side question:  I've noticed documentation will always say something like "read interfaces(5)"...  I can handle "man interface," but what is the number in parenthesis... I've never been able to figure it out!

---

### Post by Molerat on 2005-11-13
Bumping again, hope that's okay.

---

### Post by ranf on 2005-11-13
[QUOTE=Molerat]Side question:  I've noticed documentation will always say something like "read interfaces(5)"...  I can handle "man interface," but what is the number in parenthesis... I've never been able to figure it out![/QUOTE]
`man man' 
The man pages are sorted into sections. The (5) means section 5.

---

### Post by Molerat on 2005-11-14
[QUOTE=ranf]`man man' 
The man pages are sorted into sections. The (5) means section 5.[/QUOTE]

Oh.  Well.  I feel stupid now.  Heh.  Thanks.

How about the interfaces, anyone have any suggestions there?

---

### Post by Molerat on 2005-11-20
Oh well, if anyone is interested, I added:

```

ifdown --force ath0
ifdown --force eth0

```

To my hibernation and resume scripts.  Resuming from hibernation usually hangs for a minute while if-whatever is trying to force ath0 down, probably because it's not up to begin with.  But if I don't have it, I found that sometimes it comes back on itself.

I'm sure there's better ways of doing this, but damned if I know what they are.

---

### Post by crsz on 2005-11-21
Hi,

I had more or less the same problem. I found that there are two things to do:

1. Edit file /etc/default/hotplug, and change the line NET_AGENT_POLICY to
NET_AGENT_POLICY=auto

2. Edit file /etc/network/interfaces and comment out the lines with 'auto eth0' or
'auto eth1', if any.

It works fine on my laptop. Network does not start at boot and I activate it with
sudo ifup/ifdown. Eventually I installed network-manager, so the network starts
automatically only when I plug the cable.

Cheers,

Roberto

---

### Post by Molerat on 2005-11-27
^ NetworkManager is perfect, thanks.

Here's some useful information if anyone else stumbles onto this thread:  [http://ubuntuforums.org/showthread.php?t=94268](http://ubuntuforums.org/showthread.php?t=94268)

---

