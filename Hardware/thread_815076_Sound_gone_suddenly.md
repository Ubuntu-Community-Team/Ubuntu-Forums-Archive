---
title: "Sound gone suddenly"
date: 2008-06-01
forum: Hardware
---

### Post by sink on 2008-06-01
I was trying to installing windows xp with virtual box but I cannot power on the new created one. It said I need to install a kernel module, so I install it with Synaptic Manager. It told me to reboot. After I reboot, the computer lost its sound, it seems that the driver is not loaded.
The virtual box still didn't worked too :(

I don't what's wrong, I removed the package I just installed , didn't work.
Then I want to try the solution in the thread " Comprehensive sound problem"

No luck either.

Anyone can help me? I just installed ubuntu for a week.
Have been good until today :(

---

### Post by sink on 2008-06-01
Please help :(

---

### Post by bobbob1016 on 2008-06-01
What type of sound card?
Also, just for clarification, you are running Ubuntu, and you are installing Windows in a VirtualBox?
It might also help if you could post what kernel module you installed.
If you followed a thread or guide or something posting that can't hurt either.

---

### Post by sink on 2008-06-01
Sound card: not sure...

I am using ubuntu 8.04

the kernel is the most updated one(just update a few days ago)

---

### Post by bobbob1016 on 2008-06-01
I meant which kernel module did you install?
Could you find out your sound card?  As in what type of computer are you using, and what model.  For example, Dell Inspiron (insert number here), or HP Pavilion (insert model number), then someone can google it and find your sound card and help you more.  You need to be as descriptive as possible.  Could you post what guides you followed?

---

### Post by sink on 2008-06-01
I just reinstall ubuntu again. 
It has sound now.

But I didn't update ubuntu yet.

I 'll see if it would work after I do all the updates

The device is HDA intel on the sound preference.

Thanks!

---

### Post by dasunst3r on 2008-06-02
There was a kernel update that made VirtualBox's kernel module not work.  To fix that, type this into the terminal: *sudo dpkg-reconfigure virtualbox*.  This will walk you through the setup procedures again and recompile the kernel module for your new kernel.

---

### Post by sink on 2008-06-02
Thanks, 

but I don't know why, I reinstall ubuntu and now virtual box works again( this time I install personal version of virtual box instead)

---

