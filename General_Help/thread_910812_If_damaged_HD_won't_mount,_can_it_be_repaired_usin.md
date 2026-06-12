---
title: "If damaged HD won't mount, can it be repaired using dd_rhelp?"
date: 2008-09-04
forum: General Help
---

### Post by ddixonr on 2008-09-04
HD from a Dell running Windows stopped booting. A pbr loading descriptor #2 error appears, which I know refers to the Windows partition. Why Dell insists on pre-loading utility and recovery partitions that cause more problems is beyond me. Anyway, tried the Windows recovery console using FIXBOOT and FIXMBR commands. No luck.

Now I turned to the greatest OS ever, Ubuntu. I found the dd_rhelp program, but I believe the HD needs to at least be able to mount in order to start the process. Anybody know about this?

Thanks.

---

### Post by sefs on 2009-07-09
I think it does not need to be mounted. In fact it is better IF IT IS NOT mounted at all.  

If you do a 
```

sudo fdisk -l

```

and you see it listed then thats all you need to go to town on it.

---

### Post by lavinog on 2009-07-09
> **sefs said:**
> I think it does not need to be mounted. In fact it is better IF IT IS NOT mounted at all.  

If you do a 
```

sudo fdisk -l

```

and you see it listed then thats all you need to go to town on it.

It uses dd which works with the raw device (don't mount)

To OP: Is this fixed yet?

---

