---
title: "Asus x555u Audio issues"
date: 2016-06-17
forum: Hardware
---

### Post by Juan_Fiorenzano on 2016-06-17
Hello community how are you doing? I have this problem with my laptop's audio. The system recognize the hardware but simply doesn't emit any sound I raised the volume to the max but nothing happens, I upgrade my kernel to 4.4.8 due to the systems doesn't recognized that my earphones was plugged, now my laptop is completely mute. This is the output of lspci which concern with my audio device.

```

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at df328000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

```

If you see in the command output, in Capabilities section said <access denied> I don't know if this has something to do.

---

### Post by QDR06VV9 on 2016-06-17
Have you yet tried to  install pulseaudio volume control and checking the configuration settings to make sure the right device is being used?
The package you want will be [B]"pavucontrol"

[/B]

---

### Post by Juan_Fiorenzano on 2016-06-17
> **runrickus said:**
> Have you yet tried to  install pulseaudio volume control and checking the configuration settings to make sure the right device is being used?
The package you want will be [B]"pavucontrol"

[/B]

I've already installed pulseaudio know it recognized when I plug my earphone but still soundless, in the device section say Built-in Audio

---

### Post by QDR06VV9 on 2016-06-17
Look under the Configuration Tab at the top...mine shows this <Screenshot>
We are taking this slowly at first to eliminate what is causing this.

---

### Post by Juan_Fiorenzano on 2016-06-17
This is my configuration tab

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=269627&d=1466187159[/IMG]

---

### Post by QDR06VV9 on 2016-06-17
Ok that's what I wanted to see..and looks good.
Now we need to check that the driver is installed properly.
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```

After installing the modules, **you will need to reboot for the changes to take effect. **

If  the modules are already installed, proceed to the next step to check to  see whether your hardware is recognizing the sound card as installed. 
 
[h=3]Is the sound card physically installed and recognized by your hardware?[/h] Open a terminal and type 

```
lspci -v | grep -A7 -i "audio"
```
Paste the output of the above back here using code tags.

---

### Post by Juan_Fiorenzano on 2016-06-17
When I type this:
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```

the output are these errors messages
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-4.4.8-040408-generic
E: Couldn't find any package by glob 'linux-restricted-modules-4.4.8-040408-generic'
E: Couldn't find any package by regex 'linux-restricted-modules-4.4.8-040408-generic'


```

---

### Post by QDR06VV9 on 2016-06-17
What Version of Ubuntu are you using?
```
lsb_release -a
```

---

### Post by Juan_Fiorenzano on 2016-06-17
I am using Ubuntu 16.04, but I installed the 4.4.8 kernel version.

```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04 LTS
Release:    16.04
Codename:    xenial


```

---

### Post by QDR06VV9 on 2016-06-17
Well that makes for messy diagnosis solution.
Lets see what options we have to boot from.
Post back the return of this in the terminal:
```
dpkg -l | grep linux-image | grep ii
```
This will return only properly-installed packages with that name

---

### Post by Juan_Fiorenzano on 2016-06-17
This is the output

```

ii  linux-image-4.4.0-10-generic               4.4.0-10.25                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.8-040408-generic           4.4.8-040408.201604200335                           amd64        Linux kernel image for version 4.4.8 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-10-generic         4.4.0-10.25                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-24-generic         4.4.0-24.43                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.24.25                                         amd64        Generic Linux kernel image



```

---

### Post by QDR06VV9 on 2016-06-17
Will you boot to this kernel 4.4.0-10 and run this after booting to that kernel
```
sudo apt-get install linux-restricted-modules-`uname -r` linux-generic
```
And if they are already installed proceed to the next step to check to  see  whether your hardware is recognizing the sound card as installed. 
```
lspci -v | grep -A7 -i "audio"
```
And paste the return from the above...here

---

### Post by Juan_Fiorenzano on 2016-06-17
this is the output

```

dpkg -l | grep linux-image | grep ii
ii  linux-image-4.4.0-10-generic               4.4.0-10.25                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                         amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.8-040408-generic           4.4.8-040408.201604200335                           amd64        Linux kernel image for version 4.4.8 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-10-generic         4.4.0-10.25                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-24-generic         4.4.0-24.43                                         amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.4.0.24.25                                         amd64        Generic Linux kernel image



```

---

### Post by QDR06VV9 on 2016-06-17
See my above post #12

---

### Post by Juan_Fiorenzano on 2016-06-17
> **runrickus said:**
> See my above post #12

Sorry I was lost for a moment.

Maybe this is a very dumb questions but, how I can boot using the 4.4.0 kernel version??

---

### Post by QDR06VV9 on 2016-06-17
There are no dumb questions here!
Do see grub-menu when you first power on your computer?
if not give me the spec's on your machine IE: Dell Laptop or Asus PC I think you know what i mean by this.:)

---

### Post by Juan_Fiorenzano on 2016-06-17
yes I can see the grup-menu

---

### Post by QDR06VV9 on 2016-06-17
Ok great now from that menu arrow down to Advanced Options and again arrow down to the 4.4.0-10-generic kernel and hit Enter.

---

### Post by Juan_Fiorenzano on 2016-06-17
I follow all the steps I boot using the 4.4.0.24 generic but when I run the following command:
```

