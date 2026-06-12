---
title: "PS/2 Mouse not working"
date: 2005-07-01
forum: Hardware &amp; Laptops
---

### Post by vasanth on 2005-07-01
Hi,


    My PS/2 mouse does not work in ubuntu.its an gigabyte made.
Any ideas?

Thanks
Vasanth

---

### Post by WaTTz on 2005-07-01
as funny as this may sound.....try unplugging it and plugging it back in while ur computer is on..i had the same problem and it worked when i did this..i have no idea why

---

### Post by vasanth on 2005-07-04
Hi,
    thanks for ur idea.I tried it and of no use.i've another problem.i could not find the xmms or xine in my system. is there an application to find and install the packages and also cannot use KDE.


thanks 
vasanth

---

### Post by Yagisan on 2005-07-04
[QUOTE=vasanth]Hi,


    My PS/2 mouse does not work in ubuntu.its an gigabyte made.
Any ideas?

Thanks
Vasanth[/QUOTE]

Could you run```
lsmod | grep psmouse
``` in a terminal and see if you get a line that looks similar to > psmouse                21260  0
If you get no output from that command run the following command from a terminal ```
sudo nano /etc/modules
``` and check to see if you have **mousedev** and **psmouse** listed. If any of those two are missing, add them to the end of the file, with mousedev listed before psmouse. Reboot and see if your mouse works. If not, try another mouse.

Please avoid plugging and unplugging PS/2 Keyboards and Mice while the system is on. It can blow the fuse on the motherboard which is a more expensive problem to fix.

---

### Post by vasanth on 2005-07-04
Hey,

       Thanks for ur reply.i'll try that.And one more help.I could not find xmms or xine installed in my system.i've only the installation CD(No internet).I could not find xmms and xine in cd either.i tried totem and one moremusic player(from the menu) but they say that no plugin(decoder) is available.should i query for mpg123 decoder(if so how to query the installed debs)'im new to debian like system.Please help.


Thanks
Vasanth

---

### Post by Yagisan on 2005-07-05
[QUOTE=vasanth]Hey,

       Thanks for ur reply.i'll try that.And one more help.I could not find xmms or xine installed in my system.i've only the installation CD(No internet).I could not find xmms and xine in cd either.i tried totem and one moremusic player(from the menu) but they say that no plugin(decoder) is available.should i query for mpg123 decoder(if so how to query the installed debs)'im new to debian like system.Please help.


Thanks
Vasanth[/QUOTE]
xmms is not on the CD so you will need the internet for that. Nothing on the CD can play MP3 files, you can find instructions here [http://ubuntuguide.org/](http://ubuntuguide.org/) for xmms

---

### Post by vasanth on 2005-07-11
i've tried checking the /etc/modues and the modules were loaded properly.Is there anything i can do to get a working ps/2 mouse?

---

### Post by Yagisan on 2005-07-13
[QUOTE=vasanth]i've tried checking the /etc/modues and the modules were loaded properly.Is there anything i can do to get a working ps/2 mouse?[/QUOTE]Could you try another mouse ? I once had a Microsoft "PS/2" mouse. It had the PS/2 connector, but it didn't speak the PS/2 mouse language, even Windows 98 could not use it. Logitech seem to work fine, so borrow another mouse and test that. If it works, get a new mouse.

---

### Post by daxumaming on 2005-07-23
I'm also having problems with my PS/2 mouse. It just won't work. Ps/2 & USB keyboard no problem, just my mouse. I know it's not the mouse coz it's working in vector linux & win xp also installed on other partitions. i did what was said above, everything looks good.

where and what other files do i need to check or edit? help please.

---

