---
title: "OpenGL &amp; Radeon Xpress 200m"
date: 2008-07-25
forum: Hardware
---

### Post by systemshock869 on 2008-07-25
Hi, I'm pretty much a Linux noob.  Trying to learn though.

I have downloaded the Linux driver from ATI.com, and really have no idea what to do with it.  There are some instructions on the site, but they are really hard to follow for someone with no Linux background.

The file is a .run and it is called 'ati-driver-installer-...'
When I try to run it, it says that it is a binary file and opens it in Kate.

Can anybody help me?  I really want OpenGL!

---

### Post by uraldinho on 2008-07-25
1. cd /your_download_directory here 
2. sudo ./ati_installer_full_name_comes_here.run
3. click on OK, or Next in the installation steps. 

To test whether it's installed properly try fglrxinfo command, you should get something like this: 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon Xpress Series
OpenGL version string: 2.1.7415 Release

If you get something to do with Mesa it means your installation didn't work somewhere.

---

### Post by systemshock869 on 2008-07-25
```
debbie@debs-linux:~/Desktop$ ls
ati-driver-installer-8-7-x86.x86_64.run  install_flash_player_9_linux
c01035677.pdf                            n_v1linux
firefox-2.0.0.14                         n_v1linux.tar
debbie@debs-linux:~/Desktop$ sudo ./ati-driver-installer-8-7-x86.x86_64.run
[sudo] password for debbie:
sudo: ./ati-driver-installer-8-7-x86.x86_64.run: command not found
debbie@debs-linux:~/Desktop$ sudo ati-driver-installer-8-7-x86.x86_64.run
sudo: ati-driver-installer-8-7-x86.x86_64.run: command not found
debbie@debs-linux:~/Desktop$
```
that's what i get..

---

### Post by systemshock869 on 2008-07-28
any suggestions?

---

### Post by stchman on 2008-07-28
> **systemshock869 said:**
> Hi, I'm pretty much a Linux noob.  Trying to learn though.

I have downloaded the Linux driver from ATI.com, and really have no idea what to do with it.  There are some instructions on the site, but they are really hard to follow for someone with no Linux background.

The file is a .run and it is called 'ati-driver-installer-...'
When I try to run it, it says that it is a binary file and opens it in Kate.

Can anybody help me?  I really want OpenGL!

I used to own a laptop with that video card and the restricted driver in Hardy works well even enables Compiz.

---

### Post by markbuntu on 2008-07-28
Try the directions here, Method 2, follow them very carefully and you should have your driver working:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

Once you have done that, you can try some of the tweaks here to improve performance:


[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by systemshock869 on 2008-08-01
```
sh ati-driver-installer-8-7-x86.x86_64.run --buildpkg Ubuntu/hardy
```
on this line, do i say 'Ubuntu' or 'Kubuntu'?  i'm running Kubuntu.. sorry for the newb question

---

### Post by systemshock869 on 2008-08-01
i followed the directions, and have it installed now.  thanks for the link!
however, it isn't working well at all.
1.) testing with super tux kart.. it runs really slow and there are artifacts all over the place.
2.) scrolling in firefox is slow (the only program i've tried)
3.) least important, but still annoying, is that my icons in the bottom right corner are bigger, so two rows won't fit.. they are all lined up side by side.  and i have a new one, the 'hardware drivers' program, which stays there all the time.

yeah it looks like everything is generally going really slow

---

### Post by systemshock869 on 2008-08-05
can anybody help me out?  the computer is painfully slow now.  especially 3d applications.

---

### Post by markbuntu on 2008-08-06
If you tried any of the tweaks in the second link, put them back the way they were or delete them from your xorg.conf file and run 

aticonfig --initial -f

---

