---
title: "nvidia driver wont enable properly"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by espo111 on 2007-07-08
In my second install of feisty fawn, when i try to enable the restricted nvidia driver, i get the infamous "failed to start x server"  and "no screens found."

message and xwindows will not start up.

then i run "sudo dpkg-reconfigure xserver-xorg" and i can start x & gnome. but still no effects. 

I am going after "desktop effect" and it has worked in previous installs, and a few live CDs.

how do i get my GeForce 4200 to work properly. 

any ideas??

---

### Post by easoukenka on 2007-07-08
sounds like your having a problem similiar to mine.  i am using kubuntu though but came here for some help as i am just baffled.  check out my post at [http://kubuntuforums.net/forums/index.php?topic=3084836.0](http://kubuntuforums.net/forums/index.php?topic=3084836.0)

it may help others fix your problem as i have posted all of my specs already

---

### Post by espo111 on 2007-07-08
> **easoukenka said:**
> sounds like your having a problem similiar to mine.  i am using kubuntu though but came here for some help as i am just baffled.  check out my post at [http://kubuntuforums.net/forums/index.php?topic=3084836.0](http://kubuntuforums.net/forums/index.php?topic=3084836.0)

it may help others fix your problem as i have posted all of my specs already


mine seems a little different than yours, my system does not hang, it gives me the xorg diagnostic report screen, and tells me about the log file it created. 

and all i do is re-run reconfigure and it works, but as soon as i ren-enable the nvidia drive it dies. I even tried the envy program, nothing.

i am going to try the legacy drive to see what it does, but i did not have to do that the last time. 

why cant ubuntu just use the regular nvidia driver install package!
--------------------------------------------------------------------------------------------------------------------------------
03:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4200] (rev a2) (prog-if 00 [VGA])
        Subsystem: CardExpert Technology Unknown device 1219
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 11
        Memory at e2000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=128M]
        Memory at d8000000 (32-bit, prefetchable) [size=512K]
        [virtual] Expansion ROM at d8080000 [disabled] [size=128K]
        Capabilities: <access denied>

---

### Post by rhmeyer50 on 2007-07-09
Good Day,
I just went through this with  the Fiesty live CD install and a new Nvidia card. What I found was that I could see the desktop when I used the safe mode selection from the live CD menu. I continued all the way through the install in safe mode and when I got done it booted fine from the hard disk. I later used Automatix to find the correct driver for my card. HTH
Best,
Rob

---

### Post by espo111 on 2007-07-09
> **rhmeyer50 said:**
> Good Day,
I just went through this with  the Fiesty live CD install and a new Nvidia card. What I found was that I could see the desktop when I used the safe mode selection from the live CD menu. I continued all the way through the install in safe mode and when I got done it booted fine from the hard disk. I later used Automatix to find the correct driver for my card. HTH
Best,
Rob


Automatix fix it! but i also removed all nvidia drivers first, so..... 

thanks for the tip, Automatix seems cool.

---

