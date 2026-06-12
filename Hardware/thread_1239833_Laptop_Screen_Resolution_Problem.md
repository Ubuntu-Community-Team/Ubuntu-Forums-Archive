---
title: "Laptop Screen Resolution Problem"
date: 2009-08-14
forum: Hardware
---

### Post by rEgonicS on 2009-08-14
I installed ubuntu on my desktop with no problems and enjoyed using it so I decided to install it on my laptop as well. I burned an Ubuntu Live CD with Ubuntu 9.04 64-bit using ImgBrn. Once I booted my laptop with Live, the options screen loaded with no problems. I checked off the first option and started loading Ubuntu. I first realized something was off when I saw the loading bar. There were strange light red surrounding the bar. When Ubuntu loaded, the screen resolution was very... unpleasant? Everything was much bigger than normal and stretched.(My screen is quite wide.) I tried changing the resolution in the Display options, but I could only change it from 800x600 -> 640x480? And once I did that, everything got out of place and colored abnormally. Which at that point I gave up and shut down.

Does anyone know how I might be able to fix this?


My laptop is a Sony VAIO FW-490J

---

### Post by ZaHACKieL on 2009-08-14
What video card are you using?

---

### Post by rEgonicS on 2009-08-14
ATI Mobility Radeon™ HD4650 graphics card with 512MB vRAM

---

### Post by vedek on 2009-08-14
see if your system is picking up the card although it should 

open up a terminal window and type the following

```
lspci
```

This might bring up a wall of text depending on how many pci devices you have.

just search for the ati bit and let us know it its there.

---

### Post by rEgonicS on 2009-08-14
it says this

01:00.0 VGA compatible controller: ATI Technologies Inc M96 [Mobility Radeon HD 4650]

---

### Post by vedek on 2009-08-14
u might want to check to see if the drivers are installed correctly.
 
go to system > Adminstration > Hardware drivers 
 
Make sure that the recomended one is selected and you might have to restart your pc but after that you should be good to go.

---

### Post by rEgonicS on 2009-08-14
Thanks a lot! I just installed Ubuntu and it looks good so far.

---

### Post by vedek on 2009-08-14
if you edit your first post then add [solved] to the title then people will know its fixed and they won't need to post any more

---

### Post by Amendra on 2009-08-19
hi can any one please help me my lap is hp pavilion dv 6 1125ee
it has a 1gb vga card...

i set the hard ware and drivers activated...
my screen resoluton is 1024x768...but it is not the one 
real resolution in windows is 1366x768
wide screen...
what can i do...

---

