---
title: "Trying to mount creative zen mp3 on ubuntu"
date: 2015-09-06
forum: Hardware
---

### Post by mikki2 on 2015-09-06
I've just installed ubuntu on my laptop and love it. One minor thing I'd like to get
working is have it mount my ancient mp3 player st I can push/pull songs. I've
installed ntfs-3g and usbmount. 
When I plug in the device on the usb port, sylog sees it:

Sep  6 09:44:56 ubu kernel: [ 4380.963601] usb 1-2: new high-speed USB device number 2 using xhci_hcd
Sep  6 09:44:56 ubu kernel: [ 4381.092397] usb 1-2: New USB device found, idVendor=041e, idProduct=411b
Sep  6 09:44:56 ubu kernel: [ 4381.092400] usb 1-2: New USB device strings: Mfr=1, Product=2, SerialNum
ber=3
Sep  6 09:44:56 ubu kernel: [ 4381.092402] usb 1-2: Product: Creative Zen Touch
Sep  6 09:44:56 ubu kernel: [ 4381.092404] usb 1-2: Manufacturer: Creative Technology
Sep  6 09:44:56 ubu kernel: [ 4381.092405] usb 1-2: SerialNumber: 01012551B703931C
Sep  6 09:44:56 ubu mtp-probe: checking bus 1, device 2: "/sys/devices/pci0000:00/0000:00:14.0/usb1/1-2
"
Sep  6 09:44:56 ubu mtp-probe: bus: 1, device: 2 was not an MTP device

Not sure how to reference the device in a mount command. I would think something like
mount -t ntfs /dev/usb /media/usb1     (having created /media/usb1)   or
ntfs-3g  /dev/usb /media/usb1


Any ideas?

Thanks

---

### Post by coffeecat on 2015-09-06
The Ubuntu, Linux and OS Chat sub-forum is for chat, not support &#8211; hence the name. So..

*Thread moved to **Hardware**.*


[quote=mikki2]installed ntfs-3g and usbmount. [/quote]

The package ntfs-3g is already installed in all supported version of Ubuntu - it has been for years. And besides, are you sure that your mp3 player uses the ntfs filesystem? This link seems to suggest not: [http://support.creative.com/kb/ShowArticle.aspx?sid=4779](http://support.creative.com/kb/ShowArticle.aspx?sid=4779) More importantly, I suggest you now uninstall usbmount. Usbmount is a sure road to frustration and annoyance. It is designed for server installations and interferes with the automounting functionality built into the various GUI desktops.

**Edit:** Which release of Ubuntu are you using, and which version (flavour)? This thread below is a bit old in Ubuntu terms as things move quickly, and mtp support is better than it was, but it may be helpful:

[http://ubuntuforums.org/showthread.php?t=1910497](http://ubuntuforums.org/showthread.php?t=1910497)

It's possible that the latest version of Ubuntu might mount your device automatically once the OS has been cleansed of the contamination caused by usbmount. If not, there might be something useful in the thread.

---

### Post by kostkon on 2015-09-06
You probably need [Gnomad2]("http://gnomad2.sourceforge.net/"). It's in the repos.

---

