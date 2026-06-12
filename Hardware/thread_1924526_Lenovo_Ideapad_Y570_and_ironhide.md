---
title: "Lenovo Ideapad Y570 and ironhide?"
date: 2012-02-12
forum: Hardware
---

### Post by Cha0sBG on 2012-02-12
Hey guys, so yea i installed ubuntu, but can't get ironhide to work properly with my nvidia gt 555m ... it doesn't recognize my laptop ? On the model config select it says something like lenovo 20911 or something similar. Any of you can give me a lending hand ? Stuck on this for hours now and can't do anything, i 
```
sudo apt-get remove
```

ironhide and want to try again from scratch.
Any suggestions ?

---

### Post by Starks on 2012-02-12
Ironhide is dead.

[https://github.com/Bumblebee-Project/Bumblebee](https://github.com/Bumblebee-Project/Bumblebee)

Pay attention to these:
[https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu](https://github.com/Bumblebee-Project/Bumblebee/wiki/Upgrading-on-Ubuntu)
[https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo](https://github.com/Bumblebee-Project/bbswitch/tree/hack-lenovo)

---

### Post by Cha0sBG on 2012-02-12
Wait ... What ? Why in the world did i think that bumblebee was dead and ironhide was it's continued state ... anyways gonna try this and report back

EDIT:
```
Installation
The recommended method to install Bumblebee on Ubuntu is by using its Stable Releases PPA, so install that one, refresh the packages list and install Bumblebee using the nvidia driver:

sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
Now proceed with Post-installation.


Post-installation
If you are using 11.10 Oneiric and later and intend to use 32-bit applications on a 64-bit installation, install additional compatibility libraries:

sudo apt-get install virtualgl-libs:i386
Allow yourself to use Bumblebee (replace $USER by your username):

sudo usermod -a -G bumblebee $USER
For blacklisting to take effect, you may also have to update your initial ramdisk:

sudo update-initramfs -u
Re-login or reboot for the changes take effect.

Cleaning up
Bumblebee 3.0 does not use cardon or cardoff scripts anymore. You can safely remove the /etc/bumblebee/cardoff and /etc/bumblebee/cardoff files. All files ending with .dpkg-backup or similar can also be removed.

Configuration
There is often no configuration needed to get everything to work. The configuration files are located at /etc/bumblebee. The optirun program can also give you suggestions to correct settings in case something is wrong. Messages are printed to /var/log/syslog. To get all error messages related to bumblebeed (the Bumblebee Daemon), run:

grep bumblebeed /var/log/syslog
```


Is this the clean install method ? If i was to say reinstall everything from a new clean installed ubuntu

---

### Post by Starks on 2012-02-13
I'd still follow the upgrading-from-Ironhide directions.

There may still be lingering files.

---

### Post by Cha0sBG on 2012-02-14
Well i installed Bumblebee from scratch since i love testing on my machine and well doesn't work :D Even added the acpi-handle-hack module ... nothing .. says that it can't get access of my GPU

---

