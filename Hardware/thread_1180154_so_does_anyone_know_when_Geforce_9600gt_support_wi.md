---
title: "so does anyone know when Geforce 9600gt support will be added to the linux-restric..."
date: 2009-06-06
forum: Hardware
---

### Post by SIGTERMer on 2009-06-06
So does anyone know when Geforce 9600gt support will be added to the linux-restricted-modules package? i'm running x86_64 8.04 by the way.

thanks in advance.

---

### Post by surfed on 2009-06-06
> **SIGTERMer said:**
> So does anyone know when Geforce 9600gt support will be added to the linux-restricted-modules package? i'm running x86_64 8.04 by the way.

thanks in advance.


Activate your nvidia card in System/Hardware Drivers Menu. 9600gt is fully supported.

---

### Post by SIGTERMer on 2009-06-06
> **surfed said:**
> Activate your nvidia card in System/Hardware Drivers Menu. 9600gt is fully supported.

that's the first thing i tried but the card isn't listed although it shows up with "lspci" :( 
and yes i updated my system

thanks for the quick reply anyways :)

---

### Post by cariboo on 2009-06-06
Your graphics adapter is supported by the nvidia-glx-173 driver, it is an older chipset, so the newer drivers don't support it.

---

### Post by surfed on 2009-06-06
> **cariboo907 said:**
> Your graphics adapter is supported by the nvidia-glx-173 driver, it is an older chipset, so the newer drivers don't support it.

Sorry Wrong. I am using glx 180 and my 9600gt works great.

---

### Post by SIGTERMer on 2009-06-07
thanks for the info. extremely appreciated.
but i need to ask, even though i'm using an open source driver, why didn't the restricted driver manager display the graphics card?  I mean it should have been displayed, shouldn’t it?

---

