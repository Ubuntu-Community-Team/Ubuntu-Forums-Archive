---
title: "Ran out of space on FIlesystem"
date: 2008-09-10
forum: General Help
---

### Post by lynx_hanan on 2008-09-10
Hi

My filesystem Drive is nearly full . 800 mB remain on it, i have heard that there is a way in which i can shift some of my folders  in my root partition to a new partition. ????

Links to a tutorial mayb plz???

---

### Post by iaculallad on 2008-09-10
Had you tried cleaning your cache folder?

```
sudo apt-get clean
sudo apt-get autoclean
```

Try also deleting the *.bak files in your /boot folder:
```

sudo rm /boot/*.bak
```

---

### Post by lynx_hanan on 2008-09-10
well . i installed ubuntu on 5.6 Gb partition. so i think if i do clear the cache and the bak i will still need more space one day. because im using ubuntu as my primary OS.

---

### Post by iaculallad on 2008-09-10
> **lynx_hanan said:**
> well . i installed ubuntu on 5.6 Gb partition. so i think if i do clear the cache and the bak i will still need more space one day. because im using ubuntu as my primary OS.

You have to do it outside of your Ubuntu OS environment. Boot from your LiveCD and use GParted to resize your partition.

---

### Post by lynx_hanan on 2008-09-10
cant i just initialzie a new partition .. copy /home directry there .. and add aline to mount /home to that new partition in fstab ????????

i read it once somewehere

---

### Post by iaculallad on 2008-09-10
> **lynx_hanan said:**
> cant i just initialzie a new partition .. copy /home directry there .. and add aline to mount /home to that new partition in fstab ????????

i read it once somewehere

Try reading this [page]("http://www.psychocats.net/ubuntu/separatehome") on how to create a separate home partition.

---

### Post by balaknair on 2008-09-10
Yep
I agree with iaculallad, try the guide at psychocats. It's probably the easiest guide I've found on this topic.
All the best.

---

### Post by lynx_hanan on 2008-09-10
i Have three OS's installed. the order of install was Vista->RedHat Enterprise Linux 5->Ubuntu 8.04

the red hat partiton is ext3, and 11 gb, it dont require it anymore, my ubuntu partiton is 5.6 gb, i just want this 11 gb to goto ubuntu

the only solutions i have heard off is to cretae a speerate partion for home or user???

are there anymore solutions to get this space to goto ubuntu ????

like merging ????

---

### Post by iaculallad on 2008-09-10
> **lynx_hanan said:**
> i Have three OS's installed. the order of install was Vista->RedHat Enterprise Linux 5->Ubuntu 8.04

the red hat partiton is ext3, and 11 gb, it dont require it anymore, my ubuntu partiton is 5.6 gb, i just want this 11 gb to goto ubuntu

the only solutions i have heard off is to cretae a speerate partion for home or user???

are there anymore solutions to get this space to goto ubuntu ????

like merging ????

Creating a separate home partition could be one solution. Another would be to format you're RedHat partition and add it to your Ubuntu partition. That can be achieved by booting on your Ubuntu LiveCD and using Gparted.

---

### Post by lynx_hanan on 2008-09-10
i also mentioned the order of OS's . i believe the i installed ubuntu last so GRUB loader was intalled by ubuntu. even if i do format the RedhAT partition !! will it effect by boot loader settings????

---

### Post by iaculallad on 2008-09-10
> **lynx_hanan said:**
> i also mentioned the order of OS's . i believe the i installed ubuntu last so GRUB loader was intalled by ubuntu. even if i do format the RedhAT partition !! will it effect by boot loader settings????

Yes, it would have an effect in your GRUB menu. But still, you could edit your menu.lst manually and remove the entries pointing at your RedHat OS.

---

