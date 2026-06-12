---
title: "Can't Install Nvidia Drivers?"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by Drunner611 on 2007-04-01
I don't know what I am doing wrong here.  I downloaded the newest linux x64 driver for my 7900gt.  When I try to run it.  it just does this.

ben@C2D:~$ sh '/home/ben/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run' 
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 1.0-9755.......................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
ben@C2D:~$ sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 1.0-9755.......................................................................................................................................
nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.
ben@C2D:~$ sudo NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
sudo: NVIDIA-Linux-x86_64-1.0-9755-pkg2.run: command not found
ben@C2D:~$ sudo sh NVIDIA-Linux-x86_64-1.0-9755-pkg2.run
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86_64 1.0-9755.......................................................................................................................................
ben@C2D:~$ 


I'm not really sure what the correct command that I'm suppose to be using here is, but this one seemed to get me pretty far, just not far enough.  Any ideas.

Total noob here, been reading here for a week, first post.  Running Feisty.

---

### Post by Rui Pais on 2007-04-01
hi,
should be 
```
sudo sh /home/ben/NVIDIA-Linux-x86_64-1.0-9755-pkg2.run 
```
from a console and with no X server running.

hth

---

### Post by Rui Pais on 2007-04-01
I just realize now thats your first post.

Welcome to the forum :)

That's an advanced and non supported way of installing Nvidia drivers...
Maybe you should stick with the conventional way of installing it, [here  is an How-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").


EDIT: If you still want to try the method of your post, but have doubts about my previous instructions, just post here.

---

### Post by Drunner611 on 2007-04-01
No, LOL>  I want to do it the easy way,  I just have no idea what that is.  I'm following the guide now and I'll report back.  Thanks

---

### Post by darkmaster on 2007-04-01
> **Drunner611 said:**
> No, LOL>  I want to do it the easy way,  I just have no idea what that is.  I'm following the guide now and I'll report back.  Thanks

If I can be of any help, I suggest you to leave any how to alone and just use Envy. Here's my guide for using it:

[http://thedarkmaster.wordpress.com/2007/03/12/install-painlessly-nvidia-or-ati-proprietary-drivers-on-ubuntu-edgy-dapper/]("http://thedarkmaster.wordpress.com/2007/03/12/install-painlessly-nvidia-or-ati-proprietary-drivers-on-ubuntu-edgy-dapper/")

Envy didn't really need an how-to to be used. My instructions are really the easyest I could write down, I hope this will help you! Let me know any progress!

---

### Post by Drunner611 on 2007-04-01
> **Rui Pais said:**
> I just realize now thats your first post.

Welcome to the forum :)

That's an advanced and non supported way of installing Nvidia drivers...
Maybe you should stick with the conventional way of installing it, [here  is an How-to]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia").


EDIT: If you still want to try the method of your post, but have doubts about my previous instructions, just post here.

Thank you very much RUI.  That worked like a charm.  Honestly, these last 2 days have been some of the most rewarding to my knowledge of computers.  Linux is sweet.  I'm sure you'll see me around here alot.

---

### Post by Rui Pais on 2007-04-01
Glad you make it :)

yes i sincerely hope seeing you around and enjoying,
have fun.

---

