---
title: "Input signal out of range : HD ATI 3850 GFX Card"
date: 2009-03-08
forum: Hardware
---

### Post by jasonp on 2009-03-08
Whenever i bootup ubuntu normally i get the black screen with the error notice 'Input signal out of range' therefore i reboot go into ubuntu recovery mode and use the option xfix then i click cancel and ubuntu boots :)

problem is the screenresolution is low so , i need help on sorting this problem out for ubuntu to boot normally in a decent resolution with special effects etc 

Please help

thanks

---

### Post by jasonp on 2009-03-09
bump :)

please help guys

---

### Post by mike.sufc on 2009-03-09
I have the exact same problem!  I also have an ATI 3850 and a Hanns G monitor.

It displays this on my monitor during the graphical installation, so I used the alternate CD...But after it is successfully installed, I get the same error before the login screen.

I hit ctrl-alt-f1 to go to the command line and typed

sudo dpkg-reconfigure -phigh xserver-xorg

as that is what I heard would solve the problem but it hasn't.  Some help would be MUCH appreciated :)

---

### Post by mike.sufc on 2009-03-16
Does anybody have any ideas about this??  I would really like to install and use Ubuntu, but just can't :(

---

### Post by markbuntu on 2009-03-16
The problem is that the ubuntu installer is trying to load a kludged driver. What you should have done when you installed, I know this is sort of too late and of course you did not know this, was choose F4 safe graphics mode at the install menu screen. 

This forces the generic VESA driver to be used which is a default for all graphics cards but has very limited capabilities. Next, get all the updates. After all the updates install and you reboot, you can use the restricted driver that the little popup screen keeps telling you about. Or you can go to System/Preferences/Hardware Drivers and enable it.

If that does not work or you want to use the latest driver from ati instead you can go to their site and download it and run the installer

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

To run the installer, first make it executable (you can do this with nautilus/properties) open a terminal and cd to the directory you downloaded to and 

sudo sh ./ati-driver-installer-9.2-x86.x86_64.run

You can also do this from the recovery mode after running xfix and continue to get to your desktop. Save the installer because you will need to run it again after every kernel update.

---

### Post by mike.sufc on 2009-03-24
Thanks for the reply.  I actually cant install in safe mode.  When I choose this, the Ubuntu loading graphic comes up but is all squashed and distorted and is green!!

I used the alternative installation CD which works fine, so it is fully installed no problemos.  But when I start up in ubuntu, i can't get past the login screen as it wont show it.  I hit ctrl f1 to login via command line...But then i cant really go anywhere from there!

---

### Post by gregb49 on 2009-03-24
Isn't this more likely to be that the sync rate is too high for your LCD monitor? It might be worth trying```
sudo dpkg-reconfigure xserver-xorg
```again, setting a lower horizontal or vert sync rate. 

Alternatively, if you have a distribution that does work, say KNOPPIX, from a live CD, have a look at the /etc/X11/xorg.conf file for settings that work, then you can amend your file. I've had this problem with older LCD displays.

---

### Post by mike.sufc on 2009-03-24
:( yes I have tried reconfiguring the xserver using that line you suggested but to no avail.  

when it says input signal out of range, I hit ctrl f1 and login in.  I then type sudo dpkg-reconfigure xserver-xorg.

Then what should I do?  I hit ctrl f4 but it is still out of range :(

---

### Post by gregb49 on 2009-03-24
> **mike.sufc said:**
> :( yes I have tried reconfiguring the xserver using that line you suggested but to no avail. This is the non-subtle approach, if it is possible for you to do. Find a debian distro that will work from a live CD, then examine the xorg.conf file to find out the settings that will work, then amend the miscreant xorg.conf file to include the settings. Having a few disks handy such as KNOPPIX, MEPIS, MINT etc, I find useful.

Someone else out there will have the subtle, clever approach, I'm sure.

---

