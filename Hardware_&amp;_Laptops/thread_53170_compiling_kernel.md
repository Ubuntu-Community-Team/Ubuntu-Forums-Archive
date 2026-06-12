---
title: "compiling kernel"
date: 2005-07-30
forum: Hardware &amp; Laptops
---

### Post by traaf on 2005-07-30
hi
I have a motherboard asus P5GD1 with IT8212 RAID controller, wich i use as standard IDE 
it seems this controller is not yet supported by ubuntu, and i have to compile and patch the kernel to have it OK

i got linux-2.6.11 kernel from kernel.org
and alan cox' patch-2.6.11-ac7

i'm newb with linux 
it the 1st time i try that

after searches on the web i tried these command lines
```

# tar zxvf /usr/src/linux-2.6.11.tar.gz
# cd /usr/src/linux-2.6.11
# cp /home/regis/patch-2.6.11-ac7.bz2 /usr/src/linux-2.6.11
# bzip2 -dc patch-2.6.11-ac7.bz2 | patch -p1
# mv /usr/src/linux-2.6.11 /usr/src/linux-2.6.11ac7
# cd /usr/src/linux-2.6.11ac7
# make xconfig
# make dep
# make clean
# make bzImage
# make oldconfig
# make all

```
but i have an error when i arrive here:
```

# make modules_install
  INSTALL arch/i386/crypto/aes-i586.ko
cp: can not copy `arch/i386/crypto/aes-i586.ko': no such file or directory
make[1]: *** [arch/i386/crypto/aes-i586.ko] Erreur 1
make: *** [_modinst_] Erreur 2

```

can someone tell me where i sucked?
thx

---

### Post by traaf on 2005-07-31
no idea?

---

### Post by luca_linux on 2005-07-31
Could you translate the error message you got in english, please?

---

### Post by traaf on 2005-07-31
done

---

### Post by luca_linux on 2005-07-31
It sounds like that module has not been compiled...maybe it's broken in that version. Try to compile again and if it doesn't work, try to download the kernel sources again and install them again.

---

