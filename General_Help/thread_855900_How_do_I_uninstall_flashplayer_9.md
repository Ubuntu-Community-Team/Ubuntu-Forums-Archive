---
title: "How do I uninstall flashplayer 9?"
date: 2008-07-10
forum: General Help
---

### Post by Exacerbate on 2008-07-10
For a while now I've been trying to uninstall flash player 9 since it's crashing Ubuntu when I try to watch youtube videos and such. This wouldn't be difficult, but I can't find it in Synaptics package manager, Add/Remove, or Firefox. It shows up in firefox under 'plug-ins', but I'm unable to uninstall it, only disable it.

---

### Post by iaculallad on 2008-07-10
On your terminal:

```
sudo apt-get remove --purge flashplugin-nonfree
```

---

### Post by Exacerbate on 2008-07-10
Didn't work. It's telling me it's not installed when it quite obviously is.

---

### Post by shp on 2008-07-10
How did u originally install it?

---

### Post by Exacerbate on 2008-07-10
I went to youtube, it told me that I didn't have flash installed, so I clicked on the link and downloaded it.

---

### Post by shp on 2008-07-11
yeah from adobe's site right so it wont be registered within synaptic

i dont actually know how to remove it however if u want to disable it you can try (in firefox)

Tools > Addons> Plugins > Flash (or something) > Disable
(if your using firefox 3)

---

### Post by shp on 2008-07-11
you can also try

an extension to disable flash until you click it
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

to fix the problem with the flash crashing your browser
[http://ubuntuforums.org/showthread.php?t=855890](http://ubuntuforums.org/showthread.php?t=855890)

---

### Post by Exacerbate on 2008-07-11
Well what it's doing is crashing UBuntu alltogether forcing me to restart. I've heard this is a common problem and I was told to get flash 7 instead. I've installed 7 but 9 is still there and firefox is still using it.

---

### Post by shp on 2008-07-11
did u try disabling it?

and do they both appear in about: plugins

---

### Post by Exacerbate on 2008-07-11
Yeah I've disabled it but I cannot watch youtube videos and such. Both do not show up under plugins.

---

### Post by aysiu on 2008-07-11
> **Exacerbate said:**
> I went to youtube, it told me that I didn't have flash installed, so I clicked on the link and downloaded it.
Well, what did you do with the download?

Did you install it to /usr/lib/mozilla?

---

### Post by shp on 2008-07-11
you probably need flash player 9 to watch the youtube videos

and if they both don't show up on about: plugins, what does?

---

### Post by Exacerbate on 2008-07-11
> **aysiu said:**
> Well, what did you do with the download?

Did you install it to /usr/lib/mozilla?
I did.

Also, shp, Flash 9 shows up in plugins, but not 7.

---

### Post by Execute_Method on 2008-07-11
You should try flash10 beta which has integrated Ubuntu support:

From adobelabs website:

> System requirements for Flash Player 9 are available on Adobe.com. Flash Player 10 no longer supports Mac OS X versions 10.1, 10.2, and 10.3, nor Windows 98. Ubuntu support has been added, and we have updated our support for Red Hat Enterprise Linux and SUSE Linux distributions as follows:

To remove flash9:

> Delete libflashplayer.so binary and flashplayer.xpt file in directory /home//.mozilla/plugins/

Then install flash10 beta. I have gotten in the habit of using **checkinstall to allow for easy removal of programs that don't have a .deb** package available:

download the flash10beta tarball and save it to your home directory:

[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_070208.tar.gz)

open a terminal

then:

decompress it:

```
tar xvfz flashplayer10_install_linux_070208.tar.gz

```

install checkinstall
```
sudo apt-get install checkinstall
```

change directories:

```
cd install_flash_player_10_linux
```

install with checkinstall:

```
sudo checkinstall ./flash-installer
```

you will be asked for the directory to install it in use
it gives and example
This should be it:
```
/usr/lib/firefox-3.0/plugins
```

There will be a .deb package created called install-flash-player-10-linux
with the description you input during the checkinstall.

you can remove it easily by using synaptic or apt.

---

### Post by aysiu on 2008-07-11
Well, if you actually want to remove it, you should launch the file browser as root (*gksudo nautilus*, *gksudo thunar*, or *kdesu konqueror*) and then browse to /usr/lib/mozilla/plugins and delete the appropriate Flash plugin files.

You do realize if you remove Flash, you won't be able to view YouTube at all?

---

### Post by Exacerbate on 2008-07-11
So I've disabled flash 9, installed 10, but youtube videos don't show up. It doesn't throw me the "Hello, you either have javascript disabled...." but the video did not show up. When I disabled Flash 10, as well as flash 9, the video DID show the error. So I'm kind of at a loss here.

---

