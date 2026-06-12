---
title: "The problem of network card"
date: 2007-06-17
forum: Hardware &amp; Laptops
---

### Post by 545112202 on 2007-06-17
Hi,I have a problem,I use ubuntu7.04-GNOME,dell latitude csx ht500,
eveytime my box wakes up form suspended,it can't connect the internet with NETGEAR FA410 card 10/100 mbps PCMCIA,but the introdution lights have't went out,
and the problem appears the same after I draw off the card and then insert it ,
so I have to reboot the computer and it works normally,
who can tell me what is the problem?
thanks advanced !:)

---

### Post by mikesignguy on 2007-06-17
i have the same problem  

but you don't need to reboot the computer to get the card to wake up

terminal:  sudo /etc/init.d/networking restart


someone else may have some insight as to why this happens ...

---

### Post by 545112202 on 2007-11-03
yes ,the order:sudo /ect/init.d/networking restart 
can work in 7.04,but not wrok 7.10 which i install today well,i can't surf the internet after my 7.10 waked up......please help me ~~!:confused::(

---

### Post by 545112202 on 2007-11-03
yes ,the order:sudo /ect/init.d/networking restart 
can work in 7.04,but not wrok 7.10 which i install today well,i can't surf the internet after my 7.10 waked up......please help me ~~!:confused::(i don't want to reboot my computer for it ...

---

### Post by 545112202 on 2007-11-04
i am very sorry i am worry,the order is ok in 7.10:)

---

