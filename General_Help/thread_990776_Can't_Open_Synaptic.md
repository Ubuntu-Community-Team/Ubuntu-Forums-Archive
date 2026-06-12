---
title: "Can't Open Synaptic"
date: 2008-11-23
forum: General Help
---

### Post by Jordy27 on 2008-11-23
I tried opening synaptic today to check for updates. When it opened, the normal 'building dependency tree' loading bar appeared but go stuck at about 1/3. After a lot of struggle it eventually got to halfway but then synaptic closed without any warning. I have tried this several times, after rebooting etc, but still get the same result (this applies for update manager as well) despite the fact that I had synaptic running fine earlier today.

When I use apt-get i get the following:

> 
jordan@Xubuntu:~$ sudo apt-get check
Reading package lists... Done
Bus errordependency tree... 50%
jordan@Xubuntu:~$ 


Any help would be very much appreciated!

---

### Post by rudihawk on 2008-11-23
try:
```
sudo apt-get -f
```

I think that will attempt to fix the errors.

---

### Post by cdtech on 2008-11-23
You should check your "dmesg" to see if there are any error's when you use the "apt-get" command. Could be a drive issue.....

---

### Post by jmszr on 2008-11-23
Jordy27,
        This has worked for me before: "sudo rm /var/cache/apt/*.bin". With out the quote marks,naturally.

---

### Post by noway2 on 2009-05-23
> **jmszr said:**
> Jordy27,
        This has worked for me before: "sudo rm /var/cache/apt/*.bin". With out the quote marks,naturally.
This did the trick for me too!

I am curious, though, as to what causes this to happen.

dmesg does give various error messages, such as doesn't supprot DPO or FUA, unrecovered read error, DRDY ERR, but quite honestly I have no idea what these mean or how severe they are.

---

### Post by rne1223 on 2009-07-17
Yeah...that sure did the trick, but can someone please explain why those this work. I would greatly appreciate it.

---

### Post by ciscosurfer on 2009-07-17
> **noway2 said:**
> ...I am curious, though, as to what causes this to happen...

> **rne1223 said:**
> Yeah...that sure did the trick, but can someone please explain why those this work. I would greatly appreciate it.Sometimes the package cache can get scrambled or corrupt or just needs to be rebuilt. The command```
sudo rm /var/cache/apt/*.bin
```effectively removes all files that end with .bin, so what this means is that the pkgcache.bin and srcpkgcache.bin files will be removed, thus forcing apt to recreate new package (and source package if you build from source) caches. It is one way to allow apt to start fresh again. And because Synaptic uses apt as its backend, removing these files helps Synpatic along.

---

