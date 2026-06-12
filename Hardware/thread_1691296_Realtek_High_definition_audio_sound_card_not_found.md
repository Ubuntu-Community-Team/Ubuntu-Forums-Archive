---
title: "Realtek High definition audio sound card not found"
date: 2011-02-19
forum: Hardware
---

### Post by gulati8 on 2011-02-19
Hi,

I'm new to Ubuntu and linux and it looks like I've having a similar problem to a lot of people but can't quite work out the solution.  I have an Asus U45J and I just installed Ubuntu 10.10 with wubi so I have a dual boot with Windows 7.

Initially, I could only get sound out of my headphones.  So I tried downloading the latest driver from the Realtek site - LinuxPkg_5.16.tar.bz2 - and running the ./install executable.  Now my sound card is not recognized as being present at all and I cannot get sound even through the headphones.

In the sound preferences, under the Hardware tab there are no devices listed.

I ran this script:
sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

And the output is available here:
[http://www.alsa-project.org/db/?f=eb0ff8e823ff807cc8dc0f2af654306fdaab9705](http://www.alsa-project.org/db/?f=eb0ff8e823ff807cc8dc0f2af654306fdaab9705)

I also tried running sudo alsaconf but get a "command not found" error.
I also tried running sudo alsactl init and get "No soundcards found.."

I'd appreciate any help.

Thanks,
Amit

---

### Post by gulati8 on 2011-02-20
I was able to get sound working through my headphones by running the following command:

sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2

which I found in another post here on the Ubuntu forums.  However, I am still not able to get sound out of my speakers and I still get a "command not found: error when I try

sudo alsaconf

I ran this command again:

sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

Here is the new output

[http://www.alsa-project.org/db/?f=bf9feb3c4576804e2e5f64c6cbf00dda69ad2113](http://www.alsa-project.org/db/?f=bf9feb3c4576804e2e5f64c6cbf00dda69ad2113)

Thanks.

---

### Post by mastablasta on 2011-02-21
what kind of output do you have in sound preferences? maybe you will have to say goodbye to HD sound. so try to put it on analog stereo duplex. just to try it first.
 
when an upgrade is made in 10.04 one needs alsa drivers, utils and libraries. i guess you have those. except drivers. 
 
Realtek /intel combo is one of the most used here in this area. and to me it seems Ubuntu has a solution for it i just don't understand why it's so crappy. oh and just wait untill you get an update that messes up the sound. it will start all over again from the start...
 
 i mean what kind of system provide updates that mess up with your driver settings?

---

### Post by mastablasta on 2011-02-21
try 
 
sudo reload alsa
 
to restart alsa. slight chance, but maybe it will mkae sound work.

---

