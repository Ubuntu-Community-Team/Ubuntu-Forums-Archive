---
title: "Microphone on acer 5930g"
date: 2009-04-22
forum: Hardware
---

### Post by geekluca on 2009-04-22
Hi there,
I just installed ubuntu jaunty on my acer 5930g, I want to use skype but the microphone doesn't work,sound recorder also doesnt't work...here my alsamixer, alsamixer -V all, and my sound preference...
what can I do? ):P

---

### Post by geekluca on 2009-04-23
Up!:)

---

### Post by geekluca on 2009-04-23
up!

---

### Post by geekluca on 2009-04-28
c'mon no one can help me??

---

### Post by geekluca on 2009-04-28
i can't believe....this forum is huge...anyone can help me?

---

### Post by eju on 2009-04-29
I also had the same problem with microphon on skype application,
there is some disscusion about these issue that i read them already but they don't work on my IBM R50e, May be they work for you
in [ubuntu forum]("http://ubuntuforums.org/showthread.php?t=1133973&highlight=skype")
and in [idyllictux]("http://idyllictux.wordpress.com") wordpress blog

---

### Post by geekluca on 2009-05-04
Thanks, but nothing change, I just upgrade alsa, but how can I configure it to work with my microphone?someone help me

---

### Post by geekluca on 2009-05-15
Help!

---

### Post by geekluca on 2009-05-19
up!

---

### Post by ptihibou on 2009-05-20
You might want to try this:

 Go to [www.alsa-project.org]("http://www.alsa-project.org/") and download the alsa-driver, alsa-lib, and alsa-utils version 1.0.20. I did it for my AAO D150 with Ubuntu 9.04 Netbook Remix and compiled and install the drivers and now my internal mic works [IMG]http://www.aspireoneuser.com/forum/images/smilies/icon_e_biggrin.gif[/IMG]  Good luck  [IMG]http://www.aspireoneuser.com/forum/images/smilies/icon_e_smile.gif[/IMG]

---

### Post by geekluca on 2009-05-20
ok thanks, but when i compile I have to add certain options?

---

### Post by ptihibou on 2009-05-20
I do not think so but I am not sure as I do not know the characteristics of your machine. I would think that you just have to do, for each of the three categories 

sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install

If the problem you have is due to the Alsa driver this should fix it

before you do anything you can check which version of Alsa you have by doing 

cat /proc/asound/version

hope this helps ;)

---

### Post by geekluca on 2009-05-22
there is an order to install and compile alsa?

---

### Post by geekluca on 2009-05-22
It works!!!
I upgrade alsa and reboot and now it works :D thanks a lot :D

---

### Post by ptihibou on 2009-05-22
I do not exactly remember which order I used ( I think alsa-driver, then alsa-lib, then alsa-utils) but I do not think it matters. Just try it and see the results ;)

---

### Post by verby on 2009-05-24
can you give instructions how to do this?

> **geekluca said:**
> It works!!!
I upgrade alsa and reboot and now it works :D thanks a lot :D

---

### Post by geekluca on 2009-05-25
just upgrade alsa,in this order
alsa-driver
alsa-lib
alsa-utils
with the option
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
sudo make
sudo make install
for every file
after you upgrade, reboot
and then here's my alsamixer, so you can check the same option, in audio record i use capture 1 and in skype I use Default device for audio in
for audio out and ringing I use HDA Intel(hw:Intel,0)

---

### Post by verby on 2009-05-26
> **geekluca said:**
> sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)

can you explain this line?
do I replace uname with my name?

---

### Post by geekluca on 2009-05-26
no...just unpack the tar.gz file, then open a terminal and with the command
```
cd PATH OF THE DIRECTORY
```move to the directory where you unpack the file, than copy and paste the command in the terminal
```
sudo ./configure --with-cards=hda-intel --with-kernel=/usr/src/linux-headers-$(uname -r)
```and hit enter, when the command stops, write
sudo make and press enter
ant then
sudo make install and press enter
for every alsa...first alsa-driver, then alsa-lib and then alsa-utils

---

### Post by xzinkx on 2010-10-07
is it safe for me just to run this .deb version of alsa-driver instead of compiling it myself? [http://ftp.debian.org/pool/main/a/alsa-driver/](http://ftp.debian.org/pool/main/a/alsa-driver/) . Thanks, BTW also using an Acer 5930g and cant get the mic to work in skype.

---

