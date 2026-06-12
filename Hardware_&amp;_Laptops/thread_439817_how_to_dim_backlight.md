---
title: "how to dim backlight"
date: 2007-05-11
forum: Hardware &amp; Laptops
---

### Post by rygar on 2007-05-11
my laptop battery is dying way too fast in ubuntu.  xp will dim the backlight when i disconnect the ac power, ubuntu does not!  there is no option for it in 'power management'.  how can i get ubuntu to dim the backlight when its running on battery?

i can't dim the backlight with the Fn key either.  i thought it might be due to my keyboard layout (i have a toshiba satellite m45-s355, i choose satellite 3000 because it was the closest), but some of the other Fn functions work.

optional question:  i know this has been asked a lot, but any other tips for saving battery power?  i've heard a lot of different tips, but i would imagine some of them are really efficient whereas others don't do that much...

---

### Post by misfitpierce on 2007-05-11
laptop should have a FN button and up and down brightness keys... google dim backlighting for your model... as for power.... Set cpu to powersave inside ubuntu when off power source and dim lighting... most you can do!

---

### Post by jjordan on 2007-05-11
So many laptops so many configurations.  Without going into a diatribe of why laptop power management SEEMS to work better under Windows.  Let me say that there is still room for improvement in this area of Linux however it is going to require cooperation of laptop manufactureres to really work it out.

Anyway, what kind of laptop (mfr and model), what desktop (KDE, Gnome or Xfce), and what program are you using for power management (too many to list but right click on the icon and look at the name or the "about". 

In the most basic form most laptop backlights can be directly controlled by typing:
**echo X > /proc/acpi/video/GFX0/LCD/brightness**
into a terminal
Where X is a number from 1 to 8, 8 being brightest and 1 being dimest. (0 being off)

Some laptops and installations may require a diffrent path.

-j

---

### Post by rygar on 2007-05-11
I am using a Toshiba M45-S355

I use Gnome as well, and right now the only power management software I use is in system -> administration -> power management

there is no folder LCD in /proc/acpi/video/GFX0
there are folders for DD01 through DD05, all which contain a file 'brightness'

but 'cat brightness' on any of them displays '<not supported>'
:(

---

### Post by elias@cpaefs.com on 2007-05-28
I hope this helps:

[http://ubuntuforums.org/showthread.php?t=316358&highlight=toshiba+m45]("http://ubuntuforums.org/showthread.php?t=316358&highlight=toshiba+m45")

The omnibook module was the only thing that work for me.

---

### Post by rygar on 2007-05-29
fabulous, thanks so much!  i can now change my brightness by doing

cd /proc/ominibook
sudo su
echo 0 > lcd

is there any way i can tell my computer "if you start running on battery, execute this command", and likewise "if you are plugged in, run this command", so it will automatically lower and raise brightness?

---

### Post by rosegarden78 on 2008-01-19
Or type the following command in a terminal:

xgamma -gamma 0.75

If that doesn't work you need to install xgamma from the repos.

I have posted my own solution here on setting it up:

[http://ubuntuforums.org/showthread.php?p=4168042#post4168042](http://ubuntuforums.org/showthread.php?p=4168042#post4168042)

---

