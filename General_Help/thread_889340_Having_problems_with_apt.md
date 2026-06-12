---
title: "Having problems with apt"
date: 2008-08-14
forum: General Help
---

### Post by zmjjmz on 2008-08-14
So, whenever I try to install something with apt-get, I get this:
```
$ sudo apt-get install qtpfsgui exiv2
[sudo] password for zj1992:
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  libexiv2-2
The following NEW packages will be installed:
  exiv2 libexiv2-2 qtpfsgui
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2004kB of archives.
After this operation, 4919kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libexiv2-2 0.16-3ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe exiv2 0.16-3ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe qtpfsgui 1.9.0-1ubuntu0.1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/libexiv2-2_0.16-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/e/exiv2/libexiv2-2_0.16-3ubuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/e/exiv2/exiv2_0.16-3ubuntu1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/e/exiv2/exiv2_0.16-3ubuntu1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qtpfsgui/qtpfsgui_1.9.0-1ubuntu0.1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/q/qtpfsgui/qtpfsgui_1.9.0-1ubuntu0.1_i386.deb)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Neither apt-get update nor apt-get install --fix-missing work, and in fact return the same errors.
Synaptic and gnome-app-install suffer from the same errors too.

I personally am not really sure what's happening -- is my own computer refusing apt-get?
By the way, I've tried rebooting, so this is (hopefully) a configuration issue.

---

### Post by Mister.Vash on 2008-08-14
Check and see if you have a proxy defined.

echo $http_proxy and see if that comes backs with something - if it does you may need to remove it

These lines indicate that is is trying to connect to that site via your local network on port 4001
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libexiv2-2 0.16-3ubuntu1
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by zmjjmz on 2008-08-14
Oh dear, my proxy is htpp://localhost:4001
That explains it, but how can I reset/remove it?

---

### Post by decoherence on 2008-08-14
in the terminal,

```
unset http_proxy
```

---

### Post by zmjjmz on 2008-08-14
Thanks, I'll mark this is as solved.

---

### Post by zmjjmz on 2008-08-21
Sorry about reopening the thread, but the fix (unset http_proxy) only solved the problem for apt-get, and did so only once. I have to do it before I call on apt-get each time.
On the other hand, other applications such as the graphical apt tools do not work, and all web browsers except Epiphany, Kazehakase, Flock, and Firefox fail to connect (which is probably due to Gecko having its own configurations for proxies).

---

