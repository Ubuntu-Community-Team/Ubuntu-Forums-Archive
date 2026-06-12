---
title: "Video display problem"
date: 2008-12-01
forum: General Help
---

### Post by jventre on 2008-12-01
Ever since I upgraded to 8.10 I am having a problem with my video display coming on. When I boot the system I don't see the startup screens. I enter my USER ID and Password on a black screen and the system completes its boot process. After several minutes the display finally appears. If I turn the monitor off and leave the system for a while then turn the monitor back on the display does not appear for at least several minutes. Same problem occurs when coming out of suspend or hibernate modes. I did not have this problem on 8.04. I'm using a MAG flat screen monitor on an IBM desktop system. Has anyone else experienced this problem and know a solution>

---

### Post by miniyak on 2008-12-02
i have basically the same problem right now in hardy and had a similar problem when i upgraded to intrepid (my solution then was going back to hardy) i can get past the hardy problem by starting in recovery mode but im not going to be happy with starting in recovery mode every time ( i could change the bootloader to run recovery mode by default, that could be acceptable, or maybe one of the older kernel versions. that was just upgraded and could be part of the problem but i dont really know) we are using the same brand (MAG) monitor however mine is a old crt. i didn't try logging in on the black screen so i dont know if the system actually boots or not in normal mode but i think ill try it next time to see how similar our problems are.... how can you tell that the system boots up after logging btw?.....(the problem with intrepid i got past the login than every thing went black and all you could see was the waiting cursor(frozen) this was on a sony projection tv though not the mag monitor)...   im sorry i couldn't be of more help.... my system is a dell dimension2350 2.2ghz 512mb ram ....(new to forums...how do i put sys.info at the bottom of my replys?)

---

### Post by jventre on 2008-12-02
I know the system boots because I can see the hardrive light flasking after I enter my ID/PW.  I leave the system on and after several minutes the display appears with the system sully booted.

---

### Post by Grolsche on 2008-12-02
I did have a similar problem and found that the system did that when i installed the ATI binary x.org driver.

I dont know if this is the same problem with yours but perhaps its worth checking out any drivers you have installed and install each one at a time witha  reboot to check. I found that if I removed the Ati driver and rebooted, it rebooted normally.

---

### Post by miniyak on 2008-12-03
i just found if i boot my system with the last kernel versions everything works fine (though keep in mind i am using hardy so this might not work for it might be a different problem all together im not sure exactly why this is happening) the permanent solution would be changing the boot loader config file to boot the older kernel version first or if you duel boot just select the older one instead of the newer one. 

first you should see if this solution works for you. if you have a full install(no other operating systems)when you power on your comp. you should see your bios screen(prob. displays the brand of your comp. also where you boot from cd) after that the grub boot loader should appear for about 3 seconds you need to press the esc button within those 3 seconds in order to see the boot options then you can pick and older kernel option( in my case i chose "ubuntu 8.04.1, kernel 2.6.24-21-generic" yours would say 8.11vs8.04) you may need to choose a different one but you can use your digression to figure out which one is needed. If this does not work and you have the same issue, our problem are prob. not the same. if you can boot in with out the black screen then all you need to do is change the boot loader to the older version. 

their are multiple ways to change the grub boot loader. the way i used was by going to the add remove option under applications then searching for "grub" under system tools than downloading startup-manager(there are others but thats the one than i choose.)  the program should show up in administration under the system options. the program is strait forward change the kernel version than close and it should automatically boot that way.

btw im not using any ati hardware or divers that i know of.

---

### Post by jventre on 2008-12-05
The problem is I don't see the boot screen either.  I don't see the old BIOS screen that tells me to hit F1 to enter the Setup and things like that.  The problem apparently starts before the OS even boots and that is what bothers me since I'm not sure why upgrading to 8.10 whould have affected that.  Also, Ubuntu is the only OS on teh system so there is no dual boot option available.

---

### Post by miniyak on 2008-12-05
thats not good... maybe your monitor just died, try with another monitor if you can or see if your monitor works on an other computer. Also by accident the power setting on the psu might be set wrong this happened with a friends comp once,(not sure how) its a little red switch on the back of your cpu, that is if your using a desktop not a laptop... it should be set to 115 i think

---

### Post by jventre on 2008-12-10
Determined the problem is with teh monitor itself and not the OS.

---

