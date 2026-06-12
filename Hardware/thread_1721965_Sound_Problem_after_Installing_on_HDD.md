---
title: "Sound Problem after Installing on HDD"
date: 2011-04-05
forum: Hardware
---

### Post by shivkumars on 2011-04-05
Hi,
I am having PC with Intel C2D 7200 processor with Asus P5-KPL-CM motherboard, The motherboard has 2 jacks for speaker/earphone: front and rear. 
I have installed Ubuntu 10.04 recently after running everything in live-cd mode to check that all the essential features are working. 
In live-cd mode both front and rear speaker jacks are working fine but after installation to HDD sound output from front jack has stopped, the rear jack speaker output is working fine.
I am not very good with CLI but can can tweak setting files if some guidance is provided.

---

### Post by lidex on 2011-04-05
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by shivkumars on 2011-04-05
@lidex: Here is the link 
[http://www.alsa-project.org/db/?f=b75c4532c2b20ad0567c7cef3a9d3dd52cc1d00d](http://www.alsa-project.org/db/?f=b75c4532c2b20ad0567c7cef3a9d3dd52cc1d00d)

PS: I am using Ubuntu 10.10 & not 10.04 as stated in my first post.

---

