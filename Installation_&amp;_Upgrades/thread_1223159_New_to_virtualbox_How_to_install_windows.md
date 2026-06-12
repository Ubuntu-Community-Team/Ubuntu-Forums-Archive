---
title: "New to virtualbox: How to install windows"
date: 2009-07-25
forum: Installation &amp; Upgrades
---

### Post by niceguy123 on 2009-07-25
Hi,

I just installed virtualbox on 64 bit laptop under Ubuntu Jaunty. How do I now install windows. 

This computer originally came with Windows vista pre-installed and has a license for but I totally deleted it when it gave me a hard time installing Ubuntu as a dual boot.

---

### Post by merlinus on 2009-07-25
You will need original disks to install.  Perhaps you have an option to create this from a restore partition, or you may have to contact the OEM for same.

---

### Post by PhoHammer on 2009-07-26
Or one could hypothetically get a "generic" iso of winders on the interwebs and use one's
rightfully paid for key...

is it sacrilegious to speak of such activities here? Please don't hurt me if it is, I'm
just trying to help out a fellow ubuntee

---

### Post by merlinus on 2009-07-26
What you are calling "generic" translates to pirated, and has more than a fair chance of containing assorted vermin and virii.

So I do not think suggesting this is a good idea on these forums.

---

### Post by niceguy123 on 2009-07-26
OK, I installed VB and an old MS Windows XP that I had. 

Questions:

1. The windows screen is very small (about 1/4 my screen) is there a way to get it enlarged to full screen?

2. Where can I find temp files from web browsing on IE in Windows under VB?

---

### Post by brett- on 2009-07-26
If you install virtual box guest additions (an option within your vbox install) you will have full screen, large screen and seamless mouse support.

---

### Post by niceguy123 on 2009-07-26
> **brett- said:**
> If you install virtual box guest additions (an option within your vbox install) you will have full screen, large screen and seamless mouse support.

If I have already installed without that, can I change the configuration or do I need to reinstall?

---

### Post by merlinus on 2009-07-26
You will need to download the guest additions .iso, but can install it into your current vm.  There is info for doing this (Help/Guest Additions).

---

### Post by moster on 2009-07-27
Just when you start your Windows xp in virtualbox, select menu "Devices" and last option "Install guest additions". It will automatically load virtual CD and run setup in you XP.

---

### Post by ZhuaSD on 2009-07-27
After you go to devices at the top of the window and add guest additions iso to the CD-Rom, open the virtual environment and go to My Computer, and from their click on the guest additions icon.  That will open up the folder and you can click autorun.exe or whatever.

---

### Post by niceguy123 on 2009-07-27
Thanks, it worked.

---

