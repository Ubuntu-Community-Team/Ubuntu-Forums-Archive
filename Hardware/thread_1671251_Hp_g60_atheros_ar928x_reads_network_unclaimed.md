---
title: "Hp g60 atheros ar928x reads network unclaimed"
date: 2011-01-19
forum: Hardware
---

### Post by alexnows on 2011-01-19
ive done everything on the forums followed every ndiswrapper installation procedure entered in everyones codes who have fixed there problem followed steps to the t but nothing i need more assistance someone please help me id like wireless to work

---

### Post by Zeevix on 2011-06-11
tell me about it, i have had my post up here for a while and no one has given me any reply!!!
 
i'm also facing the same issue and done the same things also...FOLLOWED EVERY POST.

---

### Post by jboyette on 2011-08-19
I had a similar issue, and found that rfkill had blocked the Atheros wireless card.   In terminal, try this command:

sudo rfkill unblock all

---

### Post by walt.smith1960 on 2011-08-19
What Ubuntu/Linux version? USB or PCI?  I'm using an Atheros USB device that works OOB in 11.04.  Earlier kernels I used an installer found on Sourceforge.  

[http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/](http://sourceforge.net/projects/ath9k-htc/files/ath9k_htc-installer/)

I've only used this on a USB device, not sure what would happen if you were to run it on a PCI device.

---

