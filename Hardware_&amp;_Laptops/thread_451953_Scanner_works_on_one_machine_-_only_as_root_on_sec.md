---
title: "Scanner works on one machine - only as root on second"
date: 2007-05-22
forum: Hardware &amp; Laptops
---

### Post by 4ebees on 2007-05-22
Hi all,

This is seriously driving me crazy.

I have a Diamond View scanner, recognised as

lsusb

Bus 002 Device 004: ID 04a5:2060 Acer Peripherals Inc. (now BenQ Corp.) Prisa 620U+/640U

Now this works on my desktop running Dapper 6.06. I've installed 6.06 on my HP lappie and it works - as root only.

I've checked all permissions and settings I can think of by comparing laptop setup with desktop setup. I had FC4 installed on the lappy recently and the scanner worked fine <shakes head>

So,

sudo scanimage -L
Password:
device `snapscan:libusb:002:004' is a Acer FlatbedScanner13 flatbed scanner

sane-find-scanner
<snip>
found USB scanner (vendor=0x04a5 [Color], product=0x2060 [ FlatbedScanner 13]) at libusb:002:004

All well and good.

if I run 'groups', I get:

patrick root adm dialout cdrom floppy tape audio dip video plugdev lpadmin scanner saned

I read if I ran Xsane as root first I'd create a file:

/home/patrick/.sane/xsane/

which would be owned as root and so had to change owner to me. This didn't work.

I changed ownership of the firmware .bin file u96v121.bin to me. That didn't work.

BTW the firmware is here:

/usr/share/sane/snapscan/u96v121.bin

exactly the same as my desktop.

I ran:

sudo chmod a+w /dev/bus/usb/$002/004

per:

[http://ubuntuforums.org/showthread.php?t=166944&highlight=xsane+root](http://ubuntuforums.org/showthread.php?t=166944&highlight=xsane+root)

That didn't work.

Plus, sometimes I run the scanner after rebooting and the damn thing is in a different USB location.

I've rebooted a half dozen times, no change.

I'm seriously at a dead end here. My skills are minimal as it is, and this has defeated me.

I've google boogled and checked Ubuntuforums

I've even included myself as 'user' in groups, but to no avail.

All of the changes made above have been set back to the original settings following repeated failure, so I'm hoping to start again with some assistance.

The only major difference between the machines that I can think of is that on the laptop I have a separate root password - the desktop is always on, is accessible all the time and has only one user account. The laptop goes out of the house and is used by my children, relatives and friends sometimes, so I don't want anyone else knowing the root password (natch).

Any assistance or advice would be greatly appreciated.

---

### Post by Tilo on 2007-05-31
what about the ownership of the device files for the scanner on each of the systems? 
how are the permissions set for the device files?

---

### Post by 4ebees on 2007-06-02
> **Tilo said:**
> what about the ownership of the device files for the scanner on each of the systems? 
how are the permissions set for the device files?

Hi Tilo,

Sorry for being so slow.. do you mean the .bin firmware file or something else?

Regards,

4ebees

---

