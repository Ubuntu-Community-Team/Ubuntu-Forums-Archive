---
title: "Error saying &quot;size mismatch&quot; during installation.."
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by shredder12 on 2009-02-19
I tried to install vlc player using apt..
```
sudo apt-get install vlc
```
and got the following error..
```
Get:1 http://archive.ubuntu.com intrepid/universe libdvdnav4 4.1.2-3 [74.6kB]
Get:2 http://archive.ubuntu.com intrepid/universe libmpeg2-4 0.4.1-3 [55.9kB]
Fetched 59.5kB in 0s (207kB/s)                    
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/libd/libdvdnav/libdvdnav4_4.1.2-3_i386.deb  Size mismatch
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/universe/m/mpeg2dec/libmpeg2-4_0.4.1-3_i386.deb  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I am getting a similar error while installing linuxdcpp either using apt or synaptic..
any help please..

---

### Post by itang sanjana on 2009-02-19
Hello,
Try using another server/mirror locate in your Software Sources.
Menu: System->Administration->Software Sources

*you have to be a root

See also:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

HTH

---

### Post by shredder12 on 2009-02-19
ya i changed the server from server of india to main server.. but still having the same problem..

---

### Post by itang sanjana on 2009-02-19
Well there's nothing else I can do. Sorry ..
[https://bugs.launchpad.net/update-manager/+bug/77528](https://bugs.launchpad.net/update-manager/+bug/77528)

---

### Post by shredder12 on 2009-02-21
well the problem got solved by itself..

---

