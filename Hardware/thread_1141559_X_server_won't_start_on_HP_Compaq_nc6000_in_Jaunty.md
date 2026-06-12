---
title: "X server won't start on HP Compaq nc6000 in Jaunty"
date: 2009-04-28
forum: Hardware
---

### Post by rubenverweij on 2009-04-28
Hello all,

I upgraded my nc6000 from 8.10 to 9.04 today and I still wish I hadn't. :(
The X server stopped working and I cannot login. The graphics card is an Ati Radeon Mobility 6200.
I looked into the X.org log file, I can't find anything there, I can't post it here because the laptop has no internet at the moment (I'm positively sure I can configure it as soon as the x server is okay again).
What I did found was that it consequently fails to terminate the xfstt server on shutdown.
I tried already dpkg-reconfigure xserver-xorg, dpkg-reconfigure xfstt, xfix. I have set the xorg.conf file to the default settings with xfix, I used my backup, I tried vesa and mesa, all to no avail.
The screen does display a scattered version of my wallpaper with green and black gaps all over it :lolflag:.

Does anybody have a suggestion:confused:

Thanks in advance,

Ruben

---

### Post by shatterblast on 2009-04-28
Deleted.

---

### Post by shatterblast on 2009-04-28
The simplest method might be going into the Terminal option from the bottom left of the screen if it gives you the choice to even log in.  If not, you might try pressing CTRL + SHIFT + F4 for a black log in screen.  If you press some buttons to get the command shell, then you will need to log in of course.

After that, try the following:

sudo apt-get install envyng-core
sudo envy-ng -t

That should allow a reinstall of your ATI drivers at a minimum.  After that, you can probably tweak what drivers you really want after X works again.

---

### Post by rubenverweij on 2009-04-28
Thanks for your reply.
I have no internet connection on the laptop though, and the script downloads specific drivers I gather?
Would I be able to download them manually and put them on a USB stick?

---

### Post by shatterblast on 2009-04-28
If you can connect a cable from a DSL or cable modem to your notebook before turning it on, it should work fine.  Most modems I'm aware of ship with at least one.  Envyng will let you select an appropriate driver, download it for you, and install it, but the software also requires an Internet connection for the entire process I believe.  I consider it the easiest way.

Gdebi can be used to install a DEB file if you can download one specific to your graphics hardware.  In my understanding, you could put the appropriate DEB file on a USB device just fine.  It would just have to be connected to the computer before it boots up.  Assuming it detects the USB drive correctly, it would probably be listed under "/media".  So the process might go something like:

[log-in with user name and password]

cd /media
dir

[search for the name of your drive]

cd /input_drive_name_here
dir

[search for the name of your ATI file]

sudo gdebi ati_file_name_here.DEB

sudo reboot

I'm assuming though that the USB drive will mount after a reboot or whatever.  Otherwise, you might have to use the "mount" command.  It's something I'm not familiar with.  Also, names are case-sensitive in terminal.  If your USB drive name is in all caps, you will have to type it out as such.  There is also a copy and paste function with the mouse if you right click I think.  It helps in avoiding the need to type out long names.  That or you can just rename your DEB driver file to something really simple.

---

