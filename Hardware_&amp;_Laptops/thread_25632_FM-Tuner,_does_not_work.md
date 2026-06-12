---
title: "FM-Tuner, does not work"
date: 2005-04-10
forum: Hardware &amp; Laptops
---

### Post by moffen on 2005-04-10
Hi..

I am the glad owner of a Medion 2819, TV/FM-tuner card (with chipset PHILIPS SAA7134), but I have a problem. 

I have installed the commando-line program "radio", but when I try this, this output come : 

open /dev/radio: No such file or directory

I then tried with:
radio -c /dev/video0

Then the program start, but there is only noise. What can I do?

My TV-Tuner is working perfectly with "TVTME"

How to get it to work?

/Moffen

---

### Post by humanity_to_others on 2005-04-10
should be
```
radio -c /dev/radio0
```

---

### Post by c_dog on 2005-04-10
The static noise you're hearing is because it's probably working. You need to tell 'radio' which frequency or station to use. It's much easier to use the 'gradio' Gnome front-end for 'radio' than the ncurses version. Just be sure that you also have an FM antenna plugged into the right port on your tuner card, also.

---

### Post by moffen on 2005-04-10
I have tried "radio -c /dev/radio0" but there is no sound, not even noise

---

### Post by humanity_to_others on 2005-04-10
Turn on line-in sound.

---

### Post by moffen on 2005-04-10
[QUOTE=c_dog]The static noise you're hearing is because it's probably working. You need to tell 'radio' which frequency or station to use. It's much easier to use the 'gradio' Gnome front-end for 'radio' than the ncurses version. Just be sure that you also have an FM antenna plugged into the right port on your tuner card, also.[/QUOTE]

Ok I tried gradio, but it's an frontend, but there is no sound. 

I have tried to tell a known frequency, but it still doesn't work. Not even the autoscan.

Now I have tried the commands:

radio (there is no sound)

radio -c /dev/radio0 (still no sound)

radio -c /dev/video0 (sound, but only noise)

Not any luck yet.

---

### Post by moffen on 2005-04-10
[QUOTE=humanity_to_others]Turn on line-in sound.[/QUOTE]

Line-in is turned on, it is also used with my TV-Tuner (the same card) and the sound is working with TV.

---

### Post by moffen on 2005-04-10
When I try to scan for channels now with:

radio -c /dev/radio

It find nothing, but if I tune in manually, I found a little, very weakness signal, from the stations, but nothing useful that I can hear. It worked in MS Windows 2000, as I used it for just 2 days ago, so it's nothing with the cable or something like that.

Any ideas?

---

### Post by humanity_to_others on 2005-04-10
Applications > Sound & Video > Volume Control
[IMG]http://xs404.xs.to/pics/05151/volufdadfs.png[/IMG] 
[IMG]http://xs404.xs.to/pics/05151/volufdfadf.png[/IMG]
I can listen radio with my Flyvideo 3000 (saa7134).

---

### Post by moffen on 2005-04-10
[QUOTE=humanity_to_others]Applications > Sound & Video > Volume Control
[IMG]http://xs404.xs.to/pics/05151/volufdadfs.png[/IMG] 
[IMG]http://xs404.xs.to/pics/05151/volufdfadf.png[/IMG]
I can listen radio with my Flyvideo 3000 (saa7134).[/QUOTE]

Do you get Stereo? and which program do you use?
I only get some sound with /dev/video0, and nothing with /dev/radio0

---

### Post by humanity_to_others on 2005-04-10
I have to turn on Line-in volume while I'm switching Tv to radio. In /dev directory you can find your radio or radio0 device. And If you want to use radio for fm you must show your device:
```
radio -c /dev/radio0
```
But in gradio no configuration needed. just
```
gradio 
```

---

### Post by humanity_to_others on 2005-04-10
[QUOTE=moffen]I only get some sound with /dev/video0,[/QUOTE] I tried 
```
radio -c /dev/video0
```but not very clear with noises.

---

### Post by moffen on 2005-04-10
It doesn't work anyway, not any sound in neither radio or gradio. I have tried to raise any volume, when radio or gradio is open, but nothing happen.

But thanks for your help anyway  O:)

---

### Post by humanity_to_others on 2005-04-10
This page may help you: [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

### Post by xalphas on 2005-06-05
I tested it mdk 10.2 and suse both are working with my tuner and i can listen to fm radio. I know there is a missing symlink for /dev/radio. I follow some guides and figured the symlink.

```
xalphas@ubuntu:~$ ls -l /.dev/radio
lrwxrwxrwx  1 root root 6 2005-06-05 16:02 /.dev/radio -> radio0
``` 

Line-in sound is on so why i still can't hear anything. any help?

thx.

---

### Post by xalphas on 2005-06-05
Solved  :) After i wrote this message i find a page mentions about this situation. Here is it. 

Two steps and restart
```
sudo mousepad /etc/udev/rules.d/00_video4linux.rules
```

add this 

```
# make a symlink to the first radio device
KERNEL=”radio0&#8243;, SYMLINK=”radio”
``` 

Restart. Open line volume and enjoy the stations  :razz: 

source page : [http://www.wlug.org.nz/RadioTuner](http://www.wlug.org.nz/RadioTuner)

---

### Post by peter07 on 2005-07-12
I have got AverTV GO 007 Radio & TV card. I've tried to watch TV, but I still can't ([http://ubuntuforums.org/showthread....ighlight=AVERTV](http://ubuntuforums.org/showthread....ighlight=AVERTV))

Now I'm trying to listen radio. I've just installed gradio, radio etc. I olny gets error message:

> open /dev/radio: No such file or directory

Please help me. I'm newbie :)

---

### Post by xalphas on 2005-07-15
> **xalphas]Solved  :) After i wrote this message i find a page mentions about this situation. Here is it. 

Two steps and restart
```
sudo mousepad /etc/udev/rules.d/00_video4linux.rules
```

add this 

```
# make a symlink to the first radio device
KERNEL=”radio0&#8243 said:**
> http://www.wlug.org.nz/RadioTuner[/url]

Did you follow the steps for my radio configuration? It fixes the radio link and works well.

---

### Post by peter07 on 2005-07-15
Not yet ...

> 
sudo mousepad - what is it ??

I've tried:

> 
man mousepad 

but there is no manual entry :(

---

### Post by peter07 on 2005-07-18
I've made all steps form [http://www.wlug.org.nz/RadioTuner:](http://www.wlug.org.nz/RadioTuner:)

Firs I created 00_video4linux.rules ( using my methods ) than I added the text.

After reboot radio still doesn't work. Why???

I use radio/Tv tuner AverTv GO 007.

---

### Post by peter07 on 2005-07-19
I've tried also other ways to made links:

> ln -s /dev/radio0 /dev/radio

but with no result ....

<Help>

---

