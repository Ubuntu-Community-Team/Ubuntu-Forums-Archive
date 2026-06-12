---
title: "I couldn't enable Driver of my GF6200 Graphic Card in &quot;Restricted Drivers Manager&quot;"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by henrytran on 2008-01-03
Dear everybody !

Please help me to solve my problem.

When I checked to enable the driver of my graphic card in "Restricted Drivers Manager".

Some windows appeared to install something. It had finished after some minutes, it is really successful, no error box appeared.

After that, I tried to look at the "Restricted Driver Manager" tool again. I discovered that the driver of my graphic card already didn't enable !!! It was still un-check, It was still unable, so, I could re-check it again in oder to re-install the driver again. Then, It was still unabe. I already tried to restart my PC but could not ...

please help me.

My PC information: 
AGP Geforce 6200 128MB. 
CPU: Sempron 2800+ socket 754
Mainboard: MSI (I didn't remember mainboard's model, because I am in my company now, I can't check it)
Ubuntu 7.10.

Thank you very much.

---

### Post by Yellow Pasque on 2008-01-03
Let's see what it's really doing. Terminal time!
```
sudo apt-get install nvidia-glx
```

---

### Post by tommcd on 2008-01-03
He wants the nvidia-glx-new driver. I have the same card and that is what I use.
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)
After installing the driver run "sudo nvidia-xconfig" to enable the driver.

---

### Post by henrytran on 2008-01-03
Thanks your answer. I will try when I go home to night. I am still in my company

more information. I couldn't increase more refresh rate to 75Hz, I couldn't drop-down this option, so I always must chose 60Hz, It is bad for my eyes. 

I could change resolution 1024x768 to another, but COULD NOT change refrest rate.

---

### Post by tommcd on 2008-01-03
> **henrytran said:**
> Thanks your answer. I will try when I go home to night. I am still in my company

more information. I couldn't increase more refresh rate to 75Hz, I couldn't drop-down this option, so I always must chose 60Hz, It is bad for my eyes. 

I could change resolution 1024x768 to another, but COULD NOT change refrest rate.
To change the refresh rate you need to edit you xorg.conf. First, back it up for safety: 
"sudo cp /etc/X11/xorg.con /etc/X11/xorg.conf.bak". Remember linux is cAse seNsiTive, so that is a capital X.
Then run "gksudo gedit /etc/X11/xorg.conf". Scroll down to the Section "Monitor" part. Edit the HorizSync and VertRefresh numbers to match the specs of your monitor, which you can (hopefully!!) find in your monitor's manual or the manufacturer's website. For reference, mine looks like this:
```


Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "The monitor"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "UseEdidFreqs" "1"
    Option         "ReducedBlanking"
EndSection

```

---

