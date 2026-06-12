---
title: "T61p Nvidia Quadro 570M - Resolution problem"
date: 2008-05-27
forum: Hardware
---

### Post by alexbellinger on 2008-05-27
Firstly just wanted to say I'm really enjoying my journey into Ubuntu and you guys on the forums here rock.  I've been doing a lot of reading and it's been indispensable stuff.

I'm running Hardy on a T61p which has an Nvidia Quadro 570M graphics card. The card works fine, but does not list all the resolutions I would like and which I know work with the card - specifically 1280x768. 

I've followed a lot of threads here and have edited Display section of xconfig file and have also tried gksudo displayconfig-gtk, but can find no way of setting the resolutions I'd like.

Am I missing something or is this an issue with the nvidia linux drivers which I can't get around?

Many thanks

Alex

---

### Post by overdrank on 2008-05-27
> **alexbellinger said:**
> Firstly just wanted to say I'm really enjoying my journey into Ubuntu and you guys on the forums here rock.  I've been doing a lot of reading and it's been indispensable stuff.

I'm running Hardy on a T61p which has an Nvidia Quadro 570M graphics card. The card works fine, but does not list all the resolutions I would like and which I know work with the card - specifically 1280x768. 

I've followed a lot of threads here and have edited Display section of xconfig file and have also tried gksudo displayconfig-gtk, but can find no way of setting the resolutions I'd like.

Am I missing something or is this an issue with the nvidia linux drivers which I can't get around?

Many thanks

Alex

Hi and welcome, you may try and install the nvidia settings either by the command ```
sudo apt-get install nvidia-settings
``` in the terminal located under applications, accessories. Or via synaptic manager located under system, administration. Then try and use the alt, F2 keys and enter the command ```
gksu nvidia-settings
``` There you may adjust your resolutions.

---

### Post by alexbellinger on 2008-05-28
Thanks for this overdrank.  I've got to this stage by installing Envy, have the correct drivers for the Quadro 570M and have the the nvidia-settings in place.  

The problem is I'm after a resolution of 1280x768 which doesn't show up on the list. Only 3 of the current resolutions are set at 16:10 aspect ratio which is what I need for my T61p's WUXGA screen without them looking distorted. The highest resolutions are too small to read.

How would I go about adding 1280x768 so that nvidia-settings recognises it and then implements it?

Thanks again

Alex

---

