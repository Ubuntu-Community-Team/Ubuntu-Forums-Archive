---
title: "installing xubuntu on a kohjinsha SAF100 ?"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by bjaz on 2009-08-30
I bought this kohjinsha SA1F00 secondhand in Japan, it has 512mb of ram and plenty of diskspace.
[http://www.biztoolbelt.com/2006/12/kohjinsha_sa1f00_umpc.html](http://www.biztoolbelt.com/2006/12/kohjinsha_sa1f00_umpc.html)

yet i can't seem to install xubuntu, the screen goes back after the cursor bounces back and forth. i'm thinking it might be an unsupported graphic card issue, i've no clue and can't seem to find anything on the subject. if it is indeed a graphic card issue, does this mean i'm doomed to have to use the japanese windows xp (not fun)- or might there be things to try ?

would something like this be useful ?
[http://www.notebookera.com/notebook-drivers/Kohjinsha-SA-Notebook-AES_Linux_LX_02.01.0100-Drivers-for-Linux-Unoffical_132430.shtml](http://www.notebookera.com/notebook-drivers/Kohjinsha-SA-Notebook-AES_Linux_LX_02.01.0100-Drivers-for-Linux-Unoffical_132430.shtml)

apparently some people have managed to install something on this machine
[http://groups.google.ie/group/kohjinsha-sa1f00-users/browse_thread/thread/ad2d04600c05b7be](http://groups.google.ie/group/kohjinsha-sa1f00-users/browse_thread/thread/ad2d04600c05b7be)

but i'm completly lost here

thanks for your help

ben

---

### Post by bjaz on 2009-08-30
i managed to complete an install with an alternative live cd i had of jaunty.
yet when i try to boot, the screen goes completely black. i tried the autooveride graphic problems option, to no avail.

apparently i must have messed up the japanese windows install, which is no big problem since i was planning on using this machine with xubuntu only.
maybe i should do a full erase reinstall once i'm sure xubuntu can work on this machine

booting into gparted won't display properly either. what can i try to fix this machine's display, hoping it's just a setting issue ?

b

---

### Post by bjaz on 2009-08-31
i really hope there is a way to fix this. from, what i remember, changing the display options involved working with the xconf file, but i reqlly don't know how to do this via command lines, or what i should try in this case.

i also made an ubuntu live CD, but since xubuntu is probably already installed, and i can't use gparted to erase repartition the disk, this doesn't really help

b

---

### Post by bjaz on 2009-08-31
argh. I just found out that the pc was sold without a japanese windows XP CD, despite having a licenced copy, serial etc... which means that I can't reinstall.
if i can't get ubuntu or xubuntu working, i'm in a pretty tight spot. 
wouldn't mind at least having access to G-parted so i can see what the existing partitions look like, but display is odd.

can anyone out there please help me out a little ? 
i think xubuntu's installed, but can't display

thanks in advance for your help

ben

---

### Post by Siona on 2009-10-20
Hey bjaz,

 I am in a similar situation as you are: Bought a second hand Kohjinsha SAF100 from Japan and trying to install a linux distribution on it.  

 I was able to install Ubuntu but only using an external display. 

 I cannot use the laptop screen (it's totally black) when I am using X Windows. But it can display command line environment all right.

 Are you still there? Did you find any solution at all? 

 Best.

---

### Post by bjaz on 2010-05-08
I'm still here, sorry for the late late answer- 

 Upgrading the ram to 1GB improved things a bit.
It now works under Xubuntu, yet it's very very slow to boot the soundcard is't fully supported : the phone out and line in won't work.

the windows is gone, and since it was one of these recovery partition type of installs, I can't re-install it.
it's sad that windows worked better than ubuntu in this case, and i really wish I could run a regular Ubuntu version- I'm probably going to buy some secondhand eeepc or similar in the future, as this machine isn't really going anywhere, it can hardly read a video file, no phone out, can't stream flash videos hence not ideal for a portable, travel machine...

ben

---

### Post by bjaz on 2010-05-11
I finally gave up on xubuntu and standard ubuntu for this machine-doesn't work and I wasn't getting any help to try to fix things-

 installed crunchbang, wifi, sound, display, mousepad, phone jack worked out of the box

i'm still working on the japanese language support though

hope this helps


ben

---

