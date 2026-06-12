---
title: "SWAP partition not being used, even when RAM is loaded"
date: 2008-07-29
forum: General Help
---

### Post by manil on 2008-07-29
hi, iv just been ubuntu for about 2 weeks and its great. but i noticed that every time i tried to run intensive software simultaneously or tried 3d applications, the computer slowed or hung.

i foudn that the SWAP partition i made on installation, 2 GB, twice the size of my RAM is not utilized. the 'free' command registers this:

manil@manil-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1025756     953808      71948          0      29632     461256
-/+ buffers/cache:     462920     562836
Swap:      2000052          0    2000052


i think an alternative might be to use swapd or swapspace. but id prefer to use the harddrive since its faster. any ideas please?

---

### Post by pauper on 2008-07-29
Please, post the output:

```
sysctl vm.swappiness
```

---

### Post by manil on 2008-07-29
sysctl vm.swappiness in the terminal outputs:

manil@manil-desktop:~$ sysctl vm.swappiness
**vm.swappiness = 60**

curious about exactly what that command means, but i just need some help to fix this. i cant even run scorched3d on a P4 3.2 GHz CPU. :(

then i can put ubuntu on my laptop.

---

### Post by Diabolis on 2008-07-29
[This post explains it, happy reading.]("http://ubuntuforums.org/showpost.php?p=1255511&postcount=43")

---

### Post by pauper on 2008-07-29
Range is from 0 to 100. To swap out more pages increase the value. Setting a 
value of 0 will make your system run out of RAM first and only then to switch
to swap partition.

An example:

```
sudo sysctl vm.swappiness=70
```

When you find the value you are happy with pass this command:

```
echo "vm.swappiness = 70" | sudo tee -a /etc/sysctl.conf
```

Note: Please, pay attention to syntax--"sysctl vm.swappiness*=70*", but
echo "vm.swappiness* = 70*".

This article might interest you:

[http://lwn.net/Articles/83588/](http://lwn.net/Articles/83588/)

---

### Post by manil on 2008-07-30
tried the method suggested. even with vm.swappiness set to 100, 0% of the SWAP is used, no matter the level of RAM usage. read both the articles btw, enlightening, dint kno i had to enable support of >1 GB RAM. anyway, back to the issue... is this a normal problem??

---

