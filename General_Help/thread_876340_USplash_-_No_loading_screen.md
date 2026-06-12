---
title: "USplash - No loading screen"
date: 2008-07-31
forum: General Help
---

### Post by Spops on 2008-07-31
Hi everyone,

I just installed Ubuntu 8.04.1 as a wubi install.  For some odd reason I do not get a loading screen on this computer like I do with my laptop.  From digging around on the internet a few people have talked about USplash.  So I did a search for USplash and found this tutorial:

[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

I followed all of the steps but could not install any that poped up in the directory.  The only one that successfully installed was the one listed in that tutorial.  But even after all of that I still have no loading screen

Any clue how to fix this?

FYI here are my system specs:

Intel Pentium 4 2.80 GHZ
512 MB of RAM
Intel Corporation 82865G Integrated Graphics Controller

---

### Post by chrisccoulson on 2008-07-31
Do you see any errors on the screen at all? What is the contents of the file /etc/usplash.conf? Is the resolution set to a resolution supported by your screen?

---

### Post by Spops on 2008-07-31
> **chrisccoulson said:**
> Do you see any errors on the screen at all? What is the contents of the file /etc/usplash.conf? Is the resolution set to a resolution supported by your screen?

After I select Ubuntu there is some text that flashes on the screen fairly quickly.  Than it just goes to a black screen for over a minute.  Than I get the screen to enter username/password.  

My moniter is a Dell 17" and the resolution is set to 1280x1024

---

### Post by Spops on 2008-08-01
Anyone able to help me get the loading screen to work?

---

### Post by chrisccoulson on 2008-08-01
Could you post the contents of your /etc/usplash.conf file please?

---

### Post by Spops on 2008-08-01
> **chrisccoulson said:**
> Could you post the contents of your /etc/usplash.conf file please?

Where do I find that?  I am still fairly new to Linux

---

### Post by primolarry on 2008-08-01
Couple of weeks ago I broke my usplash config as well, and was unable to restore to the original ubuntu usplash theme. After trying a lot of solutions I found, what really fixed it was instaling Startup_Manager:

```
sudo apt-get install startupmanager
```

Go to Administration -> Startup Manager, go to the appearance tab and choose a usplash theme (probably, you will have only the default one).

Close the program, w**ait for it to finish its post-conf operations**, reboot, and it should be ok now.

Regards

---

### Post by Spops on 2008-08-01
> **primolarry said:**
> Couple of weeks ago I broke my usplash config as well, and was unable to restore to the original ubuntu usplash theme. After trying a lot of solutions I found, what really fixed it was instaling Startup_Manager:

```
sudo apt-get install startupmanager
```

Go to Administration -> Startup Manager, go to the appearance tab and choose a usplash theme (probably, you will have only the default one).

Close the program, w**ait for it to finish its post-conf operations**, reboot, and it should be ok now.

Regards

Unfortunately that did not work :(

This is an install of Ubuntu 8.04,1 through Windows.  I have even tried in the past to uninstall Ubuntu and reinstall it.

---

### Post by Spops on 2008-08-01
This is what all of my settings look like in the startup manager.  I figured that screen shots would give you more information:

[img]http://img204.imageshack.us/img204/8416/screenshotstartupmanagenq3.png[/img]

[img]http://img262.imageshack.us/img262/2895/screenshotstartupmanagenn3.png[/img]

[img]http://img300.imageshack.us/img300/1561/screenshotstartupmanageij2.png[/img]

[img]http://img357.imageshack.us/img357/3891/screenshotstartupmanagekf3.png[/img]

---

### Post by primolarry on 2008-08-01
> **Spops said:**
> Where do I find that?  I am still fairly new to Linux

open a console and type:

```
gedit /etc/usplash.conf
```

---

### Post by Spops on 2008-08-01
> **primolarry said:**
> open a console and type:

```
gedit /etc/usplash.conf
```

This is what I got in a new window:

```
# Usplash configuration file
xres=1280
yres=1024
```

---

### Post by chrisccoulson on 2008-08-01
Looks ok. Could you try typing the following in to a terminal:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

---

### Post by Spops on 2008-08-01
> **chrisccoulson said:**
> Looks ok. Could you try typing the following in to a terminal:
```
sudo update-usplash-theme usplash-theme-ubuntu
```

Thanks for all of the help thus far.  This is what I get:

```
administrator@administrator-desktop:~$ sudo update-usplash-theme usplash-theme-ubuntu
[sudo] password for administrator: 
Using '/usr/lib/usplash/usplash-theme-ubuntu.so' to provide 'usplash-artwork.so'.
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
administrator@administrator-desktop:~$ 

```

---

### Post by chrisccoulson on 2008-08-01
That looks ok. Now do you get a USplash when you reboot?

---

### Post by Spops on 2008-08-01
> **chrisccoulson said:**
> That looks ok. Now do you get a USplash when you reboot?

Nope still no loading screen when I start Ubuntu or Shut it down :(

Anything else you can think of?

And thanks again for helping me.

---

### Post by forger on 2008-08-01
1) reboot
2) try this command in a terminal once you log in again:
```
dmesg | grep -i usplash | tail
```

Paste the output, if there is any. Your usplash could be crashing like mine does :(
I get the "Ubuntu" and until the part where the progress bar goes back and forth, but when it starts the process (when it loads the file for the booting process), it crashes and shows the "text version" of the loading progress

---

### Post by Spops on 2008-08-01
> **forger said:**
> 1) reboot
2) try this command in a terminal once you log in again:
```
dmesg | grep -i usplash | tail
```

