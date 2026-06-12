---
title: "ubantu and cdma x1 modem"
date: 2010-01-21
forum: Hardware
---

### Post by ashrafhumax on 2010-01-21
hello every one
thank you for your support that help me to depend on ubantu as main operation system for my notebook
i wonder if i can instal cdma usb modem to ubantu 9.4 
how to ???
 this is the picture of the modem
[IMG]http://wb7.itrademarket.com/pdimage/77/1589477_1589477_zte_mg880.gif[/IMG]

i found a folder caled linux in the operating program after installing in windows and atext show these steps bellow 
is it helpful???
1, Load driver-zte evdo

1),Copy ztemt.ko from release's relevant directory to certain directory (take /home/lm/ztemt for example);
    e.g., you need install Fedora core 6:
       cp release/Fedora/FC6/ztemt.ko  /home/lm/ztemt/

2),cp us-test/wvdial-conf /etc/

3),Load driver
     insmod /home/lm/ztemt/ztemt.ko

4),Insert network card;

5),Run wvdial and to dial successfully (need root authorization). Normally, the following prompts will appear:
    --> pid of pppd: 2450
    --> Using interface ppp0
    --> Authentication (CHAP) started
    --> Authentication (CHAP) successful
    --> local  IP address 220.205.100.27
    --> remote IP address 220.192.56.19
    --> primary   DNS address 220.192.32.103
    --> secondary DNS address 220.192.0.130
    --> Script /etc/ppp/ip-up run successful
    --> Default route Ok.
    --> Nameserver (DNS) Ok.
    --> Connected... Press Ctrl-C to disconnect

6,FAQ
1),require software support:
     udev
     wvdial

2),It might not be able to resolve domain name after running wvdial to dial successfully. 
In this case, you need manually add primary DNS address and secondary DNS address to /etc/resolv.conf.

thank you alot
ashraf

---

### Post by mörgæs on 2010-01-21
Well, it looks like you have the instructions right in front of you :-) 

Maybe you have to add **sudo** in front of some of the commands.

---

