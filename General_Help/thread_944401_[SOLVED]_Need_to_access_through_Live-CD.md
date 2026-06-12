---
title: "[SOLVED] Need to access through Live-CD"
date: 2008-10-11
forum: General Help
---

### Post by DougieFresh4U on 2008-10-11
I did it again. Playing with graphics drivers, I removed **vesa** and tried to use the **intel driver** but my machine didn't cooperate and would not boot up all the way.. So I have popped in the Live-CD and I do not know how to access Synaptic to re-install drivers. When I go to **"Places"** from the menu bar it lists my install a**s"39.6 GB Media"** I have gone through that but not sure how to access anything correctly. Please some one guide through this mess
I promise I won't fiddle any more :lolflag:

---

### Post by DougieFresh4U on 2008-10-11
Can some one please help me to mount via Live-CD so I can get into Synaptic and install vesa driver

---

### Post by Bucky Ball on 2008-10-11
You should be able to
```

apt-get install

```
whatever package you're after, as that's what Synaptics basically does.

---

### Post by DougieFresh4U on 2008-10-11
> **Bucky Ball said:**
> You should be able to
```

apt-get install

```
whatever package you're after, as that's what Synaptics basically does.

I can not log in normally as x is broke. therefore I am using live cd

---

### Post by DougieFresh4U on 2008-10-11
Please help as I am messing it up more and more with guesses and trial and error

---

### Post by DougieFresh4U on 2008-10-11
Some body please help
I have done a lot of reading and tried many codes and I fear that I am messing it up more. 
I am on live cd and need to x and I need to get at my files. From live cd I am able to see disk listed as shown in screen shot posted above but a lot of things I click when in that media thingy tells me it can't open as I do not own or have permission

---

### Post by Prospero2006 on 2008-10-11
You'll need to log in using recovery mode until you get X back up.
The configuration file is located at /etc/X11/xorg.conf

In that file you'll find a parameter for the 'intel' driver.
Edit it with the 'pico' text editor and change the 'intel' driver
to 'vesa'

Once you've edited /etc/X11/xorg.conf, type startx and check for error messages.

---

### Post by DougieFresh4U on 2008-10-11
> **Prospero2006 said:**
> You'll need to log in using recovery mode until you get X back up.
The configuration file is located at /etc/X11/xorg.conf

In that file you'll find a parameter for the 'intel' driver.
Edit it with the 'pico' text editor and change the 'intel' driver
to 'vesa'

Once you've edited /etc/X11/xorg.conf, type startx and check for error messages.

Hello and thank you.
I have tried going the recovery mode but can't. May be I am not doing it right. Is there not a way to do it through live cd, mount drive via terminal? I am so frustrated and lost as I have been tinkering all day with this

---

### Post by bodhi.zazen on 2008-10-11
Boot to recovery mode

You will get a menu -> select "xfix"

when that is done -> continue to boot normally.

---

### Post by DougieFresh4U on 2008-10-11
> **bodhi.zazen said:**
> Boot to recovery mode

You will get a menu -> select "xfix"

when that is done -> continue to boot normally.

Thank you
what you are saying is get live cd out of machine and boot machine and select recovery from grub menu and usually that dumps me to a shell which I would need to type some thing in and that would be "xfix" ?

---

### Post by bodhi.zazen on 2008-10-11
Not exactly.

Remove the CD, boot to hard drive, select recovery mode.

As the machine boots you will eventually get a menu, on the menu select "xfix"

It will do it's thing ....

You can then select continue normal booting.

---

### Post by DougieFresh4U on 2008-10-11
> **bodhi.zazen said:**
> Not exactly.

Remove the CD, boot to hard drive, select recovery mode.

As the machine boots you will eventually get a menu, on the menu select "xfix"

It will do it's thing ....

You can then select continue normal booting.

Ah, I remember seeing that earlier, it was a gray box with a few lines of things to select and the first one was highlighted in red. I TRIED to move the red line down but no matter what I tried it wouldn't move. I tried up/down keys, page up/page down but nothing would move and had to hard shut down

---

### Post by bodhi.zazen on 2008-10-11
ouch, well you can always boot to the command line and :

```
sudo dpkg-reconfigure xserver-xorg
```

Then

```
telinit 2
```

---

### Post by DougieFresh4U on 2008-10-11
> **bodhi.zazen said:**
> ouch, well you can always boot to the command line and :

```
sudo dpkg-reconfigure xserver-xorg
```

Then

```
telinit 2
```

