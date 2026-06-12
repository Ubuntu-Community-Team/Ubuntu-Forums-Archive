---
title: "Plugging in iPhone to charge"
date: 2007-07-11
forum: Hardware &amp; Laptops
---

### Post by gadgetgirl on 2007-07-11
I use a Thinkpad with Ubuntu 7.04 on it at work, and I figured I could charge my new iPhone using the usb cable plugged into the Thinkpad. When I plug it in, the iPhone makes a noise and the screen momentarily shows the charging graphic, but then it disconnects and is no longer in the charging state. If I leave the cable plugged in, this happens over and over again, every 30 seconds. 

I believe I configured HAL correctly to ignore the iPhone so that the "import photos" dialog doesn't come up each time. Is this the same as what everyone else is seeing? 

I'm seeing this is /var/log/syslog:
```

Jul 11 15:28:26 roo kernel: [14332.236000] usb 5-4: USB disconnect, address 24
Jul 11 15:28:26 roo NetworkManager: <debug info>^I[1184185706.829274] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/temp/215'). 
Jul 11 15:28:26 roo kernel: [14332.356000] usb 5-4: new high speed USB device using ehci_hcd and address 25
Jul 11 15:28:27 roo kernel: [14332.488000] usb 5-4: configuration #1 chosen from 3 choices
Jul 11 15:28:27 roo NetworkManager: <debug info>^I[1184185707.135383] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/temp/216'). 
Jul 11 15:28:56 roo kernel: [14362.236000] usb 5-4: USB disconnect, address 25
Jul 11 15:28:56 roo NetworkManager: <debug info>^I[1184185736.830699] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/temp/216'). 
Jul 11 15:28:56 roo kernel: [14362.352000] usb 5-4: new high speed USB device using ehci_hcd and address 26
Jul 11 15:28:57 roo kernel: [14362.488000] usb 5-4: configuration #1 chosen from 3 choices
Jul 11 15:28:57 roo NetworkManager: <debug info>^I[1184185737.136320] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/temp/217'). 
Jul 11 15:29:26 roo kernel: [14392.236000] usb 5-4: USB disconnect, address 26
Jul 11 15:29:26 roo NetworkManager: <debug info>^I[1184185766.832349] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/temp/217'). 
Jul 11 15:29:26 roo kernel: [14392.360000] usb 5-4: new high speed USB device using ehci_hcd and address 27
Jul 11 15:29:27 roo kernel: [14392.492000] usb 5-4: configuration #1 chosen from 3 choices
Jul 11 15:29:27 roo NetworkManager: <debug info>^I[1184185767.143265] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/temp/218'). 
Jul 11 15:29:56 roo kernel: [14422.236000] usb 5-4: USB disconnect, address 27
Jul 11 15:29:56 roo NetworkManager: <debug info>^I[1184185796.830226] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/temp/218'). 
Jul 11 15:29:56 roo kernel: [14422.356000] usb 5-4: new high speed USB device using ehci_hcd and address 28
Jul 11 15:29:57 roo kernel: [14422.492000] usb 5-4: configuration #1 chosen from 3 choices
Jul 11 15:29:57 roo NetworkManager: <debug info>^I[1184185797.137674] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/temp/219'). 
Jul 11 15:30:26 roo kernel: [14452.236000] usb 5-4: USB disconnect, address 28
Jul 11 15:30:26 roo NetworkManager: <debug info>^I[1184185826.918762] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/temp/219'). 
Jul 11 15:30:27 roo kernel: [14452.452000] usb 5-4: new high speed USB device using ehci_hcd and address 29
Jul 11 15:30:27 roo kernel: [14452.584000] usb 5-4: configuration #1 chosen from 3 choices
Jul 11 15:30:27 roo NetworkManager: <debug info>^I[1184185827.244356] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/temp/220'). 

```
(btw, before I configured HAL to ignore the iPhone, it was being assigned a non-temp device id, but the pattern of disconnects/reconnects was the same)

Anyone have any ideas?

---

### Post by gadgetgirl on 2007-07-12
No one else charges their iPhone on an ubuntu machine?

---

### Post by tkarabian on 2007-07-20
I have this same problem. Unfortunately I don't have an answer.

---

### Post by arrrghhh on 2007-07-24
i don't have an iphone, but my cell phone does the same thing when i plug it into my computer.  just keeps cycling charging and not charging every 30 seconds, never charges for more than a second or two.


edit:

