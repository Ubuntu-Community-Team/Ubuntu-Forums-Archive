---
title: "need help installing webcam"
date: 2008-09-19
forum: Hardware
---

### Post by Hyper Tails on 2008-09-19
hi i run hardy and i got a microdia u-cam ne878 and i was following this step by step thing for installing my web cam and for some reason i keep getting this stuff
```
liam@liam-desktop:~$ cd microdia
liam@liam-desktop:~/microdia$ make
make -C /lib/modules/2.6.24-21-generic/build SUBDIRS=/home/liam/microdia modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
make: ctags: Command not found
make: *** [ctags] Error 127
liam@liam-desktop:~/microdia$ su
Password:
su: Authentication failure
liam@liam-desktop:~/microdia$ insmod ./microdia.ko
insmod: error inserting './microdia.ko': -1 Operation not permitted
liam@liam-desktop:~/microdia$

```

please help

---

### Post by IntuitiveNipple on 2008-09-19
> 
make: ctags: Command not found

It looks like the Makefile uses that command and it isn't installed.

There's an Ubuntu package "exuberant-ctags" that installs /usr/bin/ctags-exuberant. It is possible you could use that via a symbolic link:
```

sudo apt-get install exuberant-ctags
sudo ln -s /usr/bin/ctags-exuberant /usr/bin/ctag

```
Otherwise you'll probably need to use the [ctags project source](http://ctags.sourceforge.net/) to build the executable.

---

### Post by Hyper Tails on 2008-09-20
got it

but for some reason when i open up cheese i get it working for 1 second then it goes black

what's going on?

---

### Post by IntuitiveNipple on 2008-09-20
> **Hyper Tails said:**
> got it

but for some reason when i open up cheese i get it working for 1 second then it goes black

what's going on?
From the number of reports Cheese isn't that well-behaved for a lot of cameras. Try using the camera with vlc or some other video application that can connect to a V4L (Video 4 Linux) source.

---

### Post by Hyper Tails on 2008-09-20
i tried another webcam thing on cameroid.com and all it does is still show black
I don't think it chesse it problary the driver for the cam

i need to do something big now with this to show picture

---

### Post by IntuitiveNipple on 2008-09-20
As I said, try vlc. It supports a very wide range of chromas (which other applications don't). If you run it from the command-line you'll get a lot of messages telling you what it finds and any problems so if there is a problem with the driver, you can see it and report it.

---

### Post by Hyper Tails on 2008-09-20
i installed vlc and what programs will work in vlc?

---

### Post by IntuitiveNipple on 2008-09-20
Run it from a command-prompt:
```
 vlc

```
Then open a capture device, select the device name of the camera (possibly /dev/video0). vlc will report its attempts to connect to the device and any problems it encounters. If it works, a window will open with the camera output displayed in it.

---

### Post by Hyper Tails on 2008-09-20
here's my results

---

### Post by Hyper Tails on 2008-09-20
.................................................................................................................................
.................................................................................................................................
..................................................................................................................

---

### Post by Hyper Tails on 2008-09-20
please help...

---

