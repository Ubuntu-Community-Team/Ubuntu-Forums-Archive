---
title: "Problem with Wifi card and screen res"
date: 2005-11-08
forum: General Help
---

### Post by Johan_ahx on 2005-11-08
Ok, i'll start witht the first problem:

I want to install my intergrated wifi card. I have a laptop a Fujitsu Siemens AMILO A1650, i already have a wifi scanner.

Second: how do i change the screen resolution? I can only choose 1024x768 and lower.

And, third: i want some recommendations for good video and mp3 codecs so i can play my mp3:s and watch movies on sites like big-boys.com. ;)

Thanks!

---

### Post by matthewv on 2005-11-08
[QUOTE=Johan_ahx]Ok, i'll start witht the first problem:

I want to install my intergrated wifi card. I have a laptop a Fujitsu Siemens AMILO A1650, i already have a wifi scanner.
[/QUOTE]

If you have the windows drivers for your card, try following the instructions [here.]("https://wiki.ubuntu.com/SetupNdiswrapperHowto/") Make sure you have ndiswrapper-utils installed and follow the part from installing windows drivers on..

> 
Second: how do i change the screen resolution? I can only choose 1024x768 and lower.

Never had to do it, but I think you type in a terminal 
```

sudo dpkg-reconfigure xserver-xorg

```
This will ask a few questions related to your graphics setup.

> 
And, third: i want some recommendations for good video and mp3 codecs so i can play my mp3:s and watch movies on sites like big-boys.com. ;)

Thanks!
I would install totem-xine and then the codecs from [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/)

---

### Post by Johan_ahx on 2005-11-08
[QUOTE=matthewv]If you have the windows drivers for your card, try following the instructions [here.]("https://wiki.ubuntu.com/SetupNdiswrapperHowto/") Make sure you have ndiswrapper-utils installed and follow the part from installing windows drivers on..


Never had to do it, but I think you type in a terminal 
```

sudo dpkg-reconfigure xserver-xorg

```
This will ask a few questions related to your graphics setup.


I would install totem-xine and then the codecs from [http://www.mplayerhq.hu/](http://www.mplayerhq.hu/)[/QUOTE]

Hi, I tried this command: sudo dpkg-reconfigure xserver-xorg

And efter I made the settings, Ubuntu locks in the boot-sequence after I rebooted. :(

---

### Post by jvictor on 2005-11-08
As for the graphics card, the first thing to do is look for the horizontal nad vertical refresh frequencies supported by ur montir and enter then in xorg.conf. 

and enter a resolution that u know ur monitor can support like 1152x864 

that must solve ur problem

---

### Post by rplantz on 2005-11-09
There's a recent thread on screen resolution change that goes into more details about how to do it.

Bob

---

