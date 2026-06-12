---
title: "no sound, newbie and fresh install"
date: 2005-06-25
forum: Hardware &amp; Laptops
---

### Post by Lambert on 2005-06-25
I have integrated audio into an rs480 msi mobo. It's a realtek ac'97 (alc658c). I'll get something different in the future but for now this what I have to use.

there is no sound coming from the speakers and connections are correct, they work when I dual boot into windows.

I understand how to install a driver in windows but am clueless about linux. can someone answer or point me to a website that gives a good tutorial on this subject? I also have an ati x200 driver I need to install in an .rpm package.

---

### Post by andlinux21 on 2005-06-26
do a search on HOWTO and sound and there is a good guide to point you in the right direction.  My sound worked fine on my desktop but not on either of my laptops (DELL Latitude and MICRON Transport)

---

### Post by Jiilik on 2005-06-30
Sound works fine for me on the ati rs480m2-il using hoary 5.04.  It's using the snd_atiixp driver.

However the IDE driver (atiixp) is broken and will slow down IO on the system so badly that it can make your sound server break if you're in KDE.

Updating to 2.6.11 fixes this for me, but introduces a problem with my cdrw.  I have to disable my cdrw now in order to boot. *sad*

---

### Post by linuxrobot on 2005-06-30
Hello,

I'm in the same situation as Lambert.
Newbie to Linux, new install, sound won't work (except in Windows), dual boot with Windows, & sound board integrated with mobo.  

What do you mean by HOWTO and sound search?  On google.com?

Thanks!

**LinuxRobot**  8)

---

