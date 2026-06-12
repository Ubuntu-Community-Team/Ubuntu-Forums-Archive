---
title: "big problems"
date: 2008-08-06
forum: General Help
---

### Post by PIPI on 2008-08-06
I installed Hardy Heron with 2 keyboards pluged. at the first login it all worked fine, but after installing updates and setting wireless keyboards were working now and then. after restart keyboard didn't work at all. after secont reboot he just gone mad and said something about resolution and it failed to get to logon screen. one moment everything was black and then console poped out. today i installed again with just PS2 keyboard pluged. after setting wireless same thing happend. keyboard doesn't work at all and after reboot nohing works. and I almoast forgot that he is slow as hell. solution?

---

### Post by nbayiha on 2008-08-06
Dude it's a kind of hard to understand all your problem .
Let me resume it , if i got it clear: 
First your keyboard cannot be detected
Second you have Ubuntu os installed 
You have problem with your screen resolution 
and now on , your system doesn't work at all .
Am i Right ?

---

### Post by PIPI on 2008-08-06
well. keyboard is detected at first login but after that nothing. and at first login i changed screen resolution and after reboot he said that he cannot set any resolution and then console poped out. from then nothing works. i've tried to change keyboards and nothing.

---

### Post by nbayiha on 2008-08-06
You set your screen resolution after installer the driver of your graphic card ? or not ? Why did the resolution didn't set up.  
First boot your computer from recovery mode ,
then log in + password , 
and then ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

PS: write that command in a paper.

---

### Post by PIPI on 2008-08-07
i've tried that and doesn't work. I installed ubuntu again just with PS2 keyboard. now i pluged usb keyboard and installed updates. both keyboards work now. If I set wireless settings everything will go to hell. keyboards won't work and I won't be able to open any program. come on help me someone. In last 3 days I intalled ubuntu mabe 5 times and everytime sam thing happens.

---

### Post by PIPI on 2008-08-07
anyone?

---

### Post by nbayiha on 2008-08-07
Did you check your BIOS configuration ?

---

### Post by PIPI on 2008-08-07
> **nbayiha said:**
> Did you check your BIOS configuration ?


yap

---

### Post by Vorian Grey on 2008-08-07
Have you tried it with only one keyboard? I have only a USB keyboard and it's always worked fine for me.

---

### Post by hessiess on 2008-08-07
try re-installing again, install your graphics card driver but do not install the updates.

I have had a suimmaler problem with my brothers computer, everything was fine untill the updates were installed. after the updates were installed the screen defaulted to 800*600 and would not run at 1440*900, the native screen res, without scrapping the xorg conf and replacing it with an edited version from my arch install.

if possible can you also post

```
lspci
```

---

### Post by sayakb on 2008-08-07
@PIPI

Please use descriptive titles rather than "help please" or "noob here". The title should give a brief description of the actual problem.

---

