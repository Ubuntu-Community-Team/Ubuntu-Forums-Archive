---
title: "just successfully installed Ubuntu some things not working"
date: 2012-02-11
forum: Hardware
---

### Post by elesbb on 2012-02-11
Hey Ubuntu community !
Just got Ubuntu installed on my hp pavilion dv7 6163us entertainment laptop. Everything seems to be working fine except for changing screen brightness and changing touchpad settings . In the GUI it appears to be changing but nothing is noticeably different . I remember in fedora when I installed that onto my netbook I had to update the kernel to get everything working properly . How do I do this in Ubuntu ? Thanks all for your help !

---

### Post by josephmills on 2012-02-11
Hi there and Welcome to ubuntu forums 
before we go any further could you please open your terminal (ctrl+alt+t) and enter in 
```
lspci -nn | grep VGA
``` 
then paste that here thanks 
once again welcome to the forum

---

### Post by elesbb on 2012-02-11
> **josephmills said:**
> Hi there and Welcome to ubuntu forums 
before we go any further could you please open your terminal (ctrl+alt+t) and enter in 
```
lspci -nn | grep VGA
```then paste that here thanks 
once again welcome to the forum
 
 
Thanks for the invite :) i feel welcomed ^^
 
 
as for your request ..
```

seth@Seth-HP-Ubuntu:~$ lspci -nn | grep vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)

```also for some reason my wireless stopped working , i did lspci to find that and its as follows . Btw i would like to get open source wireless drivers if possible . 
 
```

07:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000

```Thanks for all the help !!!



Edit: I just realized the WiFi issue is only after standby . I can not connect to ANY WiFi network after resuming from standby .

---

### Post by elesbb on 2012-02-12
Any help ?

---

### Post by ahallubuntu on 2012-02-12
Which version of Ubuntu is it?

Can we assume you've already done all the updates to get the newest kernel, etc. after your initial install?  If not, please do so - that can fix a lot of problems.

For the brightness problem, try editing the Grub configuration file.  Open a terminal and do:

sudo gedit /etc/default/grub

and fine the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to add text after "splash":

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

(Yours may not look exactly the same - but just add that text after "splash" to whatever is in double quotes.)

save the file, quit the editor.  Then still in terminal do this:

sudo update-grub

and restart the computer and see if brightness controls work.

The standby/wifi issue is probably fixable too.  Can you just disable/enable the wireless card manually after standby?  Does that help?

---

### Post by elesbb on 2012-02-12
> **ahallubuntu said:**
> Which version of Ubuntu is it?

Can we assume you've already done all the updates to get the newest kernel, etc. after your initial install?  If not, please do so - that can fix a lot of problems.

For the brightness problem, try editing the Grub configuration file.  Open a terminal and do:

sudo gedit /etc/default/grub

and fine the line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

and change it to add text after "splash":

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"

(Yours may not look exactly the same - but just add that text after "splash" to whatever is in double quotes.)

save the file, quit the editor.  Then still in terminal do this:

sudo update-grub

and restart the computer and see if brightness controls work.

The standby/wifi issue is probably fixable too.  Can you just disable/enable the wireless card manually after standby?  Does that help?


Yes i have the latest kernel update . 
And thanks that fixed the brightness control buttons . However under system info , i go into graphics and it says driver unknown . is there any way i can fix that ?

As for the wifi , no just disabling it and then re-enabling it does not fix the connection problem . it shows that there is a wifi network so it scans perfectly fine just cant connect . Thanks for the help in fixing the brightness control buttons !

---

### Post by elesbb on 2012-02-12
A few more things ive noticed . When using gpointing-device-settings (even running as sudo) the settings dont stick . 


When i ran windows 7 , i could get like 9 hours on my battery . im lucky to get 5 with ubuntu . which sucks . anyway to fix the horrible battery drain ?

Thanks again for all your help guys i dont mean to sound a pain .

---

### Post by ahallubuntu on 2012-02-12
OK, one thing at a time. :-)

First of all, it looks like this may fix your wireless card problem:

[http://ubuntuforums.org/showthread.php?t=1850627](http://ubuntuforums.org/showthread.php?t=1850627)

Go down to biodiesel-bri's comment, Comment #6, and try that.

You can see the same discouraging comment about battery life there as you have, though.  This is a Sandy Bridge-based laptop, I take it?  I gather that Linux support for Sandy Bridge is still new and that may be why it gets lousy battery life.  One of the downsides of Linux is that drivers for newer hardware get developed for Windows and Mac by the manufacturers, with Linux a distant third if at all.  So can take time for Linux developers to catch up.

---

### Post by elesbb on 2012-02-12
> **ahallubuntu said:**
> OK, one thing at a time. :-)

First of all, it looks like this may fix your wireless card problem:

[http://ubuntuforums.org/showthread.php?t=1850627](http://ubuntuforums.org/showthread.php?t=1850627)

Go down to biodiesel-bri's comment, Comment #6, and try that.

You can see the same discouraging comment about battery life there as you have, though.  This is a Sandy Bridge-based laptop, I take it?  I gather that Linux support for Sandy Bridge is still new and that may be why it gets lousy battery life.  One of the downsides of Linux is that drivers for newer hardware get developed for Windows and Mac by the manufacturers, with Linux a distant third if at all.  So can take time for Linux developers to catch up.

that fixed the wifi thanks :-D I didn't have said conf file but I created it which worked . and yes I do . I guess that's what's I get for having the latest xP . is there anyway to complete install the graphics driver ? and a way to have the touchpad settings stick ?

I appreciate all your help like seriously ! 
^-^

---

