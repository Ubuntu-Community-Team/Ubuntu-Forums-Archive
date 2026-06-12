---
title: "Bugs, features or bad install?"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Niniel on 2009-10-31
Hello,

I installed 9.10 from scratch on a laptop that used to run 9.04. I installed from a "Live CD" that I had put on a USB stick with unetbootin. 
It went ok except the installation stalled at 95 % and the last thing I saw was something like "upgrading grub".
But after I rebooted, the new Grub menu was there and in working order. I was also able to log in. Everything seems fine.
Except...
- when I try to install the restricted drivers for my Broadcomm wireless chip, the installation stalls at "downloading drivers"; also, even after force-exiting the installation, the CPU monitor shows 100 % CPU activity
- I am not able to install anything with Synaptic. I am getting the following error:
> E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory
-the logout button does not have properties, so I can't get rid of the annoying shutdown countdown
- I can't find the setting that allows me to edit the login screen - is that gone? Configuring the login screen through the applet in Settings brings up a joke of a configuration screen where all you can do is toggle between a login screen and automatic login
- can't mount the flashdrive anymore from which I installed KK:
> Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

If anybody can shed some light on this, that would be great.

Thanks a lot.

---

### Post by Niniel on 2009-11-02
Looks like the non-configurability of GDM and the logout button are features... lovely.

---

### Post by Niniel on 2009-11-02
All right, so a re-install took care of the wireless chip, of Synaptic and everything else, too. Whatever remains are simply things that I just don't like so much. :)

---

