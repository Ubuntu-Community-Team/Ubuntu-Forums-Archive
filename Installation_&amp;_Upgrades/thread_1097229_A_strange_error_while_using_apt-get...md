---
title: "A strange error while using apt-get.."
date: 2009-03-15
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2009-03-15
I am not having a problem while installing or uninstalling using apt-get .. 
the job gets done.. but during this it shows some error.
e.g. i was trying to install traceroute and used the following command..
```
sudo apt-get install traceroute
```
and at the end I got the following error...
```
The following NEW packages will be installed:
  traceroute
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 48.8kB of archives.
After this operation, 172kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com intrepid/main traceroute 2.0.11-2 [48.8kB]
Fetched 48.8kB in 5s (9537B/s)     
Selecting previously deselected package traceroute.
(Reading database ... 139585 files and directories currently installed.)
Unpacking traceroute (from .../traceroute_2.0.11-2_i386.deb) ...
Processing triggers for man-db ...
Setting up daemontools-run (1:0.76-3) ...
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
grep: /etc/inittab: No such file or directory
Adding SV inittab entry...
cp: cannot stat `/etc/inittab': No such file or directory
dpkg: error processing daemontools-run (--configure):
 subprocess post-installation script returned error exit status 1
Setting up traceroute (2.0.11-2) ...

Errors were encountered while processing:
 daemontools-run
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
though traceroute gets installed.. i don't know why is it worrying about daemontools..
this happens all the time i use apt-get..
actually while i was installing some package today.. the system reported a crash while using apt-get..
i don't remember what was it about. but i think this problem has started since then..

---

### Post by freakyzoidberg on 2009-03-15
a daemontool-run previous install failed

you can either try to reconfigure this install before installing traceroute
by > dpkg --configure daemontools-run

or if its still fail and you dont use daemontool 
> apt-get remove daemontools-run --purge

and by the way to mount a iso image, you can use mount
> mount -o loop disk1.iso /mnt/disk

---

### Post by oldos2er on 2009-03-15
You might want to file a bug against the package daemontools-run. inittab hasn't been used in Ubuntu for several versions.

---

### Post by shredder12 on 2009-03-16
i actually have reported the crash report already to ubuntu.. and now after uninstalling daemon-tools.. this problem has been solved..

---

