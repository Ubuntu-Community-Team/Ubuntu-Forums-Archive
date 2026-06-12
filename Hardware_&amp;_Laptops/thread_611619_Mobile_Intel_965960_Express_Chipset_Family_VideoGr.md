---
title: "Mobile Intel 965/960 Express Chipset Family Video/Graphics Driver in Gutsy"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by manmath on 2007-11-13
Hey, I am using "Compaq Presario C702TU", it has a graphic card "Mobile Intel 965/960 Express Chipset Family Video/Graphics Driver". Presently I am using Vista and I am happy by its graphic performance. But I am interested to switch to Ubuntu. In this regards I would like to ask the forum members a few questions.

1. Does Gutsy Gibbon has drivers for "Mobile Intel 965/960 Express Chipset"?
2. Do I need to do some manual configuration to get my graphic card working, or will it work out of box?
3. I came to know that this gma965 is a latest from intel, so many linux distributions might not have drivers for it. What about ubuntu in relation to my graphic card - gma965?

Please tell me plain answers. Because I don't want to do any further manual configuration with graphic card. I will switch to Ubuntu only if my graphic card works fine without any new download/install, configuration or patching.

---

### Post by petay on 2007-11-13
have you tried the live cd??

if you run it and it gets as far as the graphical (x ) screen, then your in with a good chance!!

If you get that far and you still want to push it more then you can try enabling the desktop effects, quickest way i find is to right click the desktop and select change desktop background, then click on visual effects, then pick an option there. I have an internal intel 855 graphics card and it runs compiz fusion just fine, far less hardware heavy that vista is.

Hope this helps

Pete

---

### Post by nutz on 2007-11-13
I have this video chipset and it runs just fine. Go for it...

---

### Post by manmath on 2007-11-13
Thank you Nutz and Petay,

I asked the question to be sure. Because for me trying Ubuntu Gutsy is a tedious thing, as at my place there is only 64 kbps bandwidth connection. Also requesting a CD from shipit program is quite time-intensive. So, thought it better to confirm before taking all the pain. But now I am happy that Gutsy has support for Mobile Intel 965/960 Express Chipset Family Video/Graphic Cards.

Anyways, how much time does it take to get the free cd from shipit. I stay in India.

Best wishes and regards.
Manmath

---

### Post by nutz on 2007-11-13
I don't know how long it takes them to send the disk since I have always gotten it from bittorrent. If your connection is that slow you would probably have better luck getting it with bittorrent if you decide to download it.

---

### Post by manmath on 2007-11-13
Thanks a lot!

---

### Post by manmath on 2007-11-15
hi nutz,

i installed ubuntu gutsy on my compaq presario c702tu notebook. but my graphics card (mobile intel 965/960 express chipset family) is not working. also the resolution is not correct. it should be 1280x800 but all i get is 1024x768.

1. are you sure your graphic card the same is mine?
2. did you do any extra configuration like changing the content of xorg.conf or any manual configuration?
3. did you upgrade your kernel or anything, or installed something to make your graphics card work?

or did i make some mistake while installing?

nutz, please be kind to me and explain how you installed gutsy.

thanks in advance.

regards,
manmath

---

### Post by be4truth on 2008-01-13
[http://www.zyxware.com/articles/2007/11/26/laptops/installing-ubuntu-compaq-c702tu-laptop](http://www.zyxware.com/articles/2007/11/26/laptops/installing-ubuntu-compaq-c702tu-laptop)

---

### Post by manmath on 2008-01-28
Hi All,
Previously, it was a wrong installation. I re-installed Gutsy, and every bit of my hardware is auto-configured. Here I am declaring: Ubuntu has drivers for Intel GMA965/960. Thanks Ubuntu and Thanks Mark.

---

### Post by be4truth on 2008-01-28
> **manmath said:**
> Hi All,
Previously, it was a wrong installation. I re-installed Gutsy, and every bit of my hardware is auto-configured. Here I am declaring: Ubuntu has drivers for Intel GMA965/960. Thanks Ubuntu and Thanks Mark.

Did you try the 3D part? I have the right resolution but the 3D acceleration is not working - no Google Earth or 3D games for example. I read that the next release manges the 960 chipset better.

---

### Post by manmath on 2008-01-28
I never had any problem with 3d acceleration. But I disabled the 3d effects as I don't like it. Those compiz-fusion, beryl, metisse or vista aero and other 3d effects (if any) are just the cosmetics I don't like these days. For me a usable and fast desktop is enough.

Of course, I think you need to do some change graphic parameters the xorg.conf to get it working, i have never changed any though, else install the latest xorg-server and intel drivers. It will work.

---

### Post by Seven of Cups on 2008-02-08
OK.  first I have a Dell inspiron 1525 with the Mobile Intel 965 Chipset Family. graphics. 

When I install Ubuntu Gutsy with all updates complete I cannot apply effects, though my resolution (1280x800) is set perfectly from the very start.

Oddly, The latest Mandriva Release DOES auto confuigure and use the Cube at full force from installation.  So there MUST be a driver that does work out there.  The confusing thing to me is the following link: 
Contains the following response from Temujin:  > Re: Mobile Intel (r) 965 Express Chipset Family driver for Ubuntu
The G965 & G3x have issues with Compiz and are blacklisted from running it. No eye candy for you!

Does this mean that there is a linux Intel driver that WILL run 3d Acceleration from my laptop, but won't work in Ubuntu?  Personally I am more than willing to wait for Hardy... if it solves the problem.  Eyecandy is not a Distro Killer for me... but it would be nice to have it when I [COLOR="DarkGreen"]know[/COLOR] it can work in my laptop. :)

---

### Post by be4truth on 2008-02-08
> **manmath said:**
> I never had any problem with 3d acceleration. But I disabled the 3d effects as I don't like it. Those compiz-fusion, beryl, metisse or vista aero and other 3d effects (if any) are just the cosmetics I don't like these days. For me a usable and fast desktop is enough.

Of course, I think you need to do some change graphic parameters the xorg.conf to get it working, i have never changed any though, else install the latest xorg-server and intel drivers. It will work.

The point here would be to be more specific which configurations you changed to have the chipset supported. Out of the box Gutsy doesn't support it. I tried it on 2 machines - one mobo D965RY and one Acer laptop.

---

