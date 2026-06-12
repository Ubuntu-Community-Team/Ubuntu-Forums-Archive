---
title: "Nvidia d video doesn't work"
date: 2010-03-20
forum: Hardware
---

### Post by francescogondolin on 2010-03-20
Hello Everyone, 
this time I really need your help. I'm new to Ubuntu (just two months) and I describe the situation as good as I can.

System:

Laptop: Aspire 5935G
Video: NVIDIA GEFORCE GT 130M
UBUNTU VERSION: 9.10

What happened:
1) I wanted to install compiz (3d desktop...), downloaded it and then I was asked to install Nvidia accellerated graphics driver (Version 185)
2) I installed the drivers and at the restart, everything loads ( I can hear the startup music) but the screen is just black (no way to enter into the terminal with ALT-F1)

SO.....I probably messed up the situation even more

3) I looked around internet and I saw that I coould try:
 sudo dpkg-reconfigure xserver-xorg but it just DO NOTHING

4) I made sudo apt-get purge compiz*

5) I decided to further risk trying:
sudo apt-get purge nvidia*
sudo apt-get purge xorg*

But really nothing changed. Now I'm using the live CD, since I'm not able to enter in the GRUB menu anymore (by the way why is it so fast!!!???). I was wondering:

a) How can I backup all my data? Just copy-paste the /media/allstrangestuffmountedhere to an external hard-ddrive?
b) The Live CD settings works, can I export them on the system?

Hope someone can help, from monday I need to work again and I'm really worried!


------------------------------SOLVED!!!!------------------------------

For now I've found a solution:

1) BACKKKK-UP

    a) My folder on the PC is: /media/2342423483749749/home/my_folder

    b) So I went to: "cd /media/2342423483749749/home/my_folder"

    c) And after that "sudo chmod -R 777 my_folder" (in this way I had the permission to enter and copy)

    d) I copied from HardDisk to external harddrive (all my data are safe!!)


2) BRING LIVE CD SETTINGS TO MY COMPUTER

   A) Go, from the live CD, in "/media/2342423483749749/etc/"

   B) "sudo chmod -R 777 X11" (In this way you can change and move your video setting files in your Ubuntu - the one installed on the system)

   C) Copy them in a New Folder just to be sure

   D) Go, from the live CD, in "/etc/" (the live CD folder for etc)

   E) "sudo chmod -R 777 X11" (so you can copy these files)

   F) Copy the files from the live CD settings "/etc/X11" to your Hard Disk folder "/media/2342423483749749/etc/X11 (in this way you just tell to use the default settings)


This worked for me, I'm a newbie and don't really know why it works, I just know it does for me :). Hope can help someone

---

### Post by vervelover on 2010-07-31
Are you sure you're not using the intel driver with this method? do you have nvidia-settings installed? does it say you are using the nvidia card?

---

