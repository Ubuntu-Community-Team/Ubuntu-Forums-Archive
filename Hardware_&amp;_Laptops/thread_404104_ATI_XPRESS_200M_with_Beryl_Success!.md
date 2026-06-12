---
title: "ATI XPRESS 200M with Beryl Success!"
date: 2007-04-08
forum: Hardware &amp; Laptops
---

### Post by TusharG on 2007-04-08
Hi all,
  This is something is really puzzling me and I'd love to configure my Ubuntu with same settings. Out of enthu I booted a live DVD of "sabayon" Linux and it configured my ATI XPRESS 200M display along with Beryl on fly!!!!
  We all are sharing information on ubuntu forms where we have discussed many times that ATI XPRESS 200M doesnt support 3D acceleration. Infact this information is also present on ATI/AMD webs site. 
  How on earth the Sabayon linux has configured Beryl without a problem on my display card? All though i noticed it didnot configured AIGLX. Anyone can throw light on how its working without a problem. I also notice that the kernel used in 2.6.19 while ATI Display driver version is 8.28
 I really want to configure my Ubuntu with beryl. I have always managed to configure my Ubuntu with ATI display drivers but never managed with beryl. I recently used ATI's 8.35 drivers which also fixed blank screen issue.
  I'm using HP Pavilion dv8305us noteboot with 1GB RAM and 128 MB Video memory.

---

### Post by adam.tropics on 2007-04-08
ATI still doesn't support aiglx, and so we are dependent on xgl for beryl etc. That said it all works fine here....same card as you. I [followed this guide]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_XGL"), so have a read.

---

### Post by TusharG on 2007-04-09
Thanks Adam for your prompt reply. I'll follow the link.

---

### Post by randombeatnik on 2007-04-23
XGL with this laptop and 3d card runs really slow. I was messing with beryl and it wasn't even worth it to be honest. Hopefully ATI will get their act together soon and support AIGLX and we won't have to be left in the dark.

---

