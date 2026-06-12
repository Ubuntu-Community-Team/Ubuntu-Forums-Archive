---
title: "new dvd writer install"
date: 2007-03-30
forum: Hardware &amp; Laptops
---

### Post by MikeyP on 2007-03-30
Hi,

I have ubuntu installed, on a couple of year old machine with a CD writer.

I want to upgrade to a DVD writer.

Do I just turn it off, replace it, turn it back on and Ubuntu will auto-magically recognise new hardware (like M$ W1nd0ze) or is there more to it?

cheers - Mike

---

### Post by Franscisco on 2007-03-30
Hi, 
I just replaced the cd writer for the DVD writer, and if a your dvd programs are working, then, you should be able to watch your movies.

---

### Post by MikeyP on 2007-03-30
> **Franscisco said:**
> you should be able to watch your movies.

That's cool! Excellent...

What about writing, presumably K3 and the others (i think thats what its called) will just *know* that its a dvd writer not a cd writer...

---

### Post by Franscisco on 2007-03-30
Ok, I just install programs from the ADD and REMOVE PROGRAMS from applications.
So if you go to applications, then add and remove programs, then, go to SOUND and VIDEO. Just look for any program you like, download it and install it. After that, go to the TERMINAL, copy and paste as follows  

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

hit ENTER
then, on the TERMINAL again, copy and paste as follows

sudo /usr/share/doc/libdvdread3/examples/install-css.sh

hit enter

ayou should be able to watch DVDs

---

### Post by Franscisco on 2007-03-30
Go here for more info. [https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2](https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2)

---

### Post by MikeyP on 2007-03-30
cool, thanks, i'll have another look in to it...

It was really **writing** dvds that i am talking about though (i am replacing my cd-rw with a dvd-rw drive, should it "just work" out the box, like in wind00ze?)

thanks again - Mike

---

