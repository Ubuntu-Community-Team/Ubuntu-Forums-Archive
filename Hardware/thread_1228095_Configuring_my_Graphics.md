---
title: "Configuring my Graphics"
date: 2009-07-31
forum: Hardware
---

### Post by rigge on 2009-07-31
Hello everyone, I know I should have searched for a post and not make a new one. Well, I tried that and got overwhelmed with all the posts and thought this could be simpler (move me somewhere if you find it necessary). Anyway, I installed Ubuntu 9.04 Jaunty on an Acer Aspire 5100 (BL51) which had Vista before. I'm happy with Ubuntu, but I can't get anywhere with Graphics, no visual effects or 3d.

The graphics card is a Mobility Radeon X1300, which is on the ATI's Legacy list thing. My xorg.conf file is pretty much blank. I tried installing the Ati 9.3 driver with --buildpkg and dpkg -i, and got something in xorg.conf, but after rebooting it went to low graphics mode. Now I have the default settings again.

Another problem I've had is that I can't get Flash (for example Youtube) working on Opera.

Thanks alot in advance.

---

### Post by rigge on 2009-07-31
Can anyone help me up with this one?

---

### Post by saidinesh5 on 2009-07-31
hello buddy,
here,
this might help you with flash...

if you already have flash player installed in mozilla, you can skip most of this though.. you can simply copy/create links to(thats what is done in this tutorial) the corresponding files to the opera's plugin directory... and you are done :)

[http://sysblogd.wordpress.com/2008/03/18/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/](http://sysblogd.wordpress.com/2008/03/18/opera-flash-and-ubuntu-feisty-fawn-gutsy-gibbon-and-hardy-heron-also/)


as far as your ATI card is concerned,
i ll let you kno if i find anything ..

good luck :)

---

### Post by rigge on 2009-08-01
Hello! Thanks for your response, I will try that later when I get back home. :) And yes it does work in Mozilla.

---

### Post by pantera10 on 2009-08-01
hmmm well inorder to revert back to the settings u had before xorg.conf   u can go to the boot menu and select the back up...and voila...back to the same settings...by the way...im pretty sure Update Manager will have the stuff u need

---

### Post by rigge on 2009-08-01
Yes, but I've already had Ubuntu on this computer for two weeks or so. I've installed all mandatory updates. Other than that I'm not quite catching what youre trying to say.

---

### Post by alexandari on 2009-08-01
You can use Envy to install the latest ATI drivers

**sudo apt-get install envyng-core**

---

### Post by rigge on 2009-08-01
I already thought that EnvyNG would save me, but instead it also gave me no graphics. Right now feeling a bit hopeless :p

---

### Post by NormanFLinux on 2009-08-03
I tried them. The only solution for my ATI Radeon X1300 Mobility chipset was to install open source drivers and change the xorg.conf file to list the ATI driver instead of Vesa. I had to change my screen resolution after fixing the xcong.file but everything looks alright now and desktop effects and compiz now work. YMMV.

---

### Post by rigge on 2009-08-04
> **NormanFLinux said:**
> I tried them. The only solution for my ATI Radeon X1300 Mobility chipset was to install open source drivers and change the xorg.conf file to list the ATI driver instead of Vesa. I had to change my screen resolution after fixing the xcong.file but everything looks alright now and desktop effects and compiz now work. YMMV.

Any more newbie-friendly description? :)

---

### Post by rigge on 2009-08-05
Well, tried what you NormanFLinux said, didn't change anything.

---

### Post by rigge on 2009-08-06
So there is indeed no way of fixing these?

---

### Post by rigge on 2009-08-09
bump.

---

### Post by rigge on 2009-08-14
Still no progress.

---

### Post by rigge on 2009-08-16
Just tell me theres no way to get my graph's working..

---

