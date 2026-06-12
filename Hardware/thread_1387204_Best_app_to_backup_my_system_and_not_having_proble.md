---
title: "Best app to backup my system and not having problems with the new hardware"
date: 2010-01-21
forum: Hardware
---

### Post by tirengarfio on 2010-01-21
Hi,

im trying to clone my ubuntu system installed in a laptop in case the laptop crashes.

But, first of all: when i try to restore the system in a new PC, could be incompatibilities because the hardware of the broken laptop and the new laptop is different?

I dont mind if i have to buy another laptop with the same processor type (i386, etc), but, for example, the type of the RAM could be cause of problems?

So what would be the best to backup my system and not having problems with the new hardware?

cp?, rsync?, dd?, clonezilla?, partimage?

Regards

Javi

---

### Post by CharlesA on 2010-01-21
clonezilla would work.

---

### Post by The Judderman on 2010-01-21
It depends on what you want to do. cp and rsync only backup data. Clonezilla creates a image of your partition, which you can then restore. I don't know anything about partimage.

The main thing about drivers etc, is that if you had to compile drivers for your broken laptop, and you don't need the same drivers on the new one, then you will have to compile differently. However, you might find that the drivers work out of the box on the other laptop so you won't need to do any further compiling.

As you understand, there will be problems if you are running a 64bit system, as this will cause problems on a 32bit system.

Hope this helps!?

The Judderman

---

