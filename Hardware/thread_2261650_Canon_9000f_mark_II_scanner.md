---
title: "Canon 9000f mark II scanner"
date: 2015-01-20
forum: Hardware
---

### Post by zcartist on 2015-01-20
I bought this scanner because according to the sane database it is compatible. I plug it in NO SANE DEVICES FOUND. Any ideas? using 14.04
all input is from older versions

---

### Post by slickymaster on 2015-01-20
*Moved to the ***Hardware*** sub-forum*

---

### Post by phidia on 2015-01-20
forget it

---

### Post by pdc on 2015-01-20
Hi zcartist; yes, frustrating isn't it? ................. sane says it is completely supported; and yes, folks say it is not recognised;

______________--

what does ```
sane-find-scanner
``` and ```
scanimage -L
``` give please if you paste them into a terminal, one by one? and if no reply, if you add sudo in front of each command?

______________

the sane-pixma backend should drive all this [http://www.sane-project.org/man/sane-pixma.5.html;](http://www.sane-project.org/man/sane-pixma.5.html;) from here [http://home.arcor.de/wittawat/pixma/](http://home.arcor.de/wittawat/pixma/) there is an email at the end for Wittawat Yamwong and can I suggest you contact him directly and see if you get any joy?

_____________

the other thing the backend page recommends is join the sane development lists: sounds a bit exclusive but they are keen for anyone to join and ask for help

[http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel)

so if you get ahead and join; report the problem; it gets it recorded .................

_______________

there is a thread on Mint that reported similar issues [http://forums.linuxmint.com/viewtopic.php?f=51&t=174734](http://forums.linuxmint.com/viewtopic.php?f=51&t=174734)

_________

one needs to be a member of the scanner group: can you find Groups and Users in the admin part of your system? click to add yourself to scanner group

____________

an issue I now see in the Mint post is folks having usb3 ports and > new high-speed USB device number 3 using xhci_hcd

_____________

there have been issues with scanners and xhci and the recommendation is to go into BIOS settings on boot; and disable the xhci 

[http://askubuntu.com/tags/xhci-hcd/hot](http://askubuntu.com/tags/xhci-hcd/hot)

[https://wiki.archlinux.org/index.php/sane#Hangs_while_scanning_due_to_xhci_pre-boot_mode](https://wiki.archlinux.org/index.php/sane#Hangs_while_scanning_due_to_xhci_pre-boot_mode)

[http://ubuntuforums.org/archive/index.php/t-2252345.html](http://ubuntuforums.org/archive/index.php/t-2252345.html)

---

### Post by zcartist on 2015-01-20
~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x056a/0x00df at 002:012: Access denied (insufficient permissions)
could not open USB device 0x1a40/0x0101 at 002:011: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc408 at 002:010: Access denied (insufficient permissions)
could not open USB device 0x04d9/0x1203 at 002:009: Access denied (insufficient permissions)
could not open USB device 0x05f3/0x0461 at 002:008: Access denied (insufficient permissions)
could not open USB device 0x1a40/0x0201 at 002:005: Access denied (insufficient permissions)
could not open USB device 0x04a9/0x190d at 002:014: Access denied (insufficient permissions)
could not open USB device 0x0bda/0x0151 at 002:007: Access denied (insufficient permissions)
could not open USB device 0x147a/0xe018 at 002:006: Access denied (insufficient permissions)
could not open USB device 0x05e3/0x0608 at 002:003: Access denied (insufficient permissions)
could not open USB device 0x15a9/0x0004 at 002:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 008:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 003:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).


So then I did root thinking it was permissions

# sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.



I am puzzled and get no results with root access

there is this thread but it is sort of greek to me. I would need a walk through.

[http://ubuntuforums.org/showthread.php?t=2180205&highlight=9000f](http://ubuntuforums.org/showthread.php?t=2180205&highlight=9000f)

I was thinking I would just plug and scan according to sane

Thank you

---

### Post by pdc on 2015-01-20
well if I guided you to add the rule that Nick Payne covered in post #2 in the thread [http://ubuntuforums.org/showthread.php?t=2180205&highlight=9000f](http://ubuntuforums.org/showthread.php?t=2180205&highlight=9000f)

```
gksudo gedit /etc/udev/rules.d/99-local.rules
```

It is very likely that you will be creating a new file called [COLOR="#008000"]99-local.rules[/COLOR] and it will therefore be empty when you open it; and you will be using the text editor that is called [COLOR="#0000FF"]gedit[/COLOR] to create the entry;

If you paste the above into a terminal; and hit the ENTER key; and then paste what is below into the empty file that iscalled 99-local.rules; 

what you will paste is what Nick quoted..............except I have guessed at what your username is so add what is correct ............

```
SUBSYSTEM="usb_device", ACTION="add", GOTO="canon_rules_end"

# Canon CanoScan 9000F Mark II
ATTR{idVendor}="04a9", ATTR{idProduct}="190d", SYMLINK+="scan-canon", MODE="0666", OWNER="zcartist", GROUP="scanner"

LABEL="canon_rules_end"
```

____________________

do you know how to look at your BIOS settings as your computer boots? I think it is worth checking also the status of xhci and it seems worth disabling it if it is active

____________

reboot after the above: any joy?

---

### Post by zcartist on 2015-01-21
No Joy I got a long scrolling error on boot having to do with  ATTR{idVendor}="04a9", ATTR{idProduct}="190d", does not exist. I cleared the file and get no  error

---

### Post by pdc on 2015-01-21
1) did you join the sane-development mailing list?

2) did you look at the xhci in the Bios as your computer boots?

3) can you tell us if you get an ID of > 04a9:190d when you type the command ```
lsusb
``` into a terminal please? ........with the Canon plugged in and turned

---

### Post by zcartist on 2015-01-21
Bus 002 Device 011: ID 04a9:190d Canon, Inc

my cpu is usb 2  I think that problem is 3.0

I will try the mailing list

---

### Post by pdc on 2015-01-21
thanks; I was curious that you got the message > ATTR{idVendor}="04a9", ATTR{idProduct}="190d", does not exist. 

...........and on lsusb it shows up

We hope the mailing list may help

---

### Post by zcartist on 2015-01-21
Yeah the only thing I  can think of is a backend is missing

---

### Post by zcartist on 2015-01-24
This ppa from Rolf Bensch resolves the issue

[https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git](https://launchpad.net/~rolfbensch/+archive/ubuntu/sane-git) (sudo
add-apt-repository ppa:rolfbensch/sane-git).

Thank you

---

### Post by pdc on 2015-01-25
so your Canon 9000F Mark II works well now?

...........if so great; well done ............ how did you get on to the ppa you quote?

---

### Post by zcartist on 2015-01-26
It works fine...I got the ppa through the sane mailing list you posted. It seems to be a great resource. I was told the scanner does work in 14.10. It does not in 04 without the updated backend which the ppa takes care of.

and this below.is badly broken


SUBSYSTEM="usb_device", ACTION="add", GOTO="canon_rules_end"

# Canon CanoScan 9000F Mark II
ATTR{idVendor}="04a9", ATTR{idProduct}="190d", SYMLINK+="scan-canon", MODE="0666", OWNER="zcartist", GROUP="scanner"

LABEL="canon_rules_end"

Thank you

---

