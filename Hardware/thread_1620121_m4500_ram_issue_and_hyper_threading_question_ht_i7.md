---
title: "m4500 ram issue and hyper threading question ht i7"
date: 2010-11-12
forum: Hardware
---

### Post by timc76 on 2010-11-12
have a dell M4500 i7 with 8gig of ram
system moitor shows that it has 8 cores just under 4gig of ram and just under 4gig of swap memory, how come it dosn't show the full 8 gig of ram?
also when running a application, say pitivi it only uses one of the 8 cores, now i figure it shows 8 cores due to the hyperthreading, would this mean that each core is trying to do 2 applications, so if i was to turn off hyper threading it would allow a core to concentrate on just one application, not one application and leave space for running another?
or is it possible for an application to be able to use more than one core of thread

---

### Post by cascade9 on 2010-11-13
> **timc76 said:**
> have a dell M4500 i7 with 8gig of ram
system moitor shows that it has 8 cores just under 4gig of ram and just under 4gig of swap memory, how come it dosn't show the full 8 gig of ram?

You've install 32bit and for some reasonm it hasnt given you the PAE kernel. If you get ther PAE kernel you should see all your RAM, or you could install 64bit. 

> **timc76 said:**
> also when running a application, say pitivi it only uses one of the 8 cores, now i figure it shows 8 cores due to the hyperthreading, would this mean that each core is trying to do 2 applications, so if i was to turn off hyper threading it would allow a core to concentrate on just one application, not one application and leave space for running another?
or is it possible for an application to be able to use more than one core of thread

If the application is only written to use one core, then one core is all it will use. Its more than possible for applications to use multipule cores, but it needs to be written to use them. 

Hyperthreading is pretty much a hack to let a single core run multpule threads. If you had all 8 cores with hyperthreading (OK, 4 real cores) being used at once, then turning off hypertheading might allow it to run one program faster, but then its going to run other programs slower.  

Turning off hyperthreading could make a single-core only application faster if there was only 1 core loaded, but its not going to make much impact.

---

