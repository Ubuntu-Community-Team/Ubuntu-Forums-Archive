---
title: "How to get Linux hardware for my compute"
date: 2009-09-08
forum: Hardware
---

### Post by pjs675 on 2009-09-08
Hi i am new to the Ubuntu Linux OS 

How do you install the hardware, everything is for Windows i don't see it for Linux.

My computer 

AMD Athlon 11X2 250 Processor
Gigabyte M61PME-S2P Motherboard
Seagate 500 gig hard drive
Kingston 2 GB PC2-6400 DDR Ram
LG DVD burner.

I would like to use Ubuntu 9.04 Linux

What would be better to use with my system the 64 Bit or the 32 Bit Ubuntu Linux.

Thanks

---

### Post by jerrrys on 2009-09-09
you got a 500 gig hard drive,  why choose at this point?  try them both and then make a decision...

---

### Post by pjs675 on 2009-10-20
How do i had hardware for the Linux.

I installed the Linux i had 500 GB now i only have 132GB why is that.

I still can get the internet working and cant install the hardware for the video card.

---

### Post by joeoshawa on 2010-05-02
go with 10.4 fixed a few problems i had if you have problems with the sound it is just editing alsa-base.conf the info you need is in ALSA-Configuration.txt.gz your module is snd-hda-intel. The problem i had is no headphones and no mic. Still no mic due to a bug but i do have sound in the headset and the speakers (speakers always worked) btw for the rest of the info check HD-Audio.txt.gz. cheers btw you can always repartition if you want two operating systems but i am using 64 bit and it is great even with only 2 gig of ram i still use both processors and if you have 4 gig or higher you need 64 bit to use all your ram.

---

### Post by 23dornot23d on 2010-05-02
Looking at the specs for your Motherboard you have a

 [B]NVIDIA® GeForce 6100 / nForce  430 chipset

unless you have added a newer Graphics board onto this .....

[/B][http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3009](http://www.gigabyte.com.tw/Products/Motherboard/Products_Overview.aspx?ProductID=3009)

This will work if you add the following to your sources 

[https://launchpad.net/~nvidia-vdpau/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Envidia-vdpau/+archive/ppa?field.series_filter=")

it allows you to get the latest Nvidia drivers ....

I downloaded the 195.36 drivers and it works ok ..... see this has there have been
some problems ... what works for me may not work for everyone though ,,,
but I hope that this helps .....

Here is the link to the thread concerning Nvidia drivers ....

[http://ubuntuforums.org/showthread.php?p=9217202#post9217202](http://ubuntuforums.org/showthread.php?p=9217202#post9217202)

As regards the 500 Gig hard drive ..... how did you partition it ......

You may only be seeing the partition that you set up for Linux .....

---

