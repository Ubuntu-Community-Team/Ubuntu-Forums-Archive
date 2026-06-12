---
title: "[SOLVED] Hard drive capacity"
date: 2008-07-27
forum: General Help
---

### Post by kernelhaxor on 2008-07-27
I have two 500GB hard drives installed on my system.  
I just reformatted one of my hard drives (the one not containing the Unix File System) to ext3 from ntfs.  There is nothing on it yet except the lost+found folder.  However it shows 23.5GB as used (Total Capacity: 462.1GB and Free space: 438.6GB).
I checked via root account too, there is nothing on this disk except the lost+found folder.  I even deleted the lost+found folder yet there is 23.5GB missing.  Does anyone know whats happening?

---

### Post by dexter.deepak on 2008-07-27
did you shift+delete the lost+found folder ? otherwise it still takes up space in trash.

---

### Post by kernelhaxor on 2008-07-27
> **dexter.deepak said:**
> did you shift+delete the lost+found folder ? otherwise it still takes up space in trash.
I cleared the trash folder and deleted that too .. when I do 'ls -al', nothing shows up, yet 23.5GB is somehow gone.
I'll try reformatting the disk again ..
Thanks for your reply anyway

---

### Post by Ryadt on 2008-07-27
It is related to the conversion from binary to decimal values. Hard Drive manufactures uses the decimal values a drive but Operating Systems uses binary. In decimal values 1 GB = 1,000,000,000 bytes but in binary 1GB = 1,073,741,824 bytes.:(
I'll let you do the maths.:)

---

### Post by kernelhaxor on 2008-07-27
> **Ryadt said:**
> It is related to the conversion from binary to decimal values. Hard Drive manufactures uses the decimal values a drive but Operating Systems uses binary. In decimal values 1 GB = 1,000,000,000 bytes but in binary 1GB = 1,073,741,824 bytes.:(
I'll let you do the maths.:)

I am aware of those conversions .. Thats not the problem I am having ..

Like I already mentioned in my first post, this is what I see:
Total Capacity: 462.1GB and Free space: 438.6GB
Used space: 23.5GB

Clearly, thats not something resulting from conversions ..

---

### Post by tom66 on 2008-07-27
Open gparted (Applications > Accessories > Terminal > then type "sudo gparted") and check it isn't partitioned. I don't know, but if it's got a corrupted filesystem or something on the other partition it might not show up and gobble 23GBs up. 

You might need to install it. Also, it only runs under root, and be careful not to make any changes.

---

### Post by Elfy on 2008-07-27
Ext3 keep a percentage of the drive so that the drive can be booted when full (at least I think that's the reasoning) - it defaults to 5% of the drive size. Which sounds about right - it can be adjusted with tune2fs

---

### Post by coffeecat on 2008-07-27
> **tom66 said:**
> Open gparted (Applications > Accessories > Terminal > then type "sudo gparted") 

Slight clarification. If you've got Gparted installed, it's a bit easier to go to System > Administration > Partition Editor. Avoids using the terminal. Frightens the horses, you see. :wink:

---

### Post by kernelhaxor on 2008-07-27
> **tom66 said:**
> Open gparted (Applications > Accessories > Terminal > then type "sudo gparted") and check it isn't partitioned. I don't know, but if it's got a corrupted filesystem or something on the other partition it might not show up and gobble 23GBs up. 

You might need to install it. Also, it only runs under root, and be careful not to make any changes.

That I made sure.  In fact I used gparted to reformat the drive.

> **forestpixie said:**
> Ext3 keep a percentage of the drive so that the drive can be booted when full (at least I think that's the reasoning) - it defaults to 5% of the drive size. Which sounds about right - it can be adjusted with tune2fs

Perfect! That explains it! Thanks a lot.

Thank u all for trying to help!

---

### Post by Elfy on 2008-07-27
You can change it quite easily if you wish - I do on my media drives, but I don't do so on my / drive - I generally drop it to 2%. Easy to do in a terminal

Use ```
df-h
``` in aterminal to get drives then for each run

tune2fs -m *n* /dev/*sd** - change *n* to percentage reserved required, change *sd** to equal drive to change - eg to change sda6 to 2%

```
tune2fs -m 2 /dev/sda6
```

Hope that helps

---