Paste the output, if there is any. Your usplash could be crashing like mine does :(
I get the "Ubuntu" and until the part where the progress bar goes back and forth, but when it starts the process (when it loads the file for the booting process), it crashes and shows the "text version" of the loading progress

Sorry, been on the phone with dell for 2 hours :(  Anyways nothing happens when I use that code:

```
administrator@administrator-desktop:~$ dmesg | grep -i usplash | tail
administrator@administrator-desktop:~$ 

```

---

### Post by forger on 2008-08-01
Maybe there is something else in other log files, try this:
```
sudo grep -i "usplash" /var/log/*
```

Don't paste back the whole output, just look for lines like "fail" or "crash" or something similar to that

---

### Post by Spops on 2008-08-01
> **forger said:**
> Maybe there is something else in other log files, try this:
```
sudo grep -i "usplash" /var/log/*
```

Don't paste back the whole output, just look for lines like "fail" or "crash" or something similar to that


Don't see anything like that but I see a bunch of Half-installed and Half-configured

---

### Post by forger on 2008-08-02
Post the output of this command:
```
grep -i "usplash.*rip" /var/log/*|tail
```

Maybe this will work, try this command to reinstall some usplash parts:
```
sudo apt-get install --reinstall usplash libusplash0 initramfs-tools usplash-theme-ubuntu
```

---

### Post by Spops on 2008-08-02
> **forger said:**
> Post the output of this command:
```
grep -i "usplash.*rip" /var/log/*|tail
```

Maybe this will work, try this command to reinstall some usplash parts:
```
sudo apt-get install --reinstall usplash libusplash0 initramfs-tools usplash-theme-ubuntu
```

Computer is at the office, I will try it first thing Monday morning.  Thanks again for all your help

---

### Post by maestrobwh1 on 2008-08-03
I have a similar issue on both of my laptops... one was when I did an upgrade to hardy, and the other is when I had to move the partition of ubuntu... and it is common that I never get the usplash to work again properly on boot when I do something like this.  I get no errors and the conf file for usplash shows the proper resolution for my screen.

---

### Post by bruce2000 on 2008-08-03
I had a similiar problem to this - no splash during bootup or shutdown, just a "no signal" on monitor. The resolution setting in the usplash.conf file was the same as on my desktop, but i tried lowering it anyway and.. now it works, i get to see the splash screens in all their glory (well, its better than a blank screen)

---

### Post by maestrobwh1 on 2008-08-03
[http://ubuntuforums.org/showthread.php?t=857565](http://ubuntuforums.org/showthread.php?t=857565)

my issue is that through one process or another, the uuid of my swap changed so the splash was being interrupted by the fact that it could not find the "resume" device.  Fixed.

---

### Post by Spops on 2008-08-04
> **forger said:**
> Post the output of this command:
```
grep -i "usplash.*rip" /var/log/*|tail
```

Maybe this will work, try this command to reinstall some usplash parts:
```
sudo apt-get install --reinstall usplash libusplash0 initramfs-tools usplash-theme-ubuntu
```

```
administrator@administrator-desktop:~$ grep -i "usplash.*rip" /var/log/*|tail
administrator@administrator-desktop:~$ 


```

I also tried to reinstall with that code, and no change.

---

### Post by chrisccoulson on 2008-08-04
I think it's probably time for you to open a bug report on Launchpad

---

### Post by Spops on 2008-08-04
> **chrisccoulson said:**
> I think it's probably time for you to open a bug report on Launchpad

How do I do that?

---

### Post by maestrobwh1 on 2008-08-04
Before doing this, try looking at this post: it solved the issue for me... my swap was assigned a new uuid and when booting, the process looks for a device to restore from (even though you don't hibernate, I think that if the wrong uuid is in the suggested file you need to fix, usplash craps out and goes to text.

---

### Post by staticsage on 2008-08-07
I'm having the same issue. My swap partition was not changed and I confirmed this using blkid. If no one else comes up with any more ideas to try, I'll open up a bug report.

---

### Post by rbmorse on 2008-08-07
This didn't really fix the problem, but I can at least now see all my boot messages:

sudo gedit /boot/grub/menu.lst

scroll down the file until you get to the point where the lines do not start with the "#" character

Find the first line that looks like:

```
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=e2133b81-0700-4827-8fff-5052af5a97e0 ro splash vga=785
```

In a *default* installation this will be in the section that starts the normal Ubuntu session. Your UUID= ID string will be different, of course. 

remove the terms "splash" and "vga=xxx" (you may not have the later) so the line looks like:

```
kernel		/boot/vmlinuz-2.6.24-20-generic root=UUID=e2133b81-0700-4827-8fff-5052af5a97e0 ro
```

save the file
close gedit
reboot
report

---

### Post by staticsage on 2008-08-07
Strange part is that it usplash shows properly at 1280x800 in my usplash.conf, but when i switch it back to 1920x1200 (default, and my native resolution) it no longer works.

I'm also curious, what drivers are used this early in the boot process?

---

### Post by chrisccoulson on 2008-08-07
> **Spops said:**
> How do I do that?

You need to create an account at [https://launchpad.net/]("https://launchpad.net/"), and then open a bug report for USplash by clicking [this link]("https://bugs.launchpad.net/ubuntu/+source/usplash/+filebug"). Hope that helps:)

---

