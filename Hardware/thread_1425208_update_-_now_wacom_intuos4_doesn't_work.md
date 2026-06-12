---
title: "update - now wacom intuos4 doesn't work"
date: 2010-03-08
forum: Hardware
---

### Post by confubar on 2010-03-08
I let my update manager install some kernel stuff - must have lost what I did last December - with great difficulty and much gracious help - to get my new intuos4 working. [-o<
I have been trying to retrace my steps, got this far:
I backed up 10-wacom

user@dell-desktop:~$ sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/user/Desktop/10-wacom.bak

and then overwrote it with the contents of Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt
 
then 
determined that I have generic kernel
user@dell-desktop:~$ uname -r
2.6.28-18-generic

install linux-headers generic

user@dell-desktop:~$ sudo apt-get install linux-headers-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

I can't get the source code tar or go into the unpacked source code directory that I have from last time and put on my desktop
I get 
bash: ./configure: No such file or directory

Now what????????:confused:

---

### Post by confubar on 2010-03-09
> **confubar said:**
> I let my update manager install some kernel stuff - must have lost what I did last December - with great difficulty and much gracious help - to get my new intuos4 working. [-o<
I have been trying to retrace my steps, got this far:
I backed up 10-wacom

user@dell-desktop:~$ sudo cp /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi /home/user/Desktop/10-wacom.bak

and then overwrote it with the contents of Favux_Jaunty ext graphics_test 2_10-wacom.fdi.txt
 
then 
determined that I have generic kernel
user@dell-desktop:~$ uname -r
2.6.28-18-generic

install linux-headers generic

user@dell-desktop:~$ sudo apt-get install linux-headers-generic
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

I can't get the source code tar or go into the unpacked source code directory that I have from last time and put on my desktop
I get 
bash: ./configure: No such file or directory

Now what????????:confused:
I went to sourceforge, got the tar again and opened it, there it is on my desktop. I entered in a terminal again
cd linuxwacom-0.8.4-4
again I got
bash: cd: linuxwacom-0.8.4-4: No such file or directory

I don't have any idea how to proceed, since I can't find the directory.

---

### Post by confubar on 2010-03-10
I got the thing to find the tar by using "paste filenames" rather than "paste" in the terminal window.
This stuff is difficult for an inexperienced person. 
It would be a very good thing if the newer lines of wacom tablets were fully supported, as, I understand, the older ones are.

---

