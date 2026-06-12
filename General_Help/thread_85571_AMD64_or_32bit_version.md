---
title: "AMD64 or 32bit version?"
date: 2005-11-03
forum: General Help
---

### Post by btarlinian on 2005-11-03
I have an Athlon 64 3200+ pc with 512 MB of RAM and a GeForce FX 5100 graphics card. Should I use the AMD63 version or the normal x86 version. I've heard that there are problems with the AMD64 version in terms of application compatibility, but is it really that big a deal. (I need Java, a web browser, and Eclipse, and need to run at least one app under WINE.)

Thanks in advance.

---

### Post by RAOF on 2005-11-03
Well, you can get java working fine.  Eclipse working fine.  Firefox works fine (but it won't have a java-plugin).  And wine works, too.

It can be a little bit more effort, and in some cases, a lot more effort, but most stuff works out of the box, and most of the rest only requires minimal effort.

---

### Post by jvictor on 2005-11-03
Well I'm an AMD64 user and get all my stuff working , I dont use WINE, and have read threads abt wine on AMD64 to be a no-no. I guess the simple reason behind that is that u need 64 bit win apps that run on 64 bit win :-) . 

When u have all that u need natively in linux , y do u need wine ? AMD64 platform is rapidly maturing ,and we need to increase the user base to get more apps 

These are things which i do frequently on linux.. I removed win bcoz i find Ubuntu sufficient for all these

J2EE development (Spring/Struts) (Tomcat/JBoss) using Eclipse
Sun Java 1.5 works like a breeze
Firefox with user agent switcher even allows u to do online banking .. 
DVD / CD writing 
USB 2.0 thumbdrive data transfer
Digital camera image transfer
All IMs (MSN/Yahoo/Gtalk) thanks to gaim
Bittorrent downloads
Music
DVD playing
..... and much more 

This is my screenshot running 5.10 on AMD 64

[http://ubuntuforums.org/gallery/showimage.php?i=1216&original=1&c=2](http://ubuntuforums.org/gallery/showimage.php?i=1216&original=1&c=2)

So whats preventing u to take the plunge ? If u r scared that u will run into trrouble , the forum is always there to help u out ! :-) Good luck see u on AMD 64 soon...

---

### Post by queenorych on 2005-11-03
I've been running amd64 for a few months.  In ubuntu firefox/evolution/k3b/kino/mplayer all work great.

Problems:
Vncserver,wine,java-applets (though blackdown works great for me), flash (I personally dont' care)
Drivers!  A 64bit kernel needs 64 bit drivers.  If you have to have an ndiswrapper I beleive only broadcom works!  rt2500 (madwifi), and atheros should work since they are open source nativly compiled.

flash can be runing using gplflash which works for quite a bit.

That being said, see the debian amd64 howto guide.  You can always create a chroot.  It's basically a 32 bit base-system (32bit libraries and programs) that you can chroot into and install programs with aptitude or apt-get.  Once installed just a simple dchroot -d wine.  Or with a simple bash script.  wine.  Complete 32bit, exactly the same as running ubuntu for x86.

I use a debian unstable (left over) chroot for bitpim and wine (also ran openoffice in the past).

As a side note the openoffice in amd64 ubuntu is actually 32bit.  64bit openoffice will be a while.

---

### Post by tseliot on 2005-11-03
[QUOTE=btarlinian]I have an Athlon 64 3200+ pc with 512 MB of RAM and a GeForce FX 5100 graphics card. Should I use the AMD63 version or the normal x86 version. I've heard that there are problems with the AMD64 version in terms of application compatibility, but is it really that big a deal. (I need Java, a web browser, and Eclipse, and need to run at least one app under WINE.)

Thanks in advance.[/QUOTE]
Use Ubuntu 32bit if you are a newbie: it could make your life a bit easier

---

### Post by l.tambiah on 2005-11-03
I have AMD64 bit chip also, but use the i386 version of Ubuntu. But why?

[LIST]
[*]Less people are on 64 bit platform so therefore any issues you may encounter may be more difficult to solve. However if people never use the 64 bit platform how can we encourage its adoption rate.
[*]Some packages are not available in 64 bit, which can be a problem for some users depending what you use.
[*]It really isnt that much faster, you wont notice the difference, i tried it when i was a fedora user. The only differences you would encounter is faster rendering times for example if you did 3D graphics. This would be useful for film industrys as they can render content in half of the time.[/LIST]Eventually though platforms will move towards the 64 bit architecture but i think the time is not yet.

---

