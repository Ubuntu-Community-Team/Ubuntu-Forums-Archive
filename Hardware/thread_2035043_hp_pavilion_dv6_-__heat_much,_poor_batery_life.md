---
title: "hp pavilion dv6 -  heat much, poor batery life"
date: 2012-07-29
forum: Hardware
---

### Post by bhoopal on 2012-07-29
hi everyone. i just freshly installed ubuntu 12.04 64bit on my hp pavilion dv6 3075ei laptop. it has core i5 M450 , ati radeon HD 5650. i dual boot it with win7. my previous atempts to get switchable graphics have failed. has anyone been able to do it sucessfully, please post the solution. the laptop heats a lot, fan always running fast(even at no load). in win7, no such heating, nor loud fan noise... thanks in advanced. the threads i found stated their solution was not working for ati radeon 5xxx ... also it was intel hd 3000. i think mine is intel hd 2000 , as core i5 M450 is not 2nd gen. i did not install the restricted drivers.

i also wanted to know if turbo boost is activated by default?


intel core i5 M450
4gb ddr3 ram
500gb hhd , half for win7
ati radeon hd 5650
finger print reader ( no driver yet )


thanks in advanced:)

---

### Post by NikTh on 2012-07-29
Hi , 
please give little more info . 

Open a terminal and paste this command ```
lspci -nnk | grep -iA2 vga
``` 

**Put the results inside [CODE] tags , by highlighting the text and click # symbol on top of message pane. **

Thanks

---

### Post by TenPlus1 on 2012-07-29
[http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/](http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/)

---

### Post by bhoopal on 2012-07-30
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
	Subsystem: Hewlett-Packard Company Device [103c:144a]
	Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Madison [Radeon HD 5000M Series] [1002:68c1]
	Subsystem: Hewlett-Packard Company Device [103c:144a]
	Kernel driver in use: radeon
```

---

### Post by bhoopal on 2012-07-30
should I wait or try what is in Tenplus1's link?

---

### Post by NikTh on 2012-07-30
Hi , 
try these commands and tell us if temperature went down. (wait 30 secs to see the results)
```
sudo su 
echo low >  /sys/class/drm/card0/device/power_profile
exit
```

---

### Post by bhoopal on 2012-07-30
i dont have real values of temp, but i think it is cooler, and fan speed decreased a bit,not a big change though. did the codes turn off the dedicated gpu?
thanks by the way

---

### Post by NikTh on 2012-07-30
> **bhoopal said:**
> i dont have real values of temp, but i think it is cooler, and fan speed decreased a bit,not a big change though. did the codes turn off the dedicated gpu?
thanks by the way

Don't you have lm-sensors installed ?
Try to install and watch the temperature.
```
sudo apt-get install lm-sensors 
sudo sensors-detect 
sudo apt-get install psensor 
sudo reboot
```last command will reboot your pc , and then you must have a program (startup open) called psesnor and you can see the temperature values.

I saw you have radeon open source driver enabled (for ATI). 
This code i gave you (with echo low) passes a low value in the code of radeon driver. 
It is good when you have high temp values. 
This code its not valid if you had fglrx (closed source) driver. 
This code is temporally , if satisfy you , we must make it permanent. 

For the Hybrid Graphics problem i cannot help you. Sorry. 
Some say that fglrx (additional driver) fix this problem with hybrid , but I cannot confirm that. 
If you want to give it a try , install fglrx , and see if something fixed. 

Thanks

---

### Post by bhoopal on 2012-08-01
> **NikTh said:**
> Hi , 
try these commands and tell us if temperature went down. (wait 30 secs to see the results)
```
sudo su 
echo low >  /sys/class/drm/card0/device/power_profile
exit
```


there was a temp rise of about 5-10 degree Celsius at no load, after trying the lines of codes and restarting. can i undo this code? i think this code provoked the  os to use the ati over the intel hd. i would like to switch off the ati, and use only the intel hd!i wont do any graphic intensive computing. thanks for answering!:)

---

### Post by bhoopal on 2012-08-01
> **TenPlus1 said:**
> [http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/](http://usernamepending.wordpress.com/2011/11/02/getting-back-some-battery-life-in-ubuntu-11-10-by-disabling-discrete-graphics/)

i tried the codes in the post.. the temp is about 55  no load.. its fine.. how can i check if the ati is really disabled?

---

### Post by NikTh on 2012-08-01
> **bhoopal said:**
> there was a temp rise of about 5-10 degree  Celsius at no load, after trying the lines of codes and restarting. can i  undo this code? i think this code provoked the  os to use the ati over  the intel hd. i would like to switch off the ati, and use only the intel  hd!i wont do any graphic intensive computing. thanks for answering!:smile:
> **NikTh said:**
> 
This code i gave you (with echo low) passes a low value in the code of radeon driver. 
It is good when you have high temp values. 
_**This code is temporally**_ , if satisfy you , we must make it permanent. 

Hi , 
do not fear that ,code I gave you, will harm your system. You must know that ALL codes I give here (and generally) are first tested by me. :) 

To make the code permanent you must pass it to a script. So code now (you rebooted) its no longer applies. 

If you want to see what card you are using (I assume AMD) run this command
```
 /usr/lib/nux/unity support test -p 
