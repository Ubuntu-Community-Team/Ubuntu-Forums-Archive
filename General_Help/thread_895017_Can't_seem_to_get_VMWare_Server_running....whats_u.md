---
title: "Can't seem to get VMWare Server running....whats up?"
date: 2008-08-19
forum: General Help
---

### Post by Radioman991 on 2008-08-19
Hello

I have managed to successfully install VMWare  Server, thanks to one of the great tutorials on here, but it will not start...just the spinning disk

Running vmware from terminal, here is what I see..

phil@Linux-Test:~$ vmware
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_3.4' not found (required by /usr/lib/libcairo.so.2)
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
phil@Linux-Test:~$ 


What am I missing or doing wrong?

Thanks, as always

PK

---

### Post by spiderbatdad on 2008-08-19
try launching as root```
sudo vmware
```Been a while since i ran it, but it may be the .vmware folder in your home directory needs to be chowned.

---

### Post by Scunizi on 2008-08-19
VMware server 1.x.x will need the "any-any" update designed for the kernel you currently have installed and a new any-any with any subsequent kernel update. You might consider installing VMWare server 2.X beta which will allow you access to your VM's via Firefox from any machine in the house.  Works great for me.

---

### Post by juan@forum on 2008-08-21
sudo mv /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1 /usr/lib/vmware/lib/libgcc_s.so.1/libgcc_s.so.1.org

you should not run your applications as root.

---

