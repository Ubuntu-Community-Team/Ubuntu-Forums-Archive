---
title: "Xubuntu on Ibm thinkpad"
date: 2007-10-17
forum: Hardware &amp; Laptops
---

### Post by katon on 2007-10-17
Hello i installad Xubuntu on an IBM Thinkpad with a 500 mhz processor  and 256 mb of Ram memory 
It runs okey, **[SIZE="5"]but it takes a LOT of time to start [/SIZE]** like 10 minutes

What is the problem ? maybe i need to reinstall the Xubuntu? maybe my hardware minimum requiriements don;t support this distro?

thank you very much

---

### Post by kerry_s on 2007-10-17
those specs should be fine. i would suggest trying the debian xfce4 as debian is better on older low resource systems.

[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-xfce-CD-1.iso)

when you get familar with the debian system, you can do a custom install with only what you need. i use a custom install on my 450mhz 256ram laptop and nothing is slow on my setup. :)

i do a base install using the net install and build up from there.
[http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso](http://cdimage.debian.org/debian-cd/4.0_r1/i386/iso-cd/debian-40r1-i386-businesscard.iso)

good luck!

---

### Post by katon on 2007-10-18
Okey thank you very much but i don't understand de diference between the two ISO's that you have put .

One is the debian Xfce that is light like XUBUNTU 
and the second_?

I also think i have a hardware incompatibility because after the boot after GRUB there are two Leds in the front of the LCD display that blink. 
So i don;t know what to do 
debian is easy to install as XUBUNtu?

---

### Post by MeanderingCode on 2007-10-18
Out of curiousity, what is your hard drive partition scheme?

I (out of some perverse need to have the relative saftey net of a windows partition that "just works" if i'm ever up that one creek) have a huge FAT partition and the fsck (filesystem check) for FAT is *slow*, so i disabled checking of that partition on boot.
Note: i would NOT recommend doing this for your root partition, or any partition that is ext or reiser based.

Hope you find a solution!!

BTW: The windows saftey net will be unnecessary once i learn a foolproof method of backup and restore for linux.

---

### Post by kerry_s on 2007-10-18
> **katon said:**
> Okey thank you very much but i don't understand de diference between the two ISO's that you have put .

One is the debian Xfce that is light like XUBUNTU 
and the second_?

I also think i have a hardware incompatibility because after the boot after GRUB there are two Leds in the front of the LCD display that blink. 
So i don;t know what to do 
debian is easy to install as XUBUNtu?


you only need the first 1, the second 1 is the net installer, for later when you get more familiar and may want to try a custom install, to may be squeeze out even more speed.

leds, you mean the hard drive activity lights?

debian is just as easy to install as xubuntu. only difference is less bloat(stuff you really don't need) with debian.

what is your think pad model? so i can see if i can find you a good guide.

---

