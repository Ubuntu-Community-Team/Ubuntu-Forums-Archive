---
title: "[SOLVED] vlc wont play dvds"
date: 2008-12-30
forum: Hardware
---

### Post by thingy87654321 on 2008-12-30
i can not play dvds with vlc, i have a toshiba satellite m45-s351 laptop with a dvd-rw drive and a 1.73 ghz processor and 1024 megabytes of ram with a single operating system (ubuntu) and i have installed vlc media center, i can not play dvds for some reason, my friends toshiba laptop, a105, with a dvd-rw drive and a 1.73 ghz processor 1 gb of ram runs them fine, that is if they are not burnt dvds, on my 2 desktop computers have vlc and they play dvds fine

what i want to know is..

1. why cant i play dvds on vlc

2. why cant my friends laptop play burnt dvds on vlc when the windows version works fine and he has had vlc on that laptop when he was running windows and it played them

3. is there anyway to make "movie player" play dvds ( it gives a error message saying that it could not read from reasource)

the drive on my laptop works fine by the way :]

---

### Post by hansdown on 2008-12-30
Hi thingy87654321.

This link is great for setting up multimedea.

[http://www.stchman.com/](http://www.stchman.com/)

---

### Post by namdung on 2008-12-30
> **thingy87654321 said:**
> i can not play dvds with vlc, i have a toshiba satellite m45-s351 laptop with a dvd-rw drive and a 1.73 ghz processor and 1024 megabytes of ram with a single operating system (ubuntu) and i have installed vlc media center, i can not play dvds for some reason, my friends toshiba laptop, a105, with a dvd-rw drive and a 1.73 ghz processor 1 gb of ram runs them fine, that is if they are not burnt dvds, on my 2 desktop computers have vlc and they play dvds fine

what i want to know is..

1. why cant i play dvds on vlc

2. why cant my friends laptop play burnt dvds on vlc when the windows version works fine and he has had vlc on that laptop when he was running windows and it played them

3. is there anyway to make "movie player" play dvds ( it gives a error message saying that it could not read from reasource)

the drive on my laptop works fine by the way :]

In order to play DVD u need to first install the required codecs. 
To view an encrypted DVD you must have the proper CSS (Content Scrambling System) decrypter installed on your system.

Pls follow the link given in the previous post.
[http://www.stchman.com/](http://www.stchman.com/)

Are u able to play other proprietary formats like mp3, wav, mpeg etc?

Also clean ur DVD ROM, if it helps.

---

### Post by thingy87654321 on 2008-12-31
i am able to play other formats and i have tried many dvds ( mostly brand new ) and i tried a command in the terminal that is exposed to install the codecs and got this

chris@chris-laptop:~$ sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-pitfdll is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
The following packages were automatically installed and are no longer required:
  mcpp gnome-bin libgnome32 gnome-libs-data openssl-blacklist libart2
  libgnorbagtk0 libgnomeui32 imlib-base liborbit0 gdk-imlib11 libgnomesupport0
  libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.
chris@chris-laptop:~$

---

### Post by jrusso2 on 2008-12-31
> **thingy87654321 said:**
> i am able to play other formats and i have tried many dvds ( mostly brand new ) and i tried a command in the terminal that is exposed to install the codecs and got this

chris@chris-laptop:~$ sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
[sudo] password for chris: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gstreamer0.10-pitfdll is already the newest version.
gstreamer0.10-ffmpeg is already the newest version.
gstreamer0.10-plugins-bad is already the newest version.
gstreamer0.10-plugins-bad-multiverse is already the newest version.
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
The following packages were automatically installed and are no longer required:
  mcpp gnome-bin libgnome32 gnome-libs-data openssl-blacklist libart2
  libgnorbagtk0 libgnomeui32 imlib-base liborbit0 gdk-imlib11 libgnomesupport0
  libgnorba27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 203 not upgraded.
chris@chris-laptop:~$

Those are gstreamer plugins that VLC does not use.  You probably just need to download libdvdcss2 from mediabuntu repository to get VLC to play DVD.

---

### Post by thingy87654321 on 2008-12-31
does anyone know any good dvd player software for ubuntu 8.04,
that will

play the dvd without any codecs or the codecs included

not source code <--- i hate compling scource code

---

### Post by jrusso2 on 2008-12-31
VLC works fine just get libdvdcss2 it works better then LinDVD which you have to get with a Dell or Mandriva.

---

### Post by thingy87654321 on 2008-12-31
i followed the instructions on  [http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

and i changed the  settings in default.files<-- i think that is the filename

and it works

thanks for the help, i could not have done it without you

happy holidays and happy new year

---

### Post by thingy87654321 on 2008-12-31
whoooooooooooooooooooo! i farted:D

---

### Post by thingy87654321 on 2008-12-31
i used to use mandriva, it rocked all the way to the recycle bin
no really it was pretty good

---

