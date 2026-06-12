---
title: "Installation Problem/Reinstallation"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by Allyhibs on 2009-06-06
Hi, I installed ubuntu by creating a partition on my windows drive but I believe something has gone wrong during the process. Ubuntu won't recognise that there is any disk space available despite there being about 35 gb. 
If I were to wipe the ubuntu/grub partition using windows could I then reinstall ubuntu with a boot disk directly into the then empty partition? 

I hope this makes some sense!
Thanks

---

### Post by zvacet on 2009-06-06
First remove grub following [this]("http://members.iinet.net.au/~herman546/p18.html#MbrFix.exe") giude.After that download [Gparted live CD]("http://gparted.sourceforge.net/") and delete Ubuntu partition.On that empty space install Ubuntu from Ubuntu CD.

---

### Post by pastalavista on 2009-06-06
How did you create the partition? You need to boot from the Ubuntu Live CD and open Gparted (System > Administration > Partition Editor) and make sure the drive is formatted correctly.

---

### Post by Allyhibs on 2009-06-06
The partition was created using the ubuntu boot disk.

---

### Post by Allyhibs on 2009-06-06
Just to update I've solved the problem now. Used MbrFix to restore my MBR and then used partition magic to remove the ubuntu partition. I'm going to try a clean partition now to install it again.

---

