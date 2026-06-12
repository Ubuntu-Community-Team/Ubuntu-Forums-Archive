---
title: "[SOLVED] Stuck in low graphic with Nvidia 6200 AGP"
date: 2008-12-09
forum: Hardware
---

### Post by abujenin on 2008-12-09
After I upgraded to Ubuntu 8.10, I used Nvidia 177.80 bin file, it worked but without acceleration. Then tryed upgrading to 177.82, failed and got low graphic mode. Now I uninstalled it (ran .bin --uninstall), tried .80 again, but neither work. 
The recommended Hardware Drivers didn't work with me from the start. Now I'm stuck in low graphic mode.

> ~$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

It's an AGP card.

On start up, I get the following errors:
> (EE) Failed to load module "type1" (module does not exist, 0)
(EE) NVIDIA: Failed to load the NVIDIA kernel module! 

But running
> ~$ grep 'EE' /var/log/Xorg.0.log
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

I thought they should give same result!!!

Something must be missing since it work the first time.

---

### Post by phidia on 2008-12-09
I believe that recent nvidia drivers no longer support 6 series cards.
You could try to use envy to install the driver or see if synaptic has the legacy driver available.

---

### Post by abujenin on 2008-12-09
> **phidia said:**
> I believe that recent nvidia drivers no longer support 6 series cards.

6200 is still on the Supported Products List on this 177.82 [page]("http://www.nvidia.com/object/linux_display_ia32_177.82.html") or on this 2nd [page]("http://us.download.nvidia.com/XFree86/Linux-x86/177.82/README/appendix-a.html").

EnvyNG didn't work either; and was recommending the 173 driver.

---

### Post by abujenin on 2008-12-12
I followed [these steps]("http://desiato.tinyplanet.ca/~lsorense/debian/debian-nvidia-dri-howto.html") and got my screen resolution back; but as before without 3D acceleration. 
And also I have to repeat step 4 whenever updating the kernel or the drivers.

---

### Post by C0p3rn1c on 2008-12-23
I have the same problem on my fully updated ubuntu intrepid system (2.6.27-9 generic)
Error message: [http://share.ovi.com/media/c0p3rn1c.public/c0p3rn1c.10108](http://share.ovi.com/media/c0p3rn1c.public/c0p3rn1c.10108)

---

