---
title: "How to install (or Run) game from iso file?"
date: 2008-12-10
forum: Installation &amp; Upgrades
---

### Post by snipe76 on 2008-12-10
i have ubuntu 8.10 and i downloaded MedalOfHonor for Linux.
The Game Is [COLOR="Red"]**iso**[/COLOR] File.
i don't know how to [COLOR="Red"]**install**[/COLOR] it...

Here a screenshot:
[http://www.siz.co.il/up.php?i=tqyjemxy2ynm.png]("http://www.siz.co.il/up.php?i=tqyjemxy2ynm.png")

Can some 1 help me please?

---

### Post by taurus on 2008-12-10
You either need to burn it to a CD as an ISO image or you can mount it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/M
sudo mkdir /media/iso
sudo mount -t iso9660 MetalofHonor.iso /media/iso -o loop
cd /media/iso
```
and see if there is a install.run or something similar to that to either run it or install it.

---

### Post by snipe76 on 2008-12-10
> **taurus said:**
> You either need to burn it to a CD as an ISO image or you can mount it from a terminal.

Applications -> Accessories -> Terminal
```
cd ~/M
sudo mkdir /media/iso
sudo mount -t iso9660 MetalofHonor.iso /media/iso -o loop
cd /media/iso
```
and see if there is a install.run or something similar to that to either run it or install it.

THX man..!

---

### Post by snipe76 on 2008-12-10
i downloaded other game and its .run
what should i do?

---

### Post by taurus on 2008-12-10
You need to change the permissions to include an executable and then run it.

```
chmod 755 filename.run
./filename.run
```
Assuming you are in the directory where filename.run is located.

---

### Post by snipe76 on 2008-12-10
> **taurus said:**
> You need to change the permissions to include an executable and then run it.

```
chmod 755 filename.run
./filename.run
```
Assuming you are in the directory where filename.run is located.

THX!!!! Very much!!!

---

