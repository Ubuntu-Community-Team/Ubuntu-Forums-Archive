---
title: "Ubuntu is burning my webcam"
date: 2007-03-12
forum: Hardware &amp; Laptops
---

### Post by thnogueira on 2007-03-12
I have an Asus A8jp and it has a built-in webcam. I've just noted It's becoming quite hot. I had make it working by adding the module gspca to the kernel. I've removed the module and the problem continues. Is there any way to completely disable the Ubuntu access to this camera?

The command **lsusb** gives:
```

nogueira@Apuama:~$ lsusb 
Bus 005 Device 003: ID 0ac8:0321 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c019 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  

```

which means the camera is Z-Star Microelectronics Corp. Is it possible to disable the BUS 005 Device 3?

---

### Post by loell on 2007-03-12
my guess is your dual booting with windows? thats why don't want to unplug it?
if so, in windows, does the temp rises?

---

### Post by thnogueira on 2007-03-12
Yes, it is a dual boot machine and under windows the temperature doesn't rises. This is why I'm concerned about it. I don't want to have my camera broking.
Unfortunately, I can't unplug it since it's a built-in camera.

---

### Post by murmurs on 2007-07-04
> **thnogueira said:**
> I have an Asus A8jp and it has a built-in webcam. I've just noted It's becoming quite hot. I had make it working by adding the module gspca to the kernel. I've removed the module and the problem continues. Is there any way to completely disable the Ubuntu access to this camera?

The command **lsusb** gives:
```

nogueira@Apuama:~$ lsusb 
Bus 005 Device 003: ID 0ac8:0321 Z-Star Microelectronics Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c019 Logitech, Inc. 
Bus 004 Device 001: ID 0000:0000  

```

which means the camera is Z-Star Microelectronics Corp. Is it possible to disable the BUS 005 Device 3?


i have the same problem.. im using asus a8jr..
have you found a solution yet?

---

### Post by jonttu on 2007-07-06
I have the same problem with my Acer travelmate 3012.

---

### Post by murmurs on 2007-08-04
the only solution i found is to unload the module for the webcam

sudo modprobe -r gspca

if you wanna use your webcam just load the module again

sudo modprobe gspca

this works on asus a8jr ubuntu feisty fawn

---

### Post by Mr.Mechano on 2008-01-09
I've A8Jr and have noticed the same issue, but the mine doesn't became so hot.

I've tried removing and black listing the module in 
/etc/modprobe.d/blacklist 
but it stays hot. I don't know if on Windows it doesn't become hot, I've removed Winshit.
Till now (3 months) I'm having no problems.

---

### Post by raymondlo84 on 2008-02-25
:( Same problem here with my ASUS W7J... The worst is... It also burns when I am running that Windows Vi(ru)sta ... I have successfully disabled the webcam under Windows XP before and stopped that heat...

:confused::confused: help...

---

### Post by Slingshot on 2008-02-25
Hi **thnogueira**, does that webcam have a built in MIC? My Dell M1210 has the same issue under windows and linux. Disabling the webcam MIC when in Vista cools it down. Not sure howto do this in Ubuntu yet.

---

