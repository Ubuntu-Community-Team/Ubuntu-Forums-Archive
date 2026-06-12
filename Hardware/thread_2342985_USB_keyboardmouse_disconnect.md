---
title: "USB keyboard/mouse disconnect"
date: 2016-11-11
forum: Hardware
---

### Post by cspence on 2016-11-11
A few weeks ago I upgraded to 16.10. Since then my computer randomly stops responding to the usb keyboard and usb mouse. It doesn't always stop responding to both, sometimes it's just one of them. Unplugging them and plugging them back into a different port often fixes the problem, temporarily. It's very irregular. Sometimes it's soon after booting, sometimes hours later. I haven't tested it a lot with external hard drives, but I did have trouble with one once, after I decided to do a clean reinstall, and was backing up my home directory.

/var/log/syslog says things that seem suspicious to me, like: 

Nov 11 20:24:24 tater kernel: [ 6342.180038] ohci-pci 0000:00:02.0: frame counter not updating; disabled
Nov 11 20:24:24 tater kernel: [ 6342.180054] ohci-pci 0000:00:02.0: HC died; cleaning up
Nov 11 20:24:24 tater kernel: [ 6342.180117] ohci-pci 0000:00:04.0: frame counter not updating; disabled
Nov 11 20:24:24 tater kernel: [ 6342.180140] ohci-pci 0000:00:04.0: HC died; cleaning up
Nov 11 20:24:24 tater kernel: [ 6342.180211] usb 3-2: USB disconnect, device number 2
Nov 11 20:24:24 tater kernel: [ 6342.184832] usb 4-1: USB disconnect, device number 2
Nov 11 20:24:24 tater acpid: input device has been disconnected, fd 7
Nov 11 20:24:24 tater acpid: input device has been disconnected, fd 8

Apologies if this is a known problem. I did a brief search and didn't find anything that was an obvious solution, or obvious duplicate of the problem. There is [this old post]("http://askubuntu.com/questions/206614/usb-slots-stop-working-suddenly-from-time-to-time"), which is somewhat different. I'm not quite sure how to relate it.

---

### Post by cspence on 2016-11-26
This seems to be a bug in the 4.8 kernel, which may be fixed in the 4.9 kernel. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1635012](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1635012).
I haven't figured out if 16.10 will eventually upgrade to kernel 4.9, or if the fix will make it into a 4.8 version.

---

### Post by dinkstr on 2016-11-27
I've had a similar problem, every device except the mouse will stop working until I restart the system. I used a workaround which involved plugging a USB hub into the working port and plugging all my USB devices into it.

---

### Post by jonandtice on 2016-11-29
My USB audio interface kept disappearing at the same time my computer was freezing... except it wasn't freezing, I was just loosing my mouse and keyboard.  As far as I can tell, it's a problem with USB 3.0 ports.  So the solution is to either not use 3.0 ports or install a 4.7 kernel (and would have to select every time at boot) or a 4.9 kernel.  They can be downloaded from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).  You will have to install the linux-headers...all, linux-headers...generic and linux-image...generic.

---

### Post by cspence on 2016-12-17
I don't think I have usb 3 ports, but I could be mistaken. I gather that if I have usb 3 ports, I should see "xhci" and "5000M" at the ends of lines in the following (see [http://askubuntu.com/questions/217676/how-do-i-find-out-whether-my-system-has-usb-3-0-ports](http://askubuntu.com/questions/217676/how-do-i-find-out-whether-my-system-has-usb-3-0-ports)):

$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/6p, 12M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=ohci-pci/6p, 12M
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 2: Dev 2, If 1, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 3: Dev 3, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/6p, 480M
$

The ohci fits with the bit of /var/log/syslog that I pasted in my original post.

---

### Post by cspence on 2016-12-17
The problem hadn't happened in a couple of weeks, so I was thinking that one of the kernel upgrades had fixed it. But it just started happening again. The launchpad link I posted above says it's a bug in the kernel. I should have posted the link [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1634737](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1634737) which is more to the point. I hope the fix makes it into a kernel upgrade for 16.10. I suppose I could try installing an upstream kernel.

---

### Post by s-parschauer on 2017-06-13
Some usbhid devices need to be always polled to prevent a buffer overflow which causes that they disconnect and reconnect periodically.

The usbhid driver needs the quirk HID_QUIRK_ALWAYS_POLL (0x00000400) then.

I can't see your idVendor and idProduct here. "lsusb -vvv" would show it. I do an example with idVendor 0x1234 and idProduct 0x5678.

Start with kernel boot parameter  "usbhid.quirks=0x1234:0x5678:0x00000400". In  drivers/hid/usbhid/hid-quirks.c of the kernel source there is a list of  all usbhid quirks. Make sure your quirk is or gets included in the latest upstream kernel release. Please report this bug to the [EMAIL="linux-usb@vger.kernel.org"]linux-usb@vger.kernel.org[/EMAIL] mailing list to get it fixed. TIA

Also disabling USB auto-suspend by kernel boot parameter  "usbcore.autosuspend=-1" should be tried to check if it is a power  management issue instead. 		 	 		 		 		 		  		 		 		 		 		 		 			 				[HR][/HR]

---

### Post by cspence on 2017-06-20
Thanks. Actually, it seems to be fixed, now, or at least I haven't had the problem in a long time.

---

