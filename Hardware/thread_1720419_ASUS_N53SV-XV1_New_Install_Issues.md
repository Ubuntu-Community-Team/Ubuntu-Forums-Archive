---
title: "ASUS N53SV-XV1 New Install Issues"
date: 2011-04-03
forum: Hardware
---

### Post by yahooking on 2011-04-03
I just got this laptop a week or so ago. Overall this device is very good however i cannot get Ubuntu to run on this device with Intel CPU/GPU. This model has the Sandy Brigde CPU with integrated graphics and Nvidia GT540M. I understand that i cannot use the NVIDI gpu. So i installed ubuntu 10.10 from usb drive. I then booted into the system perfectly and attempted the acpi_call method to disable NVIDIA power. However i have an idictor on this laptop that tells me when i am using the nvidia vs the intel. 
Intel LED= BLUE
Nvidia LED=White
After attempting to disable the nvidia using acpi_call the light remains white meaning the gpu is never turned off. When i installed acpi_call and i ran the test.sh it did show me a working string which i added to rc.local and rebuilt initrramfs as well as blacklisted all nvidia modules. 
I see acpi_call loaded in lsmod after boot however the indicator is still showing i am running nvidia gpu.

Can anyone help me with this. I hate running winblows....

Also ASUS mediakeys do not work its not a big deal but is there anyone who has hot them working on this device.

I i manage to disble nvidia how do i get 3d acceleration on the Intel HD gpu ? Is there a package or do i install from source.
Hope to have this running soon any tips would be great guys. :)

---

### Post by love2learn on 2011-10-09
I know this post might be old but it is the first post with Ubuntu and n53sv-xv1 on google so I figured a [solved] on this title would be great for the forum.

I have just ordered the n53sv-xv1 and plan on installing ubuntu as well. I know on my old HP laptop that there was an LED that stayed on no mater what I did to the hardware it was meant to light up for. Is this the same case for the n53sv-xv1? or are you actually seeing activity from the nvidia card?

I will be able to hash out more with you when I receive my laptop on wednesday. If you have found a fix please list it here.

Thanks,
L2L

---

