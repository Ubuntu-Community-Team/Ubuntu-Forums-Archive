---
title: "Driver for GeForce 8500 GT"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by bugalo on 2007-05-01
I have just bought a Nvidia Geforce 8500 GT, and I tried to install it. I went to the oficial homepage and I found the driver:

NVIDIA-Linux-x86_64-100.14.03-pkg2.run

I tried to install it and it was OK, it worked perfectly. But, when I restarted my computer, the X didn´t work. Could someone help me with it, please?

I have an AMD 64 x2.

Thanks.

---

### Post by cptcrunch on 2007-05-01
try using this HowTo to install your card

[http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

---

### Post by Toet on 2007-05-05
Same problem here, only didn't work once from boot. Now started in recovery mode and start gdm from command-line works for me.

---

### Post by manitwo on 2007-06-14
*bump* - exactly the same prob here.

---

### Post by mastergunner on 2007-12-19
I am having the same problem. What is the exact solution to get this to work properly.

---

### Post by igknighted on 2007-12-19
The card should be fully supported.

Run "sudo nvidia-xconfig" if you have already installed the driver listed in the first post, then restart.  Should work fine.  If that still fails run "sudo dpkg-reconfigure xserver-xorg" and restart again.

What version of Ubuntu are you using?  In gutsy X should never fail like that, it should simply revert back to sake graphics mode.  Once in safe-graphics mode, run the restricted driver manager and enable the nvidia driver there.  You should almost always use this method, it makes life much easier than using the one from nvidia's site.

Also, before plopping in a new card, I would look around for the instructions for how to do so.  The "linux way" abhors going to a third party site and downlowding a file, we like to keep all software in the repos (synaptic).  The nvidia drivers you downloaded and installed are available there in a form that makes installing and configuring them much easier.

EDIT: When the OP posted this the official nvidia driver may not have supported the 8500 (at least the version in the repo's), but now it does.

---

### Post by mastergunner on 2007-12-19
I am running Gutsy amd64. When I try to adjust the screen resolution nothing happens. I go to hardware and it shows a Geforce 8 series card using the nv driver. I am a little lost. HELP!!! Oh I tried to use the nvidia restricted driver and that just blew the whole screen up I couldnt see anything. It was like using a magnifying glass. Also that driver is only good for x86 machines not amd64.

---

### Post by igknighted on 2007-12-19
> **mastergunner said:**
> I am running Gutsy amd64. When I try to adjust the screen resolution nothing happens. I go to hardware and it shows a Geforce 8 series card using the nv driver. I am a little lost. HELP!!! Oh I tried to use the nvidia restricted driver and that just blew the whole screen up I couldnt see anything. It was like using a magnifying glass. Also that driver is only good for x86 machines not amd64.

I have a Geforce 8600gt (similar card) and a 64bit AMD processor, and I use the driver from the "restricted manager" with any issues.  So I can assure you that it is not only for x86 (besides, all amd64 processors are x86 anyways).

As for "blowing up the screen", it sounds like ubuntu is not detecting your monitor's ideal settings.  Try using the screen resolution app to adjust it, or if that does not work, there should be another tool to set-up the xserver, and here you should be able to specify the desired resolution.  Also when doing this make sure the "nvidia" driver is chosen, not vesa or nv.

---

### Post by mastergunner on 2007-12-20
Where is the screen resolution app? If you are talking in system settings I am locked in and cannot adjust screen resolution. If there is one specific for the restricted driver then I do not know where that is. I ahve downloaded and install the restricted driver.

---

### Post by igknighted on 2007-12-20
Hmm, I don't use gnome, but supposedly there is a GUI app to edit xorg.conf directly.  I don't know what it is called to point you to it either, so I'll direct you as I would do it, and if someone else knows the app of which I speak, feel free to chime in.  It should be under system->administration IIRC.

Anyhow, to get the desired resolution you will need to change the xorg settings directly.  You have a couple options (all via the CLI).

a) run ```
sudo dpkg-reconfigure xserver-xorg -phigh
```
you can select the default for all the questions (make sure that nvidia is selected as the driver, not nv or vesa) and then when it gets to the resolution, make sure the resolution you want is checked (check it if it isn't).

b) First backup (sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old).  Then open the xorg.conf file yourself (gksudo gedit /etc/X11/xorg.conf) and find the section called device.  Make sure the driver listed there is "nvidia".  Then find the section called screen.  It should list a default color depth, this should be 24.  Change it if it isn't.  Then a little below that should be sets of resolutions under a list of color depths.  Find the section for the depth of 24, then add (to the beginning of the list) the resolution you want in the same format as the ones already there.  Save and exit.

Once you have completed EITHER a or b, reboot your system or hit <ctrl>+<alt>+<backspc> to restart X, and hopefully it works.  If X should fail to load, use the dpkg-reconfigure command and select the defaults or (if you used b) use "sudo cp /etc/X11/xorg.conf.old /etc/X11/xorg.conf".

---

### Post by mastergunner on 2007-12-20
I have done those and nothing works.

---

### Post by highfructose327 on 2007-12-25
mastergunner I used the code below to adjust my resolution and refresh rate, hope it helps

```
gksudo nvidia-settings
```

---

### Post by SomeStupidHippie on 2007-12-26
Have any of you guys tried Envy? That usually helps for driver issues, im not really sure about things as far as display settings go....


heres the link to the Envy site:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

