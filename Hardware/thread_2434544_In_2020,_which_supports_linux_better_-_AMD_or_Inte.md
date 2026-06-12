---
title: "In 2020, which supports linux better - AMD or Intel?"
date: 2020-01-07
forum: Hardware
---

### Post by greg2lapa on 2020-01-07
I'm looking to purchase an upcoming Lenovo Thinkpad laptop (Intel Ice Lake architecture versus AMD Ryzen 4000 mobile CPU). With respect to support for Linux drivers, which hardware is going to give me the most trouble-free experience?

---

### Post by QIII on 2020-01-07
Both are well-supported, with this caveat:  Brand new technology is always potentially problematic until the kernel is updated.  

I have machines with both and have no problems at all with either.

---

### Post by Tadaen_Sylvermane on 2020-01-07
Both do equally well. As said, the newest hardware on either side will be trouble though.

---

### Post by greg2lapa on 2020-01-09
In years past, there was agreement that Intel gave better linux support and driver support (searching the web bears this out in years past). I was wondering if that has changed at all. Sounds like AMD has caught up and there really isn't an Intel advantage on linux anymore. I noticed on the Lenovo laptops, they are even using Intel wifi cards on their AMD laptops.

---

### Post by CatKiller on 2020-01-09
> **greg2lapa said:**
> In years past, there was agreement that Intel gave better linux support and driver support (searching the web bears this out in years past). I was wondering if that has changed at all. Sounds like AMD has caught up and there really isn't an Intel advantage on linux anymore.  

For processors there's never been any difference. 

For *graphics* they've both had their rough spots. When Intel were using PowerVR, support was pretty terrible. Once they started using their own they switched to a completely open source model of development, and it's been fine. When AMD were Ati they had a proprietary driver - fglrx - like Nvidia do, except that unlike Nvidia's driver it was generally terrible. At that time the reverse engineered Ati driver wasn't great either. Once AMD bought them they ditched the proprietary driver entirely and put all their driver resources into the open source driver, which is now fine. 

The only difference - other than the performance of the hardware - between Intel and AMD graphics now is that Intel have massively more resources so that they can afford to get support for their hardware included prior to the release of that hardware and AMD can't, so support for new hardware has to trickle down. 

> I noticed on the Lenovo laptops, they are even using Intel wifi cards on their AMD laptops.

Intel wifi is the best supported under Linux. AMD don't make wifi chips - those have to come from Intel, or Realtek, or Qualcomm, or whoever.

---

### Post by TheFu on 2020-01-09
I'll disagree, especially on laptops using only intel GPUs.  Intel has better GPU support, better battery management, quicker driver updates and just fewer issues overall.  When buying a laptop, which I did about a year ago, I specifically choose an Intel system.  I'd just built an amazing Ryzen server/destop machine.  Both have different purposes.  For a laptop, intel.  For a desktop that needs as many cores as possible, AMD.

On desktops, the IOMMU support for my Ryzen isn't perfect even today, while on Intel it works well. This is mostly important for virtual machine users for HW passthru. Nobody else would likely care.  It will become perfect, but if I were counting on it, I'd have to jump through some hoops to get it.  But the price/performance has changed in favor of Ryzen about the last 3 yrs, except for gamers where fewer, faster, cores matters more. It is a great time to be buying CPUs.  Intel has dropped prices on very capable desktop CPUs to be almost competitive with AMD's pricing. I always want more cores and lower prices since I don't game at all, so I'd pick AMD Ryzen today for a desktop.  

For the last few years, there have been more Intel CPU security issues than there have been for AMD CPUs.  Both have had serious security issues and each has/is producing mitgations, but those mitigations seem to always impact performance 10-40%.  I haven't looked for performance comparisons for specific CPUs.  I figure, I'm not a target, use layered security, don't have multiple tenants on the same physical hardware, almost nobody has physical access, and don't have untrusted users with ssh access, so most of the issues don't directly impact the situation here.  Regardless, it is something to consider.

For wifi, intel is easily the easiest to deal with, by far.

For GPUs, intel on-board is the easiest. Then AMD addon GPUs, followed by nVidia.  I have nVidia for my new Ryzen machine.  Kinda wish I would have researched the AMD offers first.  For my needs, the intel/intel iGPU is sufficient.

---

### Post by QIII on 2020-01-09
I agree about laptops.  Intel/Intel just makes things easier.  Intel/AMD and Intel/NVIDIA are a pain and the OEMs have not made hybrid systems easy for Linux users.

---