Sorry to be such a pain. I have booted to command line and it tells me no can do. This is why I would like to mount from live cd via terminal. You can see from screen shot that my partition is there (39.6 GB M) But I cannot open things in it. Can't I get to my drive via terminal mounting. I do not want to do a fresh install (promise I won't tweak the graphics any more :lolflag:)

---

### Post by bodhi.zazen on 2008-10-11
do you get an error message ?

To do this from the desktop CD you need to know our Ubuntu partition.

Assuming it is /dev/sda1 (change as needed)

```
# become root

sudo -i

# mount your Ubuntu partition

mount /dev/sda1 /mnt

# chroot

chroot /mnt

# fix X

dpkg-reconfigure xserver-xorg
```

exit the terminal and reboot.

You can change anything you wish, just make a back up of the config files first (and it helps to comment your changes).

If you have a backup, you can restore without having to re-install.

---

### Post by DougieFresh4U on 2008-10-11
> **bodhi.zazen said:**
> do you get an error message ?

To do this from the desktop CD you need to know our Ubuntu partition.

Assuming it is /dev/sda1 (change as needed)

```
# become root

sudo -i

# mount your Ubuntu partition

mount /dev/sda1 /mnt

# chroot

chroot /mnt

# fix X

dpkg-reconfigure xserver-xorg
```

exit the terminal and reboot.

You can change anything you wish, just make a back up of the config files first (and it helps to comment your changes).

If you have a backup, you can restore without having to re-install.
Thank you, now were getting some where. I did x configure when it popped up but as you most likely know the Intrepid version doesn't do the graphics questions as previous releases have. So I did "displayconfig-gtk and you can see from posted terminal output what happened, it didn't open as it should. That command is what I played with that screwed all up. If I could get to my Firefox for bookmarks and saved passwords I would just reinstall- is that possible. I think were at the end of what can be done
[B]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# mount /dev/sda1 /mnt
root@ubuntu:~# chroot /mnt
root@ubuntu:/# dpkg-reconfigure xserver-xorg
grep: /proc/cmdline: No such file or directory
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20081011220908
grep: /proc/cpuinfo: No such file or directory
root@ubuntu:/# displayconfig-gtk
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 71, in __init__
    gtk.init_check()
RuntimeError: could not open display
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 73, in apport_excepthook
    pr.add_proc_info()
  File "/usr/lib/python2.5/site-packages/apport/report.py", line 349, in add_proc_info
    self['ExecutablePath'] = os.readlink('/proc/' + pid + '/exe')
OSError: [Errno 2] No such file or directory: '/proc/8431/exe'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 71, in __init__
    gtk.init_check()
RuntimeError: could not open display
[/B]

---

### Post by bodhi.zazen on 2008-10-11
yea, I did not set up your chroot for full functionality.

exit the chroot and the reboot to hard drive and you should be fine.

---

### Post by DougieFresh4U on 2008-10-11
> **bodhi.zazen said:**
> yea, I did not set up your chroot for full functionality.

exit the chroot and the reboot to hard drive and you should be fine.

Thanks 
stupid me, but what is the code to get out of this terminal. It's still open as I did not know if just closing it would hurt
again thanks so much and if this doesn't work I am just gonna fresh install

---

### Post by bodhi.zazen on 2008-10-11
exit :)

twice :twisted:

---

### Post by DougieFresh4U on 2008-10-11
> **bodhi.zazen said:**
> exit :)

twice :twisted:

Yes,** Login Screen **is back, **Password Screen** is back!!!:)
No, it goes to **blank white screenafter password is entered**.Remember now, I **removed** the** vesa driver** via Synaptic as well as **xserver-xorg all** and** all xserver drivers except intel.** It was using the vesa and I had thought it should be using intel. But when I removed all, that's what caused this whole drama. 
**I can access the Failsafe Terminal from login window**. Can I **reinstall vesa and xserver-xorg video all throuhg Failsafe Terminal**? If so, codes please. I am almost there
**You are the greatest, thanks so much for your time**
On live cd again

---

### Post by bodhi.zazen on 2008-10-12
go through the same steps to mount your ubuntu partition to /mnt and chroot /mnt ...

It may be easiest to just :

```
apt-get install ubuntu-desktop
```

If that does not install xserver-xorg

```
apt-get install xserver-xorg xserver-xorg-video-vesa
```

exit and boot to hard drive.

---

### Post by DougieFresh4U on 2008-10-12
> **bodhi.zazen said:**
> go through the same steps to mount your ubuntu partition to /mnt and chroot /mnt ...

It may be easiest to just :

```
apt-get install ubuntu-desktop
```

If that does not install xserver-xorg

```
apt-get install xserver-xorg xserver-xorg-video-vesa
```

exit and boot to hard drive.

