---
title: "Please help to install graphic driver"
date: 2008-07-06
forum: Hardware
---

### Post by pedramslhr on 2008-07-06
hi
i have a geforce 6200 TC
and i have downloaded a graphic driver from nvidia website for that.
but when i attemp to install it using sudo sh command some messages indicate a problem with kernel
and the "nvidia-installer.log" file is like this:
[[COLOR="Blue"]http://pedram.fileave.com/NewTextDocument.txt[/COLOR]]("http://pedram.fileave.com/NewTextDocument.txt")

---

### Post by Sef on 2008-07-06
Have you tried to install it from System > Administration > Restricted Drivers Manager?

---

### Post by pedramslhr on 2008-07-07
I'm using Hardy Heron 
and I checked System>Administration>Hardware Drivers

a component "NVIDIA accelarated graphics driver (latest cards)"
is listed there and i have enabled it.
but i think it is not very good for me and i need to update my driver through the file that I have downloaded

---

### Post by Sef on 2008-07-07
> I'm using Hardy Heron
and I checked System>Administration>Hardware Drivers

a component "NVIDIA accelarated graphics driver (latest cards)"
is listed there and i have enabled it.
but i think it is not very good for me and i need to update my driver through the file that I have downloaded 

Have you uninstalled that driver?

---

### Post by sdennie on 2008-07-07
> **pedramslhr said:**
> 
a component "NVIDIA accelarated graphics driver (latest cards)"
is listed there and i have enabled it.
but i think it is not very good for me and i need to update my driver through the file that I have downloaded

An nvidia 6200 should be completely supported by the driver in Hardy.  Upgrading to the newest driver from the website will not only not improve anything, it will make the maintenance of your machine more complicated.  What specifically makes you think the driver in Hardy is not sufficient?

---

### Post by wyattjo on 2008-07-07
i just made another post about this but i think i'm having the same problem... i can't get my resolution up past 640x480

---

### Post by AmericanYellow on 2008-07-07
You should just use the driver that Hardy comes with.

As for the resolution, you should install the Nvidia Settings Manager (think its called Nvidia X Server Settings and is found in 'Add/Remove Programs'). Once you have that installed you can change the resolution ot the correct one.

There is also another menu that allows you to change resolution, select your video card mode, and your monitor model, but it was removed from the "System" menu. If you look around the forums, you will can find how to access it using the terminal (I've forgotten)

---

### Post by pedramslhr on 2008-07-07
> Have you uninstalled that driver? 
no, should I do this? and does it differs to do this considering the log file?
> An nvidia 6200 should be completely supported by the driver in Hardy. Upgrading to the newest driver from the website will not only not improve anything, it will make the maintenance of your machine more complicated. What specifically makes you think the driver in Hardy is not sufficient?
I want to know have I can install a new driver just for more info
and
my Monitor is at a low refresh rate 50, and I think it can help me

---

### Post by starcannon on 2008-07-07
If a manual install guide is what you really want then I'll post mine here, I will say though, that as has been stated, the drivers in the Ubuntu Package Manager are fine and will serve you very well. That said, here's a link to my guide. If you follow it precisely, don't skip steps, you will have a fully functional latest release Nvidia driver running.

[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

GL

---

### Post by pedramslhr on 2008-07-08
> If a manual install guide is what you really want then I'll post mine here, I will say though, that as has been stated, the drivers in the Ubuntu Package Manager are fine and will serve you very well. That said, here's a link to my guide. If you follow it precisely, don't skip steps, you will have a fully functional latest release Nvidia driver running.

[http://ubuntuforums.org/showpost.php...71&postcount=6](http://ubuntuforums.org/showpost.php...71&postcount=6)

two questions:
1-I'v  modified xconfig file and screen was corrupted. then i used "nvidia-xconfig" command and made it better.
but now resolution is 800*600, there is no component listed in "Hardware Drivers" and when I attempt to run "NVIDIA X Server Settings" it displays a message like this:
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

2-and can you please about step 7 in your manual

tanx

---

### Post by pedramslhr on 2008-07-09
i'm waiting yet.
and when starting ubuntu it displays the shell envirenment and after some moment the login screen is desplayed. but before this a message is displayed about low graphics mode.
no one wants to answer me?

---

### Post by pedramslhr on 2008-07-09
I also tried this:
[http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)
 but the result is same:
[http://pedram.fileave.com/NewTextDocument.txt](http://pedram.fileave.com/NewTextDocument.txt)
and just another entry is added to boot menu

---

