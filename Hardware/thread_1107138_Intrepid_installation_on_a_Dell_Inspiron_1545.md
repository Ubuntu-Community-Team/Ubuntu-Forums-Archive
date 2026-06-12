---
title: "Intrepid installation on a Dell Inspiron 1545"
date: 2009-03-26
forum: Hardware
---

### Post by jcabraham on 2009-03-26
Hi All,

I just got a new Dell Inspiron 1545 Core2 duo. It has the "Intel GMA driver for Mobile." When I try to run the LiveCD of Ubuntu Intrepid, I get the initial splash screen when it's loading, but then I get a light brown screen and no other display. I can tell that Ubuntu has actually loaded, because I can hear the login tones, etc. If I Ctrl-Backspace, it'll drop to the shell and restart X, but then I get the brown screen again. Anybody know anything about this video?

---

### Post by albandy on 2009-03-26
When booting the cd select the safe mode.

What is happening to you could be a video driver issue, so you need to update it when installed.

---

### Post by jcabraham on 2009-03-26
Even in safe mode, I get the same experience. No display once x starts. 

I suppose I could try to load the video drivers from the command line, but I thought maybe this chipset just wasn't supported yet.

---

### Post by albandy on 2009-03-26
try using framebuffer mode:
when booting the cd select language
then press F6 and add to the end of the line vga=791, then press enter

---

### Post by DerHesse on 2009-03-27
Hi jcabraham

I ordered a 1545 for my mother today.
Too bad I had to buy the Windows License, too.

I will install jaunty jackalope.  

you could install ubuntu with  "alternate"  install CD.
It runs in non graphical mode, so you can finish the installation.
find about it here, It's not really difficult:
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

or, if your're curious for the new version 9.04: [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

---

