---
title: "FGLRX trouble with 13.04 and Mobility Radeon HD 4225/4250"
date: 2013-04-30
forum: Hardware
---

### Post by vegardsv on 2013-04-30
Hi,

I have a laptop where lshw identifies the graphics card as Mobility Radeon HD 4225/4250.

FGLRX is not supported anymore, as far as I understand. I downgraded Xorg and installed the fglrx legacy drivers using the makson96/fglrx ppa. 

Anyway, that didn't work; X complains about "no screens found".

I _think_ I need fglrx support, because without it, neither the displayport or the vga external output seems to work - only the laptop monitor works.

So my question is two-fold:

a) Is it possible to make fglrx work?

b) Is it possible to get the displayport and vga output working without the fglrx drivers?

---

### Post by Yellow Pasque on 2013-04-30
Try:
```
sudo amdconfig --initial -f
```

---

### Post by vegardsv on 2013-05-01
> **Temüjin said:**
> Try:
```
sudo amdconfig --initial -f
```

Forgot to say I tried that... Although I did it from the rescue console - perhaps I should've done it from within Xorg before rebooting...?

---

### Post by midnightramen on 2013-05-01
I could be wrong, but this sounds like the /home/<user>/.Xauthority issue. Deleting the .Xauthority file would allow it be regenerated.

---

### Post by dentaku65 on 2013-05-03
Which kind of theme are you using on xubuntu?
Are you using compiz?

---

### Post by vegardsv on 2013-05-04
> **midnightramen said:**
> I could be wrong, but this sounds like the /home/<user>/.Xauthority issue. Deleting the .Xauthority file would allow it be regenerated.

I have no such file. And it shouldn't be relevant either, as X never comes up (never reach the login screen).

---

### Post by vegardsv on 2013-05-04
> **dentaku65 said:**
> Which kind of theme are you using on xubuntu?
Are you using compiz?

Xfce, no compiz. How is this relevant? :)

---

### Post by dentaku65 on 2013-05-05
Theme can impact with LibreOffice in Xubuntu, did you try to put the official one Greybird?

Btw did you install last fglrx driver? See my guide [http://ubuntuforums.org/showthread.php?t=2139200](http://ubuntuforums.org/showthread.php?t=2139200)

---

