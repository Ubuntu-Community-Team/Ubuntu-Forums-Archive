---
title: "Wd5000aaks"
date: 2008-03-14
forum: Hardware &amp; Laptops
---

### Post by starfox5194 on 2008-03-14
hey i have a WD5000AAKS Hard drive

When i do the command line install of gutsy gibbon it isin't detected.

and i dont think that any of those drivers on the list will work for it

---

### Post by starfox5194 on 2008-03-15
*bump*

---

### Post by dogson on 2008-03-15
I have 4 AAKS running in my box, the harddrive wont need any drivers, it should "just work" if your SATA chipset is supported by linux.

---

### Post by starfox5194 on 2008-03-16
so... this is a motherboard problem?

Is there is a way to make a bad axe 2 work

---

### Post by Yellow Pasque on 2008-03-16
Checklist
1. Do you have both SATA power and SATA data cables firmly connected?
2. Does the BIOS see the drive? 
3. Do you have any jumpers currently attached?
4. Try jumpering the disk to SATA150 compatibility mode before giving up on it. See bottom diagram here: [http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1409&p_created=1138290141&p_sid=BzTFMT-i&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjEzLDIxMyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PTUwMDBBQUtTIGp1bXBlcg**&p_li=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=1409&p_created=1138290141&p_sid=BzTFMT-i&p_accessibility=0&p_redirect=&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MjEzLDIxMyZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9c2VhcmNoX2ZubCZwX3BhZ2U9MSZwX3NlYXJjaF90ZXh0PTUwMDBBQUtTIGp1bXBlcg**&p_li=&p_topview=1)

---

### Post by starfox5194 on 2008-03-19
1. Do you have both SATA power and SATA data cables firmly connected?
2. Does the BIOS see the drive?
3. Do you have any jumpers currently attached?
4. Try jumpering the disk to SATA150 compatibility mode before giving up on it. See bottom diagram here: [http://wdc.custhelp.com/cgi-bin/wdc....i=&p_topview=1](http://wdc.custhelp.com/cgi-bin/wdc....i=&p_topview=1)

1 yes
2 yes and vista...
3 no
4 sorry... but i cant see any diagram on that page

thanks for replying

---

### Post by mikedep333 on 2008-03-19
What is your hard drive controller? I have a WD5000AAKS myself and it works fine.

You could always try hardy beta when it comes out tomorrow.

---

### Post by starfox5194 on 2008-03-19
i have a bad axe 2 mobo and its Marvell SATA controller

---

### Post by starfox5194 on 2008-03-19
Fixed it! all i had to do was disable the secondary sata controller and plug my hdd into the black sata connector!

thanks a lot for your help

---

