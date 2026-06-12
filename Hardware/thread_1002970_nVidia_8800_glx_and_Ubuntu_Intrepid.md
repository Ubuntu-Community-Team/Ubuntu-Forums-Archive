---
title: "nVidia 8800 glx and Ubuntu Intrepid"
date: 2008-12-05
forum: Hardware
---

### Post by Klaue on 2008-12-05
Hi there
Firstly let me say that I know that there are allready various threads about nVidia problems on Intrepid - but sadly I was unable to find a solution in any of the threads (including the [HowTo]("http://ubuntuforums.org/showthread.php?t=945557"))

My problem is that after updating to Intrepid, Ubuntu restarted in low graphics mode. No problem, I thought. Reinstall the driver like after every update, I thought. But this time I had no luck. Everything I tried ends up in:
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Now, I allready tried installing the driver using "the Ubuntu way" throught the menus, installing it using envyng, installing it with the package (nvidia-glx-177) and installing it using nvidia's own installer, everything brought me the same error.
I also tried upgrading my xorg.conf for the new x server, but the error above still persisted. The versions created by the nvidia tool and envyng were also tried and brought an additional error which was something like "module type1 not found" beside the one above.
Another tip I found was to remove (purge) all the nvidia-packages and try again, but this diddn't help either.
The only tip I diddn't try was to downgrade the kernel to 2.6.27-3 (I have 2.6.27-9) which doesn't seem to be the best idea in my opinion

[Xorg.0.log]("http://pastebin.com/m47d8a8dd")
[The "known as working on hardy" xorg.conf]("http://pastebin.com/m29bd2eca")
[The new xorg.conf which also diddn't work]("http://pastebin.com/m2d3b8df3")

I am thankful for every idea!

Additional question: Is it possible to directly downgrade intrepid back to hardy if I wouldn't get this to work? I am now only able to use my computer at 1152x864 (or less) at 60 Hz which gives me headaches (yeah, I still use my trusty CRT) but I shun the trouble of a fresh install.

---

### Post by cariboo on 2008-12-05
It sound like the module isn't getting built properly. If the module isn't installed, a good bad or indifferent /etc/X11/xorg.conf isn't going to make any difference. I would suggest starting from scratch, as far as the graphics dreivers are concerned. Start in recovery mode and use xfix to get a basic xorg.conf, then completely remove any Nvidia drivers using either Synaptic or:

```
sudo apt-get purge nvidia*
```

The above command is an example only. One you have completely remove the Nvidia drivers, make sure you have build-essential installed. THe nect step is to clean the package archive, to do this in a terminal type:

```
sudo apt-get clean
```

then

```
sudo apt-get autoremove
```

The above two commands will remove the archived packages from /var/cache/apt/archived and remove any left over dependencies.

You should now be ready to install the drivers. Go to System-->Administration-->Hardware Drivers and follow the prompts.

Good luck

Jim

---

### Post by Klaue on 2008-12-05
Tried all of this, now it doesn't show up in the hardware drivers window
[[IMG]http://img379.imageshack.us/img379/6541/bildschirmfotohardwaretae6.th.png[/IMG]]("http://img379.imageshack.us/img379/6541/bildschirmfotohardwaretae6.png")
I suppose it needs some of the nvidia packages

---

### Post by cariboo on 2008-12-05
Does your video card actually show up when you type in a terminal:

```
sudo lshw -C display
```

Jim

---

### Post by Klaue on 2008-12-05
It does:

```
klaue@klaue-desktop:~$ sudo lshw -C display
[sudo] password for klaue: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: G80 [GeForce 8800 GTX]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

```

---

### Post by Klaue on 2008-12-07
I hate to push this, but I can't really use my computer anymore..

---

### Post by darco on 2008-12-07
Go to Synaptic and search for Envy and download the Envy-Core. Do a search on the forum for more info on Envy. You can also visit the author's website [http://albertomilone.com/index.html](http://albertomilone.com/index.html)

good luck

dacro

---

### Post by Klaue on 2008-12-07
I allready tried envy without luck

---

### Post by Klaue on 2008-12-08
OK, I know, I'm probably getting on the nerves of the people here, but can anyone give me some pointers? please? I searched for hours, tried many many things but nothing helped. I don't even know why the module doesn't load, just that it doesn't.
Can anyone at least tell me if there's some log file in which I could find a reason why it doesn't load which I could use to search for a solution?
Anything?

---

### Post by Dragonflyoh on 2009-01-03
Did you ever solve the problem? I have the same problem, did all of the suggested fixes and still get the "Failed to load the Nvidia kernel Module". Any hint will be appreciated.

---

### Post by Rohan Kapoor on 2009-01-03
> **Dragonflyoh said:**
> Did you ever solve the problem? I have the same problem, did all of the suggested fixes and still get the "Failed to load the Nvidia kernel Module". Any hint will be appreciated.
I use ATI but had similar problems with upgrading to 8.10 from 8.04. My solution was to start a scratch install of 8.10 and it worked fine. I know it's not the best option but as far as I can tell, it's the only working one!

---

### Post by Klaue on 2009-01-11
> **Dragonflyoh said:**
> Did you ever solve the problem? I have the same problem, did all of the suggested fixes and still get the "Failed to load the Nvidia kernel Module". Any hint will be appreciated.

Probably too late (sorry, was in the holidays), but: Yes I did
When I tried to load the module manually (using "sudo modprobe nvidia") it gave me this error message:
sh: /sbin/lrm-video: not found
FATAL: Error running install command for nvidia

After some googling for that, I found [this page]("http://www.sammyliu.com/index.php/2008/11/another-day-another-broken-intrepid-ibex/") which helped. In short, you gotta do this:
locate lrm-video
sudo nano /etc/modprobe.d/lrm-video (or whereever lrm-video was)
and finally comment out the line "install nvidia /sbin/lrm-video nvidia $CMDLINE_OPTS"
Restart and everything should work

---

