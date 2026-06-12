---
title: "Need help asap"
date: 2008-11-24
forum: General Help
---

### Post by damagedmafia on 2008-11-24
HI i installed the ubuntu 8.04 hardy heron onto my 900series eeepc

i also used this bash script to try to fix the bugs that i encountered after the install its called niceeepc 1.4

found on [http://wiki.eeeuser.com/niceeepc](http://wiki.eeeuser.com/niceeepc)

now i also googled for the computer to shut down properly

i have a screenshot of the gedit mod i did and what i tired to do

screenshot.png = what the halt script looks like now

screenshot1.png is what i tried to do

this is the site [http://www.tommcfarlin.com/2008/07/11/u](http://www.tommcfarlin.com/2008/07/11/u) ... ee-pc-900/ that gave me instructions

tell me how to repair this please

my msn is [email]mrtezz2006@hotmail.com.au[/email]

i need this done and if some one can do graphical slide as to the other mods that i need for the eee pc it would be great and appreciated thanx


[IMG]http://img383.imageshack.us/img383/5715/screenshot1eu3.png[/IMG]
By [damagedmafia](http://profile.imageshack.us/user/damagedmafia) at 2008-11-24


[IMG]http://img291.imageshack.us/img291/2271/screenshotgg7.png[/IMG]
By [damagedmafia](http://profile.imageshack.us/user/damagedmafia) at 2008-11-24

---

### Post by geirha on 2008-11-24
You didn't follow the instructions properly, it says to add the line ```
rmmod snd-hda-intel
``` at the specified position, not to remove a bunch of important lines further down. Restore the file and only add that one line. If you didn't take a backup of it before you edited, you'll need to reinstall the package that installs that file. ```
sudo aptitude reinstall initscripts
```

---

### Post by damagedmafia on 2008-11-24
this update didnt work there are still lines missing

---

### Post by ad_267 on 2008-11-24
To restore the script:

```
sudo dpkg -P --force-depends initscripts
sudo apt-get install initscripts

```

---

### Post by damagedmafia on 2008-11-24
still not working it says its already the newist version

---

### Post by easoukenka on 2008-11-25
Have you tried installing the eeebuntu version?

---

### Post by nigj on 2008-11-25
Hi!
I'm not sure that you want to install the eee version. Ho am I to deside for you?! Well I have tried several versions buntu 8.04 for eeepc included. Now Im running ubuntu 8.10. I downloaded an ISO image and made a USB boot disc. It actually worked right away with some small bugs of cource. My wired network connection worked just fine, but I had to fix my wireless connection. I used this link [https://help.ubuntu.com/community/EeePC/Fixes](https://help.ubuntu.com/community/EeePC/Fixes)

Why didn't I like ubuntu for eeepc? I like my desktop as clean as possible.

---

