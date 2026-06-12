---
title: "SSD and overprovisioning: unformatted or not-full partition?"
date: 2013-09-09
forum: Hardware
---

### Post by mike0112358 on 2013-09-09
Hello,

Just setup 13.04 on my new laptop with a 256gb solid state drive.

I get that overprovisioning is a good thing.  But there are different advices on the web about whether it should consist of

1) unformatted space on the disk, that is not in any partition
2) each partition having extra space that is not used.

I already did the default install, which left no unformatted space, and have copied my files over already.
So I'd rather not redo the whole process if it's not necessary.  Is the fact that my partitiion is nowhere-near full just as good?  I did a single partition for / this time, and it is (and will continue to be) something like 50%+ empty.

NB: I got the 256gb size because it was faster not because I really need the space.

---

### Post by bernard2 on 2013-09-10
I think you might have missed the point of SSD overprovisioning ... it's done behind the scenes, you don't even see it.  See, for example, [http://www.edn.com/design/systems-design/4404566/Understanding-SSD-over-provisioning](http://www.edn.com/design/systems-design/4404566/Understanding-SSD-over-provisioning)

---

### Post by mike0112358 on 2013-09-10
I get the reasons for it.

I'm not sure if 'buntu automatically overprovisions (it didn't say  anything either way).  Does anyone know? I chose the "format whole disk and install 'buntu" option during the install.

The "properties" of the drive list it as having  235.5GB of space... does that mean that the remaining 20.5GB has been  set aside?  Were it a hard drive I would assume that was formatting  loss, perhaps SSDs do not lose space to formatting?

Perhaps my underlying question is not 'buntu-spcific: does unused formatted space count as overprovionsing?
For instance [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) suggests that during the installation it is important to *not* partition the whole disk (so not behind the scenes at all), and [http://blog.lsi.com/tag/over-provisioning/](http://blog.lsi.com/tag/over-provisioning/) suggests that leaving free space on the drive is equivalent (so my half-full drive is great no matter what I do).

---

