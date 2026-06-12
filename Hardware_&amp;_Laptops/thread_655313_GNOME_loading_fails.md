---
title: "GNOME loading fails"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by BeRA on 2008-01-01
Hi,

     English is not my native language so if (when) I make some ridiculous error(s) please blame my ex english teacher :)

     I'm using Ubuntu for almost 8 months now and this is first time I really don't know what to do :confused:.  As far as it's GNU/Linux... I'm still an amateur...

     I have Acer 5100 series laptop (AMD 1.9GHz Tyler, 2GB RAM, ATI X1300, Broadcom 43xx etc.) loaded with Gutsy Gibbon. I've managed to get my graphic and wireless card working properly (also had that HDD load/unload cycles ''problem''- solved), but two days ago I decided to check that MAC style menu thing (applet that shows currently active window name) - worked fine. I've also installed that grub list manager from getdeb.net (not that I need it- just to check it out)... 
     
     Then I logged as root to delete some videos and after that tried that mac menu staff (applet) as root. Worked fine, but as I like to keep my root account on default settings- I' removed it promptly... Reboot... After a few minutes I've started my laptop only to find myself locked in command mode... GNOME fails to start. I haven't tried that boot manager, but still I had to check if it messed with my grub (everything was fine- triple checked). I've tried editing my xorg.conf... to try if it will start with mesa.... NO... checked if there is something unusual in it... nop... ok... I've tried with all other backup xorg.conf's... still nothing... I've tried some other stuff... nothing... 

     All I get after startx is 3 sec. lasting black screen (sometimes with dotted default background and something white that could be some broken message or window)

     [B]-Starting GNOME manager [fail] (everything else is OK),
     -AIGLX error: dlsym for __driCreateNewScreen_20050727 failed... etc.
[/B]
These are just some of the errors... Screen pictures are here (+video of what's going on when I execute startx) :

[[IMG]http://imgplace.com/image_bin/4318/1c121a18fcd43cb9b5532200c05cca7c.jpg.th.jpg[/IMG]](http://imgplace.com/image/view/1c121a18fcd43cb9b5532200c05cca7c) [[IMG]http://imgplace.com/image_bin/9524/5533206a677f0f1432c1f960b66c6ea1.jpg.th.jpg[/IMG]](http://imgplace.com/image/view/5533206a677f0f1432c1f960b66c6ea1) [[IMG]http://imgplace.com/image_bin/8713/2989bf534fdd621bcca3809f2cafc43c.jpg.th.jpg[/IMG]](http://imgplace.com/image/view/2989bf534fdd621bcca3809f2cafc43c) [[IMG]http://imgplace.com/image_bin/3703/144933454e041752efde0321d17c975a.jpg.th.jpg[/IMG]](http://imgplace.com/image/view/144933454e041752efde0321d17c975a) [[IMG]http://imgplace.com/image_bin/4000/8f68fef664c699916bffdfd4bebb5725.jpg.th.jpg[/IMG]](http://imgplace.com/image/view/8f68fef664c699916bffdfd4bebb5725) [http://www.supload.com/vid/6/453621758/3gp/]("http://www.supload.com/vid/6/453621758/3gp/")

Please, anybody :(

---

### Post by taurus on 2008-01-01
You need to run X first before you can start xterm.

```
startx
```

---

### Post by BeRA on 2008-01-01
That was the first thing I've tried.... no result :(

---

### Post by taurus on 2008-01-01
Maybe you have to reconfigure your X server again.

```
sudo dpkg-reconfigure xserver-xorg
```
And when you are done, see if you can start X with

```
startx
```

---

### Post by BeRA on 2008-01-01
That could be it. However, as my laptop is pretty much useless now, I'm writing this from internet cafe... I'll need some time to get home and check if this works. In meanwhile in case you or anybody else have some other idea... I would be very gratefull if you could post your thoughts...

I'll be back with results as soon as possible...

Thanks ;)

---

### Post by BeRA on 2008-01-02
I've tried to reconfigure xserver-org with

> sudo dpkg-reconfigure xserver-xorg

only to find there is no xsever-xorg package to reconfigure (can't find xserver-xorg package) :( ... Should I download and install it (.deb file from the repository) or something else is the problem? 

     If I need to install it, is there something else I need to do prior or after that (I don't want to experiment too much 'cause I have pretty much valuable data installed... can't afford to lose this installation so easy)...

---

### Post by BeRA on 2008-01-04
Anybody? :confused:

---

