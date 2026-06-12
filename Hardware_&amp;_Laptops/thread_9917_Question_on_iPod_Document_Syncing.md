---
title: "Question on iPod Document Syncing"
date: 2005-01-02
forum: Hardware &amp; Laptops
---

### Post by jslaker on 2005-01-02
I'm seriously considering ordering one of the refurbed 3G iPods Apple currently has on sale. I have a Windows box running iTunes, so I'm not too concerned about syncing up my music. 

However, one of the reasons I'm considering it is for portable document backup. Mainly what I'm interested in is whether anyone's already come up with a way to have your iPod automatically sync itself to say, your home directory? I imagine that a combination of hotplug and rsync ought to be able to do it, but I honestly have no idea how to go about setting it up myself.

Thanks for any help in advance. :)

---

### Post by jslaker on 2005-01-04
Well the iPod's ordered. Still no one with any suggestions?

---

### Post by castrojo on 2005-01-04
The ipod is just a hard drive, you could probably do this with rsync like you would any other portable device. 

It'd be easy to have a script to do it and then just run it by hand when you want to update it, but an automatic thing that went right after you plugged it in would be neat.

---

### Post by jslaker on 2005-01-04
Which is exactly why I was interested in it. ;-) Like I said, I figure some combination of rsync and hotplug would be able to do it, and I could probably write the script myself without much trouble, my problem is I just don't know where I'd put it so it was run whenever the iPod was hooked up. 

I'm willing to do the brunt of the work if someone could at least point me in the general direction of the things I need to be watching. IE: is there a specific place the kernel checks when a device is hotplugged for any kind of "set up" information? I've never done anything this low level with the OS before, so I'm honestly kind of lost as to where I should even start.

---

### Post by bitserf on 2005-01-04
hi,

why not do it how HAL does it?

check /etc/hal/device.d/fstab-update.hal for an example callout script executed whenever a volume appears/disappears. your version of this script can be a lot simpler as it doesn't have to be generic, and can be completely specific to your iPod. your script would just have to check that the device that just appeared is in fact your iPod, and once that check succeeds, mount it, do an rsync, and possibly unmount again.

a volume is the thing beneath "iPod/SCSI Host Interface/SCSI Device/iPod" in hal-device-manager, for example. its properties will be shown in the Advanced tab.

all the properties that show up on the "Advanced" tab in hal-device-manager for a volume will be in the environment as HAL_PROP_XXX_YYY for use by your callout script, so you can make the script only do stuff if $HAL_PROP_BLOCK_DEVICE and $HAL_PROP_INFO_PRODUCT are equal to values specific to your device. XXX_YYY is the property name in the Advanced tab, all uppercase and with '.' replaced with '_'.

however, you'll want to make sure that gnome-volume-manager doesn't go and automatically mount it for you, otherwise you have a race condition between your script and gnome-volume-manager mounting it :) perhaps a way to do that would be to selectively disable automounting for your removable device based on its "storage.model" property in /etc/hal/fdi/preferences.fdi.

check this post [http://www.ubuntuforums.org/showthread.php?t=9695](http://www.ubuntuforums.org/showthread.php?t=9695) for details on preferences.fdi tweaking. you'll want to change the <merge> key to set the "volume.policy.should_mount" key to "false". examples of setting this key to false are in /usr/share/hal/fdi/90defaultpolicy/storage-policy.fdi. you'll want to make all your FDI changes to /etc/hal/fdi/preferences.fdi though.

let us know how it goes :)

---

### Post by bitserf on 2005-01-04
oh, and you'll want to do a:

sudo /etc/init.d/dbus-1 restart

after making .fdi file changes. i'm also not quite sure whether gnome-volume-manager will still attempt to auto-mount after a HALD restart.

---

### Post by jslaker on 2005-01-07
[QUOTE=bitserf]oh, and you'll want to do a:

sudo /etc/init.d/dbus-1 restart

after making .fdi file changes. i'm also not quite sure whether gnome-volume-manager will still attempt to auto-mount after a HALD restart.[/QUOTE]
 Thanks for the info bitserf, sounds like what I was looking for. I got the iPod today, but unfortunately they only sent the FW cable and my notebook only has USB, so I won't be able to try this til I get a USB cable from a friend of mine. I'll definitely let you know how it goes though.

---

