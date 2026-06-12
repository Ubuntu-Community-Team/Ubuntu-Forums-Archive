---
title: "Network Manager Is Gone - Completely"
date: 2016-05-13
forum: Hardware
---

### Post by jooge on 2016-05-13
Hi folks, so I seem to be having a major issue here. I installed a couple of simple updates that I was prompted to this morning after I turned on my computer. Google Chrome, Ubuntu Base, ect.... I was then asked to reboot so all updates would take effect, so I did. After I rebooted I got a "System Error Detected" box that appeared. I noticed that my Network Manager icon was missing from the top panel. I tried rebooting only to have the same thing happen. I clicked the error box and it said this:

Error: /shin/networkmanager

I ran: mm-tool 

** (process: 6290) WARNING **: Could not initiate NNClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

NetworkManager Tool

State: Unknown

I then ran: mm-applet

** (process: 6596) WARNING **: Could not initiate NNClient /org/freedesktop/NetworkManager: The name org.freedesktop.NetworkManager was not provided by any .service files

(nm-applet:6596): nm-applet-WARNING **: Error connecting to ModemManager: Error calling StartServiceByName for org.free desktop.ModemManager1: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Cannot launch daemon, file not found or permissions invalids

(nm-applet:6596): no-applet-WARNING **: Could not find ShellVersion properly on org.gnome.Shell after 5 tries

(nm-applet:6596): no-applet-WARNING **: Failed to register as an age to: (2) The name org.freedesktop.NetworkManger was not provided by any .service files


What does all this mean and what can be done to fix this issue? I need help.

Thanks

---

### Post by Bashing-om on 2016-05-13
jooge; Hello;

Too soon to say, but are you a victim of an update bug ? Is this release 14.04 ?
See If :
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)
Applies ?

Then if YES. one solution is to re-install network-manager using a different machine to transfer the package to the broke system for installation:
[https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3](https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3)

[INDENT][INDENT]this too is fixable
[/INDENT][/INDENT]

---

### Post by jooge on 2016-05-13
> **Bashing-om said:**
> jooge; Hello;

Too soon to say, but are you a victim of an update bug ? Is this release 14.04 ?
See If :
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1539634)
Applies ?

Then if YES. one solution is to re-install network-manager using a different machine to transfer the package to the broke system for installation:
[https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3](https://launchpad.net/ubuntu/+source/network-manager/0.9.8.8-0ubuntu7.3)
[INDENT][INDENT]this too is fixable
[/INDENT]
[/INDENT]


Yes I have 14.04

---

### Post by Bashing-om on 2016-05-13
jooge; Hey !

A number of solutions:
> 
currently " This bug was fixed in the package network-manager - 0.9.8.8-0ubuntu7.3 " and that package is now in the repo : " sysop@1404mini:~$ apt list network-manager >> network-manager/trusty-updates 0.9.8.8-0ubuntu7.3 amd64 " .

An easier application for resolution might be :
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by jhrs212 on 2016-05-15
This works magically!!! 

Just follow the steps with the recovery mode and the network-manageer should be updated.

Thanks a lot!

---

### Post by jooge on 2016-05-15
> **Bashing-om said:**
> jooge; Hey !

A number of solutions:

An easier application for resolution might be :
[http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841](http://askubuntu.com/questions/771627/14-04-network-manager-stopped-working/771841#771841)
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]



Sweet! Thats it. Thank you for you help my friend.

---

### Post by Bashing-om on 2016-05-15
jooge; Great ,, good deal .

> **jooge said:**
> Sweet! Thats it. Thank you for you help my friend.

All of us together
[INDENT][INDENT]makes ubuntu what it is
[/INDENT][/INDENT]

---

