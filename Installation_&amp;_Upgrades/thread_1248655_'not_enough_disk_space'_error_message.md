---
title: "'not enough disk space' error message?"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Bing100 on 2009-08-24
I'm new to Ubuntu. I just installed Ubuntu from the CD along side Vista on my Fujitsu laptop.
I'm trying to configure my printer, but when I attempt to download drivers, I get message: 
&quot;There is not enough room on the disk to save /tmp/p99Q4Kyj.bin.part.&quot;
What does this mean? I have 147G's available on the disk.
Same thing goes for trying to download Ubuntu updates. I get a similar,&quot;not enough
free disk space. upgrade needs 360M free space on '/'. Please free 328M on '/'.&quot;
Tried to download the Ubuntu pocket guide, told I don't have enough disk space.
Again, I have 147G's available on my HD. 
Can someone take pity on me and tell me where/how to find a resolution to this? Thanks

---

### Post by cariboo on 2009-08-24
You may not have created a large enough / partiton. You can remove archived package from /var/cache/apt/archives by opening an Applications-->Accessories-->Terminal and typing:

```
sudo apt-get clean
```

this will remove downloaded packages.

To check disk space, in the same terminal type:

```
df -h
```

The above command will give disk space usage in a human readable form.

---

