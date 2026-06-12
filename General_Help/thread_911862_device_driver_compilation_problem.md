---
title: "device driver compilation problem"
date: 2008-09-06
forum: General Help
---

### Post by ksrinivas on 2008-09-06
Hi,

I am trying to compile a dynamic module in Ubuntu version2.6.24 but i am getting the following errors.

./Makefile: line 1: obj-m: command not found
./Makefile: line 3: EXTRA_CFLAGS: command not found
./Makefile: line 5: all:: command not found
./Makefile: line 6: MAKE: command not found
./Makefile: line 6: PWD: command not found
./Makefile: line 6: -C: command not found
./Makefile: line 8: clean:: command not found
./Makefile: line 9: MAKE: command not found
./Makefile: line 9: PWD: command not found
./Makefile: line 9: -C: command not found
./Makefile: line 10: RM: command not found
./Makefile: line 10: Module.markers: command not found

I have tried 
sudo apt-get update
sudo apt-get install build-essential 

but still the problem continues......

Can anybody help me in this regard.

Thanks in advance.

Regards
Srinivas

---

