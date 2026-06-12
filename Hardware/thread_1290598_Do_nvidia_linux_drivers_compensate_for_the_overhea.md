---
title: "Do nvidia linux drivers compensate for the overheating in hp laptops?"
date: 2009-10-13
forum: Hardware
---

### Post by iTrickU on 2009-10-13
Hi,

Do the latest nvidia drivers automatically underclock the GPU in HP laptops to prevent overheating due to the hardware defects which where discovered after shipping?

If they do not, is it possible for me to manually do it through config files?

---

### Post by Dark_Stang on 2009-10-13
Aaaand what laptops would you be talking about here? nVidia cards downclock if they start to overheat but overheating doesn't occur until around 100C.

---

### Post by falconindy on 2009-10-13
You could manually undervolt the laptop. Here's a guide:

[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

---

### Post by iTrickU on 2009-10-14
> **Dark_Stang said:**
> Aaaand what laptops would you be talking about here? nVidia cards downclock if they start to overheat but overheating doesn't occur until around 100C.

Yes, the dvxxxx's gpu can get that hot.

I have a dv9000, but it effects most of hp's laptop range, the first problem is the defective nvidia chips in them, the second is hp's poor quality cooling solution to cool them. These two issues combine to give the hp dvxxxx range a high failure rate. In responce hp increased the fan speeds and underclocked the gpu with a bios patch. For most users this just ensures that the laptop fails out of warranty since the fins in the heatsink get clogged with dust over time. The extended warranty is joke, it just covers half of the range and the newer laptops with the same chips and cooling solutions are not covered.

I can't use the extended warranty since i took mine apart and upgraded so many bits. :(

> **falconindy said:**
> You could manually undervolt the laptop. Here's a guide:

[http://ubuntuforums.org/showthread.php?t=786402](http://ubuntuforums.org/showthread.php?t=786402)

Thanks, i'll try it

---

### Post by yossell on 2009-10-14
I remember finding this page quite helpful

[http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/](http://tutanhamon.com.ua/technovodstvo/NVIDIA-UNIX-driver/)

powertop has also been helpful for keeping my computer as cool as it was under windows. 

yossell

---

### Post by Dark_Stang on 2009-10-14
> **iTrickU said:**
> Yes, the dvxxxx's gpu can get that hot.

I have a dv9000, but it effects most of hp's laptop range, the first problem is the defective nvidia chips in them, the second is hp's poor quality cooling solution to cool them. These two issues combine to give the hp dvxxxx range a high failure rate. In responce hp increased the fan speeds and underclocked the gpu with a bios patch. For most users this just ensures that the laptop fails out of warranty since the fins in the heatsink get clogged with dust over time. The extended warranty is joke, it just covers half of the range and the newer laptops with the same chips and cooling solutions are not covered.

I can't use the extended warranty since i took mine apart and upgraded so many bits. :(



Thanks, i'll try it
The newer laptops have different GPU's and different motherboards and do not have the issues. The older laptops have updated firmware available for the motherboards that helps control the heat. Oh, and clean out your heatsink.

The only HP models affected by the issue are dv2000-2400, dv6000-6400, and dv9000-9400. As you mentioned, the warranty on the motherboard for those models has been extended to 2 years.

---

### Post by iTrickU on 2009-10-14
> **Dark_Stang said:**
> The newer laptops have different GPU's and different motherboards and do not have the issues. The older laptops have updated firmware available for the motherboards that helps control the heat. Oh, and clean out your heatsink.

The only HP models affected by the issue are dv2000-2400, dv6000-6400, and dv9000-9400. As you mentioned, the warranty on the motherboard for those models has been extended to 2 years.

The dv9500 range and possibly newer also have these issues. They also have the same updates to the firmware to better cool the gpu, however they still do not have the extended warranty.

---

### Post by iTrickU on 2009-10-23
Ok i have now installed the system and i found a kde4 plasma widget with which to keep an eye on the gpu temperature

---

