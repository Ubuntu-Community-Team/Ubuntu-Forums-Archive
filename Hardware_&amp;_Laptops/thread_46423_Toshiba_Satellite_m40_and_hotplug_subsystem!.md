---
title: "Toshiba Satellite m40 and hotplug subsystem!"
date: 2005-07-04
forum: Hardware &amp; Laptops
---

### Post by Elisei on 2005-07-04
Hello everybody!

I am new to any linux, and dont have much experience.
I was running into , what seems to be, a hardware problem. After installation of ubuntu 5.04 on Toshiba Satellite m40 notebook, the boot up process would freeze on "Starting hotplug subsystem" statement. The system responds at this point to nothing and no addidtional commands were helping. 
The only way to bypass the "hotplug system" statement is to disable the onboard lan devices, and in fact to leave usb subsystem enabled.
Result is - i have no internet with ubuntu.
Is it possible that i need to install additional compenents prior to boot if device is enabled, and if so, does anyone know where to get them?

Any sugestions are greately appreciated!

---

### Post by kcypers on 2005-07-06
Hi Elisei,

I bought myself a Toshiba M40-114 a couple of days ago and (of course) I got the same errors. After a hard day of trying I was able to solve the hotplug subsystem error, but I still have no internet connection. But at least I can boot properly  :-? 

I'm a newbe too, so if I can't give you a step-by-step guide, because I've tried a lot before it worked. This is what you have to do:

We must download new drivers for the Ethernet card. Fist, find yourself a computer with a internet connection. You go to [www.marvell.com/drivers/search.do](http://www.marvell.com/drivers/search.do) and find: 
Product Category: PC Connectivity
Product Family: Yukon
Platform: Install package for Linux 2.4 and 2.6
There is a readme and the driver, download the driver

Now try to get the driver package on the laptop. I did it with a USB stick. First you should disable your LAN in the BIOS, otherwise you can't boot. Then you copy the driver package to the laptop and unpack it (I did it with the standard filebrowser, because I don't know the shell command to do so)

We also need the Linux Kernel source. You can take it from the cd, with the following commands in a console:
```
# sudo -s //get into root
# apt-get install build-essential linux-headers-`uname -r` //installs some stuff about the kernel source
//watch out! The ` is not a quote like ' , it's a backtick!
```

3rd part: creating a symbolic link, otherwise the installer won't work
```
# cd /usr/src
# ln -s linux-headers-2.6.10-5-386 linux   //assuming you're running kernel 2.6.10-5, the ubuntu 5.04 standard
```

Now reboot, enable the LAN card in BIOS, and start booting Linux. 
Important! Press Ctrl + C as soon as "Starting hotplug subsystem" appears on the screen, before it freezes. This will stop loading the hotplug system. Problems: no sound, no usb and no network support  :-? 

After booting, get a console again, go to the directory where you stored the driver and install the driver:
```
# sudo -s //root again
# cd DriverInstall //go into that directory
# ./install.sh //execute the installer
``` 
Choose for 1) Installation, and if all go well, you shoudn't do a thing anymore. You can create a patch too and recompile the kernel by yourself, but it failed on my laptop... probably because it's too difficult for me. You can also read DriverInstall/README, which helped me a bit. 

Then reboot, everything works, you can even assign a IP address to the LAN card, but there is no connection. So, if there is anyone who knows how to configure a Marvell Yukon 88E8036 PCI-E Fast Ethernet Card, please tell us!!!

Greetz, Kevin

---

### Post by aroman on 2005-07-20
I can confirm that this works on a Toshiba M40-JM8 system. Flawlessly...

Next in line is wireless... :)

---

### Post by aroman on 2005-07-20
[QUOTE=aroman]I can confirm that this works on a Toshiba M40-JM8 system. Flawlessly...

Next in line is wireless... :)[/QUOTE]
 Actually, forget that... it will ONLY work (for me) if hotplug doesn't load the modules. It seems that after loading ohci1394, I get a Disabling IRQ 11, nobody cared type message. I am attempting to blacklist that module to prevent hotplug from working.

---

### Post by aroman on 2005-07-20
[QUOTE=aroman]Actually, forget that... it will ONLY work (for me) if hotplug doesn't load the modules. It seems that after loading ohci1394, I get a Disabling IRQ 11, nobody cared type message. I am attempting to blacklist that module to prevent hotplug from working.[/QUOTE]
 YES, that worked!

SO, whoever's getting Disabling IRQ 11/nobody cared messages in dmesg, blacklist the module ohci1394 in /etc/hotplug/blacklist (just add it on its own line).

Wireless now...

---

### Post by aroman on 2005-07-20
[QUOTE=aroman]YES, that worked!

SO, whoever's getting Disabling IRQ 11/nobody cared messages in dmesg, blacklist the module ohci1394 in /etc/hotplug/blacklist (just add it on its own line).

Wireless now...[/QUOTE]
 Sorry for all these posts, but wireless worked out-of-the-box now... impressive, really! :D Go Ubuntu!

---

### Post by kcypers on 2005-07-24
Hi guys, 

After upgrading my Ubuntu I was stuck with the same error as before so I needed my own guide to install my ethernet card again ](*,) Then I saw all these posts of aroman, and started to read dmesg. By doing that, I saw that Ubuntu gave us the solution for the problem itself (we just had to read dmesg) What's in it? 

We have to boot with as parameter "irqpoll"

So, after installing the driver as descibed above, you can choose to blacklist the module ohci1394 (but I don't like blacklisting...) or you can change your /boot/grub/menu.lst file, adding "irqpoll" to the line:

```
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda3 ro quiet splash **irqpoll** 
(root=/dev/sda3 can be different on another system)
```

And then I could post this message right from my Ubuntu box :smile:  

Greetz, Kevin

---

### Post by aroman on 2005-08-17
Interesting... I'll have to try that when I get home. 

I removed Ubuntu from that box meanwhile but I will try to install it again (I want to experiment a bit with breezy :))

---

### Post by dunja on 2005-09-18
[QUOTE=kcypers]
```
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda3 ro quiet splash **irqpoll** 
(root=/dev/sda3 can be different on another system)
```[/QUOTE]

thanks.. solved my problem.

---

### Post by dunja on 2005-09-18
nevermind, it's back.  :-?

---

### Post by dunja on 2005-09-18
i added the "noapic" boot option and the problem is gone.

---

### Post by WolfJay_83 on 2005-09-19
This same problem occured on my Dell Latitude LS, with both 5.04 and the 5.10preview.  The **irqpoll** boot option seemed to fix the problem and also, allowed me to install my pcmcia wireless card which previously would not install!  Way to fix two problems at once!

---

### Post by kavent on 2005-11-06
[QUOTE=aroman]Actually, forget that... it will ONLY work (for me) if hotplug doesn't load the modules. It seems that after loading ohci1394, I get a Disabling IRQ 11, nobody cared type message. I am attempting to blacklist that module to prevent hotplug from working.[/QUOTE]

it works on my m40-sf3

Thanks a lot, man:p

---

### Post by kcypers on 2006-09-21
One year later... I've just installed Kubuntu/dapper without having the network problems I had before with the other distro's. \\:D/ Congratulations to the development team for adding a better support for Marvell NIC's! Great work guys.

---

