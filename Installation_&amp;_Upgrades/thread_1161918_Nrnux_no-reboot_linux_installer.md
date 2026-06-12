---
title: "Nrnux: no-reboot linux installer"
date: 2009-05-17
forum: Installation &amp; Upgrades
---

### Post by Yannick Le Saint kyncani on 2009-05-17
Hi,


I've made an ubuntu installer, specializing in creating ubuntu
usb sticks.

This one is different from others like the ubuntu official livecd or
usb-creator because :

- You don't have to reboot into a livecd

- It comes with a ton of features so you won't miss anything
  while using it, even without internet access.

- It can be very easily reinstalled from scratch with
  everything autodetected

- Very easy to use with automatic login, passwordless
  sudo, firewall and automatic security updates enabled

- It can create an i386 key from an amd64 system


Let's get something out of the way : due to qemu being used,
the installation is _very_ slow (hours).
Alternatives are being considered.


Why did I do it ?

Well, first, the install cd is not practical. I use primarily
one pc, it stays on 24 hours a day and I don't like having to
reboot just to create a linux usb stick.

Then, there was the excellent usb-creator, I could create easily
and quickly an ubuntu stick, BUT :

- I always had to reboot into my newly made stick to upgrade
  packages that have changed since the iso was made.
  
- I always had to install a whole bunch of stuff. Now I do understand
  that the iso cd has limited space available but I do not suffer
  the same limitation with 8,16,32 Gb sticks.

- The kernel cannot be upgraded.

- Usb-creator relies on a root filesystem stored into a fat32
  file, that means that updates and new packages are limited
  to the maximum 4 Gb file size. Plus regular file access is slow.

So, from a simple script to tweak usb-creator's installation
to my needs, to a script that could handle the whole installation
much like usb-creator without its limitations, I now have nrnux.
Nrnux comes with a very simple gui and can install current (jaunty)
and next (karmic) versions of ubuntu with minimum user intervention.


So, if you want to try it out, add these to your sources.list :

## Nrnux
deb [http://ppa.launchpad.net/y-lesaint/ppa/ubuntu](http://ppa.launchpad.net/y-lesaint/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/y-lesaint/ppa/ubuntu](http://ppa.launchpad.net/y-lesaint/ppa/ubuntu) jaunty main

And add nrnux's launchpad signing key with 

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AB7F250F

You can also download nrnux directly there (click "download file") :

[http://bazaar.launchpad.net/~y-lesaint/nrnux/stable/annotate/head:/nrnux](http://bazaar.launchpad.net/~y-lesaint/nrnux/stable/annotate/head:/nrnux)

It currently is a single python script so that it's very easy to try
it out without altering your sources.list and can be installed
in a user account.


How to use it :

- Partition your key if you want to. First a fat32 partition, to
  share files with windows if you want, then an ext3 for linux.

- You do have to be connected to the internet, because nrnux will
  pull the packages from the internet, not from an iso cd.

- Make sure you install nrnux's recommendations if you want to
  have access to the gui.

- Start nrnux. There is no menu icon at the moment, so press
  alt+f2 and enter "nrnux".

- When the installation has started, go do something else, because
  using qemu is very slow.


Ideas are more than welcomed, the project's page is here :

[https://launchpad.net/nrnux](https://launchpad.net/nrnux)


Now for some screenshots,

Here is the simple interface :

[http://img190.imageshack.us/my.php?image=200905171230simple.png](http://img190.imageshack.us/my.php?image=200905171230simple.png)

And the expert interface :

[http://img190.imageshack.us/my.php?image=200905171230expert.png](http://img190.imageshack.us/my.php?image=200905171230expert.png)


Have a nice day :)

---

