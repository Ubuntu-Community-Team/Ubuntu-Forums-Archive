---
title: "Uninstall Nvidia drivers or make them work"
date: 2010-10-23
forum: Hardware
---

### Post by Techrocket9 on 2010-10-23
Hi. I installed the Nvidia proprietary driver on my Asus Eee PC 1215N. I saw _[COLOR="Blue"][this warning]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus Eee PC 1215N")[/COLOR]_, but I noticed that _[COLOR="Blue"][this article]("http://asusm51ta-with-linux.blogspot.com/")[/COLOR]_ says that Vga-Switcharoo is already built into the kernel for 10.10

Anyway, I went ahead and installed the proprietary driver. However, I am now being dumped at a command prompt upon boot.

```
Sudo startx
``` returns the fatal error: no screens found

Furthermore, ```
sudo apt-get remove nvidia-glx
``` returns "Virtual packages like 'nvidia-glx' can't be removed"

I'd appreciate it if someone advised me how to either remove the Nvidia driver or make it work (the preferred option).

Thank you for your time.

---

### Post by SeijiSensei on 2010-10-23
Run "sudo nvidia-xconfig" at the $ prompt.  Reboot.  How are we doing now?

---

### Post by Techrocket9 on 2010-10-25
No dice. I think it has something to do with Nvidia's Optimus hybrid graphics, as per the links in my first post.

Also, I am slow to respond because this machine dual boots with Windows, (which is working). As long as one OS is functional, the time allocated to fixing things is almost zero. I only get the machine whenever other people don't need it. However, I still appreciate the help.

---

### Post by jerry21locke on 2010-10-25
I dont think this wont work for your. Because Nvidia is dumping you just like apple is dumping Nvidia graphics.

---

### Post by Techrocket9 on 2010-10-25
> **jerry21locke said:**
> I dont think this wont work for your. Because Nvidia is dumping you just like apple is dumping Nvidia graphics.

Well, could you at least tell me how to uninstall the Nvidia drivers?

---

### Post by SeijiSensei on 2010-10-25
Oh, right, that's the new NVIDIA card that's suppose to support on-demand graphics adapter switching, and no longer works well with Linux.  I read somewhere recently that you can disable this feature on some machines in the BIOS and force it to use the NVIDIA adapter.  Don't know if that will work on a 1215N, though, but you might browse around in the BIOS and see if it's an option for you.

---

### Post by Techrocket9 on 2010-10-25
No dice. The BIOS is pretty nerfed. (although it's the first I've seen with animations).

At this point, I would settle for uninstalling the Nvidia driver. Any help there?

---

### Post by Techrocket9 on 2010-10-26
Bump for Nvidia uninstallation help.

---

### Post by SeijiSensei on 2010-10-27
You can remove it using the "Additional Drivers" application ("Hardware Drivers" in earlier versions), the same application you used to install it.  Open the app, click on the driver in use, then click remove.

---

### Post by Techrocket9 on 2010-10-27
I'm stuck at the command line. How can I do it from there?

---

### Post by Jupp3 on 2010-11-01
> **Techrocket9 said:**
> I'm stuck at the command line. How can I do it from there?

Last time I tried nvidia drivers on my 1215N, after reboot the system would be left at shell, as with you. However, I could boot to recovery mode (select from grub) and boot to "restricted graphics" mode (or whatever that was called)

---

### Post by The Bird Man of Alcatraz on 2010-11-28
It's odd that the Eee 1015pn is supposed to work fine with Ion 2-
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201015PN)

I kinda thought the 1015pn and 1215n had the same chipset.

---

### Post by lokutus25 on 2010-11-28
If you have already installed the proprietary drivers, from CLI purge all the packages nvidia-* and remove /etc/X11/xorg.conf then reboot.

---

### Post by The Bird Man of Alcatraz on 2010-11-28
lokutus25,
do you have the option in your BIOS of disabling the Optimus switching?

---

### Post by lokutus25 on 2010-12-07
Sorry for late. No, I cant find it. My Bios versions is 0503 and seems the only available for eeePC 1215N right now.

---

### Post by unforgiven8419 on 2010-12-16
i had the same problem with my Asus eee pc 1215N, and for uninstalling nvidia i typed
```

sudo apt-get remove nvidia-settings
sudo apt-get remove nvidia-current

```

