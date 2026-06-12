---
title: "GNUitar"
date: 2009-07-28
forum: Installation &amp; Upgrades
---

### Post by pianoman91210 on 2009-07-28
[COLOR=DarkRed][SIZE=3][FONT=Comic Sans MS]Ok, I'm a complete beginner when it comes to installation on Linux, since I don't know how to work the terminal very well. ](*,) I am a musician, and recently, I discovered an effects processor called GNUitar. Now I have downloaded the tar.gz file on my desktop, version 0.3.2, but I'm clueless when it comes on how to install it. The instruction guide that comes in the package confuses me, and I would appreciate some help. I am running on Ubuntu Studio 8.10 Intrepid. Also, does anyone have any suggestions on any processor-like programs for Ubuntu? Thanks!
[/FONT][/SIZE][/COLOR]

---

### Post by Robsteranium on 2009-07-28
Sounds like you've downloaded the source code.  You'll need to compile that before installing the app.

Try the following:

```

$ cd /path/to/gnuitar-archive
$ tar -xzvf gnuitar-0.3.2.tar.gz
$ cd gnuitar-0.3.2
$ ./configure
$ make
$ make install

```

You may have to run the last line as "sudo make install".  You may also run into lot's of complaints about missing libraries etc.  You'll want to use Aptitude (try finding synaptic on the menu) to install these (you may need the -dev libraries).

Regarding fx processors - I'm not sure, let me know what you find!  You might start in the audio category at sourceforge: [http://sourceforge.net/softwaremap/trove_list.php?form_cat=113](http://sourceforge.net/softwaremap/trove_list.php?form_cat=113)

Hope this helps!

---

### Post by realzippy on 2009-07-28
..there are .deb files,which you could install:

[http://linvinus.ru/ubuntu/pool/extra/g/gnuitar/gnuitar_0.3.3-3linvinus1_i386.deb](http://linvinus.ru/ubuntu/pool/extra/g/gnuitar/gnuitar_0.3.3-3linvinus1_i386.deb)

..just click.

---

### Post by pianoman91210 on 2009-07-28
[COLOR=DarkRed][SIZE=3][FONT=Comic Sans MS]So from what I understood, the information in the code box is run in terminal, correct? Well if so, when I tried to run the first code "cd path/to/gnuitar-archive" and it replies saying 'bash: cd: path/to/gnuitar-archive: No such file or directory. Am I missing something?
 I downloaded the file on my desk as "gnuitar-0.3.2.tar.gz. Am I supposed to extract it or something? I understand tar.gz files are like .zip or .rar files, and again sorry for the total noobish-ness #-o[/FONT][/SIZE][/COLOR]

---

### Post by pianoman91210 on 2009-07-28
[SIZE=3][COLOR=DarkRed][FONT=Comic Sans MS]To realzippy: Oh, I didn't find the .deb file, but it says it's the wrong architecture : 'i386'. :confused: [/FONT][/COLOR][/SIZE]

---

### Post by realzippy on 2009-07-28
..there is no 64bit .deb file out there,found a mandriva 64 bit .rpm packet,converting with alien fails...no idea.

---

### Post by realzippy on 2009-07-29
..you could try to download the gnuitarxxx.deb file and install it:

$ sudo dpkg -i --force-architecture gnuitar_0.3.3-xxxx1_i386.deb

---

### Post by ZaHACKieL on 2009-07-29
Well, here you have a list of effects processors for linux:

[http://linux-sound.org/fx.html](http://linux-sound.org/fx.html)

I haven't tried any of those but I can tell you that it's very easy to install the first one (Creox).

To do this you only have to go to Applications > Add/Remove  and in that window just type creox and you will find the software. Just check the box at the left of the name and click the "Apply Changes" button .

Let me know if you have trouble

ZL

---

### Post by realzippy on 2009-07-29
..the problem is,he runs Ubuntustudio 64 bit...no gnuitar64 package.

---

### Post by ZaHACKieL on 2009-07-29
> **realzippy said:**
> ..the problem is,he runs Ubuntustudio 64 bit...no gnuitar64 package.

Uhmm....but maybe the Creox works, what do u think?

---

### Post by lusmo on 2010-10-02
Hello, [**there is working**]("http://www.lunux.net/download/ke-stazeni/multimedia/") 64bit deb package converted from Mandriva rpm package by alien tool.
Note: You need oss driver too (not pulse-audio/alsa only), becasuse it used oss sound system.
This package works great on my 64bit Ubuntu 10.04 with realtime kernel. Enjoy! :-)

---

