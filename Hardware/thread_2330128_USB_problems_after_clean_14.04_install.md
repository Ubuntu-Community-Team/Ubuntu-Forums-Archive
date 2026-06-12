---
title: "USB problems after clean 14.04 install"
date: 2016-07-08
forum: Hardware
---

### Post by matrbgld on 2016-07-08
Hello everybody!

I've just installed Ubuntu 14.04 on a brand new machine. Installation went smooth and everything seems to be up and running. Everything except the USB ports. I've got a wireless dongle for Mouse/Keyboard on one of the USB2 port. Both mouse and keyboard freeze at random times for no obvious reason. These freezes can take up to 30 seconds, but usually are over after 5-10 seconds. USB3 devices are not recognized at all. If I enter the BIOS and I plug in a USB3 devices I can see that it has been recognized. Not so on Ubuntu. No matter what device I put into one of the USB3 ports, it just doesn't show up.

Here are my specs: MSI 7693-040R 970 Gaming, AMD FX 8350, GTX 970 4G, 16 MB RAM, 500GB SSD. BIOS runs in UEFI mode.

Any help is highly appreciated!
Mats

---

### Post by DuckHook on 2016-07-09
*Thread moved to **Hardware** as the more appropriate forum.*

Welcome to the forums, matrbgld.

Ubuntu will sometimes have problems with the very old, the very new or the very uncommon. In your case, the problem is likely due to the very new. You have a very hotted-up system with some bleeding-edge components, but Trusty (14.04) is now over 2 years old. I would recommend that you try Xenial (16.04) on a LiveUSB to see if the USB 3.0 ports work. You can decide if you want to install after trying the LiveUSB, but don't install until you've tried out every component.

You can also try upgrading your BIOS (if an upgrade is available). *WARNING* Upgrading firmware like system BIOSes is not without danger. An improper upgrade could brick your motherboard. However, it is a natural option to try with balky system buses. If I were you, I would try Xenial first. If that fixes your problem, no need to risk a BIOS upgrade and you should leave well enough alone.

---

### Post by matrbgld on 2016-07-09
Hi BuckHook and thank you for your reply. 

As for your suggestions: I have had installed 16.04 previously on this machine but due to even more things not working I wiped it and installed 14.04. Besides the USB problems I had the unity-settings-deamon crashing on me after each and every logon plus the network-manager taking ages to start up. After I've learned that the unity-settings-deamon issue is still an open bug I decided to stick with an *experienced* version of ubuntu instead and so I moved back to 14.04. I need this computer to work.

I will try to upgrade the BIOS today.

Again, thanks for your help!

---

### Post by matrbgld on 2016-07-09
So I did upgrade the BIOS. Can't really tell if the hanging of the mouse/kb is now a thing of the past. It looks good for now. But still I can't access USB3 devices. And with the BIOS upgrade I have earned a new problem: When I boot from cold, that is the computer is switched off, I end up in the MSI EFI-Shell. After some playing around in the BIOS without any success I figured that pressing Ctrl-Alt-Delete in the EFI-Shell (to do a warm restart) the UEFI Disk with Ubuntu on in is recognized and the boot runs just fine. But I guess this is an MSI BIOS issue, so I will ask over at the MSI Forum.

---

### Post by DuckHook on 2016-07-09
Try a LiveUSB of Xenial on your system now, with the new BIOS. See if things have improved.

Time to take a look at reports and logs. Please post results of:```
lsusb
``````
sudo lshw -C bus
``````
dmesg | egrep -i 'error|warning|fatal|usb'
```Some of these results may be very long, so consider attaching as files rather than raw output.

---

### Post by squirrel3 on 2016-07-10
This method edits the grub but instead of modifying **GRUB_CMDLINE_LINUX_DEFAULT** it modifies **GRUB_CMDLINE_LINUX=""**

**Steps**

1 Open terminal, Ctrl-Alt+T
2 type gksudo gedit /etc/default/grub in terminal and press enter
3 find the line GRUB_CMDLINE_LINUX=""
4 modify the line to read GRUB_CMDLINE_LINUX="acpi=force irqpoll"
5 After that, update the bootloader via terminal by typing sudo update-grub and pressing enter
6 Restart your system

Source: [http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684), post 18 in the thread.

---

### Post by DuckHook on 2016-07-10
> **squirrel3 said:**
> 2 type gksudo gedit /etc/default/grub in terminal...Thanks for this valuable info, squirrel3. ;) The only thing I would note for the OP is that in the step quoted above, gksudo has been deprecated in Ubuntu. Use instead:```
sudo nano /etc/default/grub
```

---

### Post by squirrel3 on 2016-07-10
Glad to help.

---

### Post by mörgæs on 2016-07-10
> **matrbgld said:**
> ...I had the unity-settings-deamon crashing...

Then try a member of the 16.04 family without Unity, for example Xubuntu. The more experiments the better.

---

### Post by matrbgld on 2016-07-10
Hello and thank to all you kind people helping me out here!

@DuckHook:Here are the outputs of the installed ubuntu (14.04)
```
lsusb
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 011 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 010 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 002: ID 1a81:1002 Holtek Semiconductor, Inc. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I have attached the lshw query and the log as files.

I booted 16.04 from disk and the unity-settings-deamon did not crash. So that's good news. Difficult to tell whether mouse/kb hanging occured. But it looked good so far.
As for the USB3 devices they were still not detected.
While booting 16.04 I noted some errors written out before the pink screen appeared. They just "rolled by" and I tried to jot them down as quick as possible. The first one was related to nouveau and read "gr:failed to load fics_inst". The second one (a group of errors) were related to xhci_hcd and ended with a line reading "HC died. Cleaning up." I hope that adds some useful diagnosis info.

@squirrel3 

I followed your steps to modify /etc/default/grub and rebooted (into the current 14.04 installation). It didn't help. The mouse/kb hanging occurs and no USB3.

@mögaes
> Then try a member of the 16.04 family without Unity, for example Xubuntu. The more experiments the better.
I will try that if anything else fails. For now I would rather stick to the mainstream *buntu since I would consider myself a linux noob.

Again, thank you people for your efforts in helping me!
All the best from sunny Berlin!
Mats

---

### Post by DuckHook on 2016-07-10
All reports look fine to me. Your system is recognizing the USB ports and is providing hooks to them. However, this will happen so long as the motherboard USB components are detected. If a physical break exists between your USB chip and the port, then the system may think the USB system is working, but no USB signals will get through. In other words, it is possible that your issue is in HW and not the OS.

How did you check for USB connectivity? Have you tried different USB 3.0 ports? If you have only the one, did you try connecting different devices including USB 2 devices?

The other errors appearing at boot appear to be unrelated to your USB problem and can be dealt with later or separate threads.

---

