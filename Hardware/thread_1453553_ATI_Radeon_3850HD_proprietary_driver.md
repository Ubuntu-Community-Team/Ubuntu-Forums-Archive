---
title: "ATI Radeon 3850HD proprietary driver"
date: 2010-04-13
forum: Hardware
---

### Post by pluxon on 2010-04-13
Hello, I'm relatively new in Ubuntu so until I learn a thing or two about it a got myself a dualboot with windows.
The trouble is that after install I cannot enable full potential from my graphics card: ATI Radeon 3850HD.
First thing I did was to get the driver from AMD. I installed and I got a black screen (on a 1680x1050 LCD) with the message "Out of range". I started fiddling with it and connected a CRT and saw that the resolution was set to 1600x1200. So I changed to 1440x900 and then connected the LCD. Although it worked (enabled compiz effects'n all) the picture was a little blurry as it wasn't the native resolution for my monitor. So I fiddled some more until a screw up the system :mad: and had to format.
Since then I've been trying all sorts of things and can't seem to make it there.
I also tried enabling the driver from System>Administration>Hardware drivers. All I got was a black screen again. Since this was done from Ubuntu's repository the sh ./unistall-fglrx.sh didn't work so I formatted once more ](*,). (Not that this was the second time nor the last time)
Tell me please is there a hope for me or all my trying is in vain? ](*,)

---

### Post by khelben1979 on 2010-04-13
There's hope! Download the correct driver from the ATi webpage instead and go from there. Follow it's instructions and always do backups of the system before proceeding if it's needed.

By pressing ```
ctrl + alt + f1
``` you can access the first tty1 terminal. 

It's good knowledge if the X server fails to start.

---

### Post by pluxon on 2010-04-14
Thanks khelben1979
Accessing the tty1 terminal was helpful.
I managed to solve the problem I's almost a year now since it's been troubling me... The anguish, the sorrow... Ahhh.....
But not to make you wait, here's how I did it:
I installed once more the downloaded driver: ati-driver-installer-10-3-x86.x86_64.run, with:

     [FONT=Lucida Console]sudo sh ./ati-driver-installer-10-3-x86.x86_64.run[/FONT]

Before restart:

    [FONT=Lucida Console] sudo aticonfig --initial --input=/etc/X11/xorg.conf[/FONT]

(I have now a reached xorg.conf.fglrx-20 and xorg.conf.original-5)
Then:

     [FONT=Lucida Console]sudo aticonfig --resolution=0,1650x1050[/FONT]

Here I thought that I only need this resolution. Later I checked and I have other lower resolutions available but not higher.

Then:

     [FONT=Lucida Console]sudo aticonfig --vrefresh=0,56-75[/FONT]

(from my monitor specs)
Then:

     [FONT=Lucida Console]sudo aticonfig --hsync=0,28-83[/FONT]

(from my monitor specs)
And then (I don't know if this helped):

     [FONT=Lucida Console]sudo aticonfig --lcd-mode=full[/FONT]

I restarted and got a black screen again. Since I had a hunch that the video card thinks that my current monitor is the second monitor I changed the exit port and voila! I have 1680x1050 resolution with compiz effects enabled. In Windows the other emplacement was the first monitor. Anyhow, works great!:P

---

### Post by khelben1979 on 2010-04-14
Sounds good! Let's hope you manage to get some performance out of that driver then. :popcorn:

---

