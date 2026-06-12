---
title: "Help : Jaunty 9.04 update gone haywire : dpkg-reconfigure xserver-xorg doesn't work"
date: 2009-04-27
forum: Installation &amp; Upgrades
---

### Post by shelterit on 2009-04-27
Backed up my /home and /etc, did an update through update-manager from 8.10 to 9.04, and a reboot killed my xserver; first it made the mouse and keyboard disabled, so a reboot into rescue mode running dpkg-reconfigure xserver-xorg which asked only keyboard questions before saving a new config. A restart with that (and any new dpkg-reconfigure xserver-xorg I now try to do) now produces a garbled screen (leftovers from boot-screen, interlaced, no mouse movements). I'm now left in rescue mode.

I've made a Ubuntu 9.04 ISO disk which boots fine. How can I "transfer" the auto-detected xserver settings onto my installed drive? 

Is clean install my only option? Is there a way to do a half-clean install, where I don't have to kill the partition, but simply copy over with whatever defaults it finds instead? Or any other magic you can think of. I'm open to black magic at this point. Please advice.

---

### Post by cariboo on 2009-04-27
We need more information in order for us to help you solve your problem, at the prompt type:

```
lshw -C video > video.txt
```

The above command will list your video hardware and write it to a file called video.txt. You should be able to copy the file to the computer you are using to access the forum, and paste it into your next post.

---

### Post by shelterit on 2009-04-27
> **cariboo907 said:**
> 
```
lshw -C video > video.txt
```


  *-display UNCLAIMED
       description: VGA compatible controller
       product: Mobility Radeon HD 3650
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: latency=0

However, I'm not understanding what this info might bring to the table, unless the idea is to create a .conf file for me? I'd really love to understand how this works better.

I've been tinkering with some other options in the mean time, and I have got it to the point of correct graphics details, but then the keyboard and mouse are both disabled / not working. Trying to fix those results back into the garbled graphics world again.

Surely a rescue tool must be available, no? (And no, 'xfix' which I've heard about is not present.) And is even dpkg-reconfigure going to fix these problems, since I hear that there's a new configuration engine (so, not xorg.conf)?

---

### Post by Nano_ext3 on 2009-04-28
I have this same issue :(

---

### Post by Kareeser on 2009-04-28
You could try running the install script downloaded straight from ATi's website.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-4-x86.x86_64.run)

This is for the 3xxx series of ATi graphics cards.

Download and run "sudo sh ati-driver-installer-9-4-x86.x86_64.run"

---

### Post by Bogdon6 on 2009-04-30
I have the same problem. How can I download the file if the display driver doesn't allow me to boot up completely?

---

### Post by shelterit on 2009-04-30
Ok, I've got my system up and running again, but it was a painful excercise without any concrete answers, but I blogged it so if an Ubuntu expert could look at it and confirm my suspicions that completely uninstalling glxr (or whatever the ATI proprietary driver is called), and reinstalling it could be one way to fix this (it seems the reconfigure option doesn't reconfigure everything).

Another problem I thought of is that the udev utilities wasn't fully up to scratch. Is there some miscreption between the old and new packages?

Anyway, I blogged about my [nightmare and getting my system back over here]("http://shelter.nu/blog/2009/04/nightmare.html").

---

