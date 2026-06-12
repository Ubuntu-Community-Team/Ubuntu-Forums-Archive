---
title: "[SOLVED] device descriptor read/64, error -71 - USB problem"
date: 2008-05-17
forum: Hardware
---

### Post by toni_uk on 2008-05-17
I have a problem with my USB connections. for some resons they are not quite doing what they should. I have a new camera and on my old laptop (running Ubuntu 8.04) it is deteted immediately on the old USB 1.0. On my brand new PC also running Ubuntu 8.04 it is not detected. dmesg is showing the following:

> [ 563.332000] end_request: I/O error, dev sdb, sector 60796
[ 563.332000] printk: 24 messages suppressed.
[ 563.332000] Buffer I/O error on device sdb1, logical block 60745
[ 717.556000] usb 2-4: new high speed USB device using ehci_hcd and address 12
[ 717.668000] usb 2-4: device descriptor read/64, error -71
[ 717.884000] usb 2-4: device descriptor read/64, error -71
[ 718.100000] usb 2-4: new high speed USB device using ehci_hcd and address 13
[ 718.212000] usb 2-4: device descriptor read/64, error -71
[ 718.428000] usb 2-4: device descriptor read/64, error -71
[ 718.644000] usb 2-4: new high speed USB device using ehci_hcd and address 14
[ 719.052000] usb 2-4: device not accepting address 14, error -71
[ 719.164000] usb 2-4: new high speed USB device using ehci_hcd and address 15
[ 719.572000] usb 2-4: device not accepting address 15, error -71
[ 801.752000] usb 2-4: new high speed USB device using ehci_hcd and address 16
[ 801.864000] usb 2-4: device descriptor read/64, error -71
[ 802.080000] usb 2-4: device descriptor read/64, error -71
[ 802.296000] usb 2-4: new high speed USB device using ehci_hcd and address 17
[ 802.408000] usb 2-4: device descriptor read/64, error -71
[ 802.624000] usb 2-4: device descriptor read/64, error -71
[ 802.840000] usb 2-4: new high speed USB device using ehci_hcd and address 18
[ 803.248000] usb 2-4: device not accepting address 18, error -71
[ 803.360000] usb 2-4: new high speed USB device using ehci_hcd and address 19
[ 803.768000] usb 2-4: device not accepting address 19, error -71  

Any help appreciated - don't quite understand why it is not working. Thanks!

---

### Post by toni_uk on 2008-05-18
bump! no one?

---

### Post by pytheas22 on 2008-07-04
Did you ever solve this problem?  I'm trying to help someone with the same issue.  I think it comes down to disabling CONFIG_USB_SUSPEND, which can be done by reloading the module "usbcore" with the option "autosuspend=-1."  However doing that is tricky because it's hard to unload usbcore once the system is booted.

There are instructions [here]("http://www.mail-archive.com/barry-devel@lists.sourceforge.net/msg00398.html") on other ways to disable CONFIG_USB_SUSPEND without reloading usbcore.  Have you tried them?  I don't want to try them myself I can't break my computer right now, and it's hard to test USB stuff in a virtual machine.
> 
Debian / Ubuntu systems:
========================

Comes with usbcore (CONFIG_USB) compiled as a module and CONFIG_USB_SUSPEND
enabled (at least on Ubuntu).

Therefore, to disable autosuspend you either:

        - recompile kernel without CONFIG_USB_SUSPEND

        - configure /etc/modprobe.d/ with a file containing
                "options usbcore autosuspend=-1"
                or set to 0 depending on your kernel

If your system needs the modprobe configuration file above, and if your
system uses initrd (probably does) then you will need to rebuild the
initrd for your kernel for this to take effect.  For example:

        dpkg-reconfigure linux-image-2.6.22.1

---

### Post by prince_sabin on 2008-07-04
I have the same problem. With a camera

I tried the modprobe thing, but it did solve the problem

---

### Post by toni_uk on 2008-07-04
pytheas22: thanks. sorted it, can't remember how though. Thanks anyway - good to see that someone is looking through all the unanswered threads.

---

### Post by pytheas22 on 2008-07-05
> pytheas22: thanks. sorted it, can't remember how though. Thanks anyway - good to see that someone is looking through all the unanswered threads.

Do you have any idea how you fixed it?  At least, do you remember if CONFIG_USB_SUSPEND had anything to do with it?

