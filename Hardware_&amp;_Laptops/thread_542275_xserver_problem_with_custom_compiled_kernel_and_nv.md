---
title: "xserver problem with custom compiled kernel and nvidia driver"
date: 2007-09-03
forum: Hardware &amp; Laptops
---

### Post by meraj on 2007-09-03
Hi

I recently switched to ubuntu and set up ubuntu - 7.10 Tribe 5 on my IBM thinkpad T61 laptop. With default kernel, I was facing some problems with xserver. But after installing latest nvidia driver, I got X working and resolution is highest too.

Now I downloaded stock linux kernel 2.6.22.6 and recompiled/installed this new kernel. Now xserver does not work anymore. 

output from Xorg.0.log: 

[COLOR="Blue"](EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found
[/COLOR]

I reconfigured xorg.conf using - 

[COLOR="Blue"]sudo dpkg-reconfigure xserver-xorg [/COLOR]

set driver to vesa. It works now with 800x600 resolution. But I can't get my nvidia driver loaded.

I searched the web and found that many people faced this problem before me. But none of the solutions discussed worked for me.

I tried reinstalling nvidia driver. But that did not work. 

One thing I found that no linux-restricted-modules are installed for my custom kernel - 2.6.22.6. 

So I tried to install restricted modules using - 

[COLOR="Blue"]sudo apt-get install linux-restricted-modules-`uname -r`[/COLOR]

But it fails with message - 

[COLOR="Blue"]
E: Couldn't find package linux-restricted-modules-2.6.22.6
[/COLOR]

Also, I noticed that there is no /lib/firmware/2.6.22.6 folder. I got some warnings during initrd creation due to this.

Can someone please let me know why my nvidia module is failing to load and why is there no linux-restricted-modules-2.6.22.6? How I can get my nvidia driver loaded and get my xserver running properly?

Thanks,
Meraj

---

### Post by meraj on 2007-09-05
can anyone please help?

---

### Post by w4ett on 2007-09-05
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---

