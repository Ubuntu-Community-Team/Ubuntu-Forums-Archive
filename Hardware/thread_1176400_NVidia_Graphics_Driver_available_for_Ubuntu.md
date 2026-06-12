---
title: "NVidia Graphics Driver available for Ubuntu ?"
date: 2009-06-02
forum: Hardware
---

### Post by rahul_shilps on 2009-06-02
I have HP Pavilion dv9601AU laptop. My laptop has nVidia Graphics Driver with AMD Turion 64 bit processor. When i installed Ubuntu 8.04 on laptop the screen resolution by default is 800*600 and there is no chance for increasing resolution. I think its taking default Graphics driver not the one i have i.e nVidia Graphics Driver.

Is nVidia Graphics Driver available for Ubuntu 8.04?
I like to see great resolution because low resolution doesn't look good.

---

### Post by MichaelSammels on 2009-06-02
Yes, try installing this:

```
sudo apt-get install nvidia-settings
```
```
sudo nvidia-settings
```

---

### Post by rahul_shilps on 2009-07-11
> **MichaelSammels said:**
> Yes, try installing this:

```
sudo apt-get install nvidia-settings
``````
sudo nvidia-settings
```


--------------

Hi Michael,

I did as you said. But it installed NVIDIA X Server. Now what to do?

When i try to open NVIDIA X Server then it shows me a message (may be an error)

******************** Message ***********************************

You do not appear to be using NVIDIA X Driver.
Please edit your X Configuration file (just run 'nvidia-xconfig' as root) and restart the X Server

****************************************************************

what i am suppose to do?

:guitar:

---

### Post by rahul_shilps on 2009-07-22
I have done as you suggested.

It actually installed NVidia X Server. And i don't know what to do with it. Nothing is working even after i tried to chang some settings in Nvidia Z Server.

Please help me. I want see my screen with more good resolution which is not happening at this time.

Have a good day ahead.

---

### Post by runesvend on 2009-07-22
Have you tried letting Ubuntu pick the correct proprietary driver by using the dialog "Hardware Drivers" located under "System -> Administration"?
Alternatively, try following the instructions here: [http://www.nvidia.com/object/linux_display_ia32_185.18.14.html](http://www.nvidia.com/object/linux_display_ia32_185.18.14.html)
You might not be able to use the Jaunty version of Ubuntu, because it uses a newer version of the X.Org server (used for displaying graphics), which might not be supported by the nVidia graphics drivers. I'm not sure if this is the case, but it could be.

---

