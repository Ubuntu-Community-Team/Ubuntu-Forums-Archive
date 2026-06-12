---
title: "Can't write bluray disks"
date: 2014-12-22
forum: Hardware
---

### Post by nelson777 on 2014-12-22
I'm trying to write my first Bluray on Ubuntu 14.10 since I  bought my ASUS SBW-06D2X-U external USB unit. What happens is that it  get exessively slow (0.2-0.3x) and it crashes when it reaches around  1Gb. k3b software buffer goes immediately to 100% when the writting  starts and the device buffer oscilates between 21-29% until crashing.
  I found some people saying it may be a dma problem but I read other  messages saying that DMA doesn't work on USB drives. And also couldn't  find any procedure on how to activate DMA. Tried also Silicon-Empire and  Brasero but it won't even start to write. K3b has all the programs it  needs including cdrtools as seen in K3b configurations.  I try to write  several folders with about 37GB of data, and try to create the image and  write it. Also tried writting the image and burn it with growisofs, and  got the same result.
  I'm using 50Gb bluray medias and my notebook is a Asus Vostro 355,  I7, 8gb. It has a 120Gb ssd for the root partition and a 1TB HDD where  the files that I want to write are saved. I have set K3b to save the  image in the HDD.
  Any help appreciated. Thanks

---

### Post by nelson777 on 2014-12-22
Question is on the above post. Thanks.

---

### Post by QIII on 2014-12-22
Threads merged.  Please do not start multiple threads on the same topic in different areas of the Forums.  It dilutes the community's efforts to provide support and causes confusion.

Thanks.

---

### Post by nelson777 on 2014-12-22
Ok.. but now how can I delete the repeated post ? I got no option for it.

---

### Post by MartyBuntu on 2014-12-22
The only thing that has worked perfectly for my BluRay disk burning is Nero Linux.

---

### Post by scdbackup on 2014-12-23
> it get exessively slow (0.2-0.3x) [...] the device buffer oscilates between 21-29%  This is probably due to Defect Management which check-reads immediately after writing. I assume the medium is branded as capable of 4x speed. In this case, the low speed indicates poor results with check-reading.  > until crashing. with growisofs [...] got the same result.  What error messages did growisofs issue in the end ? There must be some lines with a frown at the start. Like:  ```
:-[ WRITE@LBA=... failed with SK=.../ASC=.../ACQ=...: ...
```  The Numbers behind SK, ASC, ASCQ tell the drive's complaint. Poor compatibility of drive and medium would possibly cause ```
3 0C 02 WRITE ERROR  AUTO-REALLOCATION FAILED
```  50 GB media are still somewhat exotic. Try whether you get better results with 25 GB  media.   [br].[/br]   (Be aware that there will be a growisofs bug at the end  of a successful burn run. It can be avoided if you format  the medium explicitely before letting growisofs write to it:    dvd+rw-format /dev/sr0 )

---

