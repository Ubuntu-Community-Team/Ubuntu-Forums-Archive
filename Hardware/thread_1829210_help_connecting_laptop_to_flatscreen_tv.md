---
title: "help connecting laptop to flatscreen tv"
date: 2011-08-20
forum: Hardware
---

### Post by Xcursion666 on 2011-08-20
i have a lenovo 3000 g530 laptop that i wish to connect to my 32 inch vizio flat screen so i can play games on a bigger screen i have the right cord for the job but the resolution doesn't display right it only fills up half of the screen with half of the picture is there anyway to fix this is it a driver issue because my brothers windows 7 laptop connects fine with no issues
thanx in advance  :confused::confused:

---

### Post by dwigyit on 2011-08-20
If you have an ATI or Nvidia card, you can go to its options and turn overscan to full (or as high as it needs to be - it basically makes the screen bigger). You will need to install the additional drivers for it to get the controls though. ATI installs itself as ATI catalyst control center and Nvidia as something fairly similar.

If you have an intel integrated card, there is probably a similar option, I don't know because I don't have one ;)

Also, some monitors have settings which force aspect ratios used in movies and stuff, check your monitor settings.

---

### Post by Xcursion666 on 2011-08-20
> **dwigyit said:**
> If you have an ATI or Nvidia card, you can go to its options and turn overscan to full (or as high as it needs to be - it basically makes the screen bigger). You will need to install the additional drivers for it to get the controls though. ATI installs itself as ATI catalyst control center and Nvidia as something fairly similar.

If you have an intel integrated card, there is probably a similar option, I don't know because I don't have one ;)

Also, some monitors have settings which force aspect ratios used in movies and stuff, check your monitor settings.

it has a intel integrated card its starting to tick me off because i dont have this problem with my acer netbook
i also have a converter box to connect my laptop to a crt tv and i have no problems with that but the picture quality sucks thats why i want to use my flat screen tv i paid 100 bucks for that converter box and its a piece of crap lol

:guitar:

---

### Post by dwigyit on 2011-08-20
If it's intel then I'm afraid I can't be the one to help you... I don't have an intel card to look at the settings for. See if there is an intel configuration utility installed though - or wait for help from someone else. Shouldn't take long ;)

---

### Post by Xcursion666 on 2011-08-22
> **dwigyit said:**
> If it's intel then I'm afraid I can't be the one to help you... I don't have an intel card to look at the settings for. See if there is an intel configuration utility installed though - or wait for help from someone else. Shouldn't take long ;)

still cant get it to work i might have better luck with the new laptop i ordered it comes with a nvidia geforce  gtx 580m

---

### Post by realzippy on 2011-08-22
1.
Do you have an *overscan* or *autoscan* option on the 32"'s menu?

2.post output from (do not connect "crappy" converter!)

```
xrandr -q
```

3.which kernel do you use (intel driver is part of the kernel)

```
uname -a
```

---

### Post by Xcursion666 on 2011-08-22
> **realzippy said:**
> 1.
Do you have an *overscan* or *autoscan* option on the 32"'s menu?

2.post output from (do not connect "crappy" converter!)

```
xrandr -q
```3.which kernel do you use (intel driver is part of the kernel)

```
uname -a
```

no i dont but here is the output

> dragonfighter@xcursion:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 8192 x 8192
LVDS1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 331mm x 207mm
   1280x800       60.0 +
   1024x768       60.0* 
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
dragonfighter@xcursion:~$

and here is the kernel i use
dragonfighter@xcursion:~$ uname -a
Linux xcursion 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:05:14 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by realzippy on 2011-08-22
according to the output your "32 inch vizio flat screen" runs at
1024x768....
What is the exact model name of it?

btw,why not running lenovo at 1280x800 ?

---

### Post by Xcursion666 on 2011-08-23
> **realzippy said:**
> according to the output your "32 inch vizio flat screen" runs at
1024x768....
What is the exact model name of it?

btw,why not running lenovo at 1280x800 ? 

i dont know the name but the model number is vo370m
and i do have my screen set at 1200x800
hopefully the new laptop i ordered from system 76 wont have this problem
ok i found out that the tv is a 37 inch my old tv was the 32 inch both  were vizo tvs though and i had the same problem on my old tv as well
hope i can resolve this issue because when my new computer arrives i am giving this lap top to my younger sister and she has the same tv i do

---

### Post by Xcursion666 on 2011-08-24
ok this is weird it works fine on my brothers sanyo tv he has the same size tv i do
i wonder if its the cord i bought at radio shack thats causing the problem its from some company called gigaware and it cost me around 30 bucks has did anybody else have problems with their products  i dont think its the tv because my brothers windows 7 pc and his mac all connect fine

---

### Post by realzippy on 2011-08-24
It is indeed possible that the cable is a problem;
the graphics device doesn't get the monitor data,so it doesn't know
that it is capable of 1920 x 1080  resolution.
However it might be possible to feed the data for this resolution manually with [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions").

---

### Post by Xcursion666 on 2011-08-24
> **realzippy said:**
> It is indeed possible that the cable is a problem;
the graphics device doesn't get the monitor data,so it doesn't know
that it is capable of 1920 x 1080  resolution.
However it might be possible to feed the data for this resolution manually with [xrandr]("https://wiki.ubuntu.com/X/Config/Resolution#Adding_undetected_resolutions").

thanks i will let you know if it works

---

### Post by realzippy on 2011-08-25
Just ask if you need help with the xrandr stuff...

---

### Post by Xcursion666 on 2011-08-30
> **realzippy said:**
> Just ask if you need help with the xrandr stuff...

thanks for the help i finally got it working

---

### Post by realzippy on 2011-08-31
...might be a help to others if you would explain how you made it.

---

