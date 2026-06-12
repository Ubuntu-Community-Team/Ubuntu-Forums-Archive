---
title: "Geforce MX440 on Ubuntu"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by ziadoz on 2007-01-19
How can I setup my Geforce MX440 64MB (AGP) on my Ubuntu box? I couldn't figure out what drivers I needed, or what alterations (if any) I would need to make to my X settings.

Cheers, :-D

---

### Post by Ravanous on 2007-01-19
Have you looked at [this document]("http://doc.gwos.org/index.php/Latest_Nvidia_Edgy")?

I found it quiet useful in setting up my nvidia card under Edgy.

---

### Post by SebMKd on 2007-01-19
I've just installed Ubuntu 6.06 on a old rig for my sister (K7S5A, XP 1900, 256MB, MX440-SE) and used the Alternate CD for that. I was surprise that I wasn't required at all to install any driver. The screen resolution, size, ..etc were fine!!! :-D 

However, I've made a lot of research before-hand and bumped into the many pages written by same author as the one Ravanous refers to (Tseliot). Among all these pages I think it's worth looking at his own website: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) . There you'll find a script that seems to solve many problems! :cool: 

Good luck!

---

### Post by EvilMarshmallow on 2007-01-19
I've been working on getting a GeForce 3 Ti 200 to work.  Judging by the size of your card (64 MB) it's probably fairly old like mine.  This means that you might need to use the legacy drivers rather than the ones that are obvious in synaptic (depends on the model number on the card, I'm not exactly sure where the cutoff is though).

Here's some info that might help you:
[http://www.ubuntuforums.org/showthread.php?t=338526](http://www.ubuntuforums.org/showthread.php?t=338526)


SebMKd,

If you didn't do anything extra to your sister's computer, you may find that 3d apps choke, even though your hardware is capable of running them.  My card installed (it's the only video on the machine) but not with good drivers... just regular VGA, no hardware acceleration at all.

---

### Post by ziadoz on 2007-01-19
Thanks for all your help. I've got it sorted, all works fine now. :)

Does anyone know if my card will run compiz?

---

### Post by CheeseEatingBulldog on 2007-01-19
I am running a 1300+ chip with the same card you are using (and the same card I used for a friend's rig, although he runs dapper and it auto-finds the lot) on an edgy install, I also run beryl/emerald and thus have been pissing about with my video drivers, and it turned out for me that using the legacy drivers was NOT the solution and rather the opposite.( I do however have to run the nvidia-setup for the driver module each time I get a kernel update, no biggie, command line in safe mode and /.the file supplied by nvidia). There are pages out there with this question on google, I am on my laptop now and not on my main machine, thus no links.

So, use the normal drivers first, that solved not only all my beryl problems but also my resolution setup.

---

