---
title: "Automatix2"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by JamieC on 2007-01-11
Hey guys, 

I was wondering whether I can rely upon automatix2 to install the driver for (and configure) my nVidia graphics card (6200 LE), does anybody know?

I just removed Ubuntu because I had a 'bodge' set up with drivers and X configuration. It worked, but it was pretty much hit-and-miss and things were all over the place. I'm going to re-install it and try and configure everything optimumly. Is there anything a manual driver installation does the automatix2 won't?

Thanks in advance, Jamie.

---

### Post by Quillz on 2007-01-11
I've heard of people installing the nVidia drivers via Automatix2 and it's worked perfectly, but I've also heard of it being installed and nothing was configured properly. You might want to install the drivers separately and configure them via the Terminal.

---

### Post by JamieC on 2007-01-11
Thanks, hm. Will something simplistic like below configure (basic support for) my aforementioned (on-board) graphics properly?

I'd appreciate it if you didn't link me to some tutorial or other, I think I've seen enough.
 
```

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

```

---

### Post by penvzila on 2007-01-11
I think the file you can download from NVIDIA pretty much does what automatix2 does.  I haven't tried to install the drivers using automatix2, though.  It's pretty easy to do yourself.

---

### Post by dabl on 2007-01-11
If you're feeling a little adventuresome, here's a great place to get the Envy installer, which will put the latest Nvidia driver on your system for you.  Follow the instructions closely:

[http://albertomilone.com/projects.html](http://albertomilone.com/projects.html)


8)

---

### Post by JamieC on 2007-01-11
> **dabl said:**
> If you're feeling a little adventuresome, here's a great place to get the Envy installer, which will put the latest Nvidia driver on your system for you.  Follow the instructions closely:

[http://albertomilone.com/projects.html](http://albertomilone.com/projects.html)


8)

Thanks, I did play with that but with no result...

It was unable to detect my graphics card, or something of the other. I don't currently have an installation for a more detailed description of the error message.

Has anyone had success using onboard graphics nVidia 6200 LE?

---

