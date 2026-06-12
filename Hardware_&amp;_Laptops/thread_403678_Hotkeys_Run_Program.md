---
title: "Hotkeys Run Program"
date: 2007-04-07
forum: Hardware &amp; Laptops
---

### Post by briansvgs on 2007-04-07
Hello,

I have a Z71V laptop. Most of my hotkeys are working, but I want to configure the internet, email, and a button that turns a play button (audio dj). I know how to get the keycodes for all of the keys (using acpi_listen), and I know how to make programs run as root when a hotkey is pressed, but I would like to know how to make a program run as the currently logged on user, and avoid any possible security compromise from running the program as root (basically, you press the button and the program runs as the currently logged on user, not as root). Can somebody please help me with this? I know that you would just need a simple bash script, but I am not yet good enough at bash programming to do this. Also, for the play button, I would like to have it check to see if the program exaile is running when the play button is pressed. If it is already running, then the button will just make the music play. If the program isn't running, then the button will launch the program and make it play. I think that I know how to write almost all of this second program, however, I don't know how to check if the program is running or not. Any help with either of these problems would be greatly appreciated.

Thanks,
Briansvgs

---

### Post by Ekril on 2007-04-11
try to install "hotkeys" and "hotkey-setup" via apt-get or aptitude or synaptic or adapt.. 

for apt-get

sudo apt-get install hotkeys hotkey-setup

Important : just trying to help . i am not a Ubuntu Pro.

---

### Post by briansvgs on 2007-04-15
Thank you. I ended up finding a script that grabs the username of the currently logged on user and then runs the program as that user. This script is used for udev,  but I should be able to customize it. If you want to look at the script, the address is:[http://linlog.skepticats.com/content/udevautorun/](http://linlog.skepticats.com/content/udevautorun/).

---

### Post by briansvgs on 2007-04-15
here is my finished program for the mail button on my laptop. When the mail button is pressed, it will execute the program evolution as the user that is currently logged into X11. 


[B]#!/bin/bash

. /etc/default/acpi-support
. /usr/share/acpi-support/power-funcs

getXconsole;
if [ x"$XAUTHORITY" != x"" ]; then
    . /usr/share/acpi-support/key-constants
    acpi_fakekey $KEY_MAIL   # [was: 236]
    LocalDisplay=':0'
X11User=`who | grep $LocalDisplay | cut -f 1 -d ' '`
if [ -z "$X11User" ] ; then 
	exit
fi
nice -n 5 su $X11User -c "evolution &> /dev/null" &
exit
fi[/B]

It probably isn't the cleanest script that you have ever seen, but it works. I will put some more time into cleaning it up later.

---

### Post by briansvgs on 2007-05-26
The hotkeys worked great in 6.10, but with feisty, they do not work at all.Any ideas why?

---

