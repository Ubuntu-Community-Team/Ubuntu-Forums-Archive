---
title: "[Howto] C-Media USB Headphone Set"
date: 2009-06-11
forum: Hardware
---

### Post by tenchi39 on 2009-06-11
This is a howto to make the C-Media USB Headphone Set work in K/Ubuntu 9.04. I used Kubuntu, didn't try it with Ubuntu...

Image of the device:
[http://www.martialarts.hu/data/blog_pictures/300-2-kmsndu10.jpg](http://www.martialarts.hu/data/blog_pictures/300-2-kmsndu10.jpg)

When you plug in the usb device, linux will recognize it, but sound will not work at all, as it is blacklisted by alsa.

First, open up alsa-base.conf:

[Kubuntu] sudo kate /etc/modprobe.d/alsa-base.conf
or:
[Ubuntu] sudo gedit /etc/modprobe.d/alsa-base.conf

Find the following line:

options snd-usb-audio index=-2

And change it to:
#options snd-usb-audio index=-2

Save and reboot your machine. You should have sound now. If not, open the sound mixer and see if something is muted.

I also had an other problem: Only one program had sound. If I played something in audacious, youtube had no sound etc...

To solve this you have to uninstall pulseaudio and install esound.

sudo apt-get remove pulseaudio
sudo apt-get install esound

Restart your machine and try again. You may have to set the proper sound device (alsa) for your programs.

I tested this with audacious, smplayer and flash.

- Please confirm that this works for you too..
- Please confirm that this works in Ubuntu 9.04 too...

---

### Post by user6726 on 2010-01-25
Thank you for your solution. It saved me a lot of time and effort. 

I use an Java application to collaborate with my school and the C-Media head set was not working. I was wasting time by installing bunch of other apps and selecting different mixers. I finally searched for a specific UBS C-Media tag and landed on your solution. In no time it worked flawlessly. 

Appreciate you took the time to post your finding. It saved me big time. Thanks again.

I am using ubuntu 9.10.

My headset does not match the image you have but the device ID comes up as C-Media. It has GigaWare name on it. I will try to take a picture of it.

---

### Post by nomad5 on 2010-06-13
Thank you very much! It works on 9.10 on a Gigawire usb headset. I also had to change the settings in sound preferences input and output to audio adapter analog.

---

