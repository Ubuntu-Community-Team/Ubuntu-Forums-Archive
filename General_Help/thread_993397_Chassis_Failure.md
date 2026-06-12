---
title: "Chassis Failure"
date: 2008-11-25
forum: General Help
---

### Post by hyburn on 2008-11-25
at boot my computer gave me a message of Chassis Failure. then to press F2. I see that this can cause disk failure. how do I fix this problem?

---

### Post by linux_tech on 2008-11-25
What is the system configuration?

what is output of 
```
dmesg
```
```
lsmod
```
```
lspci
```
```
sudo lshw | less
```
```
sudo dmidecode
```

---

