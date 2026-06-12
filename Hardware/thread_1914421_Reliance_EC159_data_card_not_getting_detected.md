---
title: "Reliance EC159 data card not getting detected"
date: 2012-01-24
forum: Hardware
---

### Post by bramalingam81 on 2012-01-24
Can someone help me to connect my reliance EC159 data card ?

lsusb :


Bus 002 Device 007: ID 12d1:1505 Huawei Technologies Co., Ltd. 
Bus 002 Device 003: ID 192f:0416 Avago Technologies, Pte. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 05c8:0403 Cheng Uei Precision Industry Co., Ltd (Foxlink) 
Bus 001 Device 004: ID 138a:0007 DigitalPersona, Inc 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



 dmesg | grep -e "modem" -e "tty" 
[    0.000000] console [tty0] enabled


I believe modem is not getting detected. 

Please help me out ! 

Thanks
Balaji

---

