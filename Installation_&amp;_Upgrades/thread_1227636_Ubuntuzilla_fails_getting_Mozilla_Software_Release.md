---
title: "Ubuntuzilla fails getting Mozilla Software Releases PK"
date: 2009-07-30
forum: Installation &amp; Upgrades
---

### Post by joelgsf on 2009-07-30
(SOLVED) I'm trying to install Firefox 3.51 with ubuntuzilla. All goes well until it tries to get "Mozilla Software Releases" Public Key, from several possible repositories, unsuccessfully, giving up after some tries. It's strange because I can access the repositories with Firefox and find several keys for Mozilla Software Releases, and even could install one using Seahorse. I'm not shure if the right one. Ubuntuzilla seems not to recognize it when I try to install again, repeating all the process (skiping the downloads already done) with the same ending.
I did all this as root.
What may be going wrong?
TIA

---

### Post by nanotube on 2009-07-31
Hi

please post the complete session output here.

also, note that you shouldn't run ubuntuzilla as root, run it with regular user. it will ask you for sudo password when it's needed.

---

### Post by joelgsf on 2009-07-31
Thank you nanotube. Prloblem solved! I had first to clean up all previous installations done as root, and, after that ... all went smoothly till having Firefox 5.1 installed. The real problem was using root to install. It was foreseeable, but I didn't saw it, only when I tried to install as myself and got an error saying that ubuntuzilla couldn't write to the Firefox directories under my home directory - they were all owned by root! Now it is all fine.

---

### Post by nanotube on 2009-08-02
sounds good :)

---

