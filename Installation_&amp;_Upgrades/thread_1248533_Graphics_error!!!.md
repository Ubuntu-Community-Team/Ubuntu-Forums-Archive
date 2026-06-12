---
title: "Graphics error!!!"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by Vibin Lakshman on 2009-08-24
When I try to install Ubuntu 9.04 , in certain systems its showing after installation "Low graphics error " .
This is bit annoying , since its only for certain systems thats having Intel products[I think so]
And while wiki 'ing I got to have done more work on xorg.conf .
But sorry I dont know how to do that ?
Can anyone teach me how to do that in easy manner
I'll be so greatefull !!!!!

---

### Post by Sam Lars on 2009-08-25
From the machines that are showing this, could you post the output of
```
lspci | grep VGA
```

---

### Post by Vibin Lakshman on 2009-08-25
> **Sam Lars said:**
> From the machines that are showing this, could you post the output of
```
lspci | grep VGA
```
OK . Here it is ..

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)

---

### Post by Sam Lars on 2009-08-26
Look in your /etc/X11/xorg.conf file. You can do
```
sudo gedit /etc/X11/xorg.conf
```
in a terminal.
This is the file that you'll want to look at.
If you haven't already, I would suggest running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and see if that works first.

---

### Post by Vibin Lakshman on 2009-08-26
> **Sam Lars said:**
> Look in your /etc/X11/xorg.conf file. You can do
```
sudo gedit /etc/X11/xorg.conf
```in a terminal.
This is the file that you'll want to look at.
If you haven't already, I would suggest running
```
sudo dpkg-reconfigure -phigh xserver-xorg
```and see if that works first.
Yes , I do have that file , I dont think I need to execute the second one .[Sorry if I'm wrong]

I'll post some the contents of this file
[... Many more commented line are here , I just truncated inorder to give proper details]
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Mo# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSectionnitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Where should I edit ?

---

### Post by Sam Lars on 2009-08-26
Well first of all, did you paste that in there twice? It looks like you pasted it in once and then pasted it in the middle of itself... what you have there is not right. You should have this:

```
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
# sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
Identifier "Configured Video Device"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection
```

Try adding another line in your Device section so that it looks like this:

```
Section "Device"
Identifier "Configured Video Device"
Driver     "intel"
EndSection
```

If that doesn't work, post your /var/log/Xorg.0.log (please put CODE tags around it, it will be long)

---

### Post by Bölvaður on 2009-08-26
[http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=lspci+|+grep+VGA")

look at this thread

---

### Post by Vibin Lakshman on 2009-08-26
> **Bölvaður said:**
> [http://ubuntuforums.org/showthread.php?t=1130582]("http://ubuntuforums.org/showthread.php?t=1130582&highlight=lspci+%7C+grep+VGA")

look at this thread
Thank You , I preferred to take that optimal/safe solution .
Hope all works fine now onwards.

Thanks for everyone , who contributed solution, "Wish to have more problems in Ubuntu 9.04":lolflag:

---

