---
title: "CD and DVD Drive NOT(!!!!) Working!!!!!"
date: 2010-06-03
forum: Hardware
---

### Post by sayk on 2010-06-03
I've got a CD drive and a DVD drive which used to work on Ubuntu 9.10 but ever since i upgraded to/installed Ubuntu 10.04 on my computer they stopped working. I really need to use the CD and the DVD drives since I have to burn some important CD's and DVD's.............

---

### Post by Grenage on 2010-06-03
Can you boot from the drive?

---

### Post by sayk on 2010-06-03
dont know but when I insert an empty CD it is not detected/read by the computer........

---

### Post by Grenage on 2010-06-03
First thing to do, is to try a CD you know works, a bootable one.  If you can boot from the drive, we can rule out it being defective.

---

### Post by sayk on 2010-06-03
I have tried inserting different ones and I dont think all of them are defective.....

---

### Post by Grenage on 2010-06-03
We're trying to rule out the drive being defective.  If you can boot the computer from a live CD, it would rule that out.

---

### Post by Yellow Pasque on 2010-06-03
Grenage is suggesting you boot from the CD drive (instead of booting Ubuntu or something else on your hard disk) to make sure the drive(s) itself is not defective. However, if you have two drives and they both stopped working at the same time when you upgraded, it's unlikely the hardware is defective. Make sure the drives are detected with:
```
sudo lshw -C disk
```
Also, look through dmesg, especially after you try inserting a disc:
```
dmesg
```

---

### Post by Sliaf on 2010-06-04
Hello,

I just updated today and I am new to Linux, after updating my DVD drive stopped working as well.  I know it is not the drive because I am unfortunately still dual booting with a Windows Vista partition and it works in windows.  Does anyone have any suggestions? 

Thank you for any help,
Sliaf

---

### Post by xuyimin on 2010-06-05
I have got the same problem in the Ubuntu 10.04 system. But I don't know how to fix it, sorry.

---

### Post by xuyimin on 2010-06-05
When I start my laptop today,I find the CD Drive works very well, I don't know what happened.

---

### Post by Yellow Pasque on 2010-06-05
> **Sliaf said:**
> Does anyone have any suggestions?
Yes. [http://ubuntuforums.org/showpost.php?p=9404199&postcount=7](http://ubuntuforums.org/showpost.php?p=9404199&postcount=7)

---

