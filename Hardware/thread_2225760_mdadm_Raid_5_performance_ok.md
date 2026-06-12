---
title: "mdadm Raid 5 performance ok?"
date: 2014-05-23
forum: Hardware
---

### Post by susi-loma on 2014-05-23
Hi.

I´m not new in build Raid arrays, but now I am using an SAS Controller and want to know if the performance is in normal range. Currently my system is still for testing, so no data will be lost. Here are the hardware details:
 
Intel CoreI7 2600K
Gigabyte Board with 8 GB RAM
1x 256 GB SSD
2x 500 GB HDD (SATA)
1x 1TB HDD (SATA)
Adapted 1405 SAS Controller
 
I installed ubuntu 14.04 on the SSD and and create a raid 5 with the three HDD. I create a partition of 500 GB and labeled it to Linux raid on all three HDDs. I changed the speed_limit_max and speed_limit_min to 500000. I set with the blockdev command the “set readahead” parameter to 4069 of the HDDs and to 32768 to the md device.
 
First I tested the performance of the single HDD. With the dd command I will get a I/O rate around 90 mb/s, the 1 TG drive get around 100 mb/s. After that I have done the test with the md device. The i/o rate is in a range from 180mb/s to 150 mb/s. Still use only dd to get the values. To get an overview of the performance, I connect the 3 HDDs to the on board SATA controller and the performance decrease to 80 – 90 mb/s.
 
I read here in the board and it looks like some boards use a SATA multiplexer to get more ports. I don´t know if it is the correct name, but more than one SATA HDDs use the same line to the controller. So the performance will be slow down if both are used at the same time.
 
A lot of info and only a short question. Is the performance of the raid 5 (3 drives) with the adaptec controller in a good range?

Thanks

---

### Post by susi-loma on 2014-05-25
Hi. Please let me know why you are not able to give me an answer. Do you need some more informations?

Cheers
Susi

---

