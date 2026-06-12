---
title: "Cannot open shared library libasound_module_conf_pulse.so"
date: 2013-09-11
forum: Hardware
---

### Post by zia.newversion on 2013-09-11
So I installed Skype on Ubuntu Raring and the audio input isn't working. I read somewhere on Google that I should run alsamixer in terminal. When I do that, I get this output:

```
ALSA lib conf.c:3314:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:951:(snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory
```

The other day, I experienced a strange problem when during boot-splash, the system said "disk drive for /tmp is not available" or something like that. I did recover from that, though I don't know how. But after that, some programs stopped working because config files/directories went missing. Some icons were gone too... I did a ```
apt-get install --reinstall $package
``` on every package that I found broken, and it worked. For the icons, I just visited the pixmaps directory and replaced/recreated bad links. That worked too. I'm mentioning all this because the problem *might *be related to that.

I have done --reinstall on alsa-base and pulseaudio, hoping it would resolve the problem. But it does not work. And I don't know how to approach the problem. Any help is appreciated.

---

### Post by TheFu on 2013-09-11
Unless you **really, really** know what you are doing, it is a bad idea to manually screw with files controlled by packages.  This can lead to "apt-hell", which nobody wants.  After a certain number of changes, you are better off reinstalling the OS.

There is a "troubleshooter: for most hardware issues at ubuntu.com .... sometimes it is at help.ubuntu.com and sometimes it is at other places.  Random google pages should be the last place to look for help about Ubuntu.  For sound issues, google "ubuntu sound troubleshooter" - you'll see what I mean.  Sometimes an old troubleshooter becomes out of date. Canonical always has a link at the top to a newer version.

Did the audio ever work before you touched it for any other use?

---

### Post by Yellow Pasque on 2013-09-11
The package is libasound2-plugins
Since Skype is a 32-bit program, make sure you have the 32-bit version of the package if you're using 64-bit Ubuntu:
```
sudo apt-get install libasound2-plugins:i386
```

---

### Post by zia.newversion on 2013-09-11
> **Temüjin said:**
> The package is libasound2-plugins
Since Skype is a 32-bit program, make sure you have the 32-bit version of the package if you're using 64-bit Ubuntu:
```
sudo apt-get install libasound2-plugins:i386
```

Thank you. The package was already installed, but as I mentioned earlier, something mysterious already broke half the config files and libraries on my system... So I did a --reinstall of the mentioned package and alsamixer works now. Even though the error isn't encountered now, the mic still doesn't work.

*I don't know what's going on with my system. I was introduced to Linux back in 2007 and I quickly grew fond of Ubuntu. I have used Hardy through Precise. I love to tinker, but I don't always have time to tinker. The problem arose when everything started to change. Kernel 3.0, Gnome 3.0, Unity... It was frustrating, yet inevitable. In any case, I had to move to Windows for my work because I didn't have time for adventures anymore. I haven't used Ubuntu in over an year. And now I don't remember anything! I remember that the mic on my laptop never worked out of the box with Ubuntu, and I had to add a line to some config file, probably alsaconfig or something like that...*

> **TheFu said:**
> Unless you **really, really** know what you are doing, it is a bad idea to manually screw with files controlled by packages.  This can lead to "apt-hell", which nobody wants.  After a certain number of changes, you are better off reinstalling the OS.

There is a "troubleshooter: for most hardware issues at ubuntu.com .... sometimes it is at help.ubuntu.com and sometimes it is at other places.  Random google pages should be the last place to look for help about Ubuntu.  For sound issues, google "ubuntu sound troubleshooter" - you'll see what I mean.  Sometimes an old troubleshooter becomes out of date. Canonical always has a link at the top to a newer version.

Did the audio ever work before you touched it for any other use?

I think of myself as no more than a desktop user. And you're right, reinstalling the OS is a viable solution. But I really don't want to do it because setting up the workspace is a pain - and it'll probably break again... I didn't know about the troubleshooter. I haven't looked for it yet. But I'll have a look at it and report my experiences here.

Thank you all for your help.

NOTE: I am still looking for a solution though. The machine is a **Dell Studio XPS 1645**. It's the one with *Core i7 Q740* and *ATI Radeon HD 5730* and I don't know the make/model of the sound hardware. The OS is *Ubuntu Raring* and the installation is somewhat broken.

---

### Post by TheFu on 2013-09-11
> **zia.newversion said:**
> I think of myself as no more than a desktop user. And you're right, reinstalling the OS is a viable solution. But I really don't want to do it because setting up the workspace is a pain - and it'll probably break again... I didn't know about the troubleshooter. I haven't looked for it yet. But I'll have a look at it and report my experiences here.

Why is "setting up a workspace a pain?"

Backup your current HOME, make a list of installed packages, then reinstall the OS.
After the reinstall, restore the HOME and using the list of packages to reinstall them.
```

dpkg --get-selections > ~/my-list-o-packages
```

Then post-new-install ....```

dpkg --set-selections < ~/my-list-o-packages
```

Simple.

If you have complex settings for those packages i.e. non-defaults, backup /etc too.
BTW, having automatic daily backups would mean you could try things out and restore if anything goes badly.  Backups have hundreds of different uses, not just the obvious 1.

---

### Post by Yellow Pasque on 2013-09-11
Try resetting pulseaudio configuration and then logging out:
```
rm -r ~/.config/pulse
```

If that doesn't work, give alsa info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by zia.newversion on 2013-09-16
> **TheFu said:**
> Why is "setting up a workspace a pain?"

Backup your current HOME, make a list of installed packages, then reinstall the OS.
After the reinstall, restore the HOME and using the list of packages to reinstall them.
```

dpkg --get-selections > ~/my-list-o-packages
```

Then post-new-install ....```

dpkg --set-selections < ~/my-list-o-packages
```

Simple.

If you have complex settings for those packages i.e. non-defaults, backup /etc too.
BTW, having automatic daily backups would mean you could try things out and restore if anything goes badly.  Backups have hundreds of different uses, not just the obvious 1.

Thank you! I learnt that just now. That is just awesome...
By the way, for some packages, I add ppa's and repos. I think if I backup and restore [FONT=courier new]sources.list[/FONT], that would do. However, there are some programs that I install through debs or makes. The ones I *build* don't go in dpkg selections I guess. But the ones I install through debs, won't they mess the system up when restoring?

At any rate, this was knowledge for me, and it was great. I'd like to know more about backups and re-installing complete OS without breaking any configurations. This is like the "restore-points" in Windows, but *much much* better. :D

---

### Post by TheFu on 2013-09-16
Don't leave the repo/PPA world or your recovery will break.  It is dangerous for other reasons as well.  Installing from source breaks the idea that patching the entire OS and all Apps through APT works.  Going with .deb and .tgz installs means you've just accepted the extra work to maintain and patch those packages as needed.

I don't need those hassles. If I wanted that, there are other OSes which work that way. ;)

The APT sources are in /etc, along with all sorts of other important settings, so you definitely want to backup /etc, /home, and probably /usr/local/.  Don't forget to capture the permissions, ownership and any ACLs for all the files that backed up too.

Sometimes an image-based backup is necessary too.  clonezilla, ddrescue, partimage ... can handle that, but doing image-based backups constantly will make anyone scream about the inefficiencies.

Check my signature for more. Also, there are many different solutions to this problem. I definitely **do not have** the 1-size-fits-all answer.

---

