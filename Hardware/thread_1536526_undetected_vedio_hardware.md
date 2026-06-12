---
title: "undetected vedio hardware"
date: 2010-07-22
forum: Hardware
---

### Post by aj47 on 2010-07-22
Hi,
ubuntu 9.x was working fine on my advent 7078 notebook untill i upgraded to 10.04 lts, hardware drivers are messed up and video hardware is undetected; i have to reboot in recovery mode, recovery menu will not show unless i press ctrl-alt-f5, instead a cursor in text mode keeps blinking.
when it boots, i cannot find where to fix / redetect hardware, i've run upgrade again many times, tried proproety hardware driver which shows no hardware

any help please!

---

### Post by quixote on 2010-07-24
To get the regular grub menu, press Shift while it starts booting, and the menu should appear.  (It's also possible to make it always appear, but we can deal with that later.)

Which video do you have?  If you don't know, run ```
lspci | grep 'VGA'      *[that's case sensitive]*
```Is other hardware also not detected?  If so, which?  And what model(s)?

Once there's a bit more data, we can start trying to deal with the problems. :D

---

### Post by uutnubu on 2010-07-25
Same problem here with a Compaq Presario 2200. 

The graphics info is:  
VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

Works fine with kernel 2.6.31-21 generic but not later versions 2.6.32-XX

The 2.6.32-XX kernels will not detect the monitor, it is identified as "unknown", resolution 1024x768, refresh rate 0 (that's a problem) and rotation Normal.  Earlier versions (2.6.31-XX) of the kernel properly detect the monitor

I'm not an expert, but is seems like something got broken when the kernel was modified to the 2.6.32.XX versions.

---

### Post by uutnubu on 2010-07-25
Solved!  Here' how I fixed mine.

Since I upgraded from Ubuntu 9.10 to 10.4 I still had grub installed, so I first upgraded to grub2 following[COLOR=Red][SIZE=3][COLOR=Black][ this procedure]("https://help.ubuntu.com/community/Grub2")[/COLOR][/SIZE].[/COLOR]

I then followed[ [SIZE=3][COLOR=Red]this process[/COLOR][/SIZE]]("https://answers.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+question/114877") which modified the grub boot process. 


 1) Hold down Shift while booting to enter the GRUB menu.
 2) Press 'e' to edit.
 3) Add "i915.modeset=1" after "quiet splash".
 4) Ctrl+x to boot.
 If adding "i915.modeset=1" to your boot parameters allows you to boot  successfully, you then need to enter the command above into a terminal  to make the changes permanent.
 If it works you need to update your grub2 kernel settings to have this boot parameter be permanent
 
You need to change the file /etc/default/grub from Applicationa&#8594;accessorie&#8594;Terminal type:
 gksudo gedit /etc/default/grub
 Change the row:
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 to
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=1"
 Then save and close then still using terminal type:
 sudo update-grub2
 Then reboot your pc.


 Works like a champ!   :D

---

