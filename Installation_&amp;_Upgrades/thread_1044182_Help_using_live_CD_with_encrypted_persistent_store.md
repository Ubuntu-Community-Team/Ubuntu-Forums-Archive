---
title: "Help using live CD with encrypted persistent store"
date: 2009-01-19
forum: Installation &amp; Upgrades
---

### Post by djbloc on 2009-01-19
I would like to use an encrypted persistent storage with a live CD/USB. My research so far has led to the following.

Booting a live CD and using usb-creator copies all the files and creates an ext3 based partition using a loopback file named 'casper-rw' in the root directory of the USB.

I can see (from extracting the initrd.gz bundle) that the persistent file is normally mounted in scripts\casper in the setup_unionfs function. This works as expected.

I would now like to replace the 'casper-rw' file with an equivalent luks based encrypted ext3 filesystem.

It would be great if I could get some advice on how to implement this. My intention is to produce a mini-howto if successful.

Thanks

---

### Post by djbloc on 2009-01-25
Any ideas? Am I going in the wrong direction potentially changing a script in the initrd.gx file?

How does ubuntu automatically load encrypted partitions from the /etc/crypttab file?

---

### Post by Mountaingod on 2009-02-04
I too would like to know this. I basically want an flash-USB Ubuntu install, but encrypted.

---

