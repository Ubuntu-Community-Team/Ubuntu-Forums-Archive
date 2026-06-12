---
title: "intel HD graphics driver not working"
date: 2013-03-21
forum: Hardware
---

### Post by snowyowls on 2013-03-21
[COLOR=#000000]I have a thinkpad E430c with the nVidia [/COLOR][COLOR=#000000]610M card.

The intel graphics in mainboard works very well at very begining in 12.04 LTS
but it doesn't work last Wednesday. 
so i try to install the bumblebee and nvidia driver

Now, when i run
```
[/COLOR]optirun glxspheres[COLOR=#000000]
```
and
```
[/COLOR]optirun nvidia-settings -c :8[COLOR=#000000]
```
it works very well
but when i run the command without optirun
```
[/COLOR]glxspheres[COLOR=#000000]
```
it dosen't work
```
[/COLOR]Polygons in scene: 62464ERROR (593): Could not obtain RGB visual with requested properties
[COLOR=#000000]
```

then i cat the [/COLOR]/var/log/Xorg.0.log[COLOR=#000000] and find that
```
[/COLOR][    30.634] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)[COLOR=#000000]
```


and the output of 
```
[/COLOR]lspci -nnk | grep -iA2 vga[COLOR=#000000]
```

is 

 ```
[/COLOR]00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)	Subsystem: Lenovo Device [17aa:5001]
	Kernel driver in use: i915
--

01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1058] (rev ff)[COLOR=#000000]
```

what shell i do now?

thanks a lot![/COLOR]

---

### Post by Yellow Pasque on 2013-03-21
You need to remove all of the nvidia and bumblebee stuff. Once you have the intel card working right, then you can install bumblebee.

---

