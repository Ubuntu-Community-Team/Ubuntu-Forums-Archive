---
title: "Intel graphics drivers vs. Ubuntu repository drivers"
date: 2014-09-13
forum: Hardware
---

### Post by Stormlord on 2014-09-13
Hi,
Can anyone tell me what the differences between Intel graphics drivers and Ubuntu repository drivers are.  Is there any reason why someone should replace the distro driver with the one offered by Intel?

Thanks!  :)

---

### Post by grahammechanical on 2014-09-13
The difference is the same no matter if it is Intel, AMD/ATI or Nvidia. The web sites contain the latest video drivers from that particular company. They will even offer beta versions of the latest drivers.

Stability is a main aim of the Ubuntu developers. So, they do not upgrade our systems with what is the latest from the makers of graphic adapters to avoid the possibility of breaking our systems. I can think of four reasons why someone would upgrade to a graphic driver offered by a maker's web site.

1) in the mistaken belief that latest = greatest.
2) in the hope that a newer version will fix problems that were present in the previous version or be more compliant with newer hardware than the previous version.
3) to be a tester of the drivers and to report bugs. Someone has to do it. Or we all become testers.
4) impatience.

Ubuntu has a six months release schedule and each release needs to be stable. It is with these six monthly releases that Ubuntu moves on to newer kernels and video drivers. The Long Term Support (LTS) releases get what are called a point release about every six months or so and it is then that the LTS version gets an upgrade to the Hardware Enablement Stack that was put into the six monthly release of Ubuntu. In this way a Ubuntu LTS release keeps up to date with the work being done to keep Linux compliant with newer hardware.

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)

Some would say, if it ain't broke - don't fix it. That is good advice but if we want we have this

[http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6](http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6)

and it will get us this

[http://www.omgubuntu.co.uk/2014/07/intel-graphics-stack-2014-q2-update](http://www.omgubuntu.co.uk/2014/07/intel-graphics-stack-2014-q2-update)

Regards.

---

### Post by Stormlord on 2014-09-13
> **grahammechanical said:**
> The difference is the same no matter if it is Intel, AMD/ATI or Nvidia. The web sites contain the latest video drivers from that particular company. They will even offer beta versions of the latest drivers.

Stability is a main aim of the Ubuntu developers. So, they do not upgrade our systems with what is the latest from the makers of graphic adapters to avoid the possibility of breaking our systems. I can think of four reasons why someone would upgrade to a graphic driver offered by a maker's web site.

1) in the mistaken belief that latest = greatest.
2) in the hope that a newer version will fix problems that were present in the previous version or be more compliant with newer hardware than the previous version.
3) to be a tester of the drivers and to report bugs. Someone has to do it. Or we all become testers.
4) impatience.

Ubuntu has a six months release schedule and each release needs to be stable. It is with these six monthly releases that Ubuntu moves on to newer kernels and video drivers. The Long Term Support (LTS) releases get what are called a point release about every six months or so and it is then that the LTS version gets an upgrade to the Hardware Enablement Stack that was put into the six monthly release of Ubuntu. In this way a Ubuntu LTS release keeps up to date with the work being done to keep Linux compliant with newer hardware.

[https://wiki.ubuntu.com/Kernel/Support](https://wiki.ubuntu.com/Kernel/Support)

Some would say, if it ain't broke - don't fix it. That is good advice but if we want we have this

[http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6](http://www.omgubuntu.co.uk/2014/08/intel-graphics-installer-linux-updated-1-0-6)

and it will get us this

[http://www.omgubuntu.co.uk/2014/07/intel-graphics-stack-2014-q2-update](http://www.omgubuntu.co.uk/2014/07/intel-graphics-stack-2014-q2-update)

Regards.


Thanks for your response.  By saying "a reason", I meant whether there was an actual driver difference between the two of them, since they are both open source and the distro driver was also updated 3-4 days ago.  :)

---

