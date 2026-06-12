---
title: "E sata"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by Lithofi on 2009-04-02
I am recently new to ubuntu from windows. I enjoy the simplicity of the Linux O/s however when installing onto a newer computer  system with ubuntu on an ide drive and 2 sata cd roms and 1 sata terrabyte drive I cannot access the sata drives.I have placed the disc manager on the ubuntu panel but it says it cannot load the drives?
I would appreciate any help you could give.
Thom out

---

### Post by taurus on 2009-04-02
Does it mean it won't mount or it won't let you write to it?  What format (filesystem) is it?

Open a terminal and post the outputs of these commands here.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by Lithofi on 2009-04-02
it will not mount the drives or recognize them.file sys is nfts windows on a 1 terra byte seagate drive
1 asus dvd r/w optical
1 lightscribe rw/cd\dvd optical.
I will try the command line code
Thanks
Thom out

---

### Post by stimpyaw on 2009-04-03
I removed because I posted my issue in its own thread. oops.

---

