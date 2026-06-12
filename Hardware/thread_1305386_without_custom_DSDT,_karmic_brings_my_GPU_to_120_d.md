---
title: "without custom DSDT, karmic brings my GPU to 120 degrees!"
date: 2009-10-29
forum: Hardware
---

### Post by krantix on 2009-10-29
As the kernel option to load a custom DSDT is not present anymore in Karmic, my GPU on a toshiba p100 goes as high as 120 degrees. The custom DSDT always fixed the problem in the past (toshiba couldn't care less of changing their buggy bios), but now I'm left with unfriendly options like compiling my own kernel?!?!?!

](*,)](*,)

---

### Post by mobrien118 on 2009-12-01
> **krantix said:**
> but now I'm left with unfriendly options like compiling my own kernel?!?!?!

I couldn't agree with you more. I just discovered that the reason that temperature monitors in THRM don't display properly on 4 of my 5 systems, as well as some overheating situation I experience on 2 of my systems are caused by the buggy DSDT. Alas, I went through the process of debugging all of them only to find that Karmic doesn't compile them into the init fs anymore. Surely there must be some way to work around what the kernel team did to disable this...no?

---

