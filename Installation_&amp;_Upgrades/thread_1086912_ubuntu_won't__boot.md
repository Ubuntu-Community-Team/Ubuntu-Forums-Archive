---
title: "ubuntu won't  boot"
date: 2009-03-04
forum: Installation &amp; Upgrades
---

### Post by enoc22 on 2009-03-04
i am having a problem with installing ubuntu from CD.
i want to have a dual boot with windows and have two hard drives(one for each OS)
I've used WUBI and ubuntu will boot fine
but i wanted to install from cd
the installation goes fine(i install ubuntu on the hard drive that doesnt not have any windows things), but when i restart it gets stuck. it will not show any boot options at all. and i have to go through and install windows again.
am i doing something wrong

Any help would be great
Oli

---

### Post by jee_bee on 2009-03-04
seem like u didn instal grub....

---

### Post by jee_bee on 2009-03-04
seem like u didn instal grub....
u ave no grub bootloader and windows doesn know linux yet
u ave two choice ...first u can instal grub from ur instal
cd .... secondo... u can make windows know then linux is 
in tha house and add it to the windows boot loader by using
easybcd in windows   BUT ... i need more info... [COLOR="DarkOrange"]are u using 
XP or Visa[/COLOR]  [COLOR="Teal"]...hard-drive ...windows should be on (hd0,0)
and linux on (hd1,0) (its not a law we just need to be sure..)[/COLOR]
[COLOR="PaleGreen"]u gonna do more window or more linux ??[/COLOR]

---

### Post by enoc22 on 2009-03-04
Alright
I am using windows XP.
Windows verses Linux usage is going to be about equal.
How do i install GRUB from the Ubuntu CD?(doesn't that install with ubuntu along with everything else)

this is just a small side note, while re-installing Windows the installation says it doesn't see any previous version of windows. although there is still a "C:/" file left

Thanks for the Help

Oli

---

### Post by xtremethegreat1 on 2009-03-04
While you install Windows, make sure that you haven't hibernated the system because in that case Ubuntu setup won't detect your windows installation. But in that case only Ubuntu should start up at boot time, which is not your case. The problem definitely is something else. Ubuntu does automatically install the grub bootloader while installing.

---

### Post by uvmedraco on 2009-03-04
does your windows install boot up? and what exactly happen in the bootup stages does it just load into XP, if so check the boot devices menu on the bios screen:popcorn:

---

### Post by jee_bee on 2009-03-05
-To reinstal use the live cd, boot from it...
(do not install just boot the live cd) 

Be shure than windows is instaled.... (u dont give us enough info!!!)

-Open a terminal... 

-Type in:  > grub [COLOR="Navy"]press enter[/COLOR]
          
          > root (hd1,0) [COLOR="Navy"]press enter [/COLOR]
          
          > setup (hd1)  [COLOR="Navy"]press enter [/COLOR]

          > quit [COLOR="navy"]press enter [/COLOR](It will close the terminal) 

-Reboot...

[COLOR="Red"]Grub is now instal[/COLOR] do that and let us know and we will see what to do after

---

### Post by enoc22 on 2009-03-05
I will try that. 

right now i have ubuntu running using WUBI(but i don't want that)

when i installed (or tried to install)ubuntu from cd the last two times, after the system restarts it goes up to the point where the bios either boots from CD or Hard drive then stops and wont do anything else. i thought it might just be the cd so i went in and changed to boot order to boot from hard drive. but it just did the same thing it would not boot to any OS, ubuntu or windows

BUT i am going to try again to install from CD
i will let you know the results

---

### Post by jee_bee on 2009-03-05
the instruction i give u are for instaling the bootmanager on 
the secondery hd that it... im pretty shure than ubuntu is instal
in ur pc semm like dosen see the grub bootmgr i guess:???:

---

