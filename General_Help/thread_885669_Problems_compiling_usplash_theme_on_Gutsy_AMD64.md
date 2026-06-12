---
title: "Problems compiling usplash theme on Gutsy AMD64"
date: 2008-08-10
forum: General Help
---

### Post by Ghaagsheblah on 2008-08-10
Have been trying for a while to create a new usplash theme for my laptop but can't get it to work. Hope that anyone out there might be able to assist with what the problem might be.

My distro is Ubuntu 7.10 Gutsy Gibbons AMD64. I am trying to create the theme by using libusplash-dev and have also tried using the example files for help. I have attached the makefile and also the "theme-file" (or what to call it).

When it comes to the actual images all of them use the same palette of 256 colors wich are greyscale.

When i compile the theme i get no errors but when i try to update the usplash theme i get the following message "Cannot find alternative `/usr/lib/usplash/simplegrey-theme.so'"

I have added some of the outputs i get from console and would appreciate any help i can get...

All the files used has also been uploaded as a tar.gz-file. 

```
$ make
make: Circular simplegrey_1024_576_cropped.png <- simplegrey_1024_576_cropped.png.c dependency dropped.
pngtousplash simplegrey_1024_576_cropped.png > simplegrey_1024_576_cropped.png.c
gcc  -g -Wall -fPIC -o simplegrey_1024_576_cropped.png.c.o -c simplegrey_1024_576_cropped.png.c
make: Circular simplegrey_1024_768.png <- simplegrey_1024_768.png.c dependency dropped.
pngtousplash simplegrey_1024_768.png > simplegrey_1024_768.png.c
gcc  -g -Wall -fPIC -o simplegrey_1024_768.png.c.o -c simplegrey_1024_768.png.c
make: Circular simplegrey_800_600.png <- simplegrey_800_600.png.c dependency dropped.
pngtousplash simplegrey_800_600.png > simplegrey_800_600.png.c
gcc  -g -Wall -fPIC -o simplegrey_800_600.png.c.o -c simplegrey_800_600.png.c
make: Circular throbber_fore.png <- throbber_fore.png.c dependency dropped.
pngtousplash throbber_fore.png > throbber_fore.png.c
gcc  -g -Wall -fPIC -o throbber_fore.png.c.o -c throbber_fore.png.c
make: Circular throbber_back.png <- throbber_back.png.c dependency dropped.
pngtousplash throbber_back.png > throbber_back.png.c
gcc  -g -Wall -fPIC -o throbber_back.png.c.o -c throbber_back.png.c
gcc  -g -Wall -fPIC -o simplegrey-theme.c.o -c simplegrey-theme.c
make: Circular helvB10.bdf <- helvB10.bdf.c dependency dropped.
bdftousplash helvB10.bdf > helvB10.bdf.c
gcc  -g -Wall -fPIC -o helvB10.bdf.c.o -c helvB10.bdf.c
gcc  -g -Wall -fPIC -shared -o simplegrey-theme.so simplegrey_1024_576_cropped.png.c.o simplegrey_1024_768.png.c.o simplegrey_800_600.png.c.o throbber_fore.png.c.o throbber_back.png.c.o simplegrey-theme.c.o helvB10.bdf.c.o
rm helvB10.bdf.c throbber_back.png.c simplegrey_1024_768.png.c simplegrey_800_600.png.c throbber_fore.png.c simplegrey_1024_576_cropped.png.c

$ sudo make install
/usr/bin/install -c -d /usr/lib/usplash
/usr/bin/install -c -m 755 simplegrey-theme.so /usr/lib/usplash/simplegrey-theme.so

$ sudo update-usplash-theme simplegrey-theme
update-alternatives: Cannot find alternative `/usr/lib/usplash/simplegrey-theme.so'.

$ ls /usr/lib/usplash/
spacestorm-theme.so    usplash-artwork.so        usplash-theme-ichthux.so    debian-theme.so        simplegrey-theme.so  usplash-theme-ubuntu.so

$ update-alternatives --list usplash-artwork.so
/usr/lib/usplash/usplash-theme-ubuntu.so
/usr/lib/usplash/debian-theme.so
/usr/lib/usplash/usplash-theme-ichthux.so
/usr/lib/usplash/spacestorm-theme.so

```

---

### Post by Ghaagsheblah on 2008-08-10
I managed to solve the problem by simply writing the following in a console:

sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/simplegrey-theme.so 10

---

### Post by minotauros on 2009-02-28
Ubuntu 8.10

This also sorted it out for me. However, in the end you also have to update for the initial boot: sudo update-initramfs -u

If this step is not included the usplash theme only works in the log-out (but not when log-in).

To summarise (using ubuntu reflections alternative usplash [http://www.gnome-look.org/content/show.php/Ubuntu+Reflections+(usplash)?content=92519):](http://www.gnome-look.org/content/show.php/Ubuntu+Reflections+(usplash)?content=92519):)

$ make
$ sudo make install
$ sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-ubuntu.so 10
$ sudo update-initramfs -u

Of course in this example the Ubuntu-Reflections produces and links an usplash-theme-ubuntu.so and not an ubuntu-reflections-theme.so 

If you are using a theme that produces a uplash .so you should direct it there...

---

