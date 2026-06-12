---
title: "Graphic card"
date: 2009-04-27
forum: Hardware
---

### Post by alimooghashang on 2009-04-27
i need to install my graphic card!
NVIDIA GeForce 8400M GS
on hp dv2680ee laptop
thanks

---

### Post by alimooghashang on 2009-04-27
when i try to install i got error

ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE       
         NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

what to do?

---

### Post by EmyrB on 2009-04-27
> **alimooghashang said:**
> i need to install my graphic card!
NVIDIA GeForce 8400M GS
on hp dv2680ee laptop
thanks

OK, first things first, are you using Ubuntu or Kubuntu?

Has a restricted driver icon appeared?

---

### Post by Cybie257 on 2009-04-27
> **alimooghashang said:**
> when i try to install i got error

ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE       
         NVIDIA DRIVER in the README available on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

what to do?

At the login screen, select options and then select terminal session/mode. This will log you into the terminal mode without the X Server. This will let you install the above as it's requesting. I haven't encountered that when I was switching video cards from ATI to nVidia, and then back to my ATI, but you should be able to get into the terminal mode by switching sessions at login.

-Cybie

EDIT: If you are already in X (Desktop), then just go to 'logout' and you can switch session from there rather than rebooting.

---

### Post by alimooghashang on 2009-04-27
> **EmyrB said:**
> OK, first things first, are you using Ubuntu or Kubuntu?


Ubunto

> **EmyrB said:**
> 

Has a restricted driver icon appeared?


which icon?
i have no icon :confused:

---

### Post by EmyrB on 2009-04-27
Usually if Ubuntu recognizes that you have a graphics card that can utilize the nVidia restricted driver a icon should pop up near the top right hand side of the screen (where the clock, volume control and network icons appear) suggesting that restricted drivers are available. If that hasn't happened, go to System > Administration > Hardware Drivers. This should tell you if you are using the restricted driver.

---

