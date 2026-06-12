---
title: "Cannot get login screen"
date: 2009-07-02
forum: Hardware
---

### Post by match002001 on 2009-07-02
Hello all,

I need your help. 

Last night I wanted to watch "Killer Klowns From Outer Space" on my TV from my Laptop (Toshiba A105-S2061) with Jaunty installed on it. I noticed that the ATI Control Panel was not installed so I installed it. Then when I tried starting it up it said something along the lines that I didn't have the correct driver. Then I restarted. It shows the splash screen but when it get to the actual login page it screws up and it looks like its trying to load but graphics are all off.

I've tried booting to safe mode and having it try and fix xorg but nogo. any other suggestions would be awesome please.

-Match

---

### Post by match002001 on 2009-07-02
Update:

I tried restoring to a backup of Xorg through the Recovery Menu under prompt but nogo :( Oh and low and behold of all things else that could fail. My CD-ROM is dead now...

---

### Post by match002001 on 2009-07-02
Update:

IT'S ALIVE!!!!

Okay well issue was not resolved the way I wanted it but it all worked out in the end. 

Thankfully I was smart and set the /home to mount on a seperate partition. I booted to USB ISO from GRUB and reformatted the / partition and told it to use my second partition for /home. After install even my theme for the desktop works perfect. 

Lesson learned: Make a seperate partition for your /home to mount. if something goofs up you can always reformat the / partition :)

Have a nice day everyone.

---

