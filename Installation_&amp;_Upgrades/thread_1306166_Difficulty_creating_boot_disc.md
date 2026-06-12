---
title: "Difficulty creating boot disc"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by richo9 on 2009-10-30
I'm working on a powerbook g4 running 10.5. Have downloaded the ubuntu desktop ISO. 
Have run md5 and got the correct hash (8790491bfa9d00f283ed9dd2d77b3906). 
Have gone into disc utility and burnt the ISO file onto a cd. BUT the cd isn't being treated as bootable. 
Have burnt several discs, and tried them in 2 different machines (both powerbook g4s), and CAN'T figure out why they are not being read as boot discs. Computer sees them, just not as bootable.
Holding down OPT during boot sequence, holding down C during boot sequence... Nothing. How do I make the disc with the ISO on it bootable?

---

### Post by CharlesA on 2009-10-30
Make sure that the machines are set to boot from CD. The images are already bootable, you don't need to do anything except burn them to a cd.

---

### Post by bashphoenux on 2009-10-30
yeah see if the bios is set to boot from CD !! :)

---

### Post by az on 2009-10-30
> **richo9 said:**
>  
Have gone into disc utility and burnt the ISO file onto a cd. BUT the cd isn't being treated as bootable. 

Boot up your machine as usual.  Put in one of the CDs you burned and browse it?  What do you see?

---

### Post by richo9 on 2009-10-30
Thanks CharlesA, but I'm not sure exactly what you mean. Do you know how to set the machines so they can boot from a cd? Isn't using C or OPT during startup using the firmware to choose the drive from which to boot?

---

### Post by richo9 on 2009-10-30
> **az said:**
> Boot up your machine as usual.  Put in one of the CDs you burned and browse it?  What do you see?

Hi az

7 folders

casper, dists, install, isolinux, pics, pool, preseed

and

autorun.inf, md5sum.txt, README.diskdefines, wubi.exe, ubuntu

---

### Post by CharlesA on 2009-10-30
> **richo9 said:**
> Thanks CharlesA, but I'm not sure exactly what you mean. Do you know how to set the machines so they can boot from a cd? Isn't using C or OPT during startup using the firmware to choose the drive from which to boot?

That should be the correct way, or at least it is according to the site [here.]("http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.htm") I haven't used a mac in a long time, so I am not sure.

---

### Post by richo9 on 2009-10-30
> **CharlesA said:**
> That should be the correct way, or at least it is according to the site [here.]("http://www.jacsoft.co.nz/Tech_Notes/Mac_Keys.htm") I haven't used a mac in a long time, so I am not sure.

Thanks mate. 

Yeah I'm positive I'm following the correct procedures to boot from a cd, BUT I'm even more positive that I've missed something annoyingly basic or simple in the creation of the actual disc...

I've just tried to change the startup disc in 'system preferences', and the ubuntu iso burnt disc isn't being recognised there either. 

Weird. 

But thanks for your time CharlesA.

---

### Post by richo9 on 2009-10-30
Solved. I've been trying to boot an intel-mac image. 
I need a powerpc install.
Thanks.

---

