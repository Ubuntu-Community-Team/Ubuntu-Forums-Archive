---
title: "Can't install Xboxdrv, error returned"
date: 2015-04-24
forum: Hardware
---

### Post by z-buildrocks on 2015-04-24
Whenever I try to install xboxdrv, it returns:
```
Setting up ubuntu-xboxdrv (20150319-1) .../usr/bin/update-desktop-database
Failed to start xboxdrv.service: Unit xboxdrv.service failed to load: No such file or directory.
dpkg: error processing package ubuntu-xboxdrv (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 ubuntu-xboxdrv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I dont know why the file/directory is missing, and I would love to get my controller working.

---

### Post by z-buildrocks on 2015-04-24
When I try to install xboxdrv, it returns:
```
Setting up ubuntu-xboxdrv (20150319-1) .../usr/bin/update-desktop-database
Failed to start xboxdrv.service: Unit xboxdrv.service failed to load: No such file or directory.
dpkg: error processing package ubuntu-xboxdrv (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 ubuntu-xboxdrv
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I dont know why the file/directory is missing, and I would love to get my controller working.

My controller hadn't been working, so I purged xboxdrv and ran apt-get autoremove, and now that happens when I try to install it. Help would be much appreciated.

---

### Post by cariboo on 2015-04-24
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by Cybolic on 2015-05-12
xboxdrv doesn't seem to work in 15.04 due to the change to from Upstart to Systemd.

I got it working by creating a new file /etc/systemd/system/xboxdrv.service:```
[Unit]
Description=Load the XBoxDrv controller driver
Documentation=man:xboxdrv(1)

[Service]
Type=forking
EnvironmentFile=-/etc/default/xboxdrv
ExecStartPre=/bin/rm -f /dev/input/js*
ExecStart=/usr/bin/xboxdrv --daemon --detach --pid-file /var/run/xboxdrv.pid --silent --dbus disabled $XBOXDRV_OPTIONS $PAD_OPTIONS $CONTROLLER0_OPTIONS

[Install]
WantedBy=multi-user.target
```

and put the following in /etc/defaults/xboxdrv file (adjust to taste):```
#!/bin/bash
# Defaults for xboxdrv service

# If enabled, can present problems on wine games
FORCE_FEEDBACK=true

# Make triggers work like buttons instead of zaxis
TRIGGER_AS_BUTTON=false

# Mimic xpad buttons
MIMIC_XPAD=false

# Additional options that are passed to xboxdrv (see xboxdrv man pages).
# These are appended once during start
XBOXDRV_OPTIONS=""

# Edit each block to give each controller slot its own options.
# These are appended last for their respective slots
CONTROLLER0_OPTIONS=""                                                                                                                                                                                                                         
CONTROLLER1_OPTIONS=""
CONTROLLER2_OPTIONS=""
CONTROLLER3_OPTIONS=""


##############################
# Don't edit after this line #
##############################

# This will store all pad options from /etc/default/xboxdrv
PAD_OPTIONS=""
# Checking if user has enabled forcefeedback
if [[ $FORCE_FEEDBACK -eq true ]] ; then
    PAD_OPTIONS="$PAD_OPTIONS --force-feedback"
fi
# Checking if user has enabled mimic_xpad
if [[ $MIMIC_XPAD -eq true ]] ; then
    PAD_OPTIONS="$PAD_OPTIONS --mimic-xpad --mimic-xpad-wireless"
fi
# Checking if user is using trigger as buttons instead of zaxis
if [[ $TRIGGER_AS_BUTTON -eq true ]] ; then
    PAD_OPTIONS="$PAD_OPTIONS --trigger-as-button"
fi
# Adding --detache-kernel-driver
PAD_OPTIONS="$PAD_OPTIONS --detach-kernel-driver"

```

You can now start xboxdrv by running
```
sudo systemctl start xboxdrv.service
```

(Note, I know next to nothing about Systemd, so this might not be the right way to do things - I just followed the guides for Ubuntu and Fedora.)

---

### Post by carmeloscollo on 2015-05-18
> **Cybolic said:**
> xboxdrv doesn't seem to work in 15.04 due to the change to from Upstart to Systemd.

I got it working by creating a new file /etc/systemd/system/xboxdrv.service:```
[Unit]
[...]
You can now start xboxdrv by running
[code]sudo systemctl start xboxdrv.service
```


Can you elaborate a bit on that? Are you trying to use ubuntu-xboxdrv from [https://launchpad.net/~rael-gc/+archive/ubuntu/ubuntu-xboxdrv?](https://launchpad.net/~rael-gc/+archive/ubuntu/ubuntu-xboxdrv?)
Did you first install from the ppa by doing a sudo apt-get install ubuntu-xboxdrv before creating the xboxdrv.service?
You also mentioned that you launch xboxdrv yourself with the systemctl command. Does this mean that it wont run on startup and you have to launch it yourself everytime?

Thank you in advance for your input! I would really love to get this running again.

P.S.: I created an issue in ubuntu-xboxdrv's GitHub repository and linked to your answer in this forum (see [https://github.com/raelgc/ubuntu_xboxdrv/issues/39#issuecomment-102951342](https://github.com/raelgc/ubuntu_xboxdrv/issues/39#issuecomment-102951342))

---

### Post by carmeloscollo on 2015-05-24
Just FYI: problem should be solved now. 

I got together with the maintainer of Ubuntu-xboxdrv on his GitHub repo and with the amazing people I met there we managed to put together a working migration to systemd.
The package has been updated and you should now be able to install the driver exactly the way you used to do and things should work the same. If you have any comments, feedback or bug reports I suggest you head over to the GitHub repo and open an issue.

---

