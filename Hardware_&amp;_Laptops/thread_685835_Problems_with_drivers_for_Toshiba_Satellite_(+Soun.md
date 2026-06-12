---
title: "Problems with drivers for Toshiba Satellite (+Sound) (+VGA)"
date: 2008-02-02
forum: Hardware &amp; Laptops
---

### Post by markinf on 2008-02-02
It looks like the sound is not working in my Toshiba Satellite X205-S7483. I even tried to install the realtek driver but didn't get nothing. I really apreciate it if anyone can help me figure this out.

The other problem is with the VGA, I have a GeForce 8700M GT, I sucessfully installed the nvidia driver (from their website) but the screen looks to have a little slowdown. And when I try to enable compiz, the system ask for restricted driver??? I'm totally confused.

I'm putting here my config;

Mobile DualCore Intel Core 2 Duo T5500, 1666 MHz (10 x 167)
2048 MB  (DDR2-667 DDR2 SDRAM)
[B]Realtek ALC268 @ Intel 82801HBM ICH8M - High Definition Audio Controller
NVIDIA GeForce 8700M GT  (256 MB)[/B]


Please help guys, thanks in advance,

Marcos
^_^

---

### Post by linuxwizard on 2008-02-02
For sound issue look over this your computer is listed there. Maybe a fix or work around.

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

---

### Post by markinf on 2008-02-03
Still can't get the driver to work. It looks like it x crash with every reboot. Should I try this envy? I preffere manual...

---

### Post by linuxwizard on 2008-02-03
I never had to use Envy didn't need it. I have seen others use it and it worked good for them.

---

### Post by markinf on 2008-02-05
I still cant get this to work. ;(

---

### Post by markinf on 2008-02-06
come on guys.

---

### Post by marines6300 on 2008-02-21
Hey does anyone have any ideas on this? I just switched over and I'm loving gutsy, but the lack of a headphone jack is really starting to annoy me.

---

### Post by José Serra on 2008-03-03
Hello, I'm also have a toshiba x205-9349 and I have the same problem with the sound, but the video works fine.

I'd tried all the methods that appear in: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)

It could be useful, if someone with this laptop can tell me witch method works for the x205. May be I'm doing something wrong.

Thank you.

---

### Post by davekiw on 2008-03-15
I have the same video and audio problems on a Toshiba X205-S9800.   Video is an NVidia GeForce 8700M GT with 512Mb and up to 256Mb Dynamically allocated shared memory.   

Mobile Intel PM965 Express chipset - Haven't tried anything for the audio yet, as the video is my prime concern.   The NVidia drivers cause the video to be real sloooooooooow, as in 5 seconds for something to react.   I uninstall them and go back to the default driver, normal speed.   I've also tgried Mepis 7.0 with the same results.   I have an 8600GT on my desktop running with full acceleration.

There has to be a relatively simple fix for this.  :confused:

---

### Post by ZeroHimself on 2008-03-23
ok, here's what i did to make my sound and video work on my toshiba satellite x205-s9359  running gutsy 7.1

[SIZE="6"]**SOUND**[/SIZE]

i went to:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
^^^^^^^^^^ sorry, the link is above, but it isn't displaying right....click on the above line

I then followed the directions for **"Method E"**
which goes like this:

Only use this if your gutsy is up to date!!!!!

get and install this 

[http://c.chez.fred.free.fr/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb](http://c.chez.fred.free.fr/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb)
^^^^^^^^^^ sorry, the link is above, but it isn't displaying right....click on the above line

if the above link is not available, go to the wiki link, find the section on METHOD E, and do some research about how to apply the patch, and recompile what needs to be recompiled.....

next, run this in a console:
```

sudo nano /etc/modprobe.d/alsa-base

```

The directions then tell you add this line:
```

options snd-hda-intel model=toshiba

```
however, mine already had the line, and i just had to modify it to **model=toshiba**

[SIZE="5"]**REBOOT before procedding!!!!!!!!**[/SIZE]

then i used the gnome menu  System->Prefrences->Sound

at the bottom of the program, under "Default mixer Tracks",

i made sure i only had PCM selected for the "HDA intel(alsa mixer"..
I then changed the device to "OSS mixer", and deselected all items

this allows me to use the volume scroll on the front side of the machine, and it only adjusts the Output..  

Before i did this, when i used it it would change the volume on "Front", and my laptop speakers would play even if i had the phones plugged in.....

next I right-clicked on the volume control on my GNOME panel(the one with the system tray- looking thing), and chose Prefrences

Under there I made  sure that under Device "HDA INTEL (alsa mixer)" that I had only "Front" selected.  

I then changed the device to "Realtek ALC268 (OSS mixer)", and selected ONLY "Volume"

I don't know why it worked out this way, (it makes almost no sense to me), but it did work for me.

now when i use my volume control slider, it only changes the system volume, and it seems to work properly with my headphone jack now

although, it's worth noting that if you play sound through an application that uses "OSS", the volume control will not work........

[SIZE="6"]**VIDEO**[/SIZE]
now, as for the video...... this one took me forever to figure out.

**first, back up your xorg.conf file** like this....
!!!!important... make sure that you can start X first before you back it up!!!!!

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.myworking

```

after you do this, you can restore the xorg.conf like this

```
sudo cp /etc/X11/xorg.conf.myworking /etc/X11/xorg.conf
```

after restoring your xorg.conf, you must either restart the X display, by  hiting CTRL+ALT+F7, and then hitting CTRL+ALT+BACK SPACE, 
or  reboot the system using ```
sudo shutdown -r now
```

now, hopefully you didn't use the "Screens and Graphics" application too much..(it made my xorg.conf unusable, and i found a backup in /etc/X11/ , that i then restored)....

anyhow if you get a corrupt display, and can't get it back, you can then hit CTRL+ALT+F1, and log in there...., and use the restore code i provided above.

but anyhow, the key here is to go to a console, and run
```
nvidia-settings
```

you can change all of that important stuff here(i don't even use the Screens and Graphics)
although, i did forget.... in order to get your TV out to work, you will need to turn it on in the Screens and Graphics program (!! which may alter your xorg.conf file, and mess up your resolution)

ok, so i gave you most of the basic steps i followed, that worked for me...
you might have to play around with these settings to get something that works for you.

:guitar: But hopefully you can rock out, and watch movies in hires now!!!:guitar:

sorry if this is a little disorganized, if you need any help, feel free to contact me....

BTW please, let me know if these work for you!!!!!, if they do, then maybe i can pass this info on to someone who can use it to make sure that the Satellites work with future versions of ubuntu!!!!

BTW, do any of you people using a satellite, have problems with your touchpad doing unexpected jumps?????, mine goes crazy after about 2 days, and i wonder if it's a problem with the machine itself, or the driver..

---

