---
title: "[SOLVED] 5 versions of linux-restricted-modules - normal ?"
date: 2008-08-22
forum: General Help
---

### Post by stoneage on 2008-08-22
I have recently been browsing Synaptic after having a problem with Nvidia drivers. I think envyng installed the vesa driver instead of the most recent one for an 8800 GS(I'm currently using nvidia-glx-new).

I notice I have 5 versions of linux-restricted-modules:-

linux-restricted-modules -19-generic  2.6.24.13-19.45
			 -18-generic  2.6.24.13-18.41
			 -17-generic  2.6.24.13-17.36
			 -16-generic  2.6.24.13-16.34
			 -14-generic  2.6.24.4-14.10

Do I need them all?
Should the earlier ones have been removed and could this be why envyNG screwed up?

---

### Post by LateNiteTV on 2008-08-22
im not positive, but they may be there for backward compatibility reasons.

---

### Post by qstraza on 2008-08-22
Do you have 5 versions of kernel too?

---

### Post by colobix on 2008-08-22
If your newest update workes fine you can delete the erlier kernels by using startup manager. You really do not need 5 versions of kernel.

---

### Post by stoneage on 2008-08-22
> **qstraza said:**
> Do you have 5 versions of kernel too?


I have 5 vesions of linux-image-2.6.24-1x.xx and StartUp-Manager lists 5 options for default operating system - but it doesn't offer a way to remove anything. I thought Synaptic would be the place for that.

---

### Post by qstraza on 2008-08-22
as previous post reads, use startup manager ;)

---

### Post by stoneage on 2008-08-22
Could you perhaps indicate how? I don't see any function in StartUp Manager for removing packages. The latest kernel is default.

---

### Post by Sef on 2008-08-22
> I notice I have 5 versions of linux-restricted-modules:-

linux-restricted-modules -19-generic 2.6.24.13-19.45
-18-generic 2.6.24.13-18.41
-17-generic 2.6.24.13-17.36
-16-generic 2.6.24.13-16.34
-14-generic 2.6.24.4-14.10

That happens because you have been upgrading.  It is best to keep one older version around in case there is a problem with the most current version.

---

### Post by stoneage on 2008-08-22
Ah-ha, thank you. So that is why they are not auto removed.

It has nothing to do with the envyng problem then?

---

### Post by stoneage on 2008-08-23
O.K. I started removing some modules, restricted modules and kernel image.

Thanks for the information and advice. Should save me a couple hundred Mb.

---

