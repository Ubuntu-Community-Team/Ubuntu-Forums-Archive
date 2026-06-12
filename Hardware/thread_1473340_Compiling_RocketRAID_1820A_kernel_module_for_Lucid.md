---
title: "Compiling RocketRAID 1820A kernel module for Lucid Lynx"
date: 2010-05-05
forum: Hardware
---

### Post by joakimmoller on 2010-05-05
After upgrading from Ubuntu 8.04 LTS to Ubuntu 10.04 LTS on my fileserver I found that the hptmv module was not compiling for the new kernel 2.6.32-21-server. But with some tampering in the code I made it compile and run.

The source of the kernelmodule I used is this:
[http://http://www.highpoint-tech.com/BIOS_Driver/rr1820a/Linux/rr18xx-opensource-v1.19-080710.tgz]("http://http//www.highpoint-tech.com/BIOS_Driver/rr1820a/Linux/rr18xx-opensource-v1.19-080710.tgz")

Apply the attached patch: Copy the patch file into to the source directory and run the following command:
```

patch -p1 -i ubuntu_lucid.patch.txt

```After applying the patch the make, make install works and its possible to access the raid array on lucid.

WARNING! I'm not a super professional on kernel modules, block devices nor c-programming. Use this patch on your own risk. Make sure you have backups of your data.

---

### Post by dino99 on 2010-05-05
[http://ubuntuforums.org/showthread.php?t=1166767](http://ubuntuforums.org/showthread.php?t=1166767)

---

### Post by changlinn on 2010-06-12
Thanks very much using both the old instructions and your patch I have my 1820a working on 2.6.32-22-generic x64
On reboot it didn't work properly but the below fixed that, thanks very much, I am personally going to ditch the 1820a I don't need that many drives now I have a 2tb and USB drives, and 10 on board sata... So I am copying the data now to the 2tb monster then I can get rid of the card.

```
sudo update-initramfs -k "2.6.32-22-generic" -c
sudo modprobe hptmv
```

Edit: Don't fancy writing a patch for the rr454 do you :) [http://ubuntuforums.org/showthread.php?t=777848&page=2](http://ubuntuforums.org/showthread.php?t=777848&page=2)

Edit2: never mind decided to ditch this raid card too and copied the data off using windows of all things to my new disks in Ubuntu.

---

### Post by meresda on 2010-10-03
I'll add another thanks . . . saved my butt :P

---

