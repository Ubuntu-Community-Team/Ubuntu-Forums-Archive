---
title: "Asus 1201N How To Lucid 10.04 -- Solved (Mostly)"
date: 2010-09-06
forum: Hardware
---

### Post by EtoIxPi on 2010-09-06
Ok, guys. I've got an asus 1201n. It's a great machine and ubuntu 10.04 is a great os but they just don't work well together by default. So I have decided to put up a thread to help who I can.

**What works:**
Nvidia display
Custom keys
Suspend/hibernate
Sound
Wireless
Wired NIC

**What has not been tested:**
Webcam
Mic
HDMI
Multi-touch
Trackpad disable


Most of the stuff listed in the "what works" section works out of the box. Here's how to get the rest of it.

**Suspend/Hibernate**
If this doesn't work it's a real killer for anyone who's serious about using a laptop. If you have to shutdown every time you close the lid you might as well just stick with the desktops.

As of this writing kernel version 2.6.32-24 does not support the acpi functions necessary to properly suspend this laptop. With this kernel it will suspend once, but not twice. This is repeatable. To fix this you will have to install a newer kernel. I personally have tested 2.6.34 and 2.6.35. Both work fine. Here are the directions for that.

1) Go to: [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

2) Select a 2.6.34 or 2.6.35 kernel for lucid

3) Download both the i386 debs and the "kernel headers all" deb

4) Save them to a directory then run "sudo dpkg -i *.deb"

5) Reboot and select the appropriate kernel in GRUB.

After this suspend/hibernate should work.



**Wireless Card**
You will probably have trouble with your wireless card after the kernel update. The drivers aren't compiled into most kernels by default. You need to compile the driver from source and install it as a module. Here are the directions for that.

1) Get the source here: [http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz](http://launchpadlibrarian.net/36688638/rtl8192se_linux_2.6.0010.1211.2009.tar.gz)

2) "tar -xzvf package.tar.gz"

2.1) "cd package"

2.2) "make"

2.3) "sudo make install" (don't worry if this part fails)

3) move <build directory>/firmware/RTL8192SE to /lib/firmware

4) move <build directory>/HAL/rtl8192/r8192se_pci.ko to /lib/modules/<your kernel>/kernel/drivers/net/wireless

5) "sudo depmod -a"

6) "sudo modprobe r8192se_pci"

7) Enjoy wireless.




**Bios Reset & Built in Hotkeys**
Last but not least you may have trouble with built in hot keys and your bios resetting every time you reboot. Here's how to fix that.

1) "cd /etc/default"

2) "sudo gedit grub"

3) change the line that says "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" to read "GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux acpi_brightness=vendor splash"" instead.

4) Save and then "sudo update-grub2"

5) Reboot.




**Enjoy!**
This isn't everything, but I think it covers the basics. Feel free to copy/paste and add to this guide as necessary!

---

### Post by Lancellor on 2010-09-11
I did the functions key  fix, but they still don't work..

---

### Post by jamesey on 2010-09-16
is the hdmi out working? how's performance when playing an intense mkv at 1080p?

---

### Post by emoguitarist06 on 2010-09-22
> **jamesey said:**
> is the hdmi out working? how's performance when playing an intense mkv at 1080p?
I've never had a problem running HDMI or 1080- mkv files :)

Webcam works out of the box

**Mic! Anyone has a solutions for this?**

---

### Post by Drewvt on 2010-10-02
> **emoguitarist06 said:**
> 

**Mic! Anyone has a solutions for this?**