Am I forgeting some thing?
```
root@ubuntu:/# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  bluez-network docbook-to-man linux-headers-2.6.27-5 linux-headers-2.6.27-6 docbook-xsl m4 autoconf
  openjade intltool libtool libx264-57 gnome-common linux-headers-2.6.27-5-generic autotools-dev
  docbook-xsl-doc-html libostyle1c2 bluez-input libltdl7-dev automake jade bluez-serial docbook-dsssl
  linux-headers-2.6.27-6-generic portmap libgnome-desktop-2 docbook
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  human-theme ubuntu-artwork
The following packages will be REMOVED:
  gtk2-engines-ubuntulooks
The following NEW packages will be installed:
  human-theme ubuntu-artwork ubuntu-desktop
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/101kB of archives.
After this operation, 385kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  human-theme ubuntu-artwork
Install these packages without verification [y/N]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 203064 files and directories currently installed.)
Removing gtk2-engines-ubuntulooks ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Selecting previously deselected package human-theme.
(Reading database ... 203054 files and directories currently installed.)
Unpacking human-theme (from .../human-theme_0.28_all.deb) ...
Selecting previously deselected package ubuntu-artwork.
Unpacking ubuntu-artwork (from .../ubuntu-artwork_46_all.deb) ...
Selecting previously deselected package ubuntu-desktop.
Unpacking ubuntu-desktop (from .../ubuntu-desktop_1.119_i386.deb) ...
Can not write log, openpty() failed (/dev/pts not mounted?)
Setting up human-theme (0.28) ...
Setting up ubuntu-artwork (46) ...

Setting up ubuntu-desktop (1.119) ...
root@ubuntu:/# apt-get install xserver-xorg xserver-xorg-video-vesa
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xorg is already the newest version.
The following packages were automatically installed and are no longer required:
  bluez-network docbook-to-man linux-headers-2.6.27-5 linux-headers-2.6.27-6 docbook-xsl m4 autoconf
  openjade intltool libtool libx264-57 gnome-common linux-headers-2.6.27-5-generic autotools-dev
  docbook-xsl-doc-html libostyle1c2 bluez-input libltdl7-dev automake jade bluez-serial docbook-dsssl
  linux-headers-2.6.27-6-generic portmap libgnome-desktop-2 docbook
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  xserver-xorg-video-vesa
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 24.2kB of archives.
After this operation, 102kB of additional disk space will be used.
Err http://archive.ubuntu.com intrepid/main xserver-xorg-video-vesa 1:2.0.0-1ubuntu3
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/x/xserver-xorg-video-vesa/xserver-xorg-video-vesa_2.0.0-1ubuntu3_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by bodhi.zazen on 2008-10-12
yea, you still need the vesa drivers.

```
apt-get update && apt-get install server-xorg-video-vesa
```

If you wish, you can do some house cleaning :

```
apt-get autoremove
```

but to be honest, I would leave that for now (lest get X back first).

---

### Post by DougieFresh4U on 2008-10-12
> **bodhi.zazen said:**
> yea, you still need the vesa drivers.

```
apt-get update && apt-get install server-xorg-video-vesa
```

If you wish, you can do some house cleaning :

```
apt-get autoremove
```

but to be honest, I would leave that for now (lest get X back first).

I'm doing some thing wrong:
```
root@ubuntu:/# apt-get update && apt-get install server-xorg-video-vesa
Err http://archive.ubuntu.com intrepid Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-backports Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-backports/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-backports/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-backports/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-backports/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-security/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-proposed Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-proposed/restricted Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-proposed/main Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-proposed/multiverse Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com intrepid-proposed/universe Translation-en_US
  Could not resolve 'archive.ubuntu.com'
Err http://archive.canonical.com intrepid Release.gpg
  Could not resolve 'archive.canonical.com'
Err http://archive.canonical.com intrepid/partner Translation-en_US
  Could not resolve 'archive.canonical.com'
Err http://ppa.launchpad.net intrepid Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net intrepid/main Translation-en_US
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net intrepid Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net intrepid/main Translation-en_US
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net intrepid Release.gpg
  Could not resolve 'ppa.launchpad.net'
Err http://ppa.launchpad.net intrepid/main Translation-en_US
  Could not resolve 'ppa.launchpad.net'
Err http://packages.medibuntu.org intrepid Release.gpg
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org intrepid/free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err http://packages.medibuntu.org intrepid/non-free Translation-en_US
  Could not resolve 'packages.medibuntu.org'
Err http://wine.budgetdedicated.com hardy Release.gpg
  Could not resolve 'wine.budgetdedicated.com'
