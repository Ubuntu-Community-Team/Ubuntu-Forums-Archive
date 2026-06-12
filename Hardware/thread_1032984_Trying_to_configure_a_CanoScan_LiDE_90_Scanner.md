---
title: "Trying to configure a CanoScan LiDE 90 Scanner"
date: 2009-01-06
forum: Hardware
---

### Post by Angry_Mushi on 2009-01-06
I'm trying to configure my scanner but, apparently there aren't drivers for Linux, I've been trying to at least get it working through wine and it gives me this Error:```
mauricio@mauricio-desktop:~$ wine lide90vst1300ea24.exe
fixme:setupapi:SetupDiGetINFClassA ".\\CNQ2412.INF" 0x33d254 0x33c664 32 (nil)
fixme:setupapi:SetupDiGetINFClassA ".\\CNQ2412.INF" 0x33cfbc 0x33c68c 32 (nil)

```

Someone told me about "Generic" drivers, what are they, how do I know it will work with my scanner and where do I get one?

any other kind of help would be appreciated

---

### Post by fb314 on 2009-03-06
> **Angry_Mushi said:**
> I'm trying to configure my scanner but, apparently there aren't drivers for Linux, I've been trying to at least get it working through wine and it gives me this Error:```
mauricio@mauricio-desktop:~$ wine lide90vst1300ea24.exe
fixme:setupapi:SetupDiGetINFClassA ".\\CNQ2412.INF" 0x33d254 0x33c664 32 (nil)
fixme:setupapi:SetupDiGetINFClassA ".\\CNQ2412.INF" 0x33cfbc 0x33c68c 32 (nil)

```

Someone told me about "Generic" drivers, what are they, how do I know it will work with my scanner and where do I get one?

any other kind of help would be appreciated

see there:
[http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)
this scanner is not (yet ?) supported by SANE project.

---

### Post by silentb on 2009-03-08
yes, unfortunately, there is currently no support for the lide 90.

---

