---
title: "USB 2.0 multicard reader"
date: 2011-09-09
forum: Hardware
---

### Post by LostAndFound on 2011-09-09
Hello,

I suspect that I have faulty hardware related to a USB 2.0 multicard reader which is built-in to my computer. My computer crashes (freezes) from time to time and it's difficult to find the cause (since I no longer can read any log-files after the freeze)

I've seen some IO errors related to a usb device 

lsusb gives:
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

dmesg | grep usb gives:
usb 1-5: new high speed USB device using ehci_hcd and address 3

(I assume that the Device 3 indicates the USB device at address 3 here, but I am not sure)

I understand I can blacklist a device (or at least a loaded module) under:
/etc/modprobe.d/blacklist

if I run
lsmod

I cannot find out which of the 50 or so modules relates to the multicard reader and if it relates to the multicard reader alone.

Or perhas there is another way to disable the multicard reader.

Any pointers would be appreciated.

---

### Post by sordna on 2012-03-28
I also would like a way to disable my memory card reader. Ever since upgrading to 12.04 (Specific - development branch) I keep getting these annoying kernel messages flooding my dmesg, as described here:
[https://bugzilla.redhat.com/show_bug.cgi?id=769747](https://bugzilla.redhat.com/show_bug.cgi?id=769747)

"[sdb] Asking for cache data failed"

I would like to be able to enable/disable this device on demand. I noticed this bootup message in my /var/log/dmesg:
[    2.415095] usbcore: registered new interface driver ums-realtek

So I'm trying: 
sudo modprobe -r ums_realtek

I think that does the trick!

---

### Post by sordna on 2012-03-28
Yup, modprobe -r ums_realtek (or modprobe -r ums-realtek or using rmmod instead of modprobe -r to unload the module) disables the device and those messages.
However, I tried putting the following lines in /etc/modprobe.d/blacklist.conf but upon reboot the module is loaded
blacklist ums-realtek
blacklist ums_realtek

If anyone figures out how to blacklist the realtek multicard reader so that module doesn't load during startup, please post.

---

