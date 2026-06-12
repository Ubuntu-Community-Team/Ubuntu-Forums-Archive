---
title: "Printer (Oki B4100)"
date: 2006-07-29
forum: Hardware &amp; Laptops
---

### Post by i386DX on 2006-07-29
I'm running Ubuntu 6.06. I have an Oki B4100 printer. There are no drivers for it on the Oki-site, but I can use the drivers of the B4200 printer. This works but I have the following problem: The print on the paper is moved a bit up, so at the top of the paper there a piece missing, and at the bottom there an extra white border.

Like this:
```

what it should be:            
 ----
|A  |
|B  |  <-paper
|C  | 
 ----

what it is
 ----
|B  |
|C  |
|   |
 ----

```

Is it possible to solve this? Maybe by changing something in the *.ppd-file? (this is the original ppd: [http://belgium.oki.com/binaryData/6683/ok4200pcl.ppd.gz](http://belgium.oki.com/binaryData/6683/ok4200pcl.ppd.gz))

---

### Post by rikard on 2007-03-23
> **i386DX said:**
> I'm running Ubuntu 6.06. I have an Oki B4100 printer. There are no drivers for it on the Oki-site, but I can use the drivers of the B4200 printer. This works but I have the following problem: The print on the paper is moved a bit up, so at the top of the paper there a piece missing, and at the bottom there an extra white border.

Like this:
```

what it should be:            
 ----
|A  |
|B  |  <-paper
|C  | 
 ----

what it is
 ----
|B  |
|C  |
|   |
 ----

```

Is it possible to solve this? Maybe by changing something in the *.ppd-file? (this is the original ppd: [http://belgium.oki.com/binaryData/6683/ok4200pcl.ppd.gz](http://belgium.oki.com/binaryData/6683/ok4200pcl.ppd.gz))


I am glad to tell you that i found the solution to this problem. I tried the same driver that you used and I also got some problems with the printing, The "test page" didn't look centered. So the solution for your problem is to download and install this driver instead, and it works just fine for the OKI B4100, [http://openprinting.org/ppd-o-matic.cgi?driver=ljet4&printer=HP-LaserJet_1100&show=0](http://openprinting.org/ppd-o-matic.cgi?driver=ljet4&printer=HP-LaserJet_1100&show=0) 
I know that this is a long time since you first wrote this but I'm putting this link out as a "thank you". Your post made me get hope. I also which that this will be useful for others out there trying to print with the OKI B4100 on the Linux OS. I tried this driver running "xubuntu 6.10 alternate".

Sincerely,
Rikard

---

### Post by Cleaner on 2007-10-31
For the record, I had the same problems (prints out from OpenOffice too far at the top) with the B4200 driver although I actually own a B4200. Using the alternative driver as suggested by rikard solved the problem for me as well. Weird, but it is like that :-)

Hope that's going to help someone

Flo

---

