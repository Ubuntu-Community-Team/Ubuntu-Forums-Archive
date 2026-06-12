---
title: "I love Ubuntu but.... help me please!!!!"
date: 2008-05-14
forum: Hardware
---

### Post by PhyChris on 2008-05-14
ok so ill start slow... (for people who don't want to read the full story theirs a summery at the bottom) i got this laptop Panasonic Toughbook CF-48 with ati radeon mobility 9000. now when i first got this laptop i installed windows xp MCE (because i have an xbox 360) now Panasonic
had drivers 4 my video card but thay were old and did not work right with windows xp mce so i pointed my web browser to ati's driver website and downloaded there driver and tried to install it.
the damn thing would not install it said it could not detect any
compatible hardware!! so after many sleepless nights googleing i found something a little utility that would change the ati driver
so it would work with Panasonic's version of the ati radeon mobility 9000. operantly Panasonic changed the device-id or somthing so u would have to go to them 4 the driver. so i ran the
little utility and everything worked perfectly... ok now im sick of windows and wanted to try Linux on my Panasonic Toughbook CF-48 . Ubuntu seemed like a good place to start and guess what i love it i love it so much/ i want to take it behind the middle school and get it pregnant!!! except 4 one thing im having the same problem i had b4 Ubuntu did not detect my video card no 2D/3D acceleration now im a complete Linux newbee and dont know how to fix the problem so if some one could help me please i really want Ubuntu to work 4 me so i can show it off to my friends but this damn video card thing is starting to ruin it 4 me.

so a briff summery of the problem: Ubuntu wont detect my ati radeon mobility 9000 Panasonic's version. is their any way to force the normal ati radeon mobility 9000 driver... because thats what i had to do in windows xp

---

### Post by Nampla on 2008-05-14
under screens and graphics look for the vesa-compliant video driver and test it.  that may work otherwise try

try: sudo dpkg-reconfigure xorg

and keep selecting and testing the different drivers for video cards.

Good Luck

---

### Post by PhyChris on 2008-05-15
sorey  but im a complete newbee  how do i get there " under screens and graphics look for the vesa-compliant video driver and test it."


and i tried that other thing and this is wat i get...   

"user@user-laptop:~$ sudo dpkg-reconfigure xorg
 sudo: unable to resolve host user-laptop     "

---

### Post by pacrep on 2008-05-15
Go through all the questions using: ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Should bring you back to commandline then: ```
sudo restart
```then you get the option to select you graphic driver.

Ctrl + F1 for the terminal, then use the first command

---

