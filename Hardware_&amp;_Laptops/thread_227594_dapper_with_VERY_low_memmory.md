---
title: "dapper with VERY low memmory"
date: 2006-08-02
forum: Hardware &amp; Laptops
---

### Post by ensenadaubuntulover on 2006-08-02
So I have this old machine for a long time and there is where I first "risked" to try linux and to my amazement it worked and worked with Mandrake 7.2 8.0 8.1 9.0 dual boot and all and I mean desktops (with fluxbox very workable) just wondering I tried a new hd (40 g) and full of illusion I tried Ubuntu 6.06 Dapper Drake th machine froze almost at boot.

step 2 

installed the hard drive in another laptop and installed Xubuntu and see what happen.

Xubuntu is EXCELLENT in fact made me verry happy so I install hard drive back and cross fingers and see...

machine did not boot because it was old and the hard drive too big

step 3

install hard drive back to oldie and partition and instal its original windows 95

step 4

installed the drive in the new machine and booted with the gparted boot disk and well... parted the disk

windows 95 2G
5 or more to Dapper
2for the swap
and the rest /home

installed Xubuntu again (did I mention it is wonderful?)

and did not wait and back to oldio

step 5

lots of issues with the screen and the monitor because of the configuration of the other machine but grub is working I can run W95 and thats something

step 6 (getting closer)


I boot on safety mode and without X it works fine it recognizes the wireles card and has a net conection ip adress

so apt-get install

apache2
php5
mysql
ssh

so by now it is a server

step 7

check video and got running the xforce with a black margin of about an inch all around the desktop

now I ssh to oldie with my desktop and can run sinaptic from there and install programs

and even it does not work with the X enviroment it works now as a server for pictures for the family and makes work with php and mysql (really amazing) UNBELIEBABLE!!! IT WORKS!!!


 cast

dell latitude            new laptop
acer notelight           oldie
and desktop as himself

---

### Post by encompass on 2006-08-02
the black border on your screen is because you screen is old lcd and your detail is lower than the default for the moniter.
you have 2 options:
1. increase the detail of the monitor
2. go into bios and make the small tick on the setting to alow "zooming" or whatever they call it.

---

### Post by ensenadaubuntulover on 2006-08-02
increase the detail... promise to do homework
i am working console only so 

let me guess it has to do with the xorg ?

ill check bios too

thanks for the tip

---

### Post by encompass on 2006-08-03
oh hey.. if your not in X just do this...
when your booting it will have a count down timer... press escape...  then you will see you booth settings I think it is "e" that edits lines for a one time special boot. at the end of the longest line put this...
vga=0x318
press enter and press b to boot it.
did it help?
if not... let the system completely boot and your back to normal.

If it did help... tell me...;P

---

### Post by kerry_s on 2006-08-03
What are your spec's? Have you tried other light weight distro's built for older machines such as DSL(a.k.a damn small linux), puppy, feather,etc..
I have a old laptop with no hard drive and have been running DSL(damn small linux) in ram for almost 6 months and it's as fast as the computer i'm using now. Sometimes you just need to find the right tool for the job, shop around find something smaller and lighter for that old rig, don't limit yourself to work with something thats not made to handle your old system.A good place to start is distrowatch, remember most linux is free, try as many as you want till you find one you like.-> [http://distrowatch.com/](http://distrowatch.com/)

---

