---
title: "Reboot instead of shut down after suspend."
date: 2013-09-17
forum: Hardware
---

### Post by Tryfon on 2013-09-17
Hi,

I have Ubuntu 13.04 64bit installed on a Lenovo T430u and I have noticed the following weird behaviour. When shutting down the computer after having put the computer in suspend at some previous time it reboots instead of powering off. If no suspend had intervened it power offs normally. Any idea why? Am I the only one witnessing this behaviour? Could it be an Ubuntu bug?

---

### Post by luis-29-09-92 on 2013-10-03
I'm with you, i think we can solve this annonying problem, as i've commented in other sites, i guess problem is wireless conection.

---

### Post by MorrisseyJ on 2014-03-15
Tryfon: I am having the same problem on a thinkpad x131e (Intel). I have been having the problem since ubuntu 12.04

luis-29-09-92: Can you point me in the direction of your other posts containing a solution. Regarding your comments about the wireless, I was having problems with my Broadcom BCM43228 chip, as the proprietary driver was causing the system to freeze when on battery power. I changed to an intel Centrino wireless chip and that solved the problem of freezing. The reboot problem on shutdown, after suspend, persisted across the different chips. 

j

---

### Post by luis-29-09-92 on 2014-03-17
> **MorrisseyJ said:**
> Tryfon: I am having the same problem on a thinkpad x131e (Intel). I have been having the problem since ubuntu 12.04

luis-29-09-92: Can you point me in the direction of your other posts containing a solution. Regarding your comments about the wireless, I was having problems with my Broadcom BCM43228 chip, as the proprietary driver was causing the system to freeze when on battery power. I changed to an intel Centrino wireless chip and that solved the problem of freezing. The reboot problem on shutdown, after suspend, persisted across the different chips. 

j

I don't know exacly what happened, but the problem get solved when i reinstall eos (for other questions, i guess too many modifications) and install a newer kernel (3.13.5), the problem disappear, i guess only weird thing is that sometimes (i can't explain how or when) S.O. dies when i suspend, it has happened me sometimes but i don't know why.

---

### Post by MorrisseyJ on 2014-04-22
Problem is solved for me on 14.04.

j

---

### Post by luis-29-09-92 on 2014-05-01
> **MorrisseyJ said:**
> Problem is solved for me on 14.04.

j
Just like this? 
If that's well I'm impatient for eOS Isis.

---

### Post by MorrisseyJ on 2014-05-30
A recent update (last week) has broken this again for me. 

Can anyone help me work out what has caused the reversion. 

Thanks,

---

### Post by MorrisseyJ on 2014-07-22
hmm, seems that another recent update fixed this again. 

It would  be great if someone could help me identify what is breaking and fixing  this process so that i could flag it in a bug report.

---

### Post by MorrisseyJ on 2015-02-01
Problem persist in 14.10. 

It would be great if someone could help me think through this.

---

### Post by kdre on 2015-11-01
Any solutions? I am having the same problem on a Thinkpad x230.

---

