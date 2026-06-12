---
title: "Dell E1405 - black screen/freeze on install at 'configuring xserver-xorg'"
date: 2006-08-23
forum: Hardware &amp; Laptops
---

### Post by bjtuna on 2006-08-23
I'm trying to install Dapper LTS on my new Dell E1405 laptop using the Alternate install CD in "Text mode". The installation goes fine until the part where it installs and configures packages. When it hits "Configuring xserver-xorg..." the screen goes black (except for two oddly-placed rectangular groups of pixels that are lit) and the machine freezes. CTRL-ALT-BACKSPACE, ALT-F1... nothing brings it back.

Any help would be greatly appreciated!

---

### Post by freeridr on 2006-08-23
i am having the exact same problem. freezes on xserver-xorg config during install, with the same oddly-placed cursors.

i have an emachine T1862. i installed dapper on my slave drive a while back to try it out, dual booting with XP. i've been trying to install the alternate CD on my master drive and i get the aforementioned freeze-up.

i re-burned the iso image and attempted to re-install but it froze at the same spot, again.

---

### Post by farang.geek on 2006-08-28
I am having the same problem with a whitebox and my ibm thinkpad x31.  Weird enough, when i used the livecd everything works fine.  What gives?

---

### Post by arijarot on 2006-09-07
> **bjtuna said:**
> I'm trying to install Dapper LTS on my new Dell E1405 laptop using the Alternate install CD in "Text mode". The installation goes fine until the part where it installs and configures packages. When it hits "Configuring xserver-xorg..." the screen goes black (except for two oddly-placed rectangular groups of pixels that are lit) and the machine freezes. CTRL-ALT-BACKSPACE, ALT-F1... nothing brings it back.

Any help would be greatly appreciated!

I am interested the 640m with ubuntu... this is something that i came across which may help: running the install in safe mode ([http://ubuntuforums.org/showthread.php?p=1415526&highlight=dvd#post1415526)](http://ubuntuforums.org/showthread.php?p=1415526&highlight=dvd#post1415526))... :-k if you already solved the problem i would love to hear about your experiences/opinion with ubuntu on the 640m (answer poll if you want [http://ubuntuforums.org/showthread.php?t=252106)](http://ubuntuforums.org/showthread.php?t=252106))....

---

### Post by bjtuna on 2006-09-07
Quick update -

All those problems, I was having with the Alternate install disc. When I switched to the normal install disc, I just let it run its normal way and it installed perfectly. Then I configured/ran 915resolution to enable widescreen, upgraded to the i810 drivers instead of the VESA and I'm in style.

---

### Post by arijarot on 2006-09-07
> **bjtuna said:**
> Quick update -

All those problems, I was having with the Alternate install disc. When I switched to the normal install disc, I just let it run its normal way and it installed perfectly. Then I configured/ran 915resolution to enable widescreen, upgraded to the i810 drivers instead of the VESA and I'm in style.

that sounds great... thanks for sharing :D 

btw, does hibernate work?

what is an i810 driver vs vesa?

---

### Post by bjtuna on 2006-09-07
The i810 driver is the xorg video driver that works with the chipset in this laptop. The VESA driver is a generic, low-performance driver that's used by default.   Run "sudo apt-get install xserver-xorg-driver-i810" and then go into /etc/X11/xorg.conf and change "Driver vesa" to "Driver i810".

Hibernate definitely works, like a charm, if I use the Gnome menu to Quit and then choose Hibernate, and then wait a few seconds until the power turns off.

I'm still not really sure what the heck happens if I just close the lid without going through the Quit->Hibernate process, but when I find out I'll try to remember to come back here and let y'all know. Does anyone happen to know how to bring the system back after doing that?



> **arijarot said:**
> that sounds great... thanks for sharing :D 

btw, does hibernate work?

---

### Post by arijarot on 2006-09-07
> **bjtuna said:**
> The i810 driver is the xorg video driver that works with the chipset in this laptop. The VESA driver is a generic, low-performance driver that's used by default.   Run "sudo apt-get install xserver-xorg-driver-i810" and then go into /etc/X11/xorg.conf and change "Driver vesa" to "Driver i810".

Hibernate definitely works, like a charm, if I use the Gnome menu to Quit and then choose Hibernate, and then wait a few seconds until the power turns off.

I'm still not really sure what the heck happens if I just close the lid without going through the Quit->Hibernate process, but when I find out I'll try to remember to come back here and let y'all know. Does anyone happen to know how to bring the system back after doing that?

not a clue, but that's really great news that the hibernate works... thanks a lot for the info bjtuna  \\:D/

---

