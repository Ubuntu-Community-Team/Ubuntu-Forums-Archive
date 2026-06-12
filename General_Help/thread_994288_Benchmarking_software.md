---
title: "Benchmarking software"
date: 2008-11-26
forum: General Help
---

### Post by allanlewis on 2008-11-26
Can anyone recommend a package I can use to benchmark my PC? I'm mainly looking to get a measurement of the hard drive and optical drive speeds, but CPU and RAM performance would be useful too.

---

### Post by Martijn van Es on 2008-11-26
hdparm has an option to show the throughput of your drives.

hdparm -t /dev/hda

You probably need to run it as root

---

### Post by allanlewis on 2008-11-27
Thanks. Will that work for my DVD drive too?

---

### Post by puurokauha on 2008-11-27
[http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/) try this one

---

### Post by virx on 2008-11-27
For CPU burn-in tests I have used Super-Pi
[ftp://pi.super-computing.org/Linux/super_pi.tar.gz](ftp://pi.super-computing.org/Linux/super_pi.tar.gz)

---

