---
title: "Lenovo y580"
date: 2013-07-05
forum: Hardware
---

### Post by Wi6791lly on 2013-07-05
I'm trying to follow this [http://ubuntuforums.org/showthread.php?t=1543006&page=141&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&page=141&p=12710212#post12710212)
I followed it and have ubuntu installed now on my computer except I somehow messed up the graphics area...I have to usual problem with these computers and all of the graphics is smooshed into the upper 1/4 of the screen or so. How do I fix this?

Currently after formatting my flash drive for really stupid reasons, I now have a fresh Ubuntu installed on there and have edited my grub.cfg file and am booting directly off the flash drive. [http://paste.ubuntu.com/5848519](http://paste.ubuntu.com/5848519) is my boot repair file aswell.

I'm curious if I run OS-Installer could I uninstall Ubuntu and just reinstall with this new flash drive..,or will this break things? I saw it was going to format this partition and I didn't want to mess things up further.

Thank you for any help you can offer.

---

### Post by mörgæs on 2013-07-07
Moved to the hardware forum.

---

### Post by ofnuts on 2013-07-07
Not the easiest system to install Ubuntu on but someone did it, and described the process:

[http://ubuntuforums.org/showthread.php?t=1543006&page=141&p=12710212#post12710212](http://ubuntuforums.org/showthread.php?t=1543006&page=141&p=12710212#post12710212)

You may also want to check here :[http://forums.lenovo.com/t5/Linux-Discussion/Y580-Linux-compatibility/td-p/1064099](http://forums.lenovo.com/t5/Linux-Discussion/Y580-Linux-compatibility/td-p/1064099) (which is where I got the link above...)

---

### Post by Wi6791lly on 2013-07-07
Thats the method I was originally following. I have a simple question now if I boot Ubuntu off my flash drive and then run the OS uninstaller tool will it mess up my computer? When I boot my computer and go into boot options, I have 2 options for Ubuntu and 2 Options for Windows. Except all 4 take me to the Grub menu. I just don't want grub to be removed and me to not be able to boot into windows at all.

---

### Post by ofnuts on 2013-07-07
> **Wi6791lly said:**
> Thats the method I was originally following. I have a simple question now if I boot Ubuntu off my flash drive and then run the OS uninstaller tool will it mess up my computer? When I boot my computer and go into boot options, I have 2 options for Ubuntu and 2 Options for Windows. Except all 4 take me to the Grub menu. I just don't want grub to be removed and me to not be able to boot into windows at all.
Aw yes... now, the $64K question is : did you create the Lenovo recovery CDs?

Otherwise, looking at it: you can change the BIOS to boot Windows directly. You can also attempt other installations over your installed Unvuntu, reusing the same partition. Installers normally give you the choice, but they will likely use the already Linux-ed partition as a default.

---

### Post by Wi6791lly on 2013-07-07
I do have a backup, So if I attempt to reinstall over, it shouldn't break anything right? Should I run OS-uninstaller first?

---

### Post by ofnuts on 2013-07-07
No, no need to uninstall first...

---

### Post by Wi6791lly on 2013-07-07
Okay...I uninstalled Ubuntu, and then ran boot repair. When I went to restart I now get
"unknown filesystem (I think)
grub rescue (I know this is the second line)"
Uhm help...I'm currently on booted ubuntu off flash drive

---

### Post by Wi6791lly on 2013-07-08
I ran a back up that was provided with my windows install, and now windows is throwing an error and asking for a Boot Repair disk or something along those lines. I need a Windows 8 ISO file. One way that was suggested I can do this is to mount my Windows 8 partition from Ubuntu and then simply copy it over. I cannot figure out how to do this. It says I need to mount it in read only mode? How do I accomplish what seems like a simple task

---

### Post by ofnuts on 2013-07-09
That's "mount -r. (other options)". 

It looks like grub is trying to boot on a partitiion that has been emptied. 

We are only two people in this topic and I'm not an expert... open another topic in the "General help" section. mention "grub" in the title.The mess you are currently in isn't specific to your machine.

---

