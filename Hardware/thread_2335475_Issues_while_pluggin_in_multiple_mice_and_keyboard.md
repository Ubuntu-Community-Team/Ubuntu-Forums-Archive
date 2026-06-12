---
title: "Issues while pluggin in multiple mice and keyboards Ubuntu 16.04"
date: 2016-08-29
forum: Hardware
---

### Post by pproets on 2016-08-29
Hello community,

I recently installed ubuntu 16.04 alongside windows 10. I am kind of an eccentric and am using multiple mice and keyboards at the same time (I like switching mice between different games, one for fps games, one for all other games).
Now here is the problem. When my razer naga and my logitech g500 are connected simultaneously while booting neither works under ubuntu.
I also use two keyboards simultaneously (Logitech g-105) and a mechanical keyboard (Easterntimes Tech i-500 - without num pad, that's why I keep the logitech plugged in). While both are plugged in, only the Logitech keyboard works during and after booting, and strangely if I press the caps-lock key after booting the light on both keyboards flash. However most of the time the mechanical keyboards doesn't work.
I unplugged the razer naga and rebooted and voila the logitech g500 worked from the beginning and vice versa.

Now after a few minutes the second keyboard starts working. So it seems there is some kind of recognition lag in ubuntu ?
Since my computer is under my desk and keyboards and mice are connected at the back of the computer, I'd rather not crawl under my desk every time I wish to use my mice and keyboards under ubuntu.

I extracted a few log lines form the /var/log/kern.log file for you, since I saw it in another thread and maybe it helps. 
```

Aug 29 12:27:00 phil-desktop kernel: [  123.044803] usb 2-1.1: USB disconnect, device number 22
Aug 29 12:27:01 phil-desktop kernel: [  123.204301] usb 2-1.1: new full-speed USB device number 23 using ehci-pci
Aug 29 12:27:01 phil-desktop kernel: [  123.276272] usb 2-1.1: device descriptor read/64, error -32
Aug 29 12:27:01 phil-desktop kernel: [  123.452261] usb 2-1.1: device descriptor read/64, error -32
Aug 29 12:27:01 phil-desktop kernel: [  123.628219] usb 2-1.1: new full-speed USB device number 24 using ehci-pci
Aug 29 12:27:01 phil-desktop kernel: [  123.700200] usb 2-1.1: device descriptor read/64, error -32
Aug 29 12:27:01 phil-desktop kernel: [  123.876180] usb 2-1.1: device descriptor read/64, error -32
Aug 29 12:27:01 phil-desktop kernel: [  124.052153] usb 2-1.1: new full-speed USB device number 25 using ehci-pci
Aug 29 12:27:02 phil-desktop kernel: [  124.460092] usb 2-1.1: device not accepting address 25, error -32
Aug 29 12:27:02 phil-desktop kernel: [  124.532055] usb 2-1.1: new full-speed USB device number 26 using ehci-pci
Aug 29 12:27:02 phil-desktop kernel: [  124.939993] usb 2-1.1: device not accepting address 26, error -32
Aug 29 12:27:02 phil-desktop kernel: [  124.940098] usb 2-1-port1: unable to enumerate USB device

```

this happened when I had a standard microsoft mouse attached that works all the time and tried to plug the other mice in and out. 
atm the microsoft mouse is plugged out and all devices work. after reboot I have to plug in the ms mouse. 
logitech g-105 keyboard works all the time as well, also in grub, the mechanical doesn't, I can't even enter bios with it, only via "del"-push on the logitech. 

I hope you got a basic idea of how my problem looks like, I'd like to start the computer and want to be able to use all usb devices to either enter bios or navigating through bios and also ubuntu !
Thanks for your time !

Best,
Phil

---

### Post by pproets on 2016-09-03
Since no one seems to have a solution I unplugged the razer naga and everything works now. I can even use grub with the mechanical keyboard. damn u naga.

---

