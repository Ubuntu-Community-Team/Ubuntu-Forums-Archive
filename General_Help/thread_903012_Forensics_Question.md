---
title: "Forensics Question"
date: 2008-08-27
forum: General Help
---

### Post by Timn on 2008-08-27
Hello Everyone,

Since upgrading to Hardy I am running into problems with being able to do forensics work for my classes at school. I have most of the problem ironed out except one: Auto mounting! Since I need to make sure the drives are read only this auto mounting in Hardy is driving me nuts. In 7.10 I was able to go to System > Preferences > Removable Drives and Media and just uncheck the options to turn off auto mounting. I have been researching this issue and have tried some options but none seem to work. I tried to turn this off by using gconf-editor and also by turning off gnome-volume-manager. Anyone know why they got rid of the options in Removable Drives and Media or how to disable auto mounting in Hardy?

Thanks for any help,
Timn

---

### Post by iaculallad on 2008-08-27
> **Timn said:**
> Hello Everyone,

Since upgrading to Hardy I am running into problems with being able to do forensics work for my classes at school. I have most of the problem ironed out except one: Auto mounting! Since I need to make sure the drives are read only this auto mounting in Hardy is driving me nuts. In 7.10 I was able to go to System > Preferences > Removable Drives and Media and just uncheck the options to turn off auto mounting. I have been researching this issue and have tried some options but none seem to work. I tried to turn this off by using gconf-editor and also by turning off gnome-volume-manager. Anyone know why they got rid of the options in Removable Drives and Media or how to disable auto mounting in Hardy?

Thanks for any help,
Timn

You could always edit your /etc/fstab file:

```
gksudo gedit /etc/fstab
```

and comment out the partitions w/c you do not want to automount at startup.

---

### Post by unutbu on 2008-08-27
Automounting is controlled by the "hardware abstraction layer" (hal). You can stop it with this command:

```
sudo /etc/init.d/hal stop
```

and turn it back on with

```
sudo /etc/init.d/hal start
```

---

### Post by Timn on 2008-08-27
Thank you! Stopping HAL works perfectly.

Thanks,
Timn

---

### Post by mssever on 2008-08-27
> **unutbu said:**
> Automounting is controlled by the "hardware abstraction layer" (hal). You can stop it with this command:
Disabling HAL should work, but it could have unintended consequences. For example, it's likely that NetworkManager won't work right without it.

Re fstab: Editing fstab won't do you any good.

I think that udev is the subsystem that actually handles mounting and automounting. Last time I messed with udev, I found its documentation to be lacking. I'm positive there's a udev rule somewhere that controls that, but I don't know what it is.

---

### Post by Vivaldi Gloria on 2008-08-28
> **mssever said:**
> Disabling HAL should work, but it could have unintended consequences. 

Yes. For example if you plug in a usb disk then it won't work.

Also giving the command "sudo /etc/init.d/hal stop" everytime is a bit tiring.

But one can add a custom rule to

```
/usr/share/hal/fdi/policy/10osvendor/20-storage-methods.fdi
```

or add a list of "volumes we specifically want to ignore".

I have never done this myself so I cannot tell exactly how to do it.


> Re fstab: Editing fstab won't do you any good.

Actually I think iaculallad is right and this is the best way. Put a line with the right options in fstab and you're done. The following flags are relevant:

```
auto= mounted at boot
noauto= not mounted at boot

ro= read only
rw= read/write
```

See

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)


> I think that udev is the subsystem that actually handles mounting and automounting. 

The job of udev is to maintain entries in the /dev directory, nothing more. EDIT: It's HAL who keeps the device list and gnome does the mounting. See [[COLOR="Blue"]hal[/COLOR]]("http://www.mythic-beasts.com/~mark/random/hal/").

The job of HAL is to act as a dynamic central repository of information about the current hardware configuration. The structure of this repository is quite open-ended; in particular it is possible to attach any additional attributes you like to objects, by setting up appropriate rules in the HAL configuration. Other processes can register their interest with HAL, so that they get notifications (via D-BUS) of any configuration changes.

from

[http://www.wlug.org.nz/HAL](http://www.wlug.org.nz/HAL)

There are docs about HAL in

[http://www.freedesktop.org/](http://www.freedesktop.org/)

but the site is down for the moment.

EDIT: The freedesktop.org site is working again. Search HAL there to find the docs. See e.g. [[COLOR="Blue"]faq[/COLOR]]("http://www.freedesktop.org/wiki/Software/HalFAQ").

---

