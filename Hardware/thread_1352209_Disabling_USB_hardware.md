---
title: "Disabling USB hardware"
date: 2009-12-11
forum: Hardware
---

### Post by maddentim on 2009-12-11
Hi, looking for a workaround here.  I have a hand-me-down laptop that has a somewhat fried system board.  

An HP pavilion dv6000 w/ amd64, the manifestation of the hardware problem is the usb ports are unrecognized (in windoze or ubuntu).  In ubuntu, the syslog shows a constant stream of messages like this: 

```
{date} ubuntu kernel: [ time stamp ] hub 2-0:1.0: unable to enumerate USB device on port 2

```
on and on and on a couple of times a second.  The issue I run into is the inability to enumerate the USB prevents the laptop from suspending or hibernating.  

I am looking for a way to blacklist (or the like) this USB device so the kernel doesn't worry about it.  I tried the suggestion here: [http://ubuntuforums.org/showpost.php?p=4309162&postcount=3]("http://ubuntuforums.org/showpost.php?p=4309162&postcount=3") but it did not accomplish my goal.

Thanks for your help!

---

### Post by prshah on 2009-12-11
> **maddentim said:**
> 
I am looking for a way to blacklist (or the like) this USB device so the kernel doesn't worry about it.  I tried the suggestion here: [http://ubuntuforums.org/showpost.php?p=4309162&postcount=3]("http://ubuntuforums.org/showpost.php?p=4309162&postcount=3") but it did not accomplish my goal.


From 9.10 onwards, config files require a ".conf" extention, which the linked post lacked. So you can repeat the instructions with ".conf" appended to the filename, or you can add the modules to the existing blacklist file (/etc/modprobe.d/blacklist.conf). To do this, edit the file, and add the lines as below```
blacklist ehci_hcd
blacklist uhci_hcd
blacklist ohci_hcd
```

You will need to restart the system for changes to take effect.

You can also attempt to turn off onboard USB in the BIOS. Post back if you want more instructions on this.

---

### Post by maddentim on 2009-12-13
@prshah, thanks for the tip.  Your advice got the blacklist to take affect, but instead of just disabling the usb, it cause the kernel to panic and not boot. ramfs issue or something. I had to undo it quick and didn't think to write the error down.

Anyway, I like your suggestion of turning it off in the BIOS.  I check the BIOS utility when you press the F10 button from the HP logo screen but there was no option for USB.  I would appreciate it if you would help me do this in the BIOS.  Thanks

---

### Post by prshah on 2009-12-14
> **maddentim said:**
> check the BIOS utility when you press the F10 button from the HP logo screen but there was no option for USB. 

Rather strange, I couldn't find it either. Maybe there is some other way to disable the onboard USB; I'll look around, and post here if I happen to find something (don't count on it).

---

### Post by maddentim on 2009-12-14
OK, thanks... I post as well if I find something...

---

### Post by maddentim on 2009-12-15
I figured it out a way to do it.  I had to add "nousb" to the end of the kernel line in my /boot/grub/menu.lst file.

from:
```

kernel          /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro quiet splash

```

to:
```

kernel          /boot/vmlinuz-2.6.31-16-generic root=/dev/sda1 ro quiet splash nousb

```

No more endless syslog messages and it suspends! yeehaw.  of course there is no usb, but it didn't work anyway...

thank's for your attention and willingness to assist.

---