i think i found a solution!  i took my solution from [this](http://ubuntuforums.org/showthread.php?t=371255) thread.  so download the [acharge binary](http://www.nikru.com/acharge/acharge) (or the [source](http://www.nikru.com/acharge/acharge.cc)) and chmod +x it wherever you saved it.  now run it by typing ```
./acharge --list
```  find the device, then type ```
./acharge [vendor#]
``` where vendor# you get from the previous command...

as i test this, it charges it longer, but it still drops it every now and then... any additional suggestions are welcome!  also thanks to the barry software for blackberries inspiring njkrut to write acharge!  we thank you!



update...

so it seems this doesn't work like i thought it did... it seemed to keep my device charging, but after a few minutes it went back to the same old crap...

---

### Post by gadgetgirl on 2007-07-31
Thanks for the info, maybe it will work better in Gutsy.

---

### Post by 65 mustang on 2007-09-12
bump, has anyone figured this out yet?

---

### Post by maxx22 on 2007-09-16
It's not the best solution but I've found that if I run gthumb --import-photos it charges as long as that application is running.

---

### Post by tychocity on 2007-09-17
download this

[http://mattcolyer.com/projects/iphone-module/iphone-module-0.1.tar.gz](http://mattcolyer.com/projects/iphone-module/iphone-module-0.1.tar.gz)

tar -zxvf iphone-module-0.1.tar.gz

cd iphone-module-0.1

save attachement into directory

mv Makefile.txt Makefile

sudo make

sudo insmod iphone.ko

sudo modprobe iphone

sudo echo iphone >> /etc/modules

plug the iphone, and press cancel to the image importer.

---

### Post by yvovandoorn on 2007-09-19
Perhaps I'm doing something wrong but...

yvandoorn@yvandoorn:~/Desktop$ cd iphone-module-0.1/
yvandoorn@yvandoorn:~/Desktop/iphone-module-0.1$ mv /home/yvandoorn/Desktop/Makefile.txt Makefile 
yvandoorn@yvandoorn:~/Desktop/iphone-module-0.1$ sudo make
Password:
make -C /lib/modules/2.6.20-16-generic/build M=/home/yvandoorn/Desktop/iphone-module-0.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /home/yvandoorn/Desktop/iphone-module-0.1/iphone.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/yvandoorn/Desktop/iphone-module-0.1/iphone.mod.o
  LD [M]  /home/yvandoorn/Desktop/iphone-module-0.1/iphone.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
yvandoorn@yvandoorn:~/Desktop/iphone-module-0.1$ sudo insmod iphone.ko
yvandoorn@yvandoorn:~/Desktop/iphone-module-0.1$ sudo modprobe iphone
FATAL: Module iphone not found.


I can't get the last step to work.

---

### Post by benanzo on 2007-09-19
Just "insmod iphone.ko" is sufficient to load the module.  This driver allows the iPhone to get a steady charge from the USB port, but unfortunately there's something (HAL?) that keeps polling the device for info so it still vibrates every 20 seconds or so.  At least it's getting a steady charge now.

Just to recap, as soon as you do "insmod iphone.ko" you will see that the module loaded as "iphone" just fine.  Test it with "lsmod | grep iphone" --


You can load it as a regular module (with modprobe) by copying iphone.ko from the source dir to:
**/lib/modules/$(uname -r)/kernel/drivers/usb/gadget**
then do:
```
sudo depmod -ae
```
then you can load it with "modprobe iphone"

---

### Post by adrianr on 2007-09-21
Thank you for the helpful makefile and post. The instructions worked for me.  My iphone now charges in Linux!

---

### Post by yvovandoorn on 2007-09-21
Yup works fine here as well. Now to get photo importing to work :-)

---

### Post by cri on 2007-09-25
Big thanks for the post, tychocity. Works like a charm ;)

---

### Post by razn on 2007-09-26
Yes, it works!

I registered to say thanks!

---

### Post by daynah on 2007-09-29
Oh dear... it didn't work like a charm for me.

It's definately charging. But... it's doing this weird thing where it blinks on and then turns off... and then comes on and off again. Actually, all my USB hubs do this also (though I have this plugged in the back), but I've just been throwing a shirt or something over the hubs because they just have a light... the iPhone has an annoying sound. Back to the outlet.

This problem is related by a good many paces, I'll make a seperate post in a bit. But if you happen to know why my computer enjoys flipping my usbs on and off...

---

### Post by manishsingh4u on 2008-05-25
> **tychocity said:**
> download this

[http://mattcolyer.com/projects/iphone-module/iphone-module-0.1.tar.gz](http://mattcolyer.com/projects/iphone-module/iphone-module-0.1.tar.gz)

tar -zxvf iphone-module-0.1.tar.gz

cd iphone-module-0.1

save attachement into directory

mv Makefile.txt Makefile

sudo make

sudo insmod iphone.ko

sudo modprobe iphone

sudo echo iphone >> /etc/modules

plug the iphone, and press cancel to the image importer.


Thanks. This works! :)

---

