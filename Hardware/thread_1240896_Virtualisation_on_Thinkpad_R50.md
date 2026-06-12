---
title: "Virtualisation on Thinkpad R50"
date: 2009-08-15
forum: Hardware
---

### Post by JediChen on 2009-08-15
Hi, i am using a IBM Thinkpad R50, which uses a Intel Centrino, and i checked that it does not support hardware virtualisation (via the command, egrep '(vmx|svm)' --color=always /proc/cpuinfo)

I understand that this means i cannot use KVM but does it mean that i cannot do virtualisation at all?

---

### Post by JediChen on 2009-08-15
Hmm....i found out about VirtualBox and it seems to be working just fine. Although it hogs my system real bad....

---

