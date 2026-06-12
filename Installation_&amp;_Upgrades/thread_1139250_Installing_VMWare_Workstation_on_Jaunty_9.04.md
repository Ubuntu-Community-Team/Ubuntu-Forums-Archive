---
title: "Installing VMWare Workstation on Jaunty 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by jda1701 on 2009-04-26
IRC was chattering about installation problems with VMWare.  Here's how I solved it.

First, install build-essential.

```
sudo aptitude install build-essential
```

Second, move the binary modules folder according to [VMWare communities website]("http://communities.vmware.com/message/1135664#1141322"), or else you'll get a seg fault. 

```
mv /usr/lib/vmware/modules/binary /usr/lib/vmware/modules/binary.old 
```

Third, rebuild the kernel modules

```
sudo vmware-modconfig --console --install-all
```

Should be able to start vmware.  If not, try starting from console (/usr/bin/vmware) and copy/paste any kind of console errors you get.

Happy VMing.


Jeff Anderson
[http://www.jeffanderson.us/](http://www.jeffanderson.us/)

---

