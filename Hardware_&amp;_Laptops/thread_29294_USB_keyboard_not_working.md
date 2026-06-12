---
title: "USB keyboard not working"
date: 2005-04-23
forum: Hardware &amp; Laptops
---

### Post by mxpx on 2005-04-23
hey everyone, i just installed hoary and the usb keyboard was working just fine. but now for some reason it isnt...i have 2 keyboards (usb and ps/2) pluged in because USB doesnt work in grub ( I dual boot WinXP and Ubuntu). maybe its a keyboard confict... iono i sure hate this ps/2 keyboard any help is welcome

system specs.
amd XP 1800 overclocked to 1900
hoary 5.04
kernal 2.6
USB keyboard - logitec internet navigator keyboard

thanks 
Brett Buford

---

### Post by heimo on 2005-04-23
Sometimes there's configuration option in BIOS - something like USB legacy support. It may have some effect.

Check lsusb (lists usb devices), check are the devices detected properly (tail -f /var/log/messages while plugging in device), check that you have USB support loaded in kernel 

lsmod | grep hcd
 ```

ehci_hcd			   32708  0 
uhci_hcd			   32816  0 
usbcore			   119000  3 ehci_hcd,uhci_hcd

``` 

Try restarting hotplug
sudo /etc/init.d/hotplug restart

Post your xorg.conf InputDevice sections - there should be one for each device (keyboards, mouse).

---

### Post by mxpx on 2005-04-23
now for some reason or anthoner it is working, maybe because i just un-pluged the PS/2 keyboard...

---

