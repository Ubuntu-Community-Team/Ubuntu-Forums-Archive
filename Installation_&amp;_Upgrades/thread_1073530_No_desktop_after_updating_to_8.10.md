---
title: "No desktop after updating to 8.10"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by ffz100 on 2009-02-18
Hi all,

I am running Ubuntu on a Lenovo ThinkPad T500. While using Ubuntu 8.04, everything worked fine, but since updating to 8.10 I cannot start GNOME anymore. When I boot the system, I get what seems to be an error message:

Loading, pease wait...
Kinit: name_to_dev_t(/dev/disk/by-uuid/...string of numbers and letters)= sda5(8,5)
kinit: No resume image, doing normal boot...

It will then just take me to a command prompt, where I can login but won't start the desktop system. When I try "startx", it exits with the error "No screens found".

Now interestingly, I tried booting from an Ubuntu 8.10 live CD, and I am experiencing the same problems. It does not start the graphical interface but just brings up a command prompt with the same error messages, and again startx says "No screens found".

This makes me think it may actually be a problem with the Ubuntu software, since when I boot from the live CD, it shouldn't use any of my configuration files and basically work like a freshly installed system, right? I also booted from a 8.04 live CD, and there everything works fine.

Does anybody have any idea what the problem might be or what I could try, except removing Ubuntu 8.10 and going back to 8.04? I can post configuration or log files, but I don't know which ones would be helpful.

Thanks in advance,

David

---

### Post by dstew on 2009-02-18
I am not sure about 8.10, but the following works on 8.04. At boot time, on your hard-disk installation, choose Recovery mode, and then select **xfix**. After you run xfix, proceed with a normal boot. Hopefully you will get a useable desktop, although the resolution might not be right. From a desktop, press alt-F2. That should get you a command line. Enter```
gksudo displayconfig-gtk
```That starts a program that lets you choose your exact monitor, and hopefully will get it looking better. You might have the same program in 8.10 in your Administration or Preferences menu listed as "Screens and Resolution".

---

### Post by ffz100 on 2009-02-18
Thank you for your suggestion. I tried it, but unfortunately it didn't work - I still cannot get a usable desktop, only the command prompt.

---

### Post by hockman5 on 2009-02-18
I just upgraded last night from 8.04 to 8.10 and don't have a desktop either. I have a blank screen but it lets me login cause I can tell by the sounds. Just no display. I tried Xfix in recovery but it didn't work either. I will keep researching and let you know what I come up with.

---

### Post by hockman5 on 2009-02-19
see my thread to find out how I fixed my problem. This might not help you if you don't have the same graphics adapter that I have, but it could steer you in the right direction.

[http://ubuntuforums.org/showthread.php?p=6762720#post6762720](http://ubuntuforums.org/showthread.php?p=6762720#post6762720)

---

