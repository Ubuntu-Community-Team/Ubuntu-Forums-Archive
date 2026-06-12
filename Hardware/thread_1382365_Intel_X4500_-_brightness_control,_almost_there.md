---
title: "Intel X4500 - brightness control, almost there"
date: 2010-01-15
forum: Hardware
---

### Post by munsell on 2010-01-15
I have a Lenovo U150 laptop and am unable to adjust the screen brightness using the keyboard shortcuts (though the keypresses are recognized).  I have found that if I do the following as root: 
 
```

echo BRIGHTNESS_VAL > /sys/class/backlight/acpi_video0/brightness

```

and reboot my laptop, the brightness is changed.  Does anyone know how to make the changes take affect immediately without having to reboot?

---

### Post by sritacco on 2010-01-16
Hi,

I have a u150 too and I've noticed the brightness problem but don't know how to solve... sorry.
I hope we can get it fixed.
The other problem I'm seeing is that the speakers don't shut off when you plug headphones in.
I've even tried building and installing the latest version of alsa which does support the Conexant 5066.
It didn't help :-(

Steve

---

### Post by munsell on 2010-01-20
Good news for us, I believe I have solutions for the sound and brightness issues.  :D

Sound Issue (Jack sensing)
[LIST]
[*]Upgrade to latest Alsa.  A script that will help you out can be found in this thread:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)
[*]Add the following to the bottom of /etc/modprobe.d/alsa-base.conf:
```
options snd-hda-intel model=dell-vostro
```
[/LIST]

This "fix" should also work for people who own the Lenovo U350 (same chipset I believe).

Brightness
Check out this link for a way to work around the brightness issue:
[http://github.com/zaius/bright](http://github.com/zaius/bright)
I will probably write a script that will work better with the Ubuntu Notify stuff in the near future.

If you have any questions, please let me know.

UPDATE - You don't need to follow the "optional driver snapshot workflow" (standard is fine) if you use the alsa script mentioned above.

---

### Post by munsell on 2010-01-20
I just realized that the thread title is now rubbish.  We should start a U150 thread to track all of the issues/fixes (I will probably do this tomorrow if one has not yet been created).

---

### Post by decibyte on 2010-02-14
Hi there


I'm a u350 owner.

Regarding the sound issue, there's a u350 related bug here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/477226)

I don't know if it is of any help. At least I guess it isn't until the bug has been fixed.

---

### Post by cloyne on 2010-09-06
> **munsell said:**
> I just realized that the thread title is now rubbish.  We should start a U150 thread to track all of the issues/fixes (I will probably do this tomorrow if one has not yet been created).


Doesn't seem as if this is done, I am having the same issues and starting a new thread for the Lenovo U150 [http://ubuntuforums.org/showthread.php?t=1569162](http://ubuntuforums.org/showthread.php?t=1569162)

---

