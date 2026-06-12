---
title: "Cdrom probs"
date: 2006-10-30
forum: Hardware &amp; Laptops
---

### Post by titan21 on 2006-10-30
Okay, I think a few people have had similar problems but nothing i have found seems to work for me.

I insert a cd on my ide cdrom and i get the error "no medium found". dmesg gives me this

[17179580.364000] Probing IDE interface ide0...
[17179581.452000] ide0 at 0xbc00-0xbc07,0xb882 on irq 225
[17179581.452000] Probing IDE interface ide1...
[17179582.164000] Probing IDE interface ide1...

and my fstab read like this...

/dev/hdb        /media/cdrom0   udf,iso9660	user,noauto     0       0

I'm a total noob! I had a bit of a headache trying t get Ubntu in the first place due to the JMicron probs (which I believe everybody under the sun was aware of!) so go easy on me!

Kernel is 2.6.17-10-generic

Your help is very much appreciated!

Thanks,

Tim

---

### Post by ahaslam on 2006-10-30
> **titan21 said:**
> 
and my fstab read like this...

/dev/hdb        /media/cdrom0   udf,iso9660	user,noauto     0       0


Is the default not hdc?

---

### Post by titan21 on 2006-11-02
If i try

mount /dev/hdc /media/cdrom0

I get

mount: special device /dev/hdc does not exist

---

### Post by Kira-cjd on 2006-11-02
reinstall cd drive

---

### Post by titan21 on 2006-11-02
The drive worked fine under windows so taking my machine apart and putting it back together is not an option if thats what you mean

By the way - I am using Edgy if that helps

---

