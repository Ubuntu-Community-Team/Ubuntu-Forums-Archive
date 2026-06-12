---
title: "Error wiping device"
date: 2018-04-04
forum: Hardware
---

### Post by ivanquijano on 2018-04-04
Hello, i have a USB Drive 
i am trying to format 
logn time ago i download and safe a folder of a Padi video, it lock my USB, now i am trying to  unblocked
and thats he messege i recive

Error wiping device: Command-line `wipefs -a "/dev/sdb1"' exited with non-zero exit status 1: wipefs: error: /dev/sdb1: la prueba de la inicialización ha fallado: Sistema de archivos de solo lectura
 (udisks-error-quark, 0)

please advise i  would like to format the usd - drive

Ubuntu 16.04 tls
4 GB ram
intel core quad 2.4
400 GB

---

### Post by TheFu on 2018-04-06
gparted
fdisk
parted
dban
sudo dd if=/dev/zero of=/dev/sdb1 bs=1M 

lots of options, assume the flash drive/media hasn't gone bad.

---

