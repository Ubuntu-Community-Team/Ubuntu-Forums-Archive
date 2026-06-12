---
title: "SATA drive on ASRock 939S56-M motherboard"
date: 2005-10-25
forum: Hardware &amp; Laptops
---

### Post by Bastaard on 2005-10-25
Hey guys,

I'm a linux n00b, but I got tired of Windows and wanted to try something new. After reading alot about different linux distributions I decided to install Kubuntu 5.04. I can't get it installed though because it can't find my harddrive. I thought maybe Kubuntu 5.10 would make a difference but it's all the same. The motherboard I'm using is the ASRock 939S56-M and the harddrive I'm using is the Samsung SP1213C (SpinPoint P80 120GB).

I read [here]("http://www.ocworkbench.com/ocwbcgi/ultimatebb.cgi?/topic/30/4783/12.html") that I'm not the only one with these kind of problems, and that Linux kernel 2.6.14-r2 might solve the trouble. Kubuntu 5.10 is based on 2.6.12 though (correct me if I'm wrong) so I wondered how long it will take for a (K)ubuntu release to include this or a newer kernel, and if it takes long, if there is any way to install Kb5.10 with the 2.6.15-r2 kernel. Apart from that, is there any other way of getting my SATA drive detected in the Kb5.10 install?

Thanks for the help!

---

### Post by Bastaard on 2005-10-27
Can noone help me out?

---

### Post by Mongopicho on 2005-11-09
Hi,

I dont know if it will work in your specific mobo, but "michaeln" in this forum
solved this problem, setting PATA/SATA interfaces as "enhanced mode" on BIOS.

Best regards.

---

### Post by Mayfairy on 2005-11-09
I'm having similar problems. I just downloaded the newest Ubuntu 64bit release and everything goes fine until it's time to partition my hard drive. It offers only manual method because it can't find my HD. 
My motherboard is Asrock 939Dual-Sata2 and the hard drive in question is Samsung P80SD 160Gt Sata II NCQ.

Is there any chance to make Ubuntu recognize my drive? If not then I guess I gotta try another distribution or wait (for how long?) for newer kernel release.

---

### Post by daffy_ on 2005-11-17
I guess you would be OK with SuSE 10.0 or FC4. I have similar problems, and everything works with SuSE10. (I have reports from others that FC4 is ok as well.)

My guess is that your controller is not recognized by the installer (although the drivers most likely are present). If you know how to specify a driver during install, you might be OK. I don't know how to do this. I would appreciate it if someone who knows could enlighten me :)

---

