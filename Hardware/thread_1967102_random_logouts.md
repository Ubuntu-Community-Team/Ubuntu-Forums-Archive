---
title: "random logouts"
date: 2012-04-27
forum: Hardware
---

### Post by lusephur on 2012-04-27
Just updated to 12.04, was running 11.10 with no issues. 
But today, there seems to be an issue when playing flash vids on youtube, or 4od in which I'm booted back to the login screen.
I did try a beta of 12.04 a month back, but since I was busy, I just reverted back to 11.10 but it seems the issue has remained. 

pastebin of dmesg here
[http://pastebin.com/TehZW6YS]("http://pastebin.com/TehZW6YS")

Running 12.04 on an Acer 6920g with nvidia 9500gm card. 
I suspect something is wrong with ither the nvidia driver or xserver, but I can't be sure.

---

### Post by cmfrtblynmb on 2012-04-28
I have the same issue.

Nvidia card, 64bit.

---

### Post by snahrck on 2012-05-04
Also have this problem. GeForce 9800 GT and fresh install of the 32bit version. I tried both drivers available in restricted drivers dialog. It occurs in many situations, using netbeans, using chrome, using firefox...
Also ctlr+alt+f1 shows only a black screen.

An user pointed that it works with Nouveau driver:
[http://ubuntuforums.org/showthread.php?t=1969914&highlight=nvidia+random](http://ubuntuforums.org/showthread.php?t=1969914&highlight=nvidia+random)

How can we switch while this isn't fixed?

---

### Post by lusephur on 2012-05-14
Tried the following suggestion/solution
> [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096)
Specfically this 
> [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096/comments/15](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/973096/comments/15)
Grabbed the 290 nvidia driver, (While the link near the bottom of the page is for the amd64 driver, the i386 version is easy to obtain.) hopefully it solves the problem till an improved updated driver is released. 

Grabbed the package, and in my case entered in a terminal
 > sudo dpkg -i nvidia-current_290.10-0ubuntu2_i386
Rebooted and fingers crossed. Alas an update will change the driver. 

What more worrying though, is this is a pretty big issue, looking over the past week through launchpad, this has been occuring for many people for a few months. (Myself, I encountered it as mentioned in the OP.) 
On the Nvidia website a number of threads exist. Not sure if the fault lies with nvidia or xorg. But it is a massive showstopper.



update, once again crashed/logged out 
restored nvidia driver to curennt, and followed this > 

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/980519/comments/65](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/980519/comments/65)

---

