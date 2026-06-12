---
title: "apt-get input/output errors from dpkg"
date: 2009-09-13
forum: Installation &amp; Upgrades
---

### Post by veggiefish on 2009-09-13
Hi, Please help me work out this, I tried sudo apt-get clean and update but the errors persist.

```

$ sudo apt-get install deluge
[sudo] password for xxxxl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  deluge-common deluge-core libboost-filesystem1.37.0 libboost-python1.37.0
  libboost-system1.37.0 libboost-thread1.37.0 libtorrent-rasterbar2
  python-libtorrent
Suggested packages:
  libtorrent-rasterbar-dbg
The following NEW packages will be installed:
  deluge deluge-common deluge-core libboost-filesystem1.37.0
  libboost-python1.37.0 libboost-system1.37.0 libboost-thread1.37.0
  libtorrent-rasterbar2 python-libtorrent
0 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
Need to get 4127kB of archives.
After this operation, 19.4MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://th.archive.ubuntu.com jaunty/universe libboost-python1.37.0 1.37.0-3ubuntu3 [335kB]
Get:2 http://th.archive.ubuntu.com jaunty/universe libboost-system1.37.0 1.37.0-3ubuntu3 [124kB]
Get:3 http://th.archive.ubuntu.com jaunty/universe libboost-filesystem1.37.0 1.37.0-3ubuntu3 [146kB]
Get:4 http://th.archive.ubuntu.com jaunty/universe libboost-thread1.37.0 1.37.0-3ubuntu3 [140kB]
Get:5 http://th.archive.ubuntu.com jaunty/universe libtorrent-rasterbar2 0.14.2-2ubuntu1 [1162kB]
Get:6 http://th.archive.ubuntu.com jaunty/universe python-libtorrent 0.14.2-2ubuntu1 [457kB]
Get:7 http://th.archive.ubuntu.com jaunty/universe deluge-core 1.1.6+dfsg-2ubuntu1 [1317kB]
Get:8 http://th.archive.ubuntu.com jaunty/universe deluge-common 1.1.6+dfsg-2ubuntu1 [188kB]
Get:9 http://th.archive.ubuntu.com jaunty/universe deluge 1.1.6+dfsg-2ubuntu1 [257kB]
Fetched 4127kB in 55s (74.8kB/s)                                               
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

and

```

~$ sudo apt-get install rtorrent
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libtorrent11 libxmlrpc-c3
The following NEW packages will be installed:
  libtorrent11 libxmlrpc-c3 rtorrent
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 902kB of archives.
After this operation, 2437kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://th.archive.ubuntu.com jaunty/universe libxmlrpc-c3 1.06.27-1 [245kB]
Get:2 http://th.archive.ubuntu.com jaunty/universe libtorrent11 0.12.2-0ubuntu1 [324kB]
Get:3 http://th.archive.ubuntu.com jaunty/universe rtorrent 0.8.2-0ubuntu1 [333kB]
Fetched 902kB in 12s (71.7kB/s)                                                
dpkg: failed in buffer_read(fd): copy info file `/var/lib/dpkg/available': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

---

### Post by sisco311 on 2009-09-13
try:
```
sudo dpkg --clear-avail
sudo apt-get update
```

---

### Post by veggiefish on 2009-09-13
Thank you that did help me install those files. But now I noticed alot of input/output errors in transmission for downloading bittorrents, and when I open update manager, I get this:

```

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5 Input/output error), E:The package lists or status file could not be parsed or opened.'

```

So something keep causing it, also my fast system has suddenly become very slow and windows like FF keep going grey for a few seconds, then coming back. Ive not made any big changes and previously such a speedy system, very worrying! Thanks for your help.

---

### Post by sisco311 on 2009-09-13
> **veggiefish said:**
> Thank you that did help me install those files. But now I noticed alot of input/output errors in transmission for downloading bittorrents, and when I open update manager, I get this:

```

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (5 Input/output error), E:The package lists or status file could not be parsed or opened.'

```

So something keep causing it, also my fast system has suddenly become very slow and windows like FF keep going grey for a few seconds, then coming back. Ive not made any big changes and previously such a speedy system, very worrying! Thanks for your help.

try to check the root partition for errors.

assuming that sda1 is /
```
sudo tune2fs -C 40 /dev/sda1
```
and reboot.

---

### Post by veggiefish on 2009-09-13
I did as you suggested, and the check ran upon reboot, but the error persists. :/

---

### Post by drs305 on 2009-09-13
If it's a list error open Synaptic or Software Sources >Settings, Repositories. Note all your selected repositories. Untick them all, then reselect them, then Reload. This will update the lists.

If it's the dpkg status file, try switching to the backup list:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo apt-get update

```

---

### Post by veggiefish on 2009-09-13
Thank you for your input.

I had already tried clicking/unclicking the repositories, but this provided the same read error.

So I followed your second piece of advice and reverted to the backup of the dpkg status.

After swapping these, I ran the apt-get update successfully and I was then able to open synaptic package manager without hitch. I then again reset the repositories, and hit "reload". This very quickly reloaded the repos.

I then opened update manager which very quickly checked the lists and found I was up to date.

I have been testing normal usage, which previously during this problem was causing my FF and other apps to go grey and the whole machine to slow to a crawl. Everything is now back to lightning quick.

Thank you.

---

### Post by veggiefish on 2009-09-23
Unfortunately although this does fix the problem it keeps happening, every day, or every time I use apt-get. I can follow these stesp to make it work temporarily, but the next time I use apt-get it doesnt work. Its not related to reboots as I did not reboot my computer for several days and the problem kept happening. Although it does still happen after reboot. Any idea what the underlying cause might be?

---

### Post by drs305 on 2009-09-23
> **veggiefish said:**
> Unfortunately although this does fix the problem it keeps happening, every day, or every time I use apt-get. I can follow these stesp to make it work temporarily, but the next time I use apt-get it doesnt work. Its not related to reboots as I did not reboot my computer for several days and the problem kept happening. Although it does still happen after reboot. Any idea what the underlying cause might be?

The continuing "read" problem may reflect a problem with an individual file's status/permissions. Take a look in in /var/lib/apt/lists and see if any of the information/permissions look different than the rest:
```

ls -la /var/lib/apt/lists

```

Have you tried a different server? It's not likely an active repository would contain an erroneous file over a long period of time, but I suppose it could.

---

### Post by veggiefish on 2010-01-13
Someone emailed me asking if I solved this, so I thought I would update the thread-

I had to use the solution provided by:

[http://ubuntuforums.org/showpost.php?p=7943852&postcount=6](http://ubuntuforums.org/showpost.php?p=7943852&postcount=6)

the next 4 or 5 times I ran apt get. Then, on the 5th time, it just stopped happening, and apt get works fine now. I did not make any other changes. Although, I did continue to update ubuntu when prompted by the system updater (may or may not be relevant!).

---

