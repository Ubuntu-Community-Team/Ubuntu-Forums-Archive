---
title: "via km400 video supported?"
date: 2004-11-08
forum: Hardware &amp; Laptops
---

### Post by irifan on 2004-11-08
Hi,

i selected the via module during  install, but ended up with some standard vga resolution (640x420 i think). At only 60 hz its killing my eyes :(

is the km 400 supported under ubuntus xfree?

if not, are there already some working xorg 6.8.1packages for horay?

tia,

---

### Post by IoN_PuLse on 2004-11-08
I have that card working however xv playback doesn't work. I'm hoping to get another nvidia card to stick in there since everything works on those =)

Here is what I did:

Download this: [http://prdownloads.sourceforge.net/unichrome/via_drv.o-unichrome_X_r26-debian_sarge_xfree86-4.3.0.dfsg1-7.gz?download](http://prdownloads.sourceforge.net/unichrome/via_drv.o-unichrome_X_r26-debian_sarge_xfree86-4.3.0.dfsg1-7.gz?download)

Unzip it by right-clicking on it and clicking "extract here", it should just remove the .gz at the end. (it does more than that but visually that's what it does)

The next step: (do this from the folder where you downloaded + extracted the file above)
```
cp via_drv.o-unichrome_X_r26-debian_sarge_xfree86-4.3.0.dfsg1-7 /usr/X11R6/lib/modules/drivers/via_drv.o
```

If the driver "via" is already selected in your XF86Config-4 file, you can restart X (kill is with CTRL+ALT+BACKSPACE, or switch to the terminal with CTRL+ALT+F1 and then log in and type /etc/init.d/gdm restart, or just reboot your machine)

Let me know if that works for you. Unichrome support is kind of lacking for Linux because VIA officially only has full drivers for distros like Redhat and Mandrake, these are open-source independant drivers.

---

### Post by irifan on 2004-11-08
it worked, thanks *bows deeply*

after killin X, it restarted in 1290*1024 @ 60  hz. so i just had to adjust the vert and horz settings for my monitor and now i enjoy ubuntu @85 hz.

since everything is working so fine up to now, i can even stop downloading those fedora core 3 isos ;)

---

### Post by IoN_PuLse on 2004-11-08
Great to hear! Ubuntu is a great distro, especially for it's first release.

---

### Post by IoN_PuLse on 2004-11-09
Update: I found another driver that works just as well and also has semi-xv support. (XV works, but is slow...)

Thanks to archive.org, which archives the internet, I could get this driver. The original website is down that hosts the driver (for some reason) and without their service, I could not have retrieved it. I am attaching this file (because it's under 100k) to this thread so it's easy for others to find it. Install it with the same instructions as above. 

So now we have good via KM400 support, only missing hardware video decoding and hardware OpenGL acceleration :) Hopefully x.org will remedy those problems. For now, I believe this is a very good solution.

---

### Post by slicer on 2005-03-03
I've got the KM400 working with the driver from [The UniChrome Project](http://unichrome.sf.net). However, OpenGL fails with this message:

Sys_Error: GLimp_Init() - could not load OpenGL subsystem

I'm using the Hoary release with the X.org server, driver 'via'. My kernel is 2.6.8.1-3-386.

---

