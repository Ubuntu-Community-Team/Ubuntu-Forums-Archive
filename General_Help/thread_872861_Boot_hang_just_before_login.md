---
title: "Boot hang just before login"
date: 2008-07-28
forum: General Help
---

### Post by fmcguire on 2008-07-28
Hello All, 

I am a little new to UBUNTU but I am learning quickly. I am using Ubuntu Hardy on my New Dell Inspiron 1525. I am running XP pro and UBUNTU and booting with GRUB. Everything has been Great since the install (since May) until.....

Yesterday I was doing some changes of my themes and had downloaded some from gnome-look.org and things were going fine. I then decided to change some of the login screens, first I changed to one called BLACK MESA and it worked fine because I rebooted and looked at it. I then changed to one called FBI and then rebooted to look at it and it would not boot down. So I powered it off manually (I know now it was a bad thing to do) 

So I rebooted and it hangs just before login screen. The screen is blue (color of desktop background) and the mouse is the spinning wheel and I can move it but it just hangs there.

I rebooted to recovery mode and tried all 3 options and no change. I booted to the CTL+ALT+F1 to get the terminal and tried the sudo dpkg-reconfigure xserver-xorg and I still get the same problem.

Is there a way I can change login screens from the command line?

Please Help

---

### Post by gjoellee on 2008-07-28
is it kernel 2.6.26-20 that hangs??? try use kernel 2.6.26-19 instead if it is so...

---

### Post by fmcguire on 2008-07-28
> **gjoellee said:**
> is it kernel 2.6.26-20 that hangs??? try use kernel 2.6.26-19 instead if it is so...

It is 2.6.26-19 I also have the two previous and got the same result.

---

### Post by caljohnsmith on 2008-07-28
Not sure if this will help with your login screen problem, but it is worth a shot:
```
sudo dpkg-reconfigure gdm
```
Also, you could boot from the Live CD, mount your Ubuntu partition, and then look at the end of /etc/log/dmesg to see what might have caused the system to hang. This assumes that the last time you logged into Ubuntu is when it hanged; it won't work if your last login was through the recovery mode, because then the dmesg file won't have the errors from when your system hanged.

---

### Post by fmcguire on 2008-07-28
Well believe it or not I fixed it. I can't believe it!!!


I figured that the theme I tried to use was corrupt or something along those lines.

 Soooooo I booted the live CD and I went to /etc/gdm/gdm.conf-custom and edited it with nautilus by changing GraphicalTheme=FBI_Terminal to GraphicalTheme=HumanList and then saved and rebooted and EUREKA!!!!

It works Great now. 

Many thanks to all that responded or even considered it. 

THANK YOU!!! and God Bless

-Fred-

---

