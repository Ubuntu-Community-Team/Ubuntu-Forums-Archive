---
title: "internet problems"
date: 2005-10-20
forum: Hardware &amp; Laptops
---

### Post by wingsfan on 2005-10-20
I am a linux newbie and am having internet troubles.  I was hoping that someone might be able to help me with trouble i am having with the internet.  I can get some pages to load and others will not load at all.  I also don't seem to be able to connect to the package manager.  I am on a college network and have a router and wondered if maybe there is a setting that i need to be aware of.

Any help would be appreciated.

Thanks,

---

### Post by hajk on 2005-10-20
Well, it would help if you were a bit more specific about the problems you're having. What is the output of "sudo ifconfig"? And what does "sudo route" show?
And what does /etc/network/interfaces look like? And /etc/resolv.conf?

You say that certain pages display OK, so you seem to have a working internet connection, where were you writing your post from?

Can't connect to the "package manager", what do you mean by that? Show us your /etc/apt/sources.list -- but be aware that there have been some problems with Ubuntu mirrors...

---

### Post by wingsfan on 2005-10-20
well here is the info you asked for
i was on my windows system when i originally wrote this but i am on ubuntu now if you need any other stuff i can get it.  Thanks for helping.

ifconfig looks like this

eth0      Link encap:Ethernet  HWaddr 00:E0:4C:A6:FE:78
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fea6:fe78/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1982 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1352720 (1.2 MiB)  TX bytes:247224 (241.4 KiB)
          Interrupt:22 Base address:0xa000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1045 (1.0 KiB)  TX bytes:1045 (1.0 KiB)

this is route 

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

here is /etc/network/interfaces

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

this is /etc/resolv.conf

nameserver 192.168.1.1

this is /etc/apt/sources.list

deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by hajk on 2005-10-20
Well, certainly no Internet access problem! :D 

But you should modify your /etc/apt/sources.list with "sudo gedit":

1. Remove the first line with "deb cdrom...".
2. Uncomment (remove ## in front of) the following pairs of deb-lines
    and also remove the "us." prefixes:

    -- with "breezy main restricted"
    -- with "breezy-updates main restricted"
    -- with "breezy universe"
    -- with "breezy-updates universe"
    -- with "breezy-security main restricted"
    -- with "breezy-security universe"
3. Do not uncomment the deb-lines with "breezy-backports", these are
    not yet available.
4. Copy the two deb-lines with "breezy universe", and change "universe"
    to "multiverse".

Save, and fire up System/Administration/Synaptic Package Manager, and 
hit the Reload button -- this should update your system.

For w32codecs and other restricted stuff look at Ubuntu Wiki under
Documentation - Retsricted Formats.

---

