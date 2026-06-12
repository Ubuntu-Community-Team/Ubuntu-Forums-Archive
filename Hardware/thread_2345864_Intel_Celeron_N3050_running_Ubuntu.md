---
title: "Intel Celeron N3050 running Ubuntu?"
date: 2016-12-08
forum: Hardware
---

### Post by freshie on 2016-12-08
Hello: 

I've been thinking about buying a fanless PC and install Ubuntu on it, in particular one with a Intel Celeron N3050 processsor, which runs at 1.6 Ghz, like an ECS mini ITX BSWI-D2-N3050, but in the Ubuntu system requirements page, Ubuntu 16.04.1 LTS, states that it must be  2 GHz dual core processor or better. Does that means that a 1.6 Ghz Celeron N3050 system can't run Ubuntu 16.04.1 LTS? Or it would be slow. Could it drive 1920 x 1200 monitor with good image quality?
 
I could consider Lubuntu, but it is for really low end systems, and it may not be up to running everyday apps. 

Thanks for any comments.

---

### Post by ajgreeny on 2016-12-08
> **freshie said:**
> Hello: 

I've been thinking about buying a fanless PC and install Ubuntu on it, in particular one with a Intel Celeron N3050 processsor, which runs at 1.6 Ghz, like an ECS mini ITX BSWI-D2-N3050, but in the Ubuntu system requirements page, Ubuntu 16.04.1 LTS, states that it must be  2 GHz dual core processor or better. Does that means that a 1.6 Ghz Celeron N3050 system can't run Ubuntu 16.04.1 LTS? Or it would be slow. Could it drive 1920 x 1200 monitor with good image quality?
 
I could consider Lubuntu, but it is for really low end systems, and it may not be up to running everyday apps. 

Thanks for any comments.
Lubuntu will run any application or utility that Ubuntu will run, and it is not solely for low end systems; many users prefer it as it uses fewer of their machine resources and leaves more for the running applications rather than OS itself.

On that hardware I would probably try Xubuntu first, and if that ran too slowly, then try Lubuntu.

---

### Post by Yellow Pasque on 2016-12-09
Just looking at clock speed can be deceptive. I doubt the N3050 would struggle with the Unity desktop. Also, keep in mind that the Celeron N3050 does turbo boost to 2.16 GHz, so it technically meets the requirement.
The N3050 is used in some certified systems: [https://certification.ubuntu.com/certification/catalog/component/dmi/4103/dmi:Intel(R)Celeron(R)CPUN3050@1.60GHz/](https://certification.ubuntu.com/certification/catalog/component/dmi/4103/dmi:Intel(R)Celeron(R)CPUN3050@1.60GHz/)
Phoronix had Unity (Ubuntu 15.04) running on an Intel NUC with the N3050 and didn't mention any issues: [http://www.phoronix.com/scan.php?page=news_item&px=Intel-Braswell-Fedora-Ubuntu](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Braswell-Fedora-Ubuntu)

Personally, I'd wait for an Apollo Lake system (e.g. with Celeron N3350), but that's me. I like the latest and greatest and I run Debian unstable. I'm not an LTS kind of guy...

---

### Post by freshie on 2016-12-09
Thanks for the comments. 

Xubuntu looks good, it's worth a try, may work better on low end systems. Ubuntu though is my first option. 

The certified pre-install for Ubuntu status for the Dell PCs listed on the web page  you mention is a valuable reference and show me that Ubuntu should work fine on my N3050 system.

---

