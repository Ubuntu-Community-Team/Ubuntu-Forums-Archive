---
title: "&quot;Desktop effects cannot be enabled&quot; Nvidia 6200 le"
date: 2008-11-06
forum: General Help
---

### Post by Death5023 on 2008-11-06
Ok i got ubuntu 8.10 a couple days ago . I downloaded the restricted driver thing. When i go and try to get desktop effects it wont work 

Amd 750 mhz 
 1 gb ram 
nvidia 6200 le 
 20 gb hard drive 
 

Any help would work Thankss

---

### Post by eternalnewbee on 2008-11-06
Have you activated your graphic card in: Main > Menu > Administration > Hardware Drivers?

---

### Post by IceReaver75 on 2008-11-06
I have the exact same card the 6200 a-le and all my desktop effects are working with the Nvidia 177.80 driver installed.  All compiz options work no problem all I'm having a problem with is the window/title bars flickering but thats more a driver problem with the nvidia driver and the xorg that Ibex uses from what I have read here.  So if you don't have the 177.80 driver installed hopefully that will work for you too.

---

### Post by Death5023 on 2008-11-06
still no luck now i cant even have themes somebody help plzzzz :(:(:frown:](*,)](*,)](*,)](*,)](*,)]

---

### Post by sharkster2007 on 2008-11-06
I had similar problems with my Nvidia 6600GT but I have now resolved this isuue hope my thread helps you [http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038)

The grey titlebar problem appears to be a bug that Nvidia is aware of lets hope they fix it quick.

---

### Post by Death5023 on 2008-11-07
Still no luck with that guide that you gave me. I tryed 177.80 and it still has that error

---

### Post by eternalnewbee on 2008-11-07
This may sound silly, but have you installed compiz?

---

### Post by Death5023 on 2008-11-07
yes i installed compiz

---

### Post by kiran88pnjr on 2008-11-07
Hi,

Your driver may not be enabled after installation.Go usr/bin/ and drag nvidia-xconfig file into your terminal and run it as root. Now you need to restart your computer.After that reenter into your desktop. Go usr/in/ again.Open nvidia-settings. Select X Server Display Configuration. Adjust your proper resolution.Click the button 'Save to X Configuration File'. Now you can see a small window. Click 'Show Preview' button and copy the entire configuration. Browse manually to the path shown there and paste the entire configuration to xorg.conf file as root and save xorg.conf. Now restart your computer and try Compiz now. I have done it in my Intrepid Ibex. But I have been using nVidia Geforce 6150 SE card with 512 MB Video memory and my processor is AMD Athlon X2 4600+ with 2.4 GHz clock speed.:popcorn:

---

### Post by Quarg on 2008-11-07
I had this problem with a workstation we were experimenting with at the school, i disabled the driver, downloaded it again, and rebooted it. and, if my memory serves me correctly (this was a while ago) I even then had to enable the driver under the drivers thing in System>Administration>hardware Drivers

---

### Post by Death5023 on 2008-11-07
kiran88pnjr can you explain that in a noob way cause i am not that good in ubuntu thanks

---

### Post by eternalnewbee on 2008-11-08
Hi Death5023.
Retrace your steps:
Is your **Hardware Driver** activated?
To check, go to: Main Menu > System > Administration > Hardware Drivers. Here's a screenshot.
If your Hardware Driver is activated, press ALT-F2 and enter this command (it will start up compiz) ```
compiz --replace
```

---

### Post by O011235813 on 2008-11-08
hey,

i'm having a similar problem with my 7900 graphics card. I have it activated from the screen you showed. However, whenever I restart, i wind up with a black screen, and white text. Which resembles the terminal, but there is no like background desktop, i can't get to the actual Ubuntu desktop. I'm completely clueless from this point.

---

### Post by eternalnewbee on 2008-11-08
> i'm having a similar problem with my 7900 graphics card. I have it activated from the screen you showed. However, whenever I restart, i wind up with a black screen, and white text. Which resembles the terminal, but there is no like background desktop, i can't get to the actual Ubuntu desktop. I'm completely clueless from this point.
If you have different choices, maybe you could try a different driver.

---

### Post by O011235813 on 2008-11-08
hmm...i have no idea....when i restart
it says some stuff

kinit: No resume image, doing normal boot...
Ubuntu 8.10 daniel-laptop tty1
daniel-laptop login:

how do i fix this? sorry i'm completely clueless

---

### Post by eternalnewbee on 2008-11-08
> how do i fix this? sorry i'm completely clueless
Same here. I suggest you open a new thread in Absolute Beginner Talk about this.
Good luck.

---

### Post by kiran88pnjr on 2008-11-08
Hi Death5023,

It is the simplest way. I too not an expert in Ubuntu. In order to work as root go to this URL : [http://www.gnome-look.org/content/show.php/Nautilus+Scripts+Pack?content=90330](http://www.gnome-look.org/content/show.php/Nautilus+Scripts+Pack?content=90330). U will get some scripts. Extract it and cut and paste it them to /home/username/.gnome2/nautilus-script/.You can see all the scripts while right clicking and a script called rootilus will help you to work as root. Where u want to work as root go there, right click and select rootilus. U can see another window opens with the same content which is the root window.This will surely help you in the task I mentioned yesterday.I will help you whenever U want. Write to me again.=D>

---