``` 

If you want to have the ability to disable or enable Intel instead Amd , I think you must install fglrx (additional driver for AMD). 

If you don't care about effects etc , then login from ubuntu-2d (Unity 2d , no compiz present) . I am almost certain you will see lower temperature either you use amd or intel.

Thanks

---

### Post by bhoopal on 2012-08-01
> **NikTh said:**
> Hi , 
do not fear that ,code I gave you, will harm your system. You must know that ALL codes I give here (and generally) are first tested by me. :) 

To make the code permanent you must pass it to a script. So code now (you rebooted) its no longer applies. 

If you want to see what card you are using (I assume AMD) run this command
```
 /usr/lib/nux/unity support test -p 
```If you want to have the ability to disable or enable Intel instead Amd , I think you must install fglrx (additional driver for AMD). 

If you don't care about effects etc , then login from ubuntu-2d (Unity 2d , no compiz present) . I am almost certain you will see lower temperature either you use amd or intel.

Thanks
results of above code is 

```
bash: /usr/lib/nux/unity: No such file or directory

```

i did what was on the first link you posted! normally the amd should be deactivated by now. if this is the case, then no need to set amd to a low value. if it's still on, then help me with the script! thanks for helping! most of my reading gave almost no hope about  the dual graphic intel hd 2000 and ati 5000 series. thats whhy i didn't install fglx. the last time i installed those, no matter how, it was crashing ubuntu graphic! i had to go into safe graphics mode to disable the latter.  as of now, i have a very stable dual boot win7/ubuntu12.04. i have no problem with windows. i have always been using ubuntu for fun :P
thanks:)

---

### Post by NikTh on 2012-08-02
Hi,
```
/usr/lib/nux/unity_support_test -p
```

I forgot the underscores. 
Thanks

---

### Post by bhoopal on 2012-08-03
> **NikTh said:**
> Hi,
```
/usr/lib/nux/unity_support_test -p
```

I forgot the underscores. 
Thanks
```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```
i think im using only the intel hd now, am i right?

---

### Post by paccamura on 2012-08-03
Hi,
I have a similar heating problem on my dell precision m2300. it sometimes gets stuck and I suspect it is related to the heating problem. it gets very hot particularly when watching streaming videos, but the problem occurs also if I'm just surfing the web, particularly if the laptop has been on for a bit.
can it be something related to the video card?

PS i'm using unity 2D because on 3D the laptop was simply too slow

thanks for your help

my output

```

mario@mario-Precision-M2300:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86M [Quadro FX 360M] [10de:042d] (rev a1)
    Subsystem: Dell Device [1028:024a]
    Kernel driver in use: nvidia
mario@mario-Precision-M2300:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro FX 360M/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes



```

---

### Post by bhoopal on 2012-08-03
> **paccamura said:**
> Hi,
I have a similar heating problem on my dell precision m2300. it sometimes gets stuck and I suspect it is related to the heating problem. it gets very hot particularly when watching streaming videos, but the problem occurs also if I'm just surfing the web, particularly if the laptop has been on for a bit.
can it be something related to the video card?

PS i'm using unity 2D because on 3D the laptop was simply too slow

thanks for your help

my output

```

mario@mario-Precision-M2300:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86M [Quadro FX 360M] [10de:042d] (rev a1)
    Subsystem: Dell Device [1028:024a]
    Kernel driver in use: nvidia
mario@mario-Precision-M2300:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: Quadro FX 360M/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 295.40

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes



```
only with ubuntu or with windows also? if with windows also, you need to clean the heat sink, clean the dried thermal paste, apply thermal grease on both cpu and gpu. 

if you're prob is software oriented, then someone else will help you! i am also having issues, like overheat with streaming videos, skype 4.0 is very buggy, when it freezes, the temp goes up to 90 degrees celcius.. and back to 47 when I force quit.

---

### Post by NikTh on 2012-08-07
> **bhoopal said:**
> ```

OpenGL vendor string:   Tungsten Graphics, Inc
OpenGL renderer string: Mesa DRI Intel(R) Ironlake Mobile 
OpenGL version string:  2.1 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```i think im using only the intel hd now, am i right?

Hi ,
yes you are using Intel. You have right :) 
Thanks

---

