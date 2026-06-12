---
title: "How do I format an External USB HD?"
date: 2008-11-19
forum: Hardware
---

### Post by joelw1351 on 2008-11-19
I need instructions to formating an External USB HD.

---

### Post by taurus on 2008-11-19
Install gparted and use it to format your external harddrive.  What kind of filesystem you want to format it to?

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

---

### Post by joelw1351 on 2008-11-19
> **taurus said:**
> Install gparted and use it to format your external harddrive.  What kind of filesystem you want to format it to?

```
sudo apt-get update
sudo apt-get install gparted
gksudo gparted
```

I want the drive read/write from my iMac. This is my first time on Linux and my second week on the iMac. So I need help.

---

### Post by notwen on 2008-11-19
I would recommend FAT32 although you won't be able to store files larger than 4GB on a FAT32 file system.  FAT32 however should show up on both Linux(Ubuntu) and OSX w/o any additional work.  Hope this helps.  =]

---

### Post by joelw1351 on 2008-11-19
> **notwen said:**
> I would recommend FAT32 although you won't be able to store files larger than 4GB on a FAT32 file system.  FAT32 however should show up on both Linux(Ubuntu) and OSX w/o any additional work.  Hope this helps.  =]

I tried to get gparted to work, but I am at a total loss on how to do this. This is my first day on Linux and my second week on Mac so I am a novice.

---

### Post by 00b00nt00 on 2008-11-20
I'm doing this from memory, because I only have my Mac handy at the moment, but...

1) Insert your USB HD.

2) Go into gparted.

3) Right mouse button on the USB HD and select the option to un-mount it (I'm assuming it is mounted).

4) (WARNING - THIS PART DESTROYS EVERYTHING ON THE DISK!!!) Right mouse button on the USB HD again and select the option for format - fat32)

5) Wait.

That's it.

---

### Post by notwen on 2008-11-20
> **joelw1351 said:**
> I tried to get gparted to work, but I am at a total loss on how to do this. This is my first day on Linux and my second week on Mac so I am a novice.

Once you open GParted(you will be prompted for your pass), in the top right hard corner you'll see a drop-down box; Use this to select your USB drive.  Once you have it selected unmount it, then proceed w/ formatting it to FAT32.  Post back if you have any questions/issues.  =]

---

### Post by joelw1351 on 2008-11-20
> **notwen said:**
> Once you open GParted(you will be prompted for your pass), in the top right hard corner you'll see a drop-down box; Use this to select your USB drive.  Once you have it selected unmount it, then proceed w/ formatting it to FAT32.  Post back if you have any questions/issues.  =]

Maybe I should have explained further, I downloaded Gparted but not sure how to install it.

---

### Post by joelw1351 on 2008-11-20
> **joelw1351 said:**
> Maybe I should have explained further, I downloaded Gparted but not sure how to install it.

here is the problem, look at terminal window. Look at line third from bottom.

joelw135@joelw135-desktop:~$ cd /home/joelw135/gparted-0.3.9
joelw135@joelw135-desktop:~/gparted-0.3.9$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
joelw135@joelw135-desktop:~/gparted-0.3.9$

---

### Post by taurus on 2008-11-20
You should reread my #2 post over again.

---

### Post by notwen on 2008-11-20
Yes, install gparted taurus' method using apt-get or even look for it in Synaptic or Add/Remove.  Unless you are very comfortable w/ compiling source then avoid it at all costs.  I only compile packages when I must, I normally find an alternative if I think compiling source is my only option.  =]

---

### Post by joelw1351 on 2008-11-20
> **notwen said:**
> Yes, install gparted taurus' method using apt-get or even look for it in Synaptic or Add/Remove.  Unless you are very comfortable w/ compiling source then avoid it at all costs.  I only compile packages when I must, I normally find an alternative if I think compiling source is my only option.  =]

According to Synaptic it is now installed, but I can't find how to load it. I'm sorry but I am lost.

---

### Post by taurus on 2008-11-20
Look in System -> Administration.

---

### Post by joelw1351 on 2008-11-20
> **taurus said:**
> Look in System -> Administration.

Thanks, I found it and it is scanning for drives. Now I hope it works.

---

### Post by joelw1351 on 2008-11-20
> **joelw1351 said:**
> Thanks, I found it and it is scanning for drives. Now I hope it works.

Thank you all! Got it working, now to get my sound working. I have the X-Fi and the driver from Creative has to be compiled, so I am searching for one that is ready to install.

---