sudo apt-get install linux-restricted-modules-`uname -r` linux-generi
```

I still having the same error message:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-restricted-modules-4.4.0-24-generic
E: Couldn't find any package by glob 'linux-restricted-modules-4.4.0-24-generic'
E: Couldn't find any package by regex 'linux-restricted-modules-4.4.0-24-generic'

```

I check if really I am using the correct kernel version and run ```
uanme -r
``` and this is the ouput:

```


uname -r
4.4.0-24-generic



```

---

### Post by QDR06VV9 on 2016-06-17
I have Dr. Appointment I will be back in about 1 hour and we will get to the bottom of this.
Or if someone else wants to jump in here feel free.

---

### Post by QDR06VV9 on 2016-06-17
Well ok then... let's  see how this looks now.
```
lspci -v | grep -A7 -i "audio"
```

---

### Post by Juan_Fiorenzano on 2016-06-17
Hello I hope you are well, this is the command's output

```

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at df328000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl



```

---

### Post by QDR06VV9 on 2016-06-17
> **Juan_Fiorenzano said:**
> Hello I hope you are well, this is the command's output


Yes I am in good shape Thanks!:)
But this is just a puzzle to me.
```

00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
    Subsystem: ASUSTeK Computer Inc. Sunrise Point-LP HD Audio
    Flags: bus master, fast devsel, latency 32, IRQ 16
    Memory at df328000 (64-bit, non-prefetchable) [size=16K]
    Memory at df300000 (64-bit, non-prefetchable) [size=64K]
    [COLOR=#b22222]_**Capabilities: <access denied>**_[/COLOR]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel, snd_soc_skl

```
This Lappy should be fully supported here...but i am not sure about 16.04 (Xenial)
Just one more command to try here:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```
Hopefully that one will go through with no errors....but if there are any errors paste them back here.

---

### Post by Juan_Fiorenzano on 2016-06-17
It finished well

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
build-essential set to manually installed.
linux-headers-4.4.0-24-generic is already the newest version (4.4.0-24.43).
linux-headers-4.4.0-24-generic set to manually installed.
The following packages were automatically installed and are no longer required:
  libgtkglext1 linux-headers-4.4.0-10 linux-headers-4.4.0-10-generic
  linux-image-4.4.0-10-generic linux-image-extra-4.4.0-10-generic
  linux-signed-image-4.4.0-10-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by Juan_Fiorenzano on 2016-06-17
But the laptop still soundless

---

### Post by QDR06VV9 on 2016-06-17
Yuck#!
Well lets try to fully update the system. Run the following one line at a time.
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```
And when that is all done Run this next
```
sudo apt autoremove
```
Reboot Again using the same kernel 4.4.0-24-generic.
I must confess I am not very hopeful here due to these other Help requests you have also. 
[http://ubuntuforums.org/showthread.php?t=2328116](http://ubuntuforums.org/showthread.php?t=2328116)
[http://ubuntuforums.org/showthread.php?t=2328117](http://ubuntuforums.org/showthread.php?t=2328117)

---

### Post by Juan_Fiorenzano on 2016-06-17
OK, I still in silent jajaja, how I can get rid of 4.4.8 kernel version definitely of the system? maybe this is the problem

---

### Post by QDR06VV9 on 2016-06-17
Did you ever have sound since installing Xenial (16.04)
But to remove that kernel do this in the terminal again one line at a time.
```
sudo apt-get remove linux-image-4.4.8-040408-generic 
sudo apt-get remove linux-headers-4.4.8-040408* 
```
And to be sure we update grub to let it know that kernel is gone
```
sudo update-grub
```
And Again remove all un-needed packages by way of
```
sudo apt autoremove
```
And after a reboot that kernel should be gone from the Advanced Grub Menu.
If there is still no sound I would try a **14.04 Trusty Live install CD or USB** using Try before installing to make sure everything is working.

---

### Post by Juan_Fiorenzano on 2016-06-18
Now my speakers works but doesn't recognize when I plug my earphones, but when the speaker doesn't work the system recognized when I plugged the earphones, so this is very weird jajajaja

---

### Post by QDR06VV9 on 2016-06-18
> **Juan_Fiorenzano said:**
> Now my speakers works but doesn't recognize when I plug my earphones, but when the speaker doesn't work the system recognized when I plugged the earphones, so this is very weird jajajaja

Well you can use the pulseaudio volume control to change to earphones when you plug-in. (in the configuration tab)
Not the best solution i know, but it should work, and maybe with the first point release of Xenial due next month this might get sorted out...fingers crossed.:D
Kind regards

---

### Post by mmifas on 2016-09-14
This affects me a lot. BTW above solution is not a perfect one. Need to create a script to make sound work. Mic not working at all. I've found this bugs on launchpad. Please mark as '[COLOR=#484848][FONT=Ubuntu]**Yes, it affects me**[/FONT][/COLOR]'
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1596381](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1596381)
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1604235](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1604235)

---

