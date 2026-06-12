---
title: "mini HOWTO: Using PHC in precise (advanced)"
date: 2012-05-04
forum: Hardware
---

### Post by roothorick on 2012-05-04
Putting this here so people can just google instead of going through the same process I did.

I did this with phc-k8 on a Turion 64 X2 processor. Will take a little tweaking to use the Intel driver.

FIRST: You must be running kernel 3.2.0-24.38 or later. At the time of this writing, this kernel is still in -proposed.

Allrighty then. Get your driver [here]("http://www.linux-phc.org/forum/viewtopic.php?f=13&t=2"). Before we can compile this, we have to tweak something quick for 3.2 kernels.  Edit Makefile. Change these two lines:
```
MODULES := phc-k8.ko mperf.ko
obj-m += phc-k8.o mperf.o
```To this:
```
MODULES := phc-k8.ko
obj-m += phc-k8.o
```Also comment this out:
```
ifneq ($(KERNELMAJOR), 2.6)
$(error Only support for 2.6 series kernels)
endif
```Now open dkms.conf and comment out these two lines:

```
BUILT_MODULE_NAME[1]="mperf"
DEST_MODULE_LOCATION[1]="/kernel/arch/x86/kernel/cpu/cpufreq/"
```With that done, make && sudo make dkms_install. Module is installed. But we're not done yet.

Edit /etc/default/grub and change this line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash cpufreq_driver=phc-k8"
```Finally, update-grub, add phc-k8 to /etc/modules, and reboot. When your system comes back up, phc-k8 will be loaded and you'll have the /sys/devices/system/cpu/cpu0/phc_* hooks. The rest I'll leave up to other guides around the Internet.

---

### Post by seidler2547 on 2012-07-10
Thanks heaps for this. I actually found that even the newest 0.4.4b1 can be compiled with a few changes, so I put together a .deb for dkms and have attached it.

It's a ZIP containing the actual .deb because the forum wouldn't let me attach .deb files :confused: Also this is my first DKMS .deb, so I hope it works, if not, tell me.

Installation should work as follows:
Download the file.
Open a terminal and "cd" to the directory of the downloaded file (e.g. "cd Downloads").
Type
```

sudo apt-get install linux-image-generic-phc linux-headers-generic-phc
unzip phc-k8-dkms_0.4.4b2_all.zip
sudo dpkg -i phc-k8-dkms_0.4.4b2_all.deb
```And then I did your last two steps (editing /etc/default/grub and /etc/modules) and it worked fine.

Lastly, I added this line into /etc/rc.local (before the exit 0):
```

echo -n "40 46 52 60" | tee /sys/devices/system/cpu/cpu?/cpufreq/phc_vids

```**BUT** of course the exact numbers certainly need to be different on other CPUs, so _don't_ just copy this line if you don't know what these numbers mean.

And when I rebooted and saw that everything worked, I uninstalled the non-PHC kernel:
```

sudo apt-get remove linux-image-generic linux-headers-generic
sudo apt-get autoremove

```


Hope it helps!

Stefan

---

### Post by maestrobwh1 on 2012-10-30
Guys, thanks for this.  I have an Asus 1201T netbook with an Ati 3200 graphics card.  It always ran hot in Ubuntu, and sucked the life out of the battery compared to XP running a cpu clock/undervolt program, RMClock.  Even not running RMClock, XP with the Hybrid Engine seemed to manage battery much better.

If someone finds this, the settings that work well for the Athlon Neo that I put into RC local are:

echo -n 27 38 > /sys/devices/system/cpu/cpu0/cpufreq/phc_vids

HIGHER numbers seem to lower voltage.  I used this post to determine what to do; go down the the bottom of page 1, then onto page 2 to see were these numbers come from.  

FYI, running an older bios, one might have 3 values depending on what make/model the processor is in, but apparently, the newer bios got rid of a step.  Not sure why.

More info at 
[http://linuxsolver.blogspot.com/2012/05/undervolting-cpu-in-ubuntu-1204.html](http://linuxsolver.blogspot.com/2012/05/undervolting-cpu-in-ubuntu-1204.html)

---

### Post by jonnyboysmithy on 2012-11-08
Before trying to undervolt it might pay to check if your cpu is supported. I went through a lot of bother only to find out mine isn't supported.:wink:

---

