---
title: "Please help with a problem starting X!"
date: 2009-06-12
forum: Installation &amp; Upgrades
---

### Post by FokkerCharlie on 2009-06-12
Hello!

Last night I tried to manually upgrade my Nvidia driver to the latest version from their website, after previously using the 180-glx driver in the repos.  Unfortunately, it's caused some problems.

Removing the old driver proceeded fine, without errors, and the Nvidia installer went smoothly.  After rebooting, I am faced only with the text screen (after usplash, no GDM), and can log in fine.  Then, I can switch to terminal 8 (ctrl+alt+f8), but the last message there refers to setting Advanced Power Management.

I tried sudo dpkg-reconfigure xserver-xorg, which returned:
xserver-xorg is broken or not fully installed.

I can't get connected to the network via the terminal here (iwlist scan finds the network, but I don't get a DCHP offer), so I can't reinstall it!  Is it possible to download the packages to some other media or something?  Aaaargh!

Please help!  I'm hoping someone has a magic bullet for this....

Charlie

---

### Post by dstew on 2009-06-12
If you have Ubuntu 9.04, try the **xfix** command from a Recovery boot, or a command line. That creates a new xorg.conf file, which hopefully will get you a GUI.

---

### Post by FokkerCharlie on 2009-06-13
Thanks, dstew

That didn't work, sadly.  Xfix returned 'Unknown command'.

I am downloading an image of the Ubuntu CD.  Can anyone give me a sample line for me to insert in /etc/apt/sources.list so that I can reinstall xserver-xorg from it?  The line isn't there at the moment.  I'm using the 9.04 amd64 image.

Cheers!
Charlie

---

### Post by gradinaruvasile on 2009-06-13
Boot in recovery mode 
Select root prompt

type 
apt-get --reinstall install xserver-xorg
dpkg-reconfigure -phigh xserver-xorg
reboot
cross fingers

---

### Post by FokkerCharlie on 2009-06-13
Hi gradinaruvasile

Thanks for your response.  Reinstalling like that doesn't seem to be working for me, it seems that xserver-xorg is no longer installed!!!!!

I added the cdrom with apt-cdrom, did apt-get update, but when I try to install xserver-xorg, the messages all seem to refer to being unable to retrieve packages from the online repos.

Am I missing something?

Cheers
Charlie

---

### Post by gradinaruvasile on 2009-06-13
No networking at all?
Try the networking option on the menu...

If not working...
Can u find the deb package on the cd copy ? Copy it to the hard drive, and issue

cd /to/folder/  - the folder where the deb is
sudo dpkg -i *

---

### Post by FokkerCharlie on 2009-06-13
Hmmmm.

First off- the networking; I have not managed to get it to connect to the network here in the hotel that I am at via the CLI.  DHClient requests many times, but gets no offers.

On the CD, I cannot find xserver-xorg package, in fact there are very few packages there!  I will see if I can download from somewhere else...

Further input, if you have any, much appreciated!
Charlie

---

### Post by gradinaruvasile on 2009-06-13
Boot from the cd and download the packages...

---

