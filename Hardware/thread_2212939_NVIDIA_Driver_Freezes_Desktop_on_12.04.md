---
title: "NVIDIA Driver Freezes Desktop on 12.04"
date: 2014-03-23
forum: Hardware
---

### Post by sam41 on 2014-03-23
I've been struggling with this for months, have tried many of the solutions in [SOLVED] posts for NVIDIA issues, but nothing seems to work for me.  I'm running 12.04, with the latest kernel, though the same issue occured with the previous kernel(s).  When I activate an NVIDIA driver my desktop will freeze ~2 minutes after logging in.  This occured with Unity, though I'm now running the xubuntu desktop and the same thing happens.  I've tried I think every version of the NVIDIA driver available (v 304, 319, 331...), all with the same result.  

Here's my system information: 

Card:
```

sam@Samylon:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation G92M [GeForce 8800M GTS] (rev a2)
```
The M is for Mobile, this is running on an (old) Gateway laptop.  

Display info: 
```
sam@Samylon:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: G92M [GeForce 8800M GTS]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:ce000000-ceffffff memory:d0000000-dfffffff memory:cc000000-cdffffff ioport:2000(size=128)
```
That's after the last nvida purge of course.

kernel: 
```
sam@Samylon:~$ sudo uname -r
3.8.1-030801-generic
```

I'm at my wit's end with this...  Recently I read that some of the problems with NVIDIA drivers were solved in the 13.04 kernel, so I was hopeful when upgraded to the latest this morning, to no avail.  I've been mulling switching to 13.04/13.10 but I'd really like to avoid a new install, its such a pain to backup files then re-install / re-setup everything; and if I have the same problem with the new kernel, I'm not convinced 13.04/13.10 would help.  My video card worked fine with windows, but has never worked with ubuntu.  

I just want minecraft to look pretty, please help.

---

### Post by d4m1r on 2014-03-24
Can you take a screenshot of the "Additional Drivers" window for us? Search for it within the Unity windows (accessible via the Windows key most often).

From what branch are you pulling your Nvidia drivers? Can you tried from the latest-greatest "dev/experimental" branch?

---

### Post by sam41 on 2014-03-27
> **d4m1r said:**
> Can you take a screenshot of the "Additional Drivers" window for us? Search for it within the Unity windows (accessible via the Windows key most often).

From what branch are you pulling your Nvidia drivers? Can you tried from the latest-greatest "dev/experimental" branch?


[IMG]http://imageshack.com/a/img19/7218/n4m1.png[/IMG]

That what you're looking for?  Not sure what branch you're refering to for where I get the drivers.  I've tried the ones listed in the additional drivers tab and I've downloaded a few others, "sudo apt-get nvidia-current something or another", (which were since purged), off the top of my head I tried versions 304 (listed here), 319, 331, 173, and I think one other.  I'll investigate the experimental ones and post my results.

---

### Post by sam41 on 2014-04-01
Update:

One thing I left out of the original post, which may or  may not be important. When the desktop freezes the mouse pointer is  still operable, I just can't click anything.  Nor can i go to console  mode (ctrl-alt-f1).  

Something else I found interesting in all  my messing this weekend is that when I boot up with the nvidia drivers  enabled and go to console mode the screen will still freeze after about 2  minutes unless I stop lightdm (sudo service lightdm stop).  

Here's a quick summary of what I tried over the weekend, commands not included:
1.   I was able to install the nvidia driver .run I downloaded from nvidia.   Per nvidia, my correct video driver is the 331.49 (recently updated).  I  was able to install the driver, got the nvidia splash screen, but the  same issue occurred, desktop freezes after about 2 minutes, mouse  pointer still functional.  
2.  purged the nivida drivers, installed again with apt-get  (sudo apt-get install nvidia-319-updates-dev) & (sudo  apt-get install nvidia-331-updates-dev).  The driver was installed and  enabled, I saw the splash screen, same issue occurred.  
3.  purged  nvidia, reinstalled xserver-xorg-core, then dpkg-reconfigure  xserver-xorg, reinstalled nvidia-319-updates-dev & nvidia-331-updates-dev, same issue occured.  
4.  This morning I tried it again, and also installed a few other recommend packages I saw listed at [http://packages.ubuntu.com/trusty/nvidia-331-updates](http://packages.ubuntu.com/trusty/nvidia-331-updates): nvidia-prime and nvidia-settings, same issue occured.  
5.   I downloaded the experimental drivers (nvidia-experimental-310).  I could only find experimental drivers for versions 304 and 310.  After installation I  didn't see them listed in the addition drivers gui or in jockey-text.

I'm  thinking this isn't an issue with installing / setting up the driver correctly.  I've been able to do that successfully I believe, though I wouldn't be  surprised if there were some magical hidden optional package that would fix everything.  

I find it very curious that if I boot up and go to  console mode quickly everything is fine if I stop lightdm, but will freeze if I don't.  Makes me  thing the issue isn't the nvidia drivers, but lightdm or something in  the xserver.  

Also, the symptoms of this really scream memory leak...

Next, I think i might give bumblebee a shot... Or try to isolate the memory leak...  

Any other suggestions would be greatly appreciated.

---

