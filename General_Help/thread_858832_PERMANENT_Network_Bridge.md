---
title: "PERMANENT Network Bridge"
date: 2008-07-14
forum: General Help
---

### Post by ProgenitorVirus on 2008-07-14
Okay, I used bridge-utils and set up a bridge ( br0 ) with my eth0 and eth1 connections.

eth0 is my Router connection and eth1 is my Xbox 360 connection.

Needless to say, both will be off together at some point.  My 360 needs my computer to be on to get online, but;  I turn off my computer every night.  When I turn my computer ON, and not my 360, my computer connects fine, but I need to make a new bridge each time when I turn my 360 on.

It SHOULD recognize to keep the bridge even if one device isn't operable, but it doesn't seem to be.  I have to reinstate the bridge each time I reboot w/o my 360 on.

Is there any way around this?  Thanks!

>> These are the commands I use to make the bridge:

sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig eth0 0.0.0.0 promisc
sudo ifconfig eth1 0.0.0.0 promisc
sudo dhclient br0

---

### Post by bodhi.zazen on 2008-07-14
You can put those commands in /etc/rc.local

I advise you bring eth0 and eth1 down first, then bridge them, then bring them back up.

You can also put it in /etc/network/interfaces

See this link (it is for KVM but can be adopted)

[https://help.ubuntu.com/community/KVM#Creating%20a%20network%20bridge%20on%20the%20host](https://help.ubuntu.com/community/KVM#Creating%20a%20network%20bridge%20on%20the%20host)

---

### Post by ProgenitorVirus on 2008-07-14
Well, I'm not going to pretend I know how to go about editing those files.  I just tried and my system wouldn't start o_____o;;;

Can anybody explain how I edit those files?  Thanks!

---

### Post by ProgenitorVirus on 2008-07-14
Okay, just tried on my own, and uhh, my system wouldn't start anymore...

Did some fixing, so now its all good but I think I'll need somebody to hold my hand through this one :\

I was sick of Microsoft, especially with their wonderful SP3, giving the US Gov't what they wanted.  Switched to Ubuntu, and loving every minute of it, but I'm still just a newbie :p

---

### Post by ProgenitorVirus on 2008-07-14
[Sorry for the Triple Post, but the Edit button doesn't seem to be working?]

Okay, for my   /etc/network/interfaces   I put:



auto lo
iface lo inet loopback

sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig eth0 0.0.0.0 promisc
sudo ifconfig eth1 0.0.0.0 promisc
sudo dhclient br0



And in my   /etc/rc.local   I put:



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

sudo brctl addbr br0
sudo brctl addif br0 eth0
sudo brctl addif br0 eth1
sudo ifconfig eth0 0.0.0.0 promisc
sudo ifconfig eth1 0.0.0.0 promisc
sudo dhclient br0

exit 0



When I configured these two files, the system wouldn't start anymore, so I don't want to try anything I haven't before without a clear set of instructions of what I have to do.

---

### Post by bodhi.zazen on 2008-07-14
OK, the problem is two fold. Do not put those commands in /etc/network/interfaces.

You can do one of two things either add commands to /etc/rc.local or configure your interfaces in /etc/network/interfaces, BUT NOT BOTH.

Second, those are commands, and are placed in rc.local

/etc/network/interfaces is a configuration file, and thus you put configuration options not commands in that file.

First backup your working configuration :

```
sudo cp /etc/rc.local /etc/rc.local.backup
sudo cp /etc/network/interfaces /etc/network/interfaces.backup
```===========

Option 1 : Add those commands to /etc/rc.local

```
gksu gedit /etc/rc.local /etc/network/interfaces
```gedit is now open and you have rc.local on one tab and interfaces on the other :)



> 
# bring your interfaces down
ifconfig eth0 down
ifconfig eth1 down

# Make a brideg and add interfaces
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

#Configure interfaces eth0 and eth1
ifconfig eth0 0.0.0.0 promisc
ifconfig eth1 0.0.0.0 promisc

#Bring br0 on line with dhcp
dhclient br0You can test this script out before you boot by :

```
sudo /etc/rc.local
```remove all those lines from /etc/network/interfaces.
reboot

==============

Option 2 configure your bridge and interfaces in /etc/network/interfaces

First, bring your network down :

```
sudo /etc/init.d/networking stop
```> 
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
        bridge_ports eth0
        bridge_ports eth1
        bridge_fd 9
        bridge_hello 2
        bridge_maxage 12
        bridge_stp off/etc/rc.local should be empty.

You can test this with :

[/code]sudo /etc/init.d/networking start[/code]

Reboot

---

### Post by ProgenitorVirus on 2008-07-15
Okay, just got back from reinstalling Ubuntu.

This was in my /etc/rc.local

# bring your interfaces down
ifconfig eth0 down
ifconfig eth1 down

# Make a brideg and add interfaces
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 eth1

#Configure interfaces eth0 and eth1
ifconfig eth0 0.0.0.0 promisc
ifconfig eth1 0.0.0.0 promisc

#Bring br0 on line with dhcp
dhclient br0 

exit 0

Now, this DID let me get online on my 360, but wouldn't let me log into my account, which is troublesome.  I did this to try and fix it via failsafe termina

cd /etc
sudo rm rc.local
sudo mv rc.local.backup rc.local

Annnd, when shutting down or starting up, it would completely hang there, saying its trying to read something or other.

I'd really like to know what I'm doing wrong here :confused:

---

### Post by bodhi.zazen on 2008-07-15
Well, logging to your account is not the same as setting up a bridge ...

My first guess would be username or password is wrong.

---

### Post by ProgenitorVirus on 2008-07-15
No, I have my username and password memorized, what would happen, is it'd log me in, and hang and not load anything.  Still responsive, but I saw nothing but an off orange tan coloured background, nothing else.

When shutting down it'd say its reading /etc/rc.local and something about a boot file?

Anyways, it just hung there as well :\

---

### Post by bodhi.zazen on 2008-07-15
And everything works if you boot with an empty /etc/rc.local ?

---

### Post by ProgenitorVirus on 2008-07-15
Well, more like an unedited /etc/rc.local

In a last effort I did exactly the following when not able to logon to my account.

Chose the Failsafe Terminal Option

Logged In

cd /etc
ls
sudo rm rc.local
[Entered Password]
sudo mv rc.local.backup rc.local
exit
restart
[Hung at something about Reading Boot something /etc/rc.local and I hard booted]
Tried to log on, same thing

I went into the /etc/ directory, explored because I forgot the file name, sudo removed rc.local, and renamed the backup rc.local removing the .backup from it so as to replace the deleted file, logged off, shutdown, waited, hard booted, tried to log on, and decided to reformat.

I don't know if this was the correct way to go about it, but it was all I knew to do and made sense to me :\

---

### Post by ProgenitorVirus on 2008-07-15
Are there any ideas out there?

---

### Post by ProgenitorVirus on 2008-07-15
Okay, I actually got it working.

Instead of editing  /etc/rc.local  I edited  /etc/network/interfaces  doing exactly the following:

sudo /etc/init.d/networking stop

gksu gedit /etc/network/interfaces

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet manual

auto eth1
iface eth1 inet manual

auto br0
iface br0 inet dhcp
bridge_ports eth0 eth1

```

sudo /etc/init.d/networking start

Rebooted and took about 3 times as long to do, but eventually came up

Like I said, this worked fine.  With the given code before, it was saying it couldn't read /etc/network/interfaces:13: and said there was a duplicate command?  Well, I took a shot and with the little I know, decided the 13 meant Line 13 of the /etc/network/interfaces , so I got rid of the separate bridge_ports for eth1, and put eth1 on a space on the first one, and got rid of the rest of the commands.

Only thing, whats with the LONG startups?

---

### Post by bodhi.zazen on 2008-07-15
Sweet :)

The long start up is due to the bridge, it takes some time for the bridge to come up. I do not know a work around for that one.

---

