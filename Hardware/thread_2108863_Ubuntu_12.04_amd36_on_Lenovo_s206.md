---
title: "Ubuntu 12.04 amd36 on Lenovo s206"
date: 2013-01-25
forum: Hardware
---

### Post by RBarak on 2013-01-25
Hi all,
This is my forth time. I'll make it short this time and add links for those who want more.
Good luck!

[B]1. Download Ubuntu 12.04 32 bit at:
[/B][http://www.ubuntu.com/download](http://www.ubuntu.com/download)

[B]2. Get an empty Usb with at least 2 GB?
[/B]Make a startup USB. I used Ubuntu program Startup Disk Creator.
++If you're using windows click here:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

[B]3. Watch a short preview of what the installation looks like:
[/B][http://www.youtube.com/watch?v=ba9Wv-XU_4M](http://www.youtube.com/watch?v=ba9Wv-XU_4M)

[B]4. Make coffee
[/B]
[B]5. Boot from the USB 
[/B]With this computer it's Fn+F12 when you restart.

[B]6. Installation:
[/B] At “Preparing to install ubuntu” click: “dowload updates while installing” and “install this third party software” (this will install your wifi driver and enable using media files and videos)

If you are partitioning manually remember to select “swap area” for the ubuntu partition.
This howto is very informative and has big clear pictures:
[http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/04/manual-disk-partitioning-guide-for-ubuntu-11-04/)

[B]7. Fixing the mouse
[/B]using “terminal” program (program menu is first circle on the left sidebar)
sudo su
<enter>
echo options psmouse proto=exps > /etc/modprobe.d/psmouse.modprobe
<enter>
reboot
new users – the sudo password is the password you entered at installation.
++ more here [http://ubuntuforums.org/showthread.php?t=1388164](http://ubuntuforums.org/showthread.php?t=1388164) 

[B]8. Getting more languages:
[/B]System Settings (left sidebar) - Keyboard Layout - “+”
then:  System Settings - Keyboard Layout - Options - Key(s) to change layout
then: System Settings - Language Support - Install/Remove Languages
++more here: [http://ubuntuforums.org/showthread.php?t=1860418](http://ubuntuforums.org/showthread.php?t=1860418)  
 
[B]9. Adding programs:
[/B]“Ubuntu Software Center” (the magic suitcase on the left sidebar) is the best way to install programs. Type the name of the program in the search box and install directly. If you don't find what you want: find a “.deb” file, then right click and open it with the Ubuntu Software Center.
Alternatively find a tutorial that begins with “sudo apt-get install”

[B]Wine:
[/B]“Wine” allows Linux to run Windows programs. I got it at “Software Center”

[B]Chromium:
[/B]Chromium - is the Ubuntu version of Google Chrom. I got it at “Software Center”

**Skype**:
I downloaded it from skype.com. It was a .deb file and I right-clicked and opened it with “Software Center”.

[B]Thunderbirds Profile
[/B]Copy the thunderbird folder from the old “home” folder to the new “home” folder.
If you can't see it click <ctr+H>

All the best.
++and more here: [http://ubuntuforums.org/showthread.php?t=1860418](http://ubuntuforums.org/showthread.php?t=1860418)

---

### Post by rvergara on 2013-03-14
My understanding is that the C60 is a 64bit processor.

Why did you install an Ubuntu 32 bit version? tried and did not work?

Thinking in buying an Ideapad 206 and installing Ubuntu for my wife.

Are you satisfied with the 206 performance running 12.04?

Thanks

---