I'm sorry no one answered your post earlier, too.  It's a good example of why looking through unanswered posts is a good way to kill time when you're bored.

---

### Post by toni_uk on 2008-09-03
hey guys, just put a clean install of Ubuntu back on my computer and of course had the same problem with the USB/Camera. Did a bit of research and found this so damn easy solution on the Mint Forum:

in the terminal type: echo -1 >/sys/module/usbcore/parameters/autosuspend

I was logged in as root - not sure whether necessary. Then just reboot and Bob's your Uncle.

Worked a treat for me.

---

### Post by just_mcateer on 2008-10-22
I tried this fix for the same error message with a different error number (-110), but it did not seem to have any effect.

Thanks,
Justin

---

### Post by pytheas22 on 2008-10-23
> I tried this fix for the same error message with a different error number (-110), but it did not seem to have any effect.

What is the total output of 'dmesg | tail' after you plug in the device?

---

### Post by Earendil1982 on 2009-04-01
Did you try this:
[http://www.mepis.org/node/5860](http://www.mepis.org/node/5860)

In short as root:
echo Y > /sys/module/usbcore/parameters/old_scheme_first

---

### Post by jmiguel77 on 2009-05-26
what if i do this :

sudo echo Y > /sys/module/usbcore/parameters/old_scheme_first

and get this:

bash: /sys/module/usbcore/parameters/old_scheme_first: Permission denied

---

### Post by pytheas22 on 2009-05-26
> **jmiguel77 said:**
> what if i do this :

sudo echo Y > /sys/module/usbcore/parameters/old_scheme_first

and get this:

bash: /sys/module/usbcore/parameters/old_scheme_first: Permission denied

The problem is that the second command (into which the first is being redirected using the > operator) isn't being run as root.  Try this:

```

echo Y | **sudo tee** /sys/module/usbcore/parameters/old_scheme_first
```

That should work.

---

### Post by dortmann on 2010-09-14
I just encountered this USB error on 10.04.  Simultaneously, my X would not boot.  I noticed "vga16fb" had somehow snuck into the system ... it was missing from etc modprobe.d framebuffer blacklist.

I after adding vga16fb to the blacklist file I have both X and usb functionality again.

DISABLE ALL FRAMEBUFFER MODULES.

lsmod | grep fb


Hope this helps.
[email]dortmann31415@yahoo.com[/email]

---

### Post by burneverything on 2010-11-17
> **pytheas22 said:**
> The problem is that the second command (into which the first is being redirected using the > operator) isn't being run as root.  Try this:

```

echo Y | **sudo tee** /sys/module/usbcore/parameters/old_scheme_first
```

That should work.
Fixed my problem with a Mac borked HDD that would not mount.

thanks

---

### Post by trippedn on 2011-10-31
> **toni_uk said:**
> hey guys, just put a clean install of Ubuntu back on my computer and of course had the same problem with the USB/Camera. Did a bit of research and found this so damn easy solution on the Mint Forum:

in the terminal type: echo -1 >/sys/module/usbcore/parameters/autosuspend

I was logged in as root - not sure whether necessary. Then just reboot and Bob's your Uncle.

Worked a treat for me.

Very old thread, but this is still very applicable. I have some devices that would not connect and this fixed it.

The old value was 2 (seconds).

Here is some documentation for some of the other values that can be configured:
```
usbcore.autosuspend=
		[USB] The autosuspend time delay (in seconds) used
		for newly-detected USB devices (default 2).  This
		is the time required before an idle device will be
		autosuspended.  Devices for which the delay is set
		to a negative value won't be autosuspended at all.

usbcore.usbfs_snoop=
		[USB] Set to log all usbfs traffic (default 0 = off).

usbcore.blinkenlights=
		[USB] Set to cycle leds on hubs (default 0 = off).

usbcore.old_scheme_first=
		[USB] Start with the old device initialization
		scheme (default 0 = off).

usbcore.use_both_schemes=
		[USB] Try the other device initialization scheme
		if the first one fails (default 1 = enabled).
	
usbcore.initial_descriptor_timeout=
		[USB] Specifies timeout for the initial 64-byte
                USB_REQ_GET_DESCRIPTOR request in milliseconds
		(default 5000 = 5.0 seconds).
```

---

