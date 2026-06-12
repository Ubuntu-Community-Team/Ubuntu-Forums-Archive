---
title: "Can't adjust the screen's brightness"
date: 2016-07-16
forum: Hardware
---

### Post by ea304gt on 2016-07-16
I'm fairly new to Ubuntu and I've managed to take care of almost   everything but brightness. Right from the begining, brightness is at its   peak and it's hurting my eyes by now and I have no obvious way to dim   it. I have a Lenovo ideapad 500 with a Windows 10/Ubuntu 14.04   partition. I have a hunch that it has to do with a missing i915 driver.

I've tried several tips roaming around, but to no avail.

Here's what I've done:

Modified and updated GRUB file as shown [URL="https://disqus.com/home/discussion/itsfoss/fix_brightness_control_not_working_for_ubuntu_1310/"]here 
[/URL]
Added a `20-intel.conf' file in the `usr' folder as mentioned [here]("https://itsfoss.com/fix-brightness-ubuntu-1310/") 

Later I noticed my `sys/class/backlight` folder is empty. Somewhere I   read that this means that Ubuntu thinks I do have knobs to manually   adjust the brightness and all that was left was to file a bug report. 

I was stubborn, and following another tip I found that I do have a   `max_brightness` and `brightness` files buried in   `/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/leds/phy0-led`. 

Now, here's the funny thing: when I do 
`cat /sys/.../max_brightness` and  
`cat /sys/.../brightness` I do get a 1 in both cases. Seems I was right   by claiming the brightness is at it's peak. Most of the comments around   mention they get 10, 200, 30000 or any other big integer. The only   non-negative integer lesser than 1 is 0, and I'm afraid setting the   brightness file to 0 will black out the screen.

I tried to set the brightness file to 0.5 just to see what happens, but   couldn't do it. Even under the `sudo -i` prompt, Ubuntu won't let me   change its value.

I found an old post from 2011 on kubuntu that suggested to install `linux-kamal-mjgbacklight` patch. First I did check

```
$ lsmod | grep ^i915
i915                  788212  0 
```

Later I installed the usual way. 

 
Don't know when exactly happened, but suddenly I have a Brightness   Slider on System Settings -> Brightness, but funny thing, no matter   how I slide it, the screen doesn't change at all.

Finally, I been roaming around the web and typed on the terminal and noticed something fishy

```
$ sudo lshw -enable pci -class display
[sudo] password for ejam: 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: Sky Lake Integrated Graphics
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:4000(size=64)
```

The UNCLAIMED tag and the fact that there is no `driver=i915' under  configuration tab tells me that Ubuntu doesn't recognize my screen's  driver, hence there is nothing in the backlight folder. I also ran

```
$ inxi -b
System:    Host: ejam-Lenovo-ideapad-500-14ISK Kernel: 3.13.0-91-generic x86_64 (64 bit) 
           Desktop: Gnome Distro: Ubuntu 14.04 trusty
Machine:   System: LENOVO (portable) product: 80NS version: Lenovo ideapad 500-14ISK
           Mobo: LENOVO model: Lenovo ideapad 5 version: SDK0J40679 WIN
           Bios: LENOVO version: CFCN23WW(V1.05) date: 01/27/2016
CPU:       Dual core Intel Core i5-6200U CPU (-HT-MCP-) clocked at 400.00 MHz 
Graphics:  Card: Intel Sky Lake Integrated Graphics 
           X.Org: 1.15.1 drivers: fbdev (unloaded: vesa) FAILED: intel Resolution: 1366x768@76.0hz 
           GLX Renderer: Gallium 0.4 on llvmpipe (LLVM 3.4, 256 bits) GLX Version: 2.1 Mesa 10.1.3
Network:   Card-1: Intel Device 3166 driver: iwlwifi 
           Card-2: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169 
Drives:    HDD Total Size: 1000.2GB (15.7% used)
Info:      Processes: 196 Uptime: 2:18 Memory: 1669.4/7900.8MB Client: Shell (bash) inxi: 1.9.17 
```

and noticed the warning: `drivers: fbdev (unloaded: vesa) FAILED: intel '. Finally

```
$ dpkg -l xserver-xorg-video-intel
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  xserver-xorg-v 2:2.99.910-0 amd64        X.Org X server -- Intel i8xx, i9x
```


I gather it is telling me that xserver-xorg-video-intel is a complete mess. I'm sort of lost now. Don't want to mess around with the screen's driver and end up with a full-black screen.

---

### Post by zltmn on 2016-08-26
My brightness slider is also not working. My screen is set to 34, with a max brightness of 255, but I can't change it.

Vid card Radeon HD5600, Ubuntu 16.04

I have an external 2nd monitor, so I have less fear of blackout. I'll find time to mess with this now that I've seen your notes. Will report back what I find.

---

### Post by zltmn on 2016-08-26
Okay, so here's what I did.

First I plugged in the 2nd monitor and changed to mirror mode.

Then I followed these instructions from someone called sriram6 (Replaced, found an easier method):
---------------------

Enter in terminal:

```
gksu nautilus
```

Enter root password.

---------------------

After that, I went to my equivalent of your [COLOR=#000000]/sys/devices/pci0000:00/0000:00:1c.5/0000:02:00.0/leds/phy0-led [/COLOR]folder and opened the brightness file, which I now had permission to change. 

I changed the number from 34 to 120 and hit Ctrl-S. To my shock, the brightness changed immediately! However, gedit gave me an error about not being able to save the file, so I closed without saving. The brightness was still at the brighter setting, and when I reopenned the file, it showed 120. So I was able to change it despite the warning.

Hope this works for you![COLOR=#000000]

[/COLOR]

---

