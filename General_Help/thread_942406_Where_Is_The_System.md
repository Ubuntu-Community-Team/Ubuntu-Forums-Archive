---
title: "Where Is The System?"
date: 2008-10-09
forum: General Help
---

### Post by matey3 on 2008-10-09
Hello;

I just posted a thread (in multi-media sec.)asking folks about my sound problem and youtube (any video on the Net has no sound but mp3s locally play fine?) Any way I would like to know where in Ubuntu Hardy 8.04 (xdm) I could find my system or hardware list?
I pulled the System--Administration--Hardware Drivers menu up but the list was empty saying there are no prop. hardware installed?
I like to know where I can see my hardware listing? (like in windows system-device manager)?


Thank You!

---

### Post by Calmatory on 2008-10-09
you could try ```
lspci
``` and ```
lshw
``` to print information of the devices the computer has.

---

### Post by _sAm_ on 2008-10-09
I would try latest version of Flash to see if that gives you sound in youtube.

If you want a GUI program to show you a list of your hardware try: sysinfo or hardinfo

sudo apt-get install sysinfo
sudo apt-get install hardinfo

The cli program lshw also has an GUI called lshw-gtk

---

### Post by Yellow Pasque on 2008-10-09
The Hardware drivers dialog is for proprietary drivers.
For your Flash sound, have you installed libflashsupport yet?
```
sudo apt-get install libflashsupport
```

---

### Post by matey3 on 2008-10-09
Thanks a lot guys. I got the sound working... it was the flash update/support. 

as for sys info. I installed sysinfo and I can see most of the HW info.
What I really wanted to do was to change my display resolution. I got this crappy onboard sis 661 mirage  video card (booted in vista to get the info) dooop! but I can't get a good res. in Ubuntu! every thing is so big and nasty! eekh
I downloaded a file with no extension from sis.com but I dont know how to install it?
Can you guys help me set up my resolution please?
Thank You Very Much indeed...

---