Err http://wine.budgetdedicated.com hardy/main Translation-en_US
  Could not resolve 'wine.budgetdedicated.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-backports/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/intrepid/partner/i18n/Translation-en_US.bz2  Could not resolve 'archive.canonical.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/restricted/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/main/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/multiverse/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/intrepid-proposed/universe/i18n/Translation-en_US.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/psyke83/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/themuso/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/themuso/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/kwwii/ubuntu/dists/intrepid/Release.gpg  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://ppa.launchpad.net/kwwii/ubuntu/dists/intrepid/main/i18n/Translation-en_US.bz2  Could not resolve 'ppa.launchpad.net'

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/Release.gpg  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://packages.medibuntu.org/dists/intrepid/non-free/i18n/Translation-en_US.bz2  Could not resolve 'packages.medibuntu.org'

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/Release.gpg  Could not resolve 'wine.budgetdedicated.com'

W: Failed to fetch http://wine.budgetdedicated.com/apt/dists/hardy/main/i18n/Translation-en_US.bz2  Could not resolve 'wine.budgetdedicated.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package server-xorg-video-vesa
root@ubuntu:/# 

```

---

### Post by bodhi.zazen on 2008-10-12
looks like you lost internet connection ?

exit the chroot and re-enter it. Keep in mind, we are running as root.

```
exit

chroot /mnt
```

Can you ping ?

ping [www.google.com](www.google.com) ?

If, re-try ... installing the vesa driver .

---

### Post by DougieFresh4U on 2008-10-12
> **bodhi.zazen said:**
> looks like you lost internet connection ?

exit the chroot and re-enter it. Keep in mind, we are running as root.

```
exit

chroot /mnt
```

Can you ping ?

ping [www.google.com](www.google.com) ?

If, re-try ... installing the vesa driver .

please tell me what this means as it's a problem with not letting me install vesa
```
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)

```

---

### Post by bodhi.zazen on 2008-10-12
Well, as I said, we did not completely set up your chroot. I do not think the errors you have posted represent significant problems.

For a more detailed explanation ...

First it would be best if you entered these commands while running from your hard drive. Either boot to recovery mode, or do a normal boot. After a normal boot, rather the logging in, hit Ctrl-Alt-F1 and log in the console. The become root with sudo -i

If you can not do either of those, you can work from a live CD. What we are doing is a chroot or CHange Root ie as far as the shell is concerned /mnt == /

This allows us to access your ubuntu partition and install packages.

Now if you wish to set up your chroot it takes a few more steps.

Open a terminal on the live CD, become root with sudo -i. Mount your ubuntu partition at /mnt.

Then, as root, from the live CD you could set up your chroot with some additional steps such as :

```
mount -o bind /proc /mnt/proc
```[FONT=monospace]

[/FONT]but this should not be necessary.


If you wish to use X applications, you need to ssh into your chroot and forward the applications.

A lot of this is a little advance and over kill for what we are wanting to do, which is install a single package and configure X.

For your interest, see these links :

[https://wiki.ubuntu.com/DebootstrapChroot](https://wiki.ubuntu.com/DebootstrapChroot)

[http://wiki.mandriva.com/en/Development/Howto/Chroot](http://wiki.mandriva.com/en/Development/Howto/Chroot)

[http://www.gelato.unsw.edu.au/IA64wiki/XinChroot](http://www.gelato.unsw.edu.au/IA64wiki/XinChroot)

I know those links are long, and you need to work through them in a logical manor as they are not all Ubuntu specific ...

but I do not want to confuse you too much with chroot as it is a little complex.

---

### Post by earthpigg on 2008-10-12
simple, probably dumb idea to follow:

boot from live cd. find your xorg.conf file on the cd. back-up the one on your hard drive (/etc/X11/xorg.conf). replace it with the one on the cd.

that would at least make him able to boot his computer from his HD into the GUI and logged in as normal, right? and from there, he can have another go at conviguring his graphic card support.

edit: dont do this until someone who knows what he is talking about confirms that this will not somehow make your computer explode.

---

### Post by bodhi.zazen on 2008-10-12
> **earthpigg said:**
> simple, probably dumb idea to follow:

boot from live cd. find your xorg.conf file on the cd. back-up the one on your hard drive (/etc/X11/xorg.conf). replace it with the one on the cd.

that would at least make him able to boot his computer from his HD into the GUI and logged in as normal, right? and from there, he can have another go at conviguring his graphic card support.

edit: dont do this until someone who knows what he is talking about confirms that this will not somehow make your computer explode.

Thanks for the suggestion, I know how hard it is to com in on a long thread.

Just for a summary then, 

The current problem is the OP removed (and thus needs to re-install) the vesa driver.

---

