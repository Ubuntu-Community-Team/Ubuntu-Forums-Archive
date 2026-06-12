---
title: "No Sound with X-fi Extreme gamer."
date: 2008-10-17
forum: General Help
---

### Post by -RYknow on 2008-10-17
Hey guys. I'm running Hardy, and my system specs are as follows. 

MOBO: Asus A8N-SLI Premium
CPU: Opteron 170
RAM: 2 gigs OCZ DDR500
GPU: EVGA 8800GTX ACS3 Edition
Sound: X-fi Extreme Gamer, Fatal1ty Edition


I've been running the machine for months without any issues. I recently got some new updates, and all of sudden my sound isn't working. I went back to the guide I used to install the card the first time, and had no luck. Here is a copy&pasted version of the guide I used...

> Installing OSS 4.0 From a .deb package

Check to see if your device is supported by OSS:
The official and outdated list can be found at [http://manuals.opensound.com/devlists/Linux.html](http://manuals.opensound.com/devlists/Linux.html)
(Ignore the old references to retail drivers; it's all free now)
I've also attached the device list from the latest build (4.0-1015) so double-check that if you don't see your card on the site's list.

Go here:[http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi)
Get the Linux 2.6 DEB package for your architecture (use x86 unless you have the amd64 Ubuntu) and save it to your home folder (i.e. the ~/ directory)

0. Get necessary packages
Code:
sudo apt-get install gcc gcc-4.2 gcc-4.2-base make build-essential binutils linux-headers-`uname -r` libssl-dev libssl0.9.8
1. Copy these directions to a text file so you can view them from a terminal, or print them out/write them down
2. Remove ALSA:
Code:
sudo apt-get remove alsa-base alsa-oss oss-compat
3. Reboot, but don't log in
4. Change your session (clicking the icon in the lower left of the login screen) to failsafe terminal.
5. Now Log In
6. Navigate to where you have the deb file saved (e.g. if it's your home dir, cd ~/ ). Note the name of the file will be oss-linux_v4.0-1015_amd64.deb if you downloaded that version
Code:
sudo dpkg -i oss-linux_v4.0-1015_i386.deb
sudo soundon
7. Just issue the exit command and when it goes back to the login screen, log in as normal.
8. OSS uses it's own mixer GUI (ossxmix). You'll need to right-click on and remove the Gnome mixer/volume control icon from the panel.
9. Add a new custom application launcher to the panel that runs the command: ossxmix - That's ossxmix, not ossmix, Name the launcher whatever you want and pick an icon. I named mine "Mixer" and chose /usr/share/icons/gnome/32x32/status/stock_volume-med.png as my icon.
10. You'll have to tell applications to use the OSS output plugin instead of ALSA. Some applications (like Audacious) have user-friendly controls for this. Others require command line input or configuring a text file. See: [http://www.4front-tech.com/wiki/inde...ions_for_OSSv4](http://www.4front-tech.com/wiki/inde...ions_for_OSSv4)

If you're still not getting sound, see what the ossdetect -v and ossinfo commands give you.

ADDENDUM: Volume Control Patch The current gstreamer-based volume control in GNOME is incompatible with OSSv4, meaning your mouse wheel and media buttons won't work. To remedy the issue, try Clive Wright's patch. I've also built and attached an AMD64 version to this post. Note that this patch was updated on 1/8/08, so if you tried it before then and it didn't work, try again.
Also, if you'd prefer to map commands to your shortcut keys, here are some scripts to use (at the bottom of the page).

ADDENDUM2: Sound in Flash
1. Run:
Code:
file /usr/lib/libflashsupport.so
If this returns info on the file, skip ahead to step 4. If the file isn't found...
2. Save the attached libflashsupport.so.gz to your Desktop
3. 
Code:
cd ~/Desktop; gunzip libflashsupport.so.gz; sudo mv libflashsupport.so /usr/lib
4. create symbolic links to /usr/lib/firefox/plugins & /usr/lib/mozilla/plugins:
Code:
sudo ln -s /usr/lib/libflashsupport.so /usr/lib/firefox/plugins; sudo ln -s /usr/lib/libflashsupport.so /usr/lib/mozilla/plugins


So, any help would be great! Can't stand not having sound, so please...help! 

-RYknow

---

### Post by -RYknow on 2008-10-18
Anyone be able to help me...?

I downloaded a driver right from Creative, how do I go about installing it?

-RYknow

---

### Post by -RYknow on 2008-10-18
Solved using [http:////help.ubuntu.com/community/OpenSound]("http:////help.ubuntu.com/community/OpenSound")

-RYknow

---

