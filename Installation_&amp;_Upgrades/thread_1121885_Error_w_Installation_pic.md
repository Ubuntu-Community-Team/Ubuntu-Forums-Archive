---
title: "Error w/ Installation *pic*"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by RCGA on 2009-04-10
I'm having trouble installing ubuntu onto my laptop. I have my HD partitioned into three parts....one is ~65GB, the other is ~11GB (fat32) and the third is ~100mb 

I'm getting this error:

Any ideas?

---

### Post by cariboo on 2009-04-10
You have to create an ext3 partition before you can install Ubuntu. It will not install on a ntfs or vfat partition. From you overly large picture, I'm going to assume you waht to install Ubuntu on your fat32 partition. 

Boot from the LiveCD and at the desktop go to System-->Administration-->Partition Editor and delete the fat32 partition, then try to install.

I've changed your picture to an attachment so that it doesn't take up some much room.

Jim

---

### Post by RCGA on 2009-04-10
I've reformated the fat32 to NTFS

Do I still need to delete it?

---

### Post by RCGA on 2009-04-10
Also, how do I boot from the LiveCD?

---

### Post by alfplayer on 2009-04-10
Are you installing Ubuntu from a CD? or a DVD?

---

### Post by RCGA on 2009-04-10
I downloaded 8.10 and burned it off from a DVD

---

### Post by RCGA on 2009-04-10
Is booting from the LiveCD just using ubuntu without installing it? If so I'm using it now

---

### Post by alfplayer on 2009-04-10
> Is booting from the LiveCD just using ubuntu without installing it? If so I'm using it now 	
Yes, that's ok.

Are you trying to dual-boot with windows? There are a lot of tutorials to do that on the web.

---

### Post by Agent.Logic_ on 2009-04-10
Did you set up a mount point for root (/)? Also, like cariboo907 said, you'd need a ext3 filesystem for the install.

---

