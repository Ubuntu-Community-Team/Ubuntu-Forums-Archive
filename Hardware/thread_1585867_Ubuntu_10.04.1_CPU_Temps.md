---
title: "Ubuntu 10.04.1 CPU Temps"
date: 2010-10-01
forum: Hardware
---

### Post by jon890 on 2010-10-01
Problem caused by new kernel 2.6.32.25, lm-sensors workaround:
add the following to the k8temp section of /etc/sensors3.conf
chip "k8temp-*"

    compute temp1 @+21, @-21
    compute temp2 @+21, @-21
    compute temp3 @+21, @-21
    compute temp4 @+21, @-21

Previous kernel 2.6.32.24 shows correct cpu temps without offset as above.

---

