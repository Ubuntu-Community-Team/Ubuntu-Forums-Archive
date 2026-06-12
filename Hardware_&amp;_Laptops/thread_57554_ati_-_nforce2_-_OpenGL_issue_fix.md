---
title: "ati - nforce2 - OpenGL issue fix"
date: 2005-08-16
forum: Hardware &amp; Laptops
---

### Post by unixpusher on 2005-08-16
Hi ,

         I just installed kubuntu 2 days ago. Along with having to re-learn thing I already knew how to do ( this is the first debian derivative i use ), I've been having all sorts of fun getting hardware 3D to work ( this is my last ati board ) . I did the usual ...

apt-get install xorg-fglrx-driver
modprobe nvidia-agp ; echo nvidia-agp >> /etc/modules
xorg.conf 
    - module name
    - agpgart ... 
 
started X, fglrxinfo shows ATI , good
i run glxgears, it runs, but it's buggy looking, 
the openGL xcreensaver don't work at all ...
 :-? 
soooo... 

I launch  kflux.kss from the shell, an I get :
  Unable to resolve Xmu symbols - please check your Xmu library installation. 

i reinstalled libxmu6 , same result...
after some googling ,  this was the fix
ln -s /usr/X11R6/lib/libXmu.so.6 /usr/lib/libXmu.so

now my openGL apps work great, I am just curious as to why there is a simlynk /usr/lib/libGL.so but not for libXmu.so ... did I not install something correctly ? is it a problem with the package ? 

thx

---

