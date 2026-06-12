---
title: "um yeah"
date: 2008-09-02
forum: General Help
---

### Post by lilmale1 on 2008-09-02
umm yeah, after building essential for the first time I am not ever able to copile some stuff. do I need some kind of unzipper 
like p7zip or something or did I download the wrong version compiler for version ubuntu 8. 

it was version the same essential from cd and everything looked well too.:guitar:

---

### Post by WRDN on 2008-09-02
What errors appear when you try to build a program?

Also, please use descriptive thread titles.

---

### Post by lilmale1 on 2008-09-02
im trying to compile and install program to read my wirless networks or configure it atleast. like networkmanager.
i think I need wireless tools so I got wireless tools and cant compile that either. before i compile networkmanger

it just says 
no such file or directory

---

### Post by luckyuser on 2008-09-02
might be a stupid q, but did you cd to the dir it is extracted in?

---

### Post by lilmale1 on 2008-09-02
do u mean to extract it first or did i cd/home/xbatis/wirless_tools.28 directory right

i did cd

but I ectracted it from the home to the home and home/xbatis/wirlessxxxxxxxxxxxxxxx 

is that right or was that dum to do that

---

### Post by WRDN on 2008-09-02
When compiling programs, you need to extract them from a tar (etc) first if they are compressed. Now, change to the new directory, and type:

```
./configure
```

This will configure the program and notify you if there are missing dependencies.

If all goes well and it configured correctly, type:

```
make
```

Providing this works, you can now type:

```
checkinstall
```

This will install the program, and add an entry in Synaptic for easy removal.

---

### Post by lilmale1 on 2008-09-02
is this right



xbatis@xbatis-desktop:~$ su
Password: 
root@xbatis-desktop:/home/xbatis# tar -zxvf wireless_tools.28.tar.gz
wireless_tools.28/
wireless_tools.28/INSTALL
wireless_tools.28/Makefile
wireless_tools.28/README
wireless_tools.28/iwpriv.c
wireless_tools.28/iwconfig.8
wireless_tools.28/iwconfig.c
wireless_tools.28/README.fr
wireless_tools.28/iwspy.c
wireless_tools.28/iwpriv.8
wireless_tools.28/iwlist.c
wireless_tools.28/iwspy.8
wireless_tools.28/iwgetid.c
wireless_tools.28/sample_pm.c
wireless_tools.28/COPYING
wireless_tools.28/PCMCIA.txt
wireless_tools.28/iwlist.8
wireless_tools.28/wireless.10.h
wireless_tools.28/iwlib.h
wireless_tools.28/iwlib.c
wireless_tools.28/CHANGELOG.h
wireless_tools.28/macaddr.c
wireless_tools.28/wireless.11.h
wireless_tools.28/iwevent.c
wireless_tools.28/iwgetid.8
wireless_tools.28/wireless.12.h
wireless_tools.28/wireless.13.h
wireless_tools.28/wireless.14.h
wireless_tools.28/iwevent.8
wireless_tools.28/wireless.15.h
wireless_tools.28/DISTRIBUTIONS.txt
wireless_tools.28/wireless.7
wireless_tools.28/sample_enc.c
wireless_tools.28/sample_priv_addr.c
wireless_tools.28/wireless.16.h
wireless_tools.28/fr/
wireless_tools.28/fr/iwconfig.8
wireless_tools.28/fr/iwevent.8
wireless_tools.28/fr/iwgetid.8
wireless_tools.28/fr/iwlist.8
wireless_tools.28/fr/iwpriv.8
wireless_tools.28/fr/iwspy.8
wireless_tools.28/fr/ifrename.8
wireless_tools.28/fr/wireless.7
wireless_tools.28/fr/iftab.5
wireless_tools.28/iftab.5
wireless_tools.28/ifrename.c
wireless_tools.28/ifrename.8
wireless_tools.28/wireless.18.h
wireless_tools.28/wireless.19.h
wireless_tools.28/wireless.17.h
wireless_tools.28/HOTPLUG.txt
wireless_tools.28/iwmulticall.c
wireless_tools.28/IFRENAME-VS-XXX.txt
wireless_tools.28/cs/
wireless_tools.28/cs/ifrename.8
wireless_tools.28/cs/iftab.5
wireless_tools.28/cs/iwconfig.8
wireless_tools.28/cs/iwevent.8
wireless_tools.28/cs/iwgetid.8
wireless_tools.28/cs/iwlist.8
wireless_tools.28/cs/iwpriv.8
wireless_tools.28/cs/iwspy.8
wireless_tools.28/cs/wireless.7
wireless_tools.28/wireless.20.h
root@xbatis-desktop:/home/xbatis# cd /home/xbatis/wireless_tools.28
root@xbatis-desktop:/home/xbatis/wireless_tools.28# ./configure
bash: ./configure: No such file or directory
root@xbatis-desktop:/home/xbatis/wireless_tools.28#

---

### Post by luckyuser on 2008-09-02
not dumb at all. what program is it that you're trying to configure? 

could you paste everything it says in the terminal to this thread? might be able to help you better.

edit: beat me to it!

---

### Post by infinitejones on 2008-09-02
I'm no expert but it looks to me like you don't have to do ./configure - you can just go straight to make. Try that and see what happens.

If you look down the list of files it extracted, there isn't one called configure. That's why it says no such file.

Also try opening the file called INSTALL - nano INSTALL or gedit INSTALL - that's probably a text file which hopefully will have sensible installation instructions. (Although I've learned not to hold my breath...)

---

### Post by WRDN on 2008-09-02
From looking at the filelist, the Makefile is already there, so just change to the "wireless_tools.28" directory, and run "make".

---

### Post by lilmale1 on 2008-09-02
what do u mean that was all:confused:

---

### Post by luckyuser on 2008-09-02
i'm curious why you don't want to use synaptic?

---

### Post by lilmale1 on 2008-09-02
:(i don't have internet yet

---

### Post by luckyuser on 2008-09-02
oh, of course **foot in mouth**

did those suggestions work?

---

### Post by lilmale1 on 2008-09-02
I did try that but I still get an error cuz ./configure aint there

---

### Post by luckyuser on 2008-09-02
let me know if this place helps. try downloading a .deb of the package you need.

[http://ftp.debian.org/debian/pool/main/w/wireless-tools/]("http://ftp.debian.org/debian/pool/main/w/wireless-tools/")

if 386, then i think you'll could try this one
[http://ftp.debian.org/debian/pool/main/w/wireless-tools/wireless-tools_29-1_i386.deb]("http://ftp.debian.org/debian/pool/main/w/wireless-tools/wireless-tools_29-1_i386.deb")

hope it works *fingers crossed*

also, if it doesn't, try searching for a deb package of the application you need.

---

### Post by lilmale1 on 2008-09-02
yeah that the last i386 worked but i need something like dbus glib 1 now when I try to install network manager

---

### Post by luckyuser on 2008-09-02
try this package
[http://http.us.debian.org/debian/pool/main/d/dbus/dbus-glib-1_0.23.4-1_i386.deb]("http://http.us.debian.org/debian/pool/main/d/dbus/dbus-glib-1_0.23.4-1_i386.deb")

or check out this site
[http://packages.debian.org/sarge/dbus-glib-1]("http://packages.debian.org/sarge/dbus-glib-1")

---

### Post by lilmale1 on 2008-09-02
hold up im trying them.
so far none are working on my asus system

---

### Post by lilmale1 on 2008-09-02
nah they didn't work
i'll keep looking
thanks for ur help 
im going chil for a lil bit

---

