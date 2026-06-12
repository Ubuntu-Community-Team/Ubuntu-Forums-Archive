---
title: "8800GTS - can't install drivers"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by Curlydave on 2007-05-23
The last time I took a stab at Linux, I had an ATI card. Poor performance aside, driver setup was straightfoward, and there were 3 workable options that I had no trouble with: Install the package, download drivers from the ATI website and run the installer, or use EasyUbuntu to set it up. All of these were followed by a minor change in the xorg config and boom, working drivers.

I'm trying it again using an 8800, and none of those methods are working. The package downloads, but then gives me a generic error when it tries to install them. (something to the effect of, "it didn't work") When I run the installer from nvidia's website, I get a weird error about X running. Easy Ubuntu just hangs when I try to install them.

What's up? Why would they just give me broken packages? I notice under display options where it lets me select my graphics card, it has all the geforce series but the 8800. Is it just not supported well? I'm assuming it's with this series because I don't see a lot of threads about people having this much trouble with nvidia drivers.

---

### Post by Matthaeus on 2007-05-23
Heaps of people have been having a lot of different issues with the 8800's, so a little more information would go a long way. Many are able to install the drivers using envy, i was not.   I would download and run the nvidia site drivers from the command line, ie not running the x server. If after that you get an API kernel mismatch error, then run the nvidia installer again and tell it to compile itself, this was the only thing that worked for me.

Matt.

---

### Post by Syke on 2007-05-23
Try the Nvidia installer again.

First press <ctrl><alt><f1> to switch to a terminal session. Log in.

Type:
```
sudo /etc/init.d/gdm stop
```
That will get rid of the "X already running" error.

While still at the terminal session, download and install the package (example below is for 32 bit/x86):
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

---

### Post by ccamen on 2007-05-23
I also have a 8800 GTS. Getting it to work with *fiesty* is not working.  Envy didn't help. I think I tried every other option.

Also, backing up files helps and the following to reconfigure the stuff....lol

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

What did work for me was this...................



> **Syke said:**
> Try the Nvidia installer again.

First press <ctrl><alt><f1> to switch to a terminal session. Log in.

Type:
```
sudo /etc/init.d/gdm stop
```
That will get rid of the "X already running" error.

While still at the terminal session, download and install the package (example below is for 32 bit/x86):
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

---

### Post by Curlydave on 2007-05-23
> **Syke said:**
> Try the Nvidia installer again.

First press <ctrl><alt><f1> to switch to a terminal session. Log in.

Type:
```
sudo /etc/init.d/gdm stop
```
That will get rid of the "X already running" error.

While still at the terminal session, download and install the package (example below is for 32 bit/x86):
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sudo sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Thanks!, It worked. I had to search and get a libc package first so it could compile a header. I'm now runnign at the right resolution and presumably 3d will work.

---

### Post by anthon.r on 2007-06-25
So how could we make deb out of that *pkg.run driver?

---

### Post by fakie_flip on 2007-06-25
dont try to make a deb out of it. if you are trying to do something fancy, then things arent going to work right on your computer like they havent been.

---

### Post by fakie_flip on 2007-06-25
> **Curlydave said:**
> Thanks!, It worked. I had to search and get a libc package first so it could compile a header. I'm now runnign at the right resolution and presumably 3d will work.

You can update the driver by pushing control alt f1 again, and then these commands.

sudo /etc/init.d/gdm stop
sudo nvidia-installer --update
sudo /etc/init.d/gdm start

---

