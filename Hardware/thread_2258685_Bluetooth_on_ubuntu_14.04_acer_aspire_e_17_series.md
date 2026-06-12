---
title: "Bluetooth on ubuntu 14.04 acer aspire e 17 series"
date: 2014-12-29
forum: Hardware
---

### Post by kain184 on 2014-12-29
hello all. i am having a problem with my bluetooth. i had it connected when i installed from the 14.04 install iso. it worked fine it is a sound logic bluetooth earbuds. was working till i ran an apt-get update. after which it will no longer connect and my bluetooth device cannot find it. under rfkill it lists 1: 
phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: acer-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
hciconfig dev lists 
hci0:    Type: BR/EDR  Bus: USB
    BD Address: 30:10:B3:EE:E4:81  ACL MTU: 1022:8  SCO MTU: 183:5
    UP RUNNING PSCAN 
    RX bytes:678 acl:0 sco:0 events:49 errors:0
    TX bytes:1015 acl:0 sco:0 commands:47 errors:0
i have tried reinstalling bluetooth but to no avail can anyone help me.

---

### Post by kain184 on 2014-12-30
ok so it took some doing but i found the answer. looking around i found alot of people having an issue with the devices not accepting an invisable device so i turned on visibility and there was all my bluetooth devices i was trying to scan. i dont know if there is a way to fix the program for blue-tooth but that was the solution for mine. edit well it kind of worked. it went back to not noticing devces the next day it seems to be an intermetent problem so still needing a full solution

---

### Post by Bucky Ball on 2014-12-30
Good news. Please mark the thread as solved (see the second link in my signature) to help others. Good luck.

PS: I have also changed the title of this thread so it is more specific to the problem and the fix for future searchers and travelers. ;)

---

