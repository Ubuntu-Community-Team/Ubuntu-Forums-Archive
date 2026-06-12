---
title: "[SOLVED] wanted second screen, now i have none!!!"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by Don_Shifty on 2008-02-15
To watch a movie i wanted to connect a second monitor. i configured it to be attached on the right and gave it some resolution. after that i got a message, that the changes would take effect after a logoff. as soon as i logged of the laptop screen was blank but i could see the attached screen. since i couldn't access anything from the attached screen i rebootet the laptop. now every time i boot ubuntu i get a blank screen (or 2 blank screens) as soon as it should show the logon screen!
i can boot it in safe mode, but obviousely it then is text-based and i can't change any screen settings!
i am using a nVIDIA GeForge Go 7600!
PLEASE HELP, I'M DESPERATE!!!!

---

### Post by Yellow Pasque on 2008-02-15
Somethimg's messed up in your /etc/X11/xorg.conf file.

Try this to reconfigure with a text-based guide:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Or you can manually edit the file with:
```
sudo vim /etc/X11/xorg.conf
```
To use vim, press the 'i' key to put it in a normal text editing mode, and when you're done press 'Esc' and type **:x[Enter**]

---

### Post by defmer on 2008-02-15
A simpler method is to use backed up xorg.conf file. check the /etc/X11/ folder for a backup copy of xorg.conf (It created this automatically).

1) rename the existing copy  "sudo cp xorg.conf xorg.conf.backup2"
2) reanme the eariler backuped up copy:- "sudo cp xorg.conf.backup xorg.conf"

THE BACKUP FILE NAME MIGHT BE A BIT DIFFERENT. this should get you GUI on your primary monitor. you can them compare the current and backed up (created is step one) and see what went wrong.

---

### Post by Don_Shifty on 2008-02-16
thanks a lot for the replies! but i don't have a /etc/x11/ folder!!!
in /etc/ there are /xdg and /xml that begin with "x". none of them contains a *.conf.backup - file!
what to do?
is there a way to access the linux partition from my XP (dual-boot)?
i appreciate your help a lot!
thanks!

---

### Post by Yellow Pasque on 2008-02-16
Linux is CaSe SeNSiTiVe.

etc/**X**11/xorg.conf

---

### Post by Don_Shifty on 2008-02-16
On second try solution #2 worked just fine!
For everybody who has the same problem:
there are 3 config files:
xorg.conf
xorg.conf.1
xorg.conf.2
xorg.conf.3
i think #1 is the oldest. i tried #3 first, but it only worked with #1. 
thaks a lot for the help!
take care, shifty

---