Have you tried the following?
[http://jr0cket.blogspot.com/2010/07/asus-eee-pc-1201n-running-ubuntu-linux.html](http://jr0cket.blogspot.com/2010/07/asus-eee-pc-1201n-running-ubuntu-linux.html)
> **Enabling the internal Microphone**
The internal microphone is muted by default and you are not able to unmute that microphone without manually configuring using the amixer command line.  I prefer to install the tool pavucontrol, which is an advanced graphical mixer.

sudo aptitude install pavucontrol

Run pavucontrol and on the Input Devices tab, unmute the microphone.  You will then need to go to the normal sound control panel and unmute the microphone.

I am also planning to purchase the 1201N, so I was looking around for tweaks.

---

### Post by emoguitarist06 on 2010-10-04
> **Drewvt said:**
> 
I am also planning to purchase the 1201N, so I was looking around for tweaks.

Why not just get the 1215N? I really want to upgrade to that one.

---

### Post by Drewvt on 2010-10-16
> **emoguitarist06 said:**
> Why not just get the 1215N? I really want to upgrade to that one.

There seem to be considerably more issues on the 1215N running Ubuntu, especially with the driver for the newer Nvidia Ion. I am sure that these problems will get smoothed out with time but I can't wait that long. 

Anyway, I am very happy with this 1201N, dualbooting with the included Windows 7; it does everything I need it to do.

---

### Post by emoguitarist06 on 2010-10-16
> **Drewvt said:**
> There seem to be considerably more issues on the 1215N running Ubuntu, especially with the driver for the newer Nvidia Ion. I am sure that these problems will get smoothed out with time but I can't wait that long. 

Anyway, I am very happy with this 1201N, dualbooting with the included Windows 7; it does everything I need it to do.

Good point. I still love my 1201N

---

### Post by Drewvt on 2010-10-17
As an update for the whole thread: I can confirm that most of the abovementioned tweaks are no longer necessary when running Ubuntu 10.10.

- suspend/hibernate just works (provided you installed swap, obviously)
- the wireless card just works
- as expected with the newer kernel, the bios does not reset itself 
- hotkeys work as far as I can tell

However, my 1201N seems to be suffering from the load cycle bug that produces a clicking sound when running on battery. 
[http://ubuntuforums.org/showthread.php?t=1257374](http://ubuntuforums.org/showthread.php?t=1257374)
Doing a "sudo hdparm -B 254 /dev/sda" is an acceptable remedy, a permanent tweak is also available but haven't tried it yet.

---

### Post by Deut316 on 2010-10-18
Finally my wirelesss is working on 10:10. However, the computer still isn hybernating and suspending. What is the purpose of the swap file and how do I load it?

---

### Post by Nburnes on 2010-10-18
> **Drewvt said:**
> As an update for the whole thread: I can confirm that most of the abovementioned tweaks are no longer necessary when running Ubuntu 10.10.

- suspend/hibernate just works (provided you installed swap, obviously)
- the wireless card just works
- as expected with the newer kernel, the bios does not reset itself 
- hotkeys work as far as I can tell

However, my 1201N seems to be suffering from the load cycle bug that produces a clicking sound when running on battery. 
[http://ubuntuforums.org/showthread.php?t=1257374](http://ubuntuforums.org/showthread.php?t=1257374)
Doing a "sudo hdparm -B 254 /dev/sda" is an acceptable remedy, a permanent tweak is also available but haven't tried it yet.

> **Deut316 said:**
> Finally my wirelesss is working on 10:10. However, the computer still isn hybernating and suspending. What is the purpose of the swap file and how do I load it?
I also get the load cycle and the sleep/hibernation bug. Been looking for a fix for a while now.

---

### Post by Deut316 on 2010-10-19
Hi,

Thanks for your help on preventing Bios from resetting itself... it was frustration.

My computer however still won hybernate and suspend itself unless I put it to sleep with fn+f2 keys.

You provided these instructions (below)to help with suspend and  hybernate. Can you give specific steps especially concerning grub as I&#7743;  not a programmer. Also note that I&#7743; using 10.10.
Thanks 
B
**Suspend/Hibernate**
 If this doesn't work it's a real killer for anyone who's serious about  using a laptop. If you have to shutdown every time you close the lid you  might as well just stick with the desktops.
 
 As of this writing kernel version 2.6.32-24 does not support the acpi  functions necessary to properly suspend this laptop. With this kernel it  will suspend once, but not twice. This is repeatable. To fix this you  will have to install a newer kernel. I personally have tested 2.6.34 and  2.6.35. Both work fine. Here are the directions for that.
 
 1) Go to: [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
 
 2) Select a 2.6.34 or 2.6.35 kernel for lucid
 
 3) Download both the i386 debs and the "kernel headers all" deb
 
 4) Save them to a directory then run "sudo dpkg -i *.deb"
 
 5) Reboot and select the appropriate kernel in GRUB.
 
 After this suspend/hibernate should work.

---

### Post by Drewvt on 2010-10-21
If you are running 10.10 then you should have kernel 2.6.35 already. The above instructions to replace the kernel are therefore pointless.

To hibernate you will need to create a swap file, that's all. The official FAQ on swap explains everything, it is quite simple.

---

### Post by Nburnes on 2010-10-22
> **Drewvt said:**
> If you are running 10.10 then you should have kernel 2.6.35 already. The above instructions to replace the kernel are therefore pointless.

To hibernate you will need to create a swap file, that's all. The official FAQ on swap explains everything, it is quite simple.
But I don't have a problem with hibernate, I have a problem with sleep. It goes to sleep, then I press the power button or press a key and I can see the screen light up and the fans/hard drive spins up, but nothing comes onto the screen.

---

### Post by Drewvt on 2010-10-23
> **Nburnes said:**
> But I don't have a problem with hibernate, I have a problem with sleep. It goes to sleep, then I press the power button or press a key and I can see the screen light up and the fans/hard drive spins up, but nothing comes onto the screen.

Ah. Suffice to say that I have never encountered anything like that. I can't get it to stop asking for my password when coming out of sleep, despite following the guides to disable that, but otherwise sleep works just fine.

The permanent fix for the load cycle bug (by editing the etc/conf file) has taken care of that problem, too.

---

### Post by eggiog on 2010-10-26
hey!
I'm planning to get this netbook soon, could someone report some infos about the ION2 chip? 
It's fully working with 10.10? 
Drivers installation? 
Hot switching with switcharoo (or anything)? 
Battery life comparison?

Thank you in advance :P

PS: my concern @ [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus) Eee PC 1215N

---

### Post by pterion on 2011-04-29
Closing the lid does not have any effect (regardless of the settings in Power Management) after installing the new kernel 2.6.34-020634-generic. Anybody?

---

