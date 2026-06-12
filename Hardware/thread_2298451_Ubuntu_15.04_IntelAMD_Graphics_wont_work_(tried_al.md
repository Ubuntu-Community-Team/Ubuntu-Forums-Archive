---
title: "Ubuntu 15.04 Intel/AMD Graphics wont work (tried all methods)"
date: 2015-10-11
forum: Hardware
---

### Post by stefanoskikristijan on 2015-10-11
Hello guys,
I have a problem configuring my AMD Radeon HD8570 card alongside Intel HD4000. I tried al methods installing fglrx using terminal, manually installing drivers etc etc, none of them work. I always run into ow graphics mod after i restart. So now i am with the standard X.ORG Driver and if someone could help me to manage how to switch to my AMD card, since every time i try to use VGA Swticheroo i get acess denied. Can anyone help me manage how to use my AMD radeon card since it is detected but i cant manage to make it run properly. Btw i have Lenovo G500 laptop with Intel i3 processor 2.4ghz, 6gb RAM, and 1TB disk(if any of this info is useful)
Here is what i get:
```
User1~$ sudo grep -i switcheroo /boot/config-*[sudo] password for User1: 


/boot/config-3.19.0-15-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.19.0-28-generic:CONFIG_VGA_SWITCHEROO=y
/boot/config-3.19.0-30-generic:CONFIG_VGA_SWITCHEROO=y


User1:~$ sudo cat /sys/kernel/debug/vgaswitcheroo/switch
0:IGD:+:Pwr:0000:00:02.0
1:DIS: :DynOff:0000:01:00.0


User1:~$ sudo echo ON > /sys/kernel/debug/vgaswitcheroo/switch


bash: /sys/kernel/debug/vgaswitcheroo/switch: Permission denied


```

---

