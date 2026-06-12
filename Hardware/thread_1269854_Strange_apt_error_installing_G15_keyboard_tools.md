---
title: "Strange apt error installing G15 keyboard tools"
date: 2009-09-18
forum: Hardware
---

### Post by yknivag on 2009-09-18
I've just purchased a Logitech G15 keyboard and am trying to conquer the lcd screen and the "G" keys.

I installed the g15 tools from Synaptic, and got an alert sayin that libg15 had failed.  I tried repairing it using the following and got a crazy error

```

gavin@elbow:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  libg15-1
The following NEW packages will be installed
  libg15-1
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/8810B of archives.
After this operation, 77.8kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 134723 files and directories currently installed.)
Unpacking libg15-1 (from .../libg15-1_1.2.6-1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libg15-1_1.2.6-1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libg15.so.1.0.0', which is also in package libg15
Errors were encountered while processing:
 /var/cache/apt/archives/libg15-1_1.2.6-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Yet...
```

gavin@elbow:~$ sudo rm /usr/lib/libg15.so.1.0.0
rm: cannot remove `/usr/lib/libg15.so.1.0.0': No such file or directory

```

How can there be a problem "overwriting" a file which doesn't exist?

Anyone know how I can get past this?

---

### Post by yknivag on 2009-09-18
How strange. Resolved in the end by running:

```

sudo apt-get -f purge libg15
sudo apt-get install libg15

```

Then installing all the other G15 tools from Synaptic.

---

