---
title: "Hacking Ubiquity"
date: 2008-11-04
forum: General Help
---

### Post by chris4585 on 2008-11-04
**Situation**
I'm making a LiveCD, the WM is openbox

**Problem**
During the livecd there is a openbox menu entry "Install" of course I need it gone when the user reboots.

**Solution**
These commands need to be ran before the user is created

```
	rm -rf /etc/skel/.config/openbox/menu.xml
	mv /etc/skel/.config/openbox/_menu.xml /etc/skel/.config/openbox/menu.xml
```

How can I hack Ubiquity to do so?  I've tried a few things none of them have worked.  I guess it would help if I could figure out how ubiquity is copying files, or where the mounted drive is, etc..

help! thanks

---

### Post by jedi453 on 2008-11-05
From the Ubiquity README

> The actual installation takes place by copying the read-only part of the
live filesystem. The writable part of the live filesystem (i.e. the running
live session) is intentionally not copied, to ensure maximum reproducibility
of the installed system. Thus, any customisations applied by the live boot
process must be re-applied after the read-only filesystem is copied. The
live boot process is responsible for installing hooks in
/usr/lib/ubiquity/target-config/ to take care of this.

I think this means that editing /etc/skel after the liveCD is booted will not affect the final install.

I'm not sure how to make ubiquity delete and move those files. You might not have to though. If you have the final version of the menu ( the after install version) in /etc/skel and have the livecd version under /home/ubuntu or /home/casper, or wherever the user for the livecd's home directory is, then it might read the home version during livecd usage and copy the /etc/skel version for the install. This is just a guess however, and I can't confirm it yet.

Edit: You might be able to add some commands to the bottom of /usr/lib/ubiquity/apt-setup/finish-install instead

rm -rf /target/etc/skel/.config/openbox/menu.xml
cp ~/.config/openbox/_menu.xml /target/etc/skel/.config/openbox/menu.xml

---

### Post by chris4585 on 2008-11-08
> **jedi453 said:**
> From the Ubiquity README



I think this means that editing /etc/skel after the liveCD is booted will not affect the final install.

I'm not sure how to make ubiquity delete and move those files. You might not have to though. If you have the final version of the menu ( the after install version) in /etc/skel and have the livecd version under /home/ubuntu or /home/casper, or wherever the user for the livecd's home directory is, then it might read the home version during livecd usage and copy the /etc/skel version for the install. This is just a guess however, and I can't confirm it yet.

Edit: You might be able to add some commands to the bottom of /usr/lib/ubiquity/apt-setup/finish-install instead

rm -rf /target/etc/skel/.config/openbox/menu.xml
cp ~/.config/openbox/_menu.xml /target/etc/skel/.config/openbox/menu.xml

hey jedi I tried what you suggested, but that didn't work 100%  What I tried before was adding those commands to /usr/lib/ubiquity/user-setup/user-setup-apply right before the user is created, but no luck, I'll contact a developer of ubiquity to see if I can get some help.

The problem is probably I don't know the targets in the command.. I tried looking at the file but no luck

cheers

---

### Post by cjwatson on 2008-11-09
Well, as so often happens, you have two obvious choices: the quick way or the right way.

The quick way is, as you suggest, to hack Ubiquity to run the commands you mention. You can do this by dropping an executable script into /usr/lib/ubiquity/target-config/ that reads like this:

```

#! /bin/sh
set -e
rm -rf /target/etc/skel/.config/openbox/menu.xml
mv /target/etc/skel/.config/openbox/_menu.xml /target/etc/skel/.config/openbox/menu.xml

```

The right way is a bit more work, but may well save you problems down the line. The rule we generally try to follow is that the contents of the squashfs should be pretty much what's in the packages, and should be how you want the installed system to look, with the exception of changes applied by the installer in response to answers to questions and local hardware configuration. Since it's often necessary to change things around a bit to work well as a live CD, it's casper's job to do this *on the fly* as the live CD is booting. Ubiquity only copies the read-only part of the filesystem, so the changes that casper makes at boot time are ignored, and thus we simply don't have the problem you're running into.

You'll find code in /scripts/casper-bottom/10adduser in the initramfs (/casper/initrd.gz on the CD) that among other things copies the Install icon onto the ubuntu user's desktop. If just copying the .desktop file into /home/ubuntu/Desktop/ won't do the trick for openbox, then that script would probably be the right place to add code to make it work.

---

### Post by jedi453 on 2008-11-10
> **chris4585 said:**
> hey jedi I tried what you suggested, but that didn't work 100%  What I tried before was adding those commands to /usr/lib/ubiquity/user-setup/user-setup-apply right before the user is created, but no luck, I'll contact a developer of ubiquity to see if I can get some help.

The problem is probably I don't know the targets in the command.. I tried looking at the file but no luck

cheers

Sorry my suggestion didn't work. I'm happy a developer is on the case now though. I'm interested in hearing what does work.

Good Luck

---

