---
title: "Nvidia Horrors"
date: 2007-04-22
forum: Hardware &amp; Laptops
---

### Post by koulanji on 2007-04-22
So I am rocking a nvidia 7600GT, and I just upgraded feisty fawn; however, my xserver crashed and failed miserably. The first thing I did was to purge the old version of envy and grab envy 0.9.2, which is supported by feisty fawn. I tried cleaning any nvidia driver that I had installed on it and reinstalling the drivers itself. After I reinstalled the drivers, I got the following errors:

So after installing the drivers, I get a message stating that errors were encountered while processing nvidia-glx

rm: cannot remove /usr/share/envy/*.deb No such file or directory

rm: cannot remove /usr/share/envy/*.asc No such file or directory

rm: cannot remove /usr/share/envy/*.changes No such file or directory

Then it tries to start the x-server and i get sudo: /etc/init.d/kdm: command not found

The last one is very interesting since I am not using kdm at all. I emailed the guy in charge of the script and he told me that these errors were completely normal and he told me to try this:

[Type:

sudo /etc/init.d/gdm stop (if you use GDM)
OR
sudo /etc/init.d/kdm stop (if you use KDM)

Then:
startx -- -verbose 5 -logverbose 5

You will see several lines with the same error.

Then if you can't get to the command line press CTRL+ALT+F1 or CTRL+C
(select NO if it asks you if you want to see the output of the error or
something like that)

Then type this in order to copy the output of the error to your home folder:
sudo cp /var/log/Xorg.0.log /home/your_username/Xorg.0.log
(Of course you have to replace "your_username" with your username)

Access the GNOME or KDE again in the following way:
sudo nano /etc/X11/xorg.conf
Set the driver back to "nv" instead of "nvidia"
CTRL+O to save
CTRL+X to exit

Then
sudo /etc/init.d/gdm restart (if you use GDM)
OR
sudo /etc/init.d/kdm restart (if you use KDM)]

I followed those instructions and everything went smoothly until I tried restarting the gdm, which would not start at all, because according to ubuntu there is still a problem with the xserver.

I then emailed the guy in charge of the script and i was told to this:

[ls /etc/X11/

and find the backup of your xorg.conf

then type:
sudo cp /etc/X11/name_of_the_backup_file /etc/X11/xorg.conf
However, when I typed the second command, and restarted the gdm I had no luck.

I then used envy to clean up any installed driver that was there  and I tried installing it manually by doing this:
"sudo aptitude install nvidia-glx nvida-kernel-common" and sudo nvidia-xconfig I then opened up the xorg conf file, sudo nano /etc/X11/xorg.conf, and changed the nvidia driver to nv. Does anyone have any suggestions. Reformatting is not an option

---

