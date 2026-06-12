---
title: "PB to detect scanner EPSON 1670"
date: 2006-02-28
forum: Hardware &amp; Laptops
---

### Post by jamin on 2006-02-28
>>First, I install the firmeware for the scanner EPSON Perfection 1670
	(source [http://ubuntuforums.org/showthread.php?t=26911](http://ubuntuforums.org/showthread.php?t=26911))
	- I download le firmware
		% wget [http://www.commercialventvac.com/~jeffs/ESFW30.BIN](http://www.commercialventvac.com/~jeffs/ESFW30.BIN)
		% sudo cp ESFW30.BIN /etc/sane.d
	- I edit /etc/saned.d/snapscan.conf
	  to change :
			firmware /path/to/your/firmware/file.bin
			=> /etc/sane.d/ESFW30.BIN
	- and then ...
		% scanimage -L
		doesn't work !!!
		
>> PB
	- I don't find the mount point ? 
		/dev/???
	- but , the scanner seems to be recognize :
	  when I turn it off 
	% dmesg
[4296994.434000] usb 3-1: USB disconnect, address 5
	- when I turn it on
	% dmesg
[4297012.101000] usb 3-1: new high speed USB device using ehci_hcd and address 6

>> Any ideas to detect the scanner ?:-k?

---

### Post by flavio20002 on 2007-12-28
hi! i had the same problem!!
Try sudo xsane...
if it works, there's a problem of permission on the file .bin...changhe the permission by nautilus (sudo nautilus) and set it to allow all the user to acess it in read...the maybe will work...

---