then i reboot, and every things goes back OK, but this is not the solution!, what's wrong with nvidia optimus in 1215N??

---

### Post by The Bird Man of Alcatraz on 2010-12-18
Sorry for the late response.  I just noticed that in this thread [http://ubuntuforums.org/showthread.php?p=10252703#post10252703](http://ubuntuforums.org/showthread.php?p=10252703#post10252703)

someone noticed that NVidia has released a new set of 32-bit Linux drivers, that supposedly support Ion.  Worth a shot?

---

### Post by mtron on 2010-12-28
> **The Bird Man of Alcatraz said:**
> I kinda thought the 1015pn and 1215n had the same chipset.

No, they don't. 

Sorry

---

### Post by IrishWristwatch on 2011-01-17
> **The Bird Man of Alcatraz said:**
> Sorry for the late response.  I just noticed that in this thread [http://ubuntuforums.org/showthread.php?p=10252703#post10252703](http://ubuntuforums.org/showthread.php?p=10252703#post10252703)

someone noticed that NVidia has released a new set of 32-bit Linux drivers, that supposedly support Ion.  Worth a shot?

I'm curious about this too.  I also can't seem to find a changelog for this update.

---

### Post by DrJohn999 on 2011-02-01
Same problem here with Asus Eee 1215N. This one has BIOS 0605, Maverick 10.10 and kernel 2.6.35-25, all updated to today.

In recovering I searched via aptitude and found the package nvidia-current-modaliases also was installed, however it has a dependency in nvidia-common so I let it be:
```

> sudo aptitude purge nvidia-settings nvidia-current
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia

```
I wonder if 11.04 will fix all of this: I'm not particularly interested in trying to install the 2.6.36 kernel until Natty is ready.

I took this system on the road for 2 weeks around Europe and the U.S., used it in several locations for presentations, ran wireless everywhere, wrote on airplanes, etc. Had to use my USB ethernet adapter as the built-in is useless with the current version. The battery life was a little short but really no additional problems other than in one place they wanted to use HDMI and we had to scramble for a VGA connector instead. There I coulda made use of the nvidia...

---

### Post by lninjo on 2011-02-17
Uninstalling the nvidia driver and settings and renaming the xorg conf file worked for me

---

### Post by whitethunder922 on 2011-03-16
> **DrJohn999 said:**
> Same problem here with Asus Eee 1215N. This one has BIOS 0605, Maverick 10.10 and kernel 2.6.35-25, all updated to today.

In recovering I searched via aptitude and found the package nvidia-current-modaliases also was installed, however it has a dependency in nvidia-common so I let it be:
```

> sudo aptitude purge nvidia-settings nvidia-current
> sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia

```
I wonder if 11.04 will fix all of this: I'm not particularly interested in trying to install the 2.6.36 kernel until Natty is ready.

I took this system on the road for 2 weeks around Europe and the U.S., used it in several locations for presentations, ran wireless everywhere, wrote on airplanes, etc. Had to use my USB ethernet adapter as the built-in is useless with the current version. The battery life was a little short but really no additional problems other than in one place they wanted to use HDMI and we had to scramble for a VGA connector instead. There I coulda made use of the nvidia...

Just installed Natty alpha 3 alongside Maverick on a Dell XPS15 L502X and no dice, so don't waste your time :)

---

### Post by webcabbie on 2011-05-04
I have a 128mb nvidia card installed also and was having the same problem getting it to work properly so I uninstantiated the drivers.

Should I understand this to mean that I now have a piece of equipment installed in my machine that does nothing since the drivers are not installed?

Anyone wanna buy a 128 mb nvidia card?

---

### Post by laopaishpe on 2011-07-07
I have older cards that use the nvidia-96 packages (proprietary). The screw up is that dependencies need to be corrected for some stupid stub package from ver. 8 to ver. 8.0 (at least this is the only thing I read on Debian lists that made sense) To do this you will have to get the "source" (it looks that it comes with the binary driver), edit some "control" dependency file, and then recompile - easy for someone who packaged ubuntu before, but a no-go for most (including myself, although using Linux for more than 10 yrs now) - maybe a nice weekend project.

Stop saying everything is working, it is not - I used to pride myself for the support Ubuntu used to have for older hardware, that newer OS-es would not bother to support anymore. I guess Canonical catches up to that business model !

---

