---
title: "installing drivers on ubuntu 12.10 for graphics card nvidia GEFORCE GT   610"
date: 2012-10-28
forum: Hardware
---

### Post by Ralph Boland on 2012-10-28
I recently bought a dual head graphics card so I could run two terminals.
The sales clerk recommended the nvidia GEFORCE GT 610 graphics card which
he said would work with Linux.
I bought and installed it on my three year old computer (AMD Athlon II X2 245 processor) running Ubuntu 12.10 (32 bit).

But only one monitor is recognized (the one plugged directly into the graphics card).
Searching the Internet I read that the ubuntu (12.04 I believe) drivers 
for this card don't work and that I need to install the linux drivers from
nvidia.  I tried to do this but I found the installation process to be
especially complex and I prefer (read must because I got lost) to go a simpler route.

Questions.

1) Does the Ubuntu driver for this card really not work for Ubuntu 12.10?

2) Is the fix really as complex as indicated in the nvidia driver installation instructions?

3) Assuming I am right to abandon ship and get another graphics card,
   what are some good choices of graphics card to get.
   Note that I do not need fancy graphics.  I mostly do programming
   with IDEs such as Eclipse and those that come with Smalltalk.

Thanks for any help.

Ralph Boland

---

### Post by oldfred on 2012-10-29
I have an older nVidia card 9600GT. With 12.10, I did have issues installing the nVidia driver. But have not installed a driver from nVidia for years and that was such a bad experience that I will not again.

With 12.10 the kernel headers are missing so the standard install does not work from Ubuntu. But if you install the headers you can install any of three versions of nVidia's driver.

# You may need headers - meta package for current version:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
sudo apt-get purge nvidia*
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot

May want nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.

The experimental was 304 but I thought I saw another newer one.

When you see you are in the desktop but no icon or bar, right click to change desktop background or  if working go into system settings:
When the window appear, click all settings, now you see the system settings window.
Next, click on Software source, go in the additional drivers tab.
Select the 3 rd option, using video driver for the nvidia or AMD... fglrx-upgrade

---

### Post by Ralph Boland on 2012-10-29
Re: installing drivers on ubuntu 12.10 for graphics card nvidia GEFORCE GT 610
> ...
> sudo apt-get purge nvidia*
> sudo apt-get install nvidia-current
> sudo apt-get install nvidia-settings
> sudo dpkg-reconfigure nvidia-current
> sudo nvidia-xconfig
> sudo reboot

> May want nvidia-current-updates or nvidia-current-experimental-XXX for 
> most recent testing version.

> The experimental was 304 but I thought I saw another newer one.

> When you see you are in the desktop but no icon or bar, right click to 
> change desktop background or if working go into system settings:
> When the window appear, click all settings, now you see the system 
> settings window.
> Next, click on Software source, go in the additional drivers tab.
> Select the 3 rd option, using video driver for the nvidia or AMD... 
> fglrx-upgrade 

I executed these instructions without any difficulties.  Thanks for the
clear info.
Unfortunately it didn't fix the problem; still only one monitor is recognized.
I had the same problem with some very old dual head monitors.

  Is is possible that it is a hardware issue?  My computer is inexpensive;
perhaps some hardware feature or setting is missing?

Ralph Boland

---

### Post by oldfred on 2012-10-29
If you go into nvidia x server settings does it give an option to configure two monitors. I only have one, and the option for twin view is greyed out.

---

### Post by Ralph Boland on 2012-10-29
Re: installing drivers on ubuntu 12.10 for graphics card nvidia GEFORCE GT 610
> If you go into nvidia x server settings does it give an option to 
> configure two monitors. I only have one, and the option for twin view is > greyed out.

I ran <sudo nvidia-settings>.
It shows only one terminal and no way to change this greyed out or otherwise.
Actually it only shows the settings and gives no way to
changes settings.

When I use the GUI to go to System-Settings/Displays I get a display
that lets me set the screen size but shows only one terminal.
Pressing <detect displays> has no effect.

Ralph

---

### Post by oldfred on 2012-10-29
Do not have dual monitors, so I cannot help much.

Do not know if these help or not:
[http://askubuntu.com/questions/198499/dual-screen-is-not-recognized](http://askubuntu.com/questions/198499/dual-screen-is-not-recognized)
[http://ubuntuforums.org/showthread.php?t=2068730](http://ubuntuforums.org/showthread.php?t=2068730)
[http://askubuntu.com/questions/207351/dual-monitor-in-ubuntu-12-04-nvidia-gpu-with-cuda-drivers](http://askubuntu.com/questions/207351/dual-monitor-in-ubuntu-12-04-nvidia-gpu-with-cuda-drivers)
[http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html](http://www.webupd8.org/2012/10/ubuntu-multi-monitor-tweaks-full-screen.html)

---

### Post by dashjalal on 2012-11-27
hi

[COLOR=Gray]* to install nvidia gt 610m driver for ubuntu 12.10 :*[/COLOR]

*[COLOR=Gray]first remove nvidai driver :[/COLOR]*

[SIZE=3] sudo apt-get remove nvidia-current && sudo apt-get remove nvidia-current-update[/SIZE]

[SIZE=4][COLOR=Gray]Then[/COLOR][/SIZE][COLOR=Gray] :[/COLOR]

[SIZE=3]sudo apt-add-repository ppa:xorg-edgers/ppa[/SIZE]

[SIZE=3]sudo apt-get update && sudo apt-get install nvidia-current nvidia-settings[/SIZE]

[COLOR=DimGray]*For Ubuntu 12.04 or earlier :*[/COLOR]

[SIZE=3]sudo apt-get remove nvidia-current && sudo apt-get remove nvidia-current-update[/SIZE]

[SIZE=4][COLOR=Gray]Then[/COLOR][/SIZE][COLOR=Gray] :[/COLOR]

[SIZE=3]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates[/SIZE]

[SIZE=3]sudo apt-get update && sudo apt-get install nvidia-current nvidia-settings



[/SIZE][CENTER][SIZE=3] [SIZE=3][SIZE=3]&#1605;&#1608;&#1601;&#1602; &#1576;&#1575;&#1588;&#1740;&#1583;[/SIZE][/SIZE] (good luck)[/SIZE]
[/CENTER]

---

### Post by praveens1 on 2013-02-03
My graphics card was showing unidentified. I am new to ubuntu and somehow changed my graphics card stting to  Intel® Ironlake Mobile x86/MMX/SSE2. After this my ubuntu freezes a lot. How sould I revert this change? 

iimk@adipoli-HP-ProBook-4320s:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

---

### Post by Yellow Pasque on 2013-02-03
@praveens1: Please start a new thread. You have a completely different GPU than the OP.

---

