---
title: "New install with monitor problems"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by swappo1 on 2009-06-14
Hello,

I have installed 9.04 on a new computer and I am having trouble setting up the resolution of the monitor.  If I change the resolution and refresh rate in the NVIDIA X Server Settings under Display, click apply, and save the to X Configuration file I get an error: Unable to create new X config backup.  I tried to save the changes manually through sudo gedit /etc/X11/xorg.config but my computer locked up.  Any ideas how to get this working right?  When I apply the settings, everything looks good.  It just doesn't stay that way because I can't save the settings.

---

### Post by swappo1 on 2009-06-14
I rebooted and edited the /etc/X11/xorg.conf file to reflect the correct resolution 1920x1080.  When I booted back into Ubuntu, I tried to open firefox and the screen crashed again.  I had to reboot, change the resolution back to what it originally was because gedit was causing the screen to crash as well.  Once I changed the resolution back, the screen stopped crashing.  What do I do now?  I have been putting off getting a new computer for months because of having to go through this.  I always had laptops in the past and I thought desktops were more linux friendly.

---

### Post by kdi on 2009-06-14
i try to help.

if you managed to log into gdm or kdm, press ctrl+alt+f3 n login as "root".enter your password.

1. type:
   sudo /etc/init.d/gdm stop

2. then, type:
   startx

in the graphical mode, go to "NVIDIA X Server Settings" to setup ur resolution n apply. it should be able to save the settings in xorg.conf.reboot ur computer n see if ur computer is running in the new resolution settings or not. it should be okay by now.

---

### Post by PureLoneWolf on 2009-06-14
Make sure you are running nvidia-settings with sudo or gksu - Otherwise it can't save anything

---

### Post by swappo1 on 2009-06-14
kdi, I tried what you wrote but when I went to save the settings in "NVIDIA X Server Settings" it again gave me an error that it was unable to create new X config backup.  

> Make sure you are running nvidia-settings with sudo or gksu - Otherwise it can't save anything 
How do I do this?  There is no log in when I try to save the settings.

When I apply the changes to the correct configuration the resolution does change.  However, if I open firefox up the computer crashes.  My mouse still works but nothing else.  I can't even ctrl-alt-del.

---

### Post by swappo1 on 2009-06-14
I just rebooted because my computer crashed when I tried to resize the terminal.  After I rebooted and without any changes applied to the monitor settings, I tried to resize the terminal and the same thing happened.  It doesn't seem like 9.04 is going to run on the machine.  I am going to try 8.04 and see what happens.

---

### Post by kdi on 2009-06-14
> **swappo1 said:**
> kdi, I tried what you wrote but when I went to save the settings in "NVIDIA X Server Settings" it again gave me an error that it was unable to create new X config backup.  


How do I do this?  There is no log in when I try to save the settings.

When I apply the changes to the correct configuration the resolution does change.  However, if I open firefox up the computer crashes.  My mouse still works but nothing else.  I can't even ctrl-alt-del.

do you really login as "root" after pressing ctrl+alt+F3? you must type "root", not your normal user login account name.only then you'll be able to login graphically after u startx. in the root account, u can do whatever u want to the file system.

if you did follow exactly what i've mentioned but failed, then, i've really no idea what is wrong with the system.:(

---

### Post by swappo1 on 2009-06-14
kdi, 
I wasn't logged in as root.  After logging in as root and following what you wrote, I got the display settings changed.  The problem now is that once I reboot, When I open firefox, the screen crashes/hangs and just gets really messed up.  Do you know what the problem is?  It seems like it is coming from the nvidia driver.

---

### Post by kdi on 2009-06-14
> **swappo1 said:**
> kdi, 
I wasn't logged in as root.  After logging in as root and following what you wrote, I got the display settings changed.  The problem now is that once I reboot, When I open firefox, the screen crashes/hangs and just gets really messed up.  Do you know what the problem is?  It seems like it is coming from the nvidia driver.

hmmm...does ur mobo have integrated graphic accelarator? anyway, lets try this trick:

press ctrl+alt+F3. login as "root" n provide ur password. type:
1. sudo nano /etc/modprobe.d/blacklist.conf.
   add these two values at the last bottom of the page:
   [B]blacklist agpgart
   blacklist intel_agp[/B]

make sure to write the first value n then hit enter (or return) to write the second value. exit n save.

2. sudo nano /etc/modules.
   add "nvidia" (without quote) at the bottom, exit n save.

3. sudo nano /etc/hotplug/blacklist.
   add "agpgart" n "intel_agp" (both without quote) at the bottom, exit n save.

in my case however, i didn't do the third step as i didn't find the file.

if the problem persists, then,revert your resolution setting to the previous working value..;)

---

### Post by swappo1 on 2009-06-14
I believe my mobo does have the graphics integrated on it.  BTW, I have an AMD with a GeForce 9100 graphics, should I change the intel part of **blacklist intel_agp** to amd?

---

### Post by swappo1 on 2009-06-14
I made the changes stated by kdi and I still get the crashing.  Changing the resolution back to 1600x1200 and applying the settings eliminates the crashing.  I edited /etc/X11/xorg.conf to reflect this resolution, reboot and still no crashing.  It is only when I set the resolution to 1920x1080 that I get crashing.

---

### Post by kdi on 2009-06-15
> **swappo1 said:**
> I believe my mobo does have the graphics integrated on it.  BTW, I have an AMD with a GeForce 9100 graphics, should I change the intel part of **blacklist intel_agp** to amd?

i don't think so because i've never heard amd are producing graphic accelarator by themselves rather ati is it. intel_agp blacklist means that the os will not load intel graphic driver. therefore the system will only detect n use nvidia graphic driver instead of intel's.

oh ya one more thing, type in the terminal:

sudo nano /etc/default/linux-restricted-modules-common

add at the bottom page "nv nvidia" (together with the quote) so that yours will look like this:

**DISABLED_MODULES="nv nvidia"**

this is to prevent inferior open source nvidia driver from loading.

try it n see if your problem solved...:)

---

### Post by swappo1 on 2009-06-20
> sudo nano /etc/default/linux-restricted-modules-common

add at the bottom page "nv nvidia" (together with the quote) so that yours will look like this:

DISABLED_MODULES="nv nvidia"
I tried it and it still doesn't solve my problem.  I opened firefox up and the screen locked up with all sorts of garbage on the screen.  Any other ideas?

---

