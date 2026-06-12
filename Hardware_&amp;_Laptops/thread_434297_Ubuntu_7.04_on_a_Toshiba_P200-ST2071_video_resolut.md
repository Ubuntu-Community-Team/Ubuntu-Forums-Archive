---
title: "Ubuntu 7.04 on a Toshiba P200-ST2071 video resolution problem. Solved!"
date: 2007-05-05
forum: Hardware &amp; Laptops
---

### Post by DonLorenzo on 2007-05-05
Greetings all.

I installed Ubuntu 7.04 on a brand new toshiba P200-ST2071. This is one of the configure-it-yourself models. I chose a T5500 CPU, 2GB memory, 80GB disk, Intel 3945 WiFi, Bluetooth. The motherboard purports to have the Intel 950 Graphics Media Accelerator (GMA) chipset.

After booting the Ubuntu 7.04 CD, I said: Install.
The installer walked me thru wiping the partition table (and Vista) then installing Ubuntu.

Remove CD, Reboot.
When it came up, the screen resolution was at 1280x768.
Toshiba says it is capable of 1440x900.
I ran the update package tool. It picked up a few replacement packages and installed same.

I read these forums at great length looking for a solution.
Everything I read was kludgy. something about the 915resolution thing.
I installed the 915resolution package, but did no manual steps toward configuration.

While messing with the package manager I notice by happenstance that two packages appeared to be very similar. One was installed, the other not.
xserver-xorg-video-i810 at service level 2.1.7.4 was installed.
xserver-xorg-video-intel at service level 2.1.9.94 was not. 
The commentary for both packages hinted at support for the same chipsets.
I said, why not? I can rebuild it if I screw it up.
I installed the xserver-xorg-video-intel package at service level 2.1.9.94.
This caused the package manager to uninstall the other.

Reboot!
The video comes up correctly at 1440x900. It's beautiful!
The question in my mind at this point is: Did the xserver-xorg-video-intel driver make use of the 915resolution driver to achieve the correct screen resolution?
Or does the -intel driver have everything it needs to do the job?

What I suspect is that the installer chose the wrong xserver package.

In any case. it works for me.

Now, can anyone give me a hint on getting some sound outta this machine.

The purported chipset is:
82815G (ICH7 Family)High Definition Audio
I have followed some of the other threads on the subject and it would appear that there is no consistent fix for the problem.

Comments? Questions?

---

### Post by bscott3125 on 2007-05-25
This solution also worked for me in getting the full resolution on a Toshiba u205-s5002 for anybody else searching like I was :)

---

### Post by DonLorenzo on 2007-05-27
> **bscott3125 said:**
> This solution also worked for me in getting the full resolution on a Toshiba u205-s5002 for anybody else searching like I was :)

Do you, perchance, have a solution to the sound problem?
I assume you also do not have any sound. Right?

---

### Post by blop on 2007-06-02
also need help with sound on this lappy...

i got sent this link by a forum user....has not helped me as im to noob to get the commands to work...

[http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php](http://linux.dobeyracing.net/how_to/toshiba_p200_laptop/Linux_on_Toshiba_Satellite_P200.php)

---

### Post by sprint4 on 2007-06-03
blop

That is my "How-To", and it's open for improvements.  ;-)  

What kind of hardware do you have, and what kind of problems are you experiencing?

Is this just a sound problem?

---

### Post by Martin Witte on 2007-06-21
I have a p200-13F, solved the resolution with this howto. To fix the sound as many others suggested here please read [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_here](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_make_sound_works_here) with_Intel_Integrated_Sound_Cards

---

