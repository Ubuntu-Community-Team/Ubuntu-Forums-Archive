---
title: "nVidia GeForce Go 7900 GTX New Driver"
date: 2009-03-17
forum: Hardware
---

### Post by rich1939 on 2009-03-17
I just visited the NVIDIA site and see that they have a new driver (v180) for Linux that I just downloaded from their site. I'm hoping that this new driver will eliminate the flashing, unhibited scrolling that requires a reboot to get back running.

My problem is that when I try to install the driver package as root, as follows:

```

# sh NVIDIA-Linux-x86-180.29-pkg1.run

```

The installer indicates that X-Server must be stopped before the installer will work. I don't know how to do that...and wonder whether there is a way to do this. I'm pretty desperate to resolve the bad behavior of the current v177 driver on my Dell XPS M1710 laptop using Intrepid Ibex.

Any suggestions?

---

### Post by taurus on 2009-03-17
Go into synaptic and Search for envy first.  Install that and see if it pulls down the new driver, 180, for you.

Otherwise, you can install it by hand but if it doesn't work, then you have to fix it by hand too.

```
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-180.29-pkg1.run
sudo /etc/init.d/gdm start
```

---

### Post by rich1939 on 2009-03-17
> **taurus said:**
> Go into synaptic and Search for envy first.  Install that and see if it pulls down the new driver, 180, for you. Otherwise, you can install it by hand but if it doesn't work, then you have to fix it by hand too.


Thanks for the info. One question: If I **have** to install the driver manually, then how do I **fix** the situation if it doesn't work out?

---

### Post by taurus on 2009-03-17
```
sudo dpkg-reconfigure xserver-xorg
```
Or boot into recovery mode from GRUB menu and pick the xfix option.

---

### Post by rich1939 on 2009-03-17
> **taurus said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
Or boot into recovery mode from GRUB menu and pick the xfix option.

It appears that envyng didn't find the v180 nVIDIA driver...so I entered the following into a root terminal:

```

/etc/init.d/gdm stop

```

And it displayed a black screen with several lines of information and then displayed the following:

```
/dev/sda:
```

Thereafter, even though I tried executing a command, it didn't do anything, no matter what I typed. I finally entered CTRL+ALT+DELETE to reboot.

Any reason I couldn't enter/execute a command?

---

### Post by taurus on 2009-03-17
Do you see a login prompt if you press <Alt>F2 (or even <Crtl><Alt>F2)?

But if you reboot and get back to GUI login screen, then you need to press <Ctrl><Alt>F2 and log in with your username and password.  Then, stop the gdm again from the prompt before you install the nvidia driver.

---

### Post by rich1939 on 2009-03-18
[QUOTE=taurus;6913707]Do you see a login prompt if you press <Alt>F2 (or even <Crtl><Alt>F2)?

I did get a login screen by pressing <Alt>F2 and proceeded to try to install the NVIDIA v180 driver; however, the installer reported that it didn't have an interface for my kernel and did I want it to look for one on the NVIDIA site. I said yes...and it reported that it didn't find one, so should it compile one to suit my kernel. I again said yes...and screwed the pooch. It went through the compile and link, but then said it was missing a "Type-1" component that was necessary. When I tried to boot-recover, I could only get a low-res UI. So I tried the Fix-X option and it was able to get me back to a high resolution (1920x1200)...but that wasn't compatible with any of the NVIDIA drivers. I tried to reload one of those that was acceptable and though it loaded, it could only display 640x480 or 800x600.

I'm not sure what to do now. I'd hate to re-install Ubuntu 8.10, but if it too has a Repair capability, maybe that would fix the kernel interface and I'd be back where I started.

What do you think? Is there a better solution for getting back my NVIDIA driver?

---

### Post by rich1939 on 2009-03-24
Here's the latest news: After I selected the Fix-X option, Ubuntu selected a driver that seems to give me my needed 1920x1200 display resolution...but when I tried to substitute an acredited nVidia driver, the system said that it was not compatible. Apparently, when I downloaded the new v180 driver and attempted to install it, including compiling and linking a new interface for it into the kernel, the interface was no longer compatible with any of the Ubuntu nVidia drivers.

The good news is that the driver now being used has **not** exhibited any of the flashing or other problems that required a reboot to fix.

Now I don't know whether any of the 3D effects of a *real* nVidia driver will work, but I'm only a developer/programmer and don't really need any of those effects at this time.

I'll report more as my experience grows with this new situation...but for now I'm satisfied. If/when a new kernel is released, and if it supports the new v180 nVidia driver, I may attempt to install it.

Ciao

---

### Post by stchman on 2009-03-24
> **rich1939 said:**
> I just visited the NVIDIA site and see that they have a new driver (v180) for Linux that I just downloaded from their site. I'm hoping that this new driver will eliminate the flashing, unhibited scrolling that requires a reboot to get back running.

My problem is that when I try to install the driver package as root, as follows:

```

# sh NVIDIA-Linux-x86-180.29-pkg1.run

```

The installer indicates that X-Server must be stopped before the installer will work. I don't know how to do that...and wonder whether there is a way to do this. I'm pretty desperate to resolve the bad behavior of the current v177 driver on my Dell XPS M1710 laptop using Intrepid Ibex.

Any suggestions?

Just enable the restricted driver in the Hardware drivers.  That driver works great with my 8800GT.

---

### Post by norwoods on 2009-03-24
i update to the latest nvidia proprietary prereleases for 64 bit Ubuntu 8.10 and nvidia 9600GT, 180.41 currently, from [www.avenard.org](www.avenard.org) (third party software source "deb [http://www.avenard.org/files/ubuntu-repos](http://www.avenard.org/files/ubuntu-repos) release/")using System-->Administration-->Synaptic Package Manager.  i am not sure which programs are needed so i install all six provided:
nvidia-180-libvdpau
nvidia-180-libvdpau-dev
nvidia-180-modaliases
nvidia-180-kernel-source
nvidia-glx-180
nvidia-glx-180-dev

---

### Post by rich1939 on 2009-03-28
> **stchman said:**
> Just enable the restricted driver in the Hardware drivers.  That driver works great with my 8800GT.

When I choose **Administration->Hardware Drivers**, I don't see a "restricted driver" in the list. Just NVIDIA 96, 173, and 177 are present.

However, at the present time, I'm not experiencing the problem I had before, although I have no idea what driver I'm running...just not one of those. I tried to switch back to v177 and it was deemed **incompatible**.

---

