---
title: "Resume from suspend not working"
date: 2007-06-21
forum: Hardware &amp; Laptops
---

### Post by karl_kashofer on 2007-06-21
Hi !

I can not get my system to resume after suspend to RAM.
It goes into suspend fine, but when I wake it up the screen never comes back.

I did echo mem > /sys/power/state from single mode and it seems to wake fine. I can type stuff after resume althought the screen is black, and upon reboot find all i typed in the bash_history. So it seems it just fails to re-initialize the graphics card.

I have played with all the settings in /etc/default/acpi-support to no avail.

Here are my system specs:
Asus M2N32-SLI Deluxe with a XfX Nvidia 7950
I am using the standard nv driver in xorg, but that does not seem to be the issue here as it also does not properly resume in console single mode.

Hibernate (suspend to disk) works fine in Linux and Suspend to RAM and resume works in the redmond OS.
Any help greatly appreciated,
Thanks,
Karl

---

### Post by karl_kashofer on 2007-06-22
Hi again !

Got it to work by installing the nvidia binary drivers...... 

So now I would like to bind one of my multimedia keys to send my system to sleep, does anyone know what the commandline equivalent to selecting "suspend to ram" from the system shutdown menu is ?

Thanks,
Karl

---

### Post by Salisbury Satan on 2007-06-22
/etc/acpi/sleep.sh will put the laptop to sleep (suspent to ram) and /etc/acpi/hibernate.sh will hibernate the laptop (suspend to disk).

---

### Post by karl_kashofer on 2007-06-24
Hi !

> **Salisbury Satan said:**
> /etc/acpi/sleep.sh will put the laptop to sleep (suspent to ram) and /etc/acpi/hibernate.sh will hibernate the laptop (suspend to disk).

These scripts will do what they say, but I am unable to bind them to a keyboard shortcut as I cant get them to run as root without requiring a password.

I tried: 
chmod +s => still runs with user privileges, no workee
sudo visudo and inserting 
karl    ALL=(ALL) NOPASSWD: /etc/acpi/sleep.sh
still asks for password...

Aside of that the sleep.sh script fails to start the screensaver in kde, it seems to only check for xscreensaver.

And, i just checked, suspend to disk is not working with the nvidida driver....


So to sum up:

nv => hibernate works, sleep not
nvidia => sleep works, hibernate not

I would really like to give a proper bug-report to the developers of the nv driver as I think its the better driver for people not needing 3d like myself.

Does anyone know where the developer community for the nv driver is hanging out ?

Thanks,
Karl

---

### Post by elsaturnino on 2007-06-24
I gave up on trying to get the default hibernate/sleep to work. Instead I switched over to uswsusp with good success. For details on getting it setup, check out [this link]("http://blog.paulbetts.org/index.php/2007/02/11/fixing-software-suspend-hibernate-with-uswsusp-in-ubuntu-feisty-and-edgy/").

---

### Post by karl_kashofer on 2007-07-01
Hi !

Just did aptitude dist-upgrade and noticed that nvidia-glx-new was updated.
I now have nvidia driver Version: 1.0.9755+2.6.20.5-16.29 installed and suspend and hibernate works !!!

Horaaayyy !

Cheers,
Karl

---

