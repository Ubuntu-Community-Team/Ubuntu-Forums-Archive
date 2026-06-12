---
title: "Installing hardy /home problems"
date: 2008-08-21
forum: General Help
---

### Post by Pepmovilin on 2008-08-21
Hi all! I've installed hardy today and I got in trouble. My disk is partitioned in one 20gb for "/" and another 60gb for "/home". So when I installed hardy I formated only the first one, and I told the program to mount /home on my previous /home. The problem is that right now hardy doesn't "see" my old /home and its using another one mounted on the same partition (so I can't see or use my old data). 
Well, I suppose that it might be a problem related with the .drmc of my old /home because in gutsy I was gettin that annoying message about ".drmc file is ignored..." I thought that installing the new hardy will repair it... Can you help me? What can I do?
Thanks in advance!!!  

P.D. As you can see I'm not an English speaker so sorry for my english.

---

### Post by ibutho on 2008-08-21
You can fix this by editing your /etc/fstab and setting up your old /home partition to be mounted as /home. Post back the ouput of running Applications -> Accessories -> Terminal and entering the command
```
sudo fdisk -l
```

---

### Post by Pepmovilin on 2008-08-21
Hi! Thanks for answer! My output: 

Disco /dev/sda: 120.0 GB, 120034123776 bytes
255 cabezas, 63 sectores/pista, 14593 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xbbc58b91

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        1278    10265503+   7  HPFS/NTFS
/dev/sda2            2199       11597    75497467+   f  W95 Ext'd (LBA)
/dev/sda3           11598       14593    24065370    7  HPFS/NTFS
/dev/sda5            2199        8725    52428064+  83  Linux
/dev/sda6   *        8726       11336    20972826   83  Linux
/dev/sda7           11337       11597     2096451   82  Linux swap / Solaris

My sda5 is the disk with my old /home. The problem is that I set it to be mounted as /home in the hardy setup but I can't see the data or use anything I had. 
Thanks!

---

### Post by Archmage on 2008-08-21
May I ask of the output of /etc/fstab?

---

### Post by Pepmovilin on 2008-08-21
Sorry, I'm stupid. The problem was that I put different users name, so the folders were differents. 
Of course, thank you so much for helping newbie people like me and making this a great community!

---

