---
title: "Samsung ecogreen f2 (HD154UI)"
date: 2010-01-20
forum: Hardware
---

### Post by baltazar3 on 2010-01-20
I have an old computer that only supports SATA 1 (150). I bought a samsung 1.5 tb drive that uses SATA 2, thinking that I could just set a jumper switch to make it work with SATA 1. However I now spoke to samsung and they say that you have to use a windows program to change the SATA type. Is there any way to make this work with linux (Ubuntu)? 

If not what 1.5 tb discs would you recommend for linux? I heard that Seagate have problems with some of their discs at the moment, and also western digital have introduced some new technologies that dosent play well with linux.

---

### Post by zwaardmeester on 2010-01-27
You say that you have already bought it, so tell us, what happens when you connect the drive and start the pc? Make sure the Sata-controller is enabled in the BIOS. 
I also have an old mobo with only sata-150 and the exactly the same disk, which is working properly. I did have to modify anything.

---

### Post by xc1024 on 2010-06-27
Hi. I'm thinking of whether to buy this HDD. Anyone can describe the compatibility with Linux and reliability?

---

### Post by cascade9 on 2010-06-27
> **baltazar3 said:**
> I have an old computer that only supports SATA 1 (150). I bought a samsung 1.5 tb drive that uses SATA 2, thinking that I could just set a jumper switch to make it work with SATA 1. However I now spoke to samsung and they say that you have to use a windows program to change the SATA type. Is there any way to make this work with linux (Ubuntu)? 

Quite often, SATAII discs will work with SATAI controllers. Kind of lame that Samsung hasnt put a jumper to go from SATAII to SATAI on the HDD, but I think it should work fine without the setting. Thats _think_, not know. 

> **baltazar3 said:**
> If not what 1.5 tb discs would you recommend for linux? I heard that Seagate have problems with some of their discs at the moment, and also western digital have introduced some new technologies that dosent play well with linux.

Seagate has never really caught the others once things moved to SATA. The new versions of the WD 'green power' drives (EARS) have 'advanced format',. which is that instead of using 512b sectors, they have 4k sectors that pretend to be 512b sectors to the OS. Things are getting better, but dont buy a WD EARS disc unless you want to have to play with partitions....a lot.  

Does it have to be 1.5TB? WD caviar black drives are fast, reliable and dont have the issues of the green power drives. There is also a jumper to convert them from SATAII to SATAI- 

[http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=2534&p_created=&p_cats=185&p_cv=1.185&p_pv=2.279&p_prods=227%2C279#jumper](http://wdc.custhelp.com/cgi-bin/wdc.cfg/php/enduser/std_adp.php?p_faqid=2534&p_created=&p_cats=185&p_cv=1.185&p_pv=2.279&p_prods=227%2C279#jumper)

But they are only avaible in 500GB, 640GB, 750GB, 1TB and 2TB models. 

Just be sure to get the SATAII model, not the SATAIII model..the SATAIII models only have a jumper to set the interface back to SATAII, not SATAI. I _think_ (again! LOL) that it should be fine, but better safe than sorry.....

---

