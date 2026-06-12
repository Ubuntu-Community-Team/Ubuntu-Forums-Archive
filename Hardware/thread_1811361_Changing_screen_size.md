---
title: "Changing screen size"
date: 2011-07-24
forum: Hardware
---

### Post by moorhead98 on 2011-07-24
Hello, I have a desktop monitor with a screen resolution of 1600 by 1200. 
About three hours ago I updated the os from 10.04 to 10.10. 
I was planning to upgrade it to natty, but ive noticed that the picture displayed on the screen is too big for the screen itself. Everything, from the gnome panel to full screen apps like firefox are too big, and hang off the left side. 
I went to the monitors application to check if the resolution was correct. It showed 1600x1200 (the correct resolution), but it still looked funny.
The Plymouth boot loader image thing is messed up as well.
Also, all the text on the computer seems unrealistically smaller. 
Any ideas? I intend to fix this problem, then upgrade to natty.

---

### Post by moorhead98 on 2011-07-25
The desktop is a 32-bit Acer Aspire M1610, if that helps

---

### Post by moorhead98 on 2011-07-31
Ok, i just updated to 11.04, and the size is still messed up. Its really annoying.
Anybody have _any_ ideas?!

---

### Post by moorhead98 on 2011-08-09
no replies...

---

### Post by Metaxa on 2011-08-10
Can you post the output of:

Sudo xrandr

and

sudo lshw -class display

This will help in solving your problem.


Regards, 

Metaxa

---

### Post by moorhead98 on 2011-08-10
> **Metaxa said:**
> Can you post the output of:

Sudo xrandr

and

sudo lshw -class display

This will help in solving your problem.


Regards, 

Metaxa

Heres the output: 

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 1600 x 1200, maximum 1600 x 1200
default connected 1600x1200+0+0 0mm x 0mm
   1600x1200       0.0* 
   1280x1024       0.0  
   1024x768        0.0  
   800x600         0.0  
   640x480         0.0  
```and

```
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0
       resources: memory:d0000000-dfffffff memory:fdde0000-fddfffff ioport:df00(size=128)
```Does that help?

---

### Post by moorhead98 on 2011-08-21
Still no replies... People are lazy

---

### Post by moorhead98 on 2011-10-01
last call for anyone who is going to help

---

### Post by realzippy on 2011-10-01
Try to install the SIS driver.

Here is a thread which explains a little:
[http://ubuntuforums.org/showthread.php?t=1847685&page=3](http://ubuntuforums.org/showthread.php?t=1847685&page=3)
you can start with post #22 ....download driver to your
*Downloads* folder,unpack it,then you can run same commands.

---

### Post by moorhead98 on 2011-10-01
> **realzippy said:**
> Try to install the SIS driver.

Here is a thread which explains a little:
[http://ubuntuforums.org/showthread.php?t=1847685&page=3](http://ubuntuforums.org/showthread.php?t=1847685&page=3)
you can start with post #22 ....download driver to your
*Downloads* folder,unpack it,then you can run same commands.

I sorta got stuck on step two there. I downloaded the driver, then extracted it into the downloads folder. Was I supposed to add a folder or something?

---

### Post by realzippy on 2011-10-02
Post the error,then we will see...

---

### Post by moorhead98 on 2011-10-09
heres what I did:

will@will-desktop:~$ sudo cp ~/Downloads/32-bit/*.so /usr/lib/xorg/modules/drivers
[sudo] password for will: 
cp: cannot stat `/home/will/Downloads/32-bit/*.so': No such file or directory


What did I do wrong?

---

