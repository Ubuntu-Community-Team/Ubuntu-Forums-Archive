---
title: "Won't boot after installing nvidia-current drivers (10.04)"
date: 2010-05-02
forum: Hardware
---

### Post by sakisds on 2010-05-02
I am using Ubuntu 10.04 and i have two(SLI) 8600 gts and each time i install the nvidia drivers ubuntu can't boot(black screen). Also i couldn't access recovery mode too, so i re-installed, installed the drivers again and ubuntu became unbootable for a second time. So i reinstalled with nothing to do. Anyone knows how to make the drivers work?

---

### Post by luctor on 2010-05-02
the black screen is the plymouth bootsplash not working.
if you wait for about a minute does ubuntu continue to login screen (that happens on my pc)

---

### Post by sakisds on 2010-05-02
I waited around 15 mins and still nothing, i don't think its just that.

---

### Post by farhaan on 2010-05-02
waiting didn't work for me :-/
The bootscreen flickers with a distorted aspect ratio for a second if i install the driver and it goes black.Reboot once or twice and it worked for me(i still cant figure out how  its working after rebooting/powerbutton :s ).
now im back on the default driver.Gotta wait till the guys fix it.Im fed up of rebooting,ive rebooted the machine more times than i ever did before installing lynx. :-/ 
im not exaggerating. :D

---

### Post by sakisds on 2010-05-02
Restarting didn't work for me, i tried 5-6 times to be sure before re-installing.

---

### Post by Geomas on 2010-05-02
I'm having the same problem on an old Acer Aspire E360. After installing the nvidea driver (173), it boots to a black screen. There's a suggested solution here, but I haven't tried it yet:

[http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html](http://www.ubuntugeek.com/how-to-fix-ubuntu-10-04-lts-lucid-blank-screen-at-startup.html)

---

### Post by sakisds on 2010-05-03
I tried to re-install the drivers today, but i ended up not booting so started to dig around the xorg files to see if i can find something. Before installing the drivers, I noticed that i was running without a /etc/X11/xorg.conf :s.

First of all, i booted using an ubuntu 10.04 live cd and i executed the following commands:

```
sudo mount /dev/sda1 /mnt
chroot /mnt
```

(Note: /dev/sda1 is my ubuntu partition)
Then i removed the nvidia drivers using this:

```
apt-get purge nvidia*
```

And rebooted with the hope that now it will boot but no luck.
Recovery mode didn't work either, so i used the live cd again, mounted my disk and then chroot. Now I tried to remove the xorg.conf, so it would be like before and then rebooted.

```
rm /etc/X11/xorg.conf
```

Now i am back at my desktop before the installation of the drivers. At least i avoided another clean installation. Everyone that can't boot could try the above steps too.

---

### Post by Christofferh on 2010-08-23
> **luctor said:**
> the black screen is the plymouth bootsplash not working.
if you wait for about a minute does ubuntu continue to login screen (that happens on my pc)

I had the problem today with Ubuntu 10.04 giving me the black screen and this was AFTER the splashscreen so I believe there might be something else.

I use ubuntu with one user for automatic login, no login screen and it's right between when the splashscreen goes down and ubuntu is about to show the mousepointer and ubuntu UI that nothing happens.

As stated earlier it's kinda hard to file a bug report on this one cause after 5 attempts I booted in to "repair broken packages" and updated my system with no success. After that I tried the graphic safe option in recovery mode with success but of course not with the nvidia drivers.

After just booting into graphic safe mode and restarting into normal mode, everything works fine. I hope it works the rest of the day today :D

---

### Post by ellgor on 2010-08-23
Hi,
 
If your still having problems I found a post that fixed it:


I read somewhere that they changed the way nvidia drivers get installed so, here is the guide:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run  (or whichever package you have, be precise, or you will get "no such file")
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM
Code:
sudo service gdm start

I would suggest that you go into recovery mode and work at it from there.

Worked for me.

Regards, Ellgor.

---

### Post by Christofferh on 2010-08-23
> **ellgor said:**
> Hi,
 
If your still having problems I found a post that fixed it:


I read somewhere that they changed the way nvidia drivers get installed so, here is the guide:


1) Download Newest Nvidia drivers from their website
2) Open module blacklist as admin:

sudo gedit /etc/modprobe.d/blacklist.conf
3) Add these lines and save: 

blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
4) Uninstall any previously installed Nvidia drivers: 

sudo apt-get --purge remove nvidia-*
5) Reboot your computer
6) When an error message pops up saying that Ubuntu cannot load Nvidia drivers, choose Exit to terminal (Exit to console)
7) Login and cd to the directory where you saved your file
 Install drivers

sudo sh NVIDIA-Linux-x86_64-195.36.24-pkg2.run  (or whichever package you have, be precise, or you will get "no such file")
8) Follow the onscreen guide from Nvidia and when done
9) Start GDM
Code:
sudo service gdm start

I would suggest that you go into recovery mode and work at it from there.

Worked for me.

Regards, Ellgor.

Cool I didn't see that approach to the problem while searching the web yesterday. Will try that next time I'm experiencing the same problem.

---

