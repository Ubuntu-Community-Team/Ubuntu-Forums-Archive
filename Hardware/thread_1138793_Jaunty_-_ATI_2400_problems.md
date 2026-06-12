---
title: "Jaunty - ATI 2400 problems"
date: 2009-04-26
forum: Hardware
---

### Post by jaborto on 2009-04-26
Hi guys.

I've tried in so many ways but it's still problematic.

The Envy installed the Ati driver but the computer crashes at the X starting.

The screen shut's down (it´s not a black screen) and restart de laptop is the only way to get out.

Some one can say something about that?



P.S.: I'm sorry about my english ;)

---

### Post by Mr K on 2009-05-12
I have similar problem. In jaunty my envy build up xorg doesn't work anymore and when I try to reinstall the nvidia driver with envy, the program (envy crashes)..:confused:

---

### Post by drubin on 2009-05-12
Is this running Jaunty 64bit or 32bit?

I have the same/similar issue under 64bit. (I think there might be an issue with the proprietary drivers for ATI 64bit.

If you can confirm I will be able to know it isn't just me and will file a launchpad bug report with it

---

### Post by Alejandro Pastrana on 2009-05-13
Hi.

I have the same issue with Ubuntu Jaunty 64 bit. Computer crashed after installing ATi driver via Envy.

---

### Post by drubin on 2009-05-13
[http://ubuntuforums.org/showthread.php?t=1155905](http://ubuntuforums.org/showthread.php?t=1155905)

This is what I did, it works perfectly but I don't have compiz but others doo with slightly different cards. (btw I am running a 2600)

---

### Post by fnn.pgk on 2009-07-09
yup , mine too . I have the same problem . I don't know that if it is from xorg.conf or the packages I installed for it to get graphic card work I installed these packages :  

xorg-driver-fglrx
fglrx-kernel-source
dkms

now I have no display at start up i am using 32 bit one on Asus F3Sr laptop with ATI Radeon Mobility HD 2400 vendor id : 94c9 

any idea hot to recover my graphic ? 
and installing my graphic card ?

also there is something else 
when I try the code below at terminal , the answer was "yes" 
but I can't see my graphic card at hardware drivers
is this ubuntu internal bug ? I didn't have this problem with older versions 
```
glxinfo | grep direct
```

also I tried this code 
```
glxgears -info
```
and the answer was 
```
unknown chip id 0x94c9, can't guess.

GL_RENDERER   = Software Rasterizer

GL_VERSION    = 2.1 Mesa 7.4

GL_VENDOR     = Mesa Project
```

any idea or suggestion ??? 
it seems that ati hd 2400 is the worst graphic card for linux base OS I had same problem at redhate enterprise 5 and fedora 9

---

### Post by cryemoxkidcry on 2009-07-09
I'm having the same problems, but I don't have the same card. I think it's just something with ATI stuff..  Same thing happened to me with 32bit Jaunty.

---

