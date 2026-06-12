---
title: "Logitech MediaPlay Mouse"
date: 2005-05-28
forum: Hardware &amp; Laptops
---

### Post by spacemonkey on 2005-05-28
I'm wondering if anyone can help me get my Logitech MediaPlay wireless mouse working on Hoary.  Right now it works great as a mouse, and it's plugged into the ps2 port, but I want the media buttons on it to be functional.  The only thing I've been able to find is this:

[http://daemon.prozone.ws/~david/projects/lmpcm_usb/](http://daemon.prozone.ws/~david/projects/lmpcm_usb/)

I tried to follow these instructions, but many of the files and folders it talks about simply do not exist on Ubuntu.  I tried compiling the driver, and the folders it tried to install to don't exist, so it gives me errors.  Does anyone know how to modify this driver to work for ubuntu.  I assume I will have to plug the mouse into the USB port to get the media buttons to work also.

---

### Post by spacemonkey on 2005-05-28
I'm extremely sorry about the multiple posts....It kept saying that it didn't go through when I clicked submit, but obviously it did.  Sorry about that.

---

### Post by raphy3 on 2006-06-04
[QUOTE=spacemonkey]I'm wondering if anyone can help me get my Logitech MediaPlay wireless mouse working on Hoary.  Right now it works great as a mouse, and it's plugged into the ps2 port, but I want the media buttons on it to be functional.  The only thing I've been able to find is this:

[http://daemon.prozone.ws/~david/projects/lmpcm_usb/](http://daemon.prozone.ws/~david/projects/lmpcm_usb/)

I tried to follow these instructions, but many of the files and folders it talks about simply do not exist on Ubuntu.  I tried compiling the driver, and the folders it tried to install to don't exist, so it gives me errors.  Does anyone know how to modify this driver to work for ubuntu.  I assume I will have to plug the mouse into the USB port to get the media buttons to work also.[/QUOTE]

Howdy friend,
If you haven't got your mouse working yet, I have a couple of ideas that could help.  To help with your problems with the missing directory, all you need to do is change the make command:
```

make -C /usr/src/linux-source-2.6.X SUBDIRS=<whatever the original is>

```
where X is your kernel version.  for me it's 2.6.12
SUBDIRS you can get from the error you get when you first try to use make:

```
make -C /lib/modules/2.6.12-10-386/build SUBDIRS=/home/raphael/lmpcm_usb-0.5.4 modules
make: *** /lib/modules/2.6.12-10-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
```

I got it to compile just fine for me when I did that.  Note, I'm on breezy, but I think it should be the same on hoary.
raphy

---

### Post by Nodren on 2006-07-02
i found this topic(which pointed me in the right direction for finding linux drivers for my mediaplay mouse, thanks!) and noticed your problem.

this is easily fixed by installing the linux-headers package(for your kernel version) using synaptic or apt-get

you can find your kernel version by running

# uname -r

---

