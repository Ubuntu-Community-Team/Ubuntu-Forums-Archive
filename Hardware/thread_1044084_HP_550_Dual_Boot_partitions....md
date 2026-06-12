---
title: "HP 550 Dual Boot partitions..."
date: 2009-01-19
forum: Hardware
---

### Post by WannabeFantasma on 2009-01-19
1st of all I'm kinda new (have this account for a while didn't use it) 

I bought a HP 550(notebook)
want to dual boot vista(pre installed) with ubuntu
1)can i delete the ubuntu partition and melt it back into "C" ? (IF i ever want vista only again?)

Will there allways be this many options when you dual boot?( [http://apcmag.com/images/apcapc/howto/Dualboot_-_XP___Ubuntu__XP_first__images/ubuntu04.jpg](http://apcmag.com/images/apcapc/howto/Dualboot_-_XP___Ubuntu__XP_first__images/ubuntu04.jpg) )

or is there a way to only put 8.10 / Vista


*-*Is there someone who has that laptop? and can give me some feedback?*-* 

 also ; i'm scared that i'm gonna have that "Laptop Hardrive Killer Bug" 

and is there a garanteed way to overcome it if i have it?

thanks to all who are willing to help

---

### Post by renzokuken on 2009-01-19
yes you can 'melt' the partition back into C:/

you could use either gparted on a live CD or the Windows own partition manager. in the days of XP, to remove grub so it boots straight into windows all you needed to do was boot from a Windows Boot Disk (either the XP CD itself or a boot disk from bootdisk.com) and run

```
fixmbr
```

not sure how that works with Vista and its bootloader though

in fact, look here 
[http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html](http://quainttech.blogspot.com/2007/05/how-to-remove-ubuntu-from-vista-dual.html)
and here
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/254009228831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/254009228831)

---

### Post by WannabeFantasma on 2009-01-19
ah ok thanks :D 

i found that site allready but... there isn't a recovery disk with my laptop :( (waiting for reply from store whether i can burn them somehow)

and some person (on youtube) said you had to put the grub into ubuntu partition or something, if i do that will the grub loader be gone when i delete ubuntu partition? (or will there just be that error 17?)

will i have those options like that screenshot? (like alot of kernels or don't know what those are) 
or just Ubuntu / vista when i need to pick OS (like in wubi i think)
(hoping for just Ubuntu/Vista)

---

