---
title: "Hardy Heron RAM Issue"
date: 2008-05-05
forum: Hardware
---

### Post by Nikoli4 on 2008-05-05
I recently upgraded the RAM in my Acer Aspire 9410 Laptop and now I can't boot into Hardy Heron.  I am dual booting with Vista and that works fine, even recognized all 4 gigs of my new RAM on a 32 bit system.  Hardy Heron worked fine with my old 1 gig of RAM.  Now the ubuntu load screen comes up but as soon as the GUI comes up the screen goes crazy and I can't see anything but colored lines.  I tried to reinstall both Hardy Heron and Gutsy Gibbon and they start loading but then it stops and just gives me a command prompt.  It almost seems like a video problem since it happens when it loads the OS, but it didn't start until I upgraded the RAM.  Maybe it has something to do with the memory sharing.  I have no clue.  Does anyone have any ideas?  

Here's the memory I installed
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820231165](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231165)


Any help would be much appreciated!!  I miss my cube.... :cry:


Thanks
Nik

---

### Post by 1875 on 2008-05-05
Have you run memtest on your system ?

---

### Post by Nikoli4 on 2008-05-05
yes and it passed just fine.  Took forever too.  lol.  That was my first thought too.  I am going to run another one just to be safe.

---

### Post by 1875 on 2008-05-05
Can you select how much ram is used for video memory in your BIOS ? If you can try setting different amounts and see if that improves things. Also try booting with only one stick of your new RAM, if no luck try other stick. Do you know what graphics chip your lappy has ?

---

### Post by cubeist on 2008-05-05
If you go into your boot settings in grub (when grub loads press e)try editing out the two options "quiet" and "splash" then carefully watch it boot to see where it hangs (or goes all crazy) and if there are any error messages or codes.

Also, if you take the new ram out, does it boot ok?

---

### Post by Nikoli4 on 2008-05-05
Ok.  I tried one stick at a time and it worked fine.  I changed the bios settings for shared memory and still wouldn't work with both sticks in.  I wrote down the error I get.  It says "Kinit: no resume image doing normal boot."  I'm running the intel 945 express chipset for graphics.

---

### Post by cubeist on 2008-05-05
> **Nikoli4 said:**
> Ok.  I tried one stick at a time and it worked fine.  I changed the bios settings for shared memory and still wouldn't work with both sticks in.  I wrote down the error I get.  It says "Kinit: no resume image doing normal boot."  I'm running the intel 945 express chipset for graphics.

First, are you using the restricted driver? Try booting in on one stick and install the restricted driver.  Then generate a new initramfs ... the easiest way is to reconfigure usplash like this:
```
sudo dpkg-reconfigure usplash
```

then shutdown, put in the second stick (make sure both are clicked in all the way...sometimes it takes a measure of force, but I am sure you know this step!)

Anyway, if that doesn't work, which it probably won't, then there are some boot options that might help (just add them to your boot line)
Caution! Even though I have personally used all of these commands at one point or another on my hp laptop, some of these options may cause conflict and may even render certain parts of your system not to run (like a fan!) So use at your own risk...
Anyway, the options:
```

noapic nolapic noirqpoll nosmp noapci

```
Anyway, there are others too but I can't remember them all...these ones have to do with hardware interrupts

---

### Post by Nikoli4 on 2008-05-06
Alright.  I tried the sudo dpkg-reconfigure usplash with no luck.  I managed to write down the entire error I'm getting. 
 
Starting up ...
Loading, Please wait ...
usplash: setting mode 1152x864 failed
usplash: using mode 1024x768
kinit: name_to_dev_t(/dev/disk/by-uuid/7204a8af-1a04-41a6-b9b0-8ea8c2e9ac1f) = sda1(8,1)
kinit: trying to resume from /dev/disk/by-uuid/7204a8af-1a04-41a6-b9b0-8ea8c2e9ac1f
kinit: no resume image, doing normal boot...

then the screen comes up with just colored lines....  and kicks me back out to a prompt


Anyone have any clues what might cause that?

---

### Post by cubeist on 2008-05-06
ok maybe, you need to tell grub to use a specific screen resolution for booting...I had to do this once with a laptop...the problem is I can't quite remember what I did...sorry... try searching the forums for DRI or grub resolutions...I'll look through my old posts to see if I can find what it is...

Edit!
Found a good link
[http://www.mepis.org/node/2992](http://www.mepis.org/node/2992)

so for you, maybe start with trying "vga=791"

---

