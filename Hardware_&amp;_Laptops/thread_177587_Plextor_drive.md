---
title: "Plextor drive"
date: 2006-05-16
forum: Hardware &amp; Laptops
---

### Post by sjpritch25 on 2006-05-16
I am thinking about purchasing a PATA Plextor DVD Burner.  Does anyone know if its compatible with Ubuntu Breezy Badger.  I have the Serial ATA version and its not.

---

### Post by wpshooter on 2006-05-16
I am using IDE Plextor CD-RW drive 40x12x40 and it works fine - that is after they got a few of the kinks worked out of K3b program.

---

### Post by JonnyRo on 2006-05-17
wpshooter, What is the model number of your burner.  You can check without opening by doing the following.  if your cd burner is /dev/hdc then do

cat /proc/ide/hdc/model

If not hdc, replace with the appropriate block device name.   I am very interested in purchasing a dvd burner that is compatible with kde and breezy.

---

### Post by vincentb on 2006-06-29
wpshooter,

I am currently facing some problem in making K3B working on Ubuntu 6.06LT (as you can read it here : [http://ubuntuforums.org/showthread.php?t=204920](http://ubuntuforums.org/showthread.php?t=204920)) I am pretty sure K3b was working on the same PC before the upgrade from 5.10 to 6.06.

Can you give more details about the K3B issues you are mentionning in your answer.

Thanks a lot in advance,

Best regards,

Vincent

---

### Post by sjpritch25 on 2006-07-02
Thanks but its working now in Dapper drake.

---

