---
title: "[SOLVED] Massive black borders"
date: 2008-07-17
forum: Hardware
---

### Post by pbeesley on 2008-07-17
Hi,
   I managed to install Ubuntu on an old Tecra 8500 (800mhz, 256mb Jesus was the previous owner type thing) ((no offense intended))

anyway....the max rez I can select is 800x600 which isn't an issue, the issue is at this rez the screen has massive black borders that are about an inch wide :( does anybody know how I would get rid of these. I previously had PCLinuxOS installed with no screen issues so its not the hardware? 

Can anyone help?

---

### Post by pbeesley on 2008-07-17
That's a Toshiba Tecra btw (yes blantent bump as the Americans are waking up)

---

### Post by pbeesley on 2008-07-18
No-one?

---

### Post by and.hunt on 2008-07-18
I also had a similar problem with my "new" (5 year old, second hand) Toshiba portege r100. The built in monitor wasn't recognised, and a resolution of 800x600 was taken as maximal resolution. (I'd installed ubuntu via wubi, which I was going to use to do a proper installation, where the problem first cropped up, I then installed a basic ubuntu via debootstrap, and only installed xorg as to see where the problem was.) It seems that Toshiba monitors don't interpolate smaller resolutions up to the full screen size: To select your full resolution you can however run:
```
sudo xfailsafedialog
```
This allows you to select your monitor, at best you should just select a generic LCD of the correct resolution.

---

### Post by pbeesley on 2008-07-18
Ok i'll try that tonight thanks

---

### Post by pbeesley on 2008-07-19
ok I managed to do something and it displayed 'fullscreen' but I couldn't get it to stick ```
fail safe session started
IOError [Errno 2] No such file or directory: '/etc/X11/xorg.conf.failsafe'  - will create xorg.conf if possible.
configure

```

---

### Post by Green_Star on 2008-08-12
I was able make my display to full screen, i too had massive black borders on my screen, try doing the following.

> 
$ aticonfig --query-dispattrib=tmds2i
Query monitors tmds2i ,Cap:0xff
Supported adjustment type for tmds2i : brightness, contrast, saturation, hue, positionX, positionY, sizeX, sizeY 

 brightness attribute information of monitor tmds2i :
 default:0, value:0, min:-100, max:100, step:1

 contrast attribute information of monitor tmds2i :
 default:100, value:100, min:0, max:200, step:1

 saturation attribute information of monitor tmds2i :
 default:100, value:100, min:0, max:200, step:1

 hue attribute information of monitor tmds2i :
 default:0, value:0, min:-30, max:30, step:1

 positionX attribute information of monitor tmds2i :
 default:67, **value:67**, min:0, max:1680, step:1

 positionY attribute information of monitor tmds2i :
 default:42, **value:42**, min:0, max:1050, step:1

 sizeX attribute information of monitor tmds2i :
 default:1546, **value:1546**, min:840, max:1680, step:1

 sizeY attribute information of monitor tmds2i :
 default:966, **value:966**, min:525, max:1050, step:1




Check the positionX and positionY values(bold values), if those are not zeros you can make those zeros by following command.(or some other values depending on your screen, zero worked for me) 

> aticonfig --set-dispattrib=tmds2i,positionX:0
aticonfig --set-dispattrib=tmds2i,positionY:0

Now change the screen resolution, mine is 1680x1050, now we have to change sizeX, and sizeY

> aticonfig --set-dispattrib=tmds2i,sizeX:1680
aticonfig --set-dispattrib=tmds2i,sizeY:1050

check the values again to make sure.
> $ aticonfig --query-dispattrib=tmds2i
Query monitors tmds2i ,Cap:0xff
Supported adjustment type for tmds2i : brightness, contrast, saturation, hue, positionX, positionY, sizeX, sizeY 

 brightness attribute information of monitor tmds2i :
 default:0, value:0, min:-100, max:100, step:1

 contrast attribute information of monitor tmds2i :
 default:100, value:100, min:0, max:200, step:1

 saturation attribute information of monitor tmds2i :
 default:100, value:100, min:0, max:200, step:1

 hue attribute information of monitor tmds2i :
 default:0, value:0, min:-30, max:30, step:1

 positionX attribute information of monitor tmds2i :
 default:67, **value:0**, min:0, max:1680, step:1

 positionY attribute information of monitor tmds2i :
 default:42, **value:0**, min:0, max:1050, step:1

 sizeX attribute information of monitor tmds2i :
 default:1546, **value:1680**, min:840, max:1680, step:1

 sizeY attribute information of monitor tmds2i :
 default:966, **value:1050**, min:525, max:1050, step:1



By doing this , it changes the values temporarily, the values will be reset to default if you restart your xserver. I am not able to figure out how to change the default values, so i wrote all these commands in a script and executing it at the beginning of my sessiong(startup)

---

