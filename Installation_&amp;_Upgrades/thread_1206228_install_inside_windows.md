---
title: "install inside windows"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by themuddaload on 2009-07-06
ok, so after not doing anything with linux/ubuntu for a long time, i just d/l'ed the latest version, and burned myself a CD. 

i figured that i would boot into a live cd, and mess around with it some. so after it finished burning and ejected i pushed it back in, and an autoplay option for wubi popped up.

i saw the option for "Install Inside Windows", and a short description afterwords saying how its installed and ran like a program, and i dont have to partition anything.

so i guess my questions are: is this totally safe? (no chance of killing something i want) will Beryl and the fancy gui things work with this? and will this work on Vista Ultimate 64bit?

thanks as always.

-Phil

---

### Post by wojox on 2009-07-06
Yes it's safe check out wubi

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by anystupidname on 2009-07-06
Is this totally safe?
[COLOR="Lime"]As safe as having Winblows on your system I suppose...[/COLOR]
(no chance of killing something i want) 
[COLOR="Lime"]No, it runs completely independantly of Winduhrs[/COLOR]
will Beryl and the fancy gui things work with this?
[COLOR="Lime"]Yes[/COLOR]
and will this work on Vista Ultimate 64bit?
[COLOR="Lime"]Yes[/COLOR]
[COLOR="Red"]Caution: Just be careful not to choose the "obliterate Earth" option[/COLOR]

---

### Post by themuddaload on 2009-07-06
Aaight, thanks for the quick replies.

---

### Post by themuddaload on 2009-07-07
ok so I just got everything loaded, and i am typing this in firefox on ubuntu.

i dont know if my graphics card is working or not, it is a nvidia 9800m gtx. ubuntu is currently running in 1280x720 resolution, and will not allow me to set it to its native 1680x1050, in "Display Preferences" it says "Monitor: Unknown"

anyone know what the prob is?

thanks.

edit: and things that should run with absolutely no problems, like xmoto... have a very crappy framerate.

---

### Post by Mark Phelps on 2009-07-07
The lower screen resolution and crappy frame rate are most probably due to your using the default open source video drivers.

Now, before you go and force an install of restricted drivers, need to tell us what model videocard/chipset you have -- because AMD/ATI have dropped support for all but their newest "HD" card/chipsets.  If you're running one of the unsupported cards/chipsets, there are no restricted drivers available for 9.04.

---

### Post by themuddaload on 2009-07-07
nvidia 9800m gtx

where exactly would i find a restricted driver?

---

### Post by themuddaload on 2009-07-07
ok, so i went to Nvidia's website, and found a correct driver for my card.

i downloaded it, and the instructions on the nvidia website say to do this:
```
sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
```
i did that and it gave me this back:
```
sh: Can't open NVIDIA-Linux-x86_64-185.18.14-pkg2.run
```

=/

---

### Post by anystupidname on 2009-07-07
> **themuddaload said:**
> ok, so i went to Nvidia's website, and found a correct driver for my card.

i downloaded it, and the instructions on the nvidia website say to do this:
```
sh NVIDIA-Linux-x86_64-185.18.14-pkg2.run
```
i did that and it gave me this back:
```
sh: Can't open NVIDIA-Linux-x86_64-185.18.14-pkg2.run
```

=/

Try:?
```
sudo sh ./NVIDIA-Linux-x86_64-185.18.14-pkg2.run
```

---

### Post by themuddaload on 2009-07-07
meh, it quit being retarded today, and found the driver it required =/

now i have another problem... flash...

so this is ubuntu 64bit, and i cant install adobe flash player because it says it is the i386 ver =0  is there any way to get around this? its pretty lame that i cant even get youtube running...

edit: i cant get java installed either... on the website it shows 2 64bit versions, but when i download them, (one is a bin, and the other is an rpm.bin) i cant figure out how to get them to install.

this is becoming a pain in the ***, why cant linux have a nice happy installer like a .msi  ='(

---

### Post by presence1960 on 2009-07-07
here is an easy fix for both: [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490) Flash works flawlessly for me on hardy, then Intrepid, now Jaunty.

You should have Java installed, you need to add a browser plug in. If you want to try a very snappy version of Java try this plug in : [http://ubuntuforums.org/showpost.php?p=6791349&postcount=59](http://ubuntuforums.org/showpost.php?p=6791349&postcount=59)

---

