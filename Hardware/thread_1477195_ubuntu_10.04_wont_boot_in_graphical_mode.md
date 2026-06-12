---
title: "ubuntu 10.04 wont boot in graphical mode"
date: 2010-05-08
forum: Hardware
---

### Post by frank8880 on 2010-05-08
hello, i;m having problems in getting ubuntu to boot in graphical mode, i mean, i don't care if it always booted in text mode if i could startx with a command but no command seems to be working...

this problem is after i installed the nvidia drivers, i had to make it boot in text mode so i used this;

#update-rc.d -f gdm remove

or 

#/etc/init.d/gdm stop

i tried both, dont remember which one worked but i was able to install the drivers..

after that i keep getting this messages when i boot up:

first pic is shown when i input: startx

second pic is show when i press CTRL+ALT+F7

last pic is show when i input: sudo /etc/init.d/gdm start


HELP ME PLEASE

---

### Post by Naitsirhc Hsem on 2010-05-08
try
```
service gdm start
```
```
gdm start
```

though it apperars you have xorg errors,  can you post your config file, /etc/X11/xorg.conf
a pic would be fine

```
nano /etc/X11/xorg.conf
```
to exit hit CTRL + x

---

### Post by frank8880 on 2010-05-08
> **Naitsirhc Hsem said:**
> try
```
service gdm start
```
```
gdm start
```

though it apperars you have xorg errors,  can you post your config file, /etc/X11/xorg.conf
a pic would be fine

```
nano /etc/X11/xorg.conf
```
to exit hit CTRL + x

thank you, i'll try that and post results

---

### Post by frank8880 on 2010-05-08
ok, first i tried: service gdm start and gdm start without being root, then i logged in as root and last but not less: i ran: nano /etc/X11/xorg.conf and that's what i got:

the pics have their names accordingly

---

### Post by Naitsirhc Hsem on 2010-05-08
have you tried sudo apt-get reinstall gdm

---

### Post by Naitsirhc Hsem on 2010-05-08
I think that you removed a gdm file in your first post that messed up gdm.

---

### Post by frank8880 on 2010-05-08
> **Naitsirhc Hsem said:**
> I think that you removed a gdm file in your first post that messed up gdm.

i think so too.... i tried:

> sudo apt-get reinstall gdm

and got: E: invalid operation reinstall, so i tried:

> sudo apt-get install gdm

and got: Reading package lists... Done
Building dependency tree
Reading state information... Done
gdm is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded

---

### Post by Naitsirhc Hsem on 2010-05-08
I'm a bit over my head for this one, I will try to request a forum staff to look at this.

---

### Post by frank8880 on 2010-05-08
> **Naitsirhc Hsem said:**
> I'm a bit over my head for this one, I will try to request a forum staff to look at this.

thank you, because there is always the noob Windows IT "expert" quick answer: format and reinstall, but i guess we are not trying to copy that, are we? :P

---

### Post by frank8880 on 2010-05-08
i think i found the problem: API mismatch: the NVIDIA kernel module has version 173.14.22, this NVIDIA driver component has version 195.36.24. Please make that the kernel module and all NVIDIA driver components the same version.

how do i do this? here's the pic it showed when i input: startx.

NOTE: i reinstalled the video card and then input startx and it booted perfectly but as root (obviously because i was logged in as root in CLI), but it only seems to boot after each time i re-install the driver...

---

### Post by frank8880 on 2010-05-09
bump

---

### Post by frank8880 on 2010-05-09
why does it take so long for ppl to respond over these forums? i thought this was the biggest ubuntu forum and ubuntu seems to be the most famous linux distro, what's wrong?

---

### Post by khelben1979 on 2010-05-09
> **frank8880 said:**
> why does it take so long for ppl to respond over these forums? i thought this was the biggest ubuntu forum and ubuntu seems to be the most famous linux distro, what's wrong?

People work for free on this internet forum. I think you should go for paid support if you want faster response times.

---

### Post by khelben1979 on 2010-05-09
Getting an older version of the nVidia driver from the nVidia homepage might be the answer to your problem here. Try with nVidia driver 173.14.22 which matches the kernel module.

Also, I could not see anything in your /etc/X11/xorg.conf file when I look at your screen dump, not so good.

---

### Post by Naitsirhc Hsem on 2010-05-09
Lucid does not use xorg.conf as I understand it

---

### Post by khelben1979 on 2010-05-10
> **Naitsirhc Hsem said:**
> Lucid does not use xorg.conf as I understand it

Hmm.. that is probably true, but he has told us that he has installed a prop. nvidia graphics driver and that driver should create a new xorg.conf file and if it's not there, there's a problem!

---

### Post by frank8880 on 2010-05-11
thanks everybody, my problem seems to have been solved.... i did 2 things and don't know what worked exactly: i installed the nvidia driver with:

#sh NVIDIAdriver.run -K

but at the boot manager, i input a startup command:

gdm start


my system seems to be "working" now even though i have some other issues but at least it's working. thanks everyone.

---

