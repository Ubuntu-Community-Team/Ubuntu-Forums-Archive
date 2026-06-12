---
title: "Issue with hard drive size."
date: 2008-08-22
forum: General Help
---

### Post by JMV290 on 2008-08-22
[IMG]http://i37.tinypic.com/vipdu1.png[/IMG]
That is a screencap from GParted.  

32GB is a bit small--and completely wrong.  The hard drive that I installed is 160GB so I don't know why the install of Ubuntu only used 32GB and won't allow me to expand it anymore.

I haven't done much and have gotten a few errors so I'm willing to completely format my harddrive and hope that solves the issue.  However, a solution for this issue might be useful for future reference.

What do I do?

---

### Post by Shazaam on 2008-08-23
Odd. Run this in terminal (Applications>Accessories>Terminal) and post the output here.....
```
sudo fdisk -lu
```
(lowercase LU)
This code will print out your drive info.

---

### Post by Patb on 2008-08-23
Odd (2). ;)

You might also try partitioning with the [Gparted Live CD]("http://gparted.sourceforge.net/livecd.php"). 

Cheers, Pat

---

### Post by JMV290 on 2008-08-23
jmv@ubuntu-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 33.8 GB, 33820284928 bytes
255 heads, 63 sectors/track, 4111 cylinders, total 66055244 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x077c0a96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    63794114    31897026   83  Linux
/dev/sda2        63794115    66043214     1124550    5  Extended
/dev/sda5        63794178    66043214     1124518+  82  Linux swap / Solaris
jmv@ubuntu-desktop:~$

---

### Post by Shazaam on 2008-08-23
Hmm. What is the make and model number of the drive? And the motherboard?

---

### Post by carolinason on 2008-08-23
yep and if it's an ide drive make sure it's jumper-ed correctly

---

### Post by JMV290 on 2008-08-23
> **Shazaam said:**
> Hmm. What is the make and model number of the drive? And the motherboard?

Maxtor DiamondMax20
The label says 160GB PATA.  

I'm not sure what the motherboard is but I can check..  It is the one that came installed on an HP Pavilion a1203w.
Here:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00497067&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&cc=us&docname=c00497067&dlc=en)
> Motherboard
Manufacturer: Asus
Motherboard Name: K8S-LA
HP/Compaq motherboard name: Salmon-GL6E

The original hard drive failed so I had to replace it, but other than that every other component is the one that came on the computer.   Would any of the other components have a problem(it seems as if I have a graphics problem too)?

---

### Post by Shazaam on 2008-08-23
It might be a bios or jumper setting issue. I found a few links for you....
[http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/stx_alp.php?p_search_text=capacity&p_new_search=1](http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/stx_alp.php?p_search_text=capacity&p_new_search=1)
[http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/std_adp.php?p_faqid=1062&p_created=1023140877&p_sid=e-pme2cj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjMzLDIzMyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9Y2FwYWNpdHk*&p_li=&p_topview=1](http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/std_adp.php?p_faqid=1062&p_created=1023140877&p_sid=e-pme2cj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjMzLDIzMyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9Y2FwYWNpdHk*&p_li=&p_topview=1)
[http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/std_adp.php?p_faqid=1299&p_created=1037211985&p_sid=e-pme2cj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjMzLDIzMyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9Y2FwYWNpdHk*&p_li=&p_topview=1](http://seagate.custhelp.com/cgi-bin/seagate.cfg/php/enduser/std_adp.php?p_faqid=1299&p_created=1037211985&p_sid=e-pme2cj&p_accessibility=&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjMzLDIzMyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfcGFnZT0xJnBfc2VhcmNoX3RleHQ9Y2FwYWNpdHk*&p_li=&p_topview=1)

---

### Post by JMV290 on 2008-09-11
[IMG]http://img.photobucket.com/albums/v479/jmv290/IMG_0071.jpg[/IMG][IMG]http://img.photobucket.com/albums/v479/jmv290/IMG_0072.jpg[/IMG]

Pictures of the BIOS, and yes the jumper settings are set to master.

I'm making sure there isn't something I can do before having to buy a PCI ATA Controller Card

---

