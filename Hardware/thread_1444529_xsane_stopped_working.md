---
title: "xsane stopped working"
date: 2010-04-01
forum: Hardware
---

### Post by col48 on 2010-04-01
Recently (at some point in the last 5 weeks) xsane has stopped detecting my MFP (HP Deskjet F2280). My setup has not had any hardware changes and the only software changes in that time have been the periodic Synaptic updates. Before this hiccup all had been well for over a year.

If I run xsane it thinks a while (2 or 3 sec?) and tells me in a little panel no devices were detected.

If I run lsusb, it finds the device, but after all it is a printer/scanner and the printing function continues to be OK so this is not a surprise - I do not know enough to understand all the lsusb output to know if anything is amiss in the detail.

What is it that xsane needs so that it detects the device as a scanner? Is there a file or specific stuff in a file which I could get from an old backup or edit (carefully!) by hand?

I don't need the scanning function often enough to pin down what might have done the mischief.

---

### Post by col48 on 2010-04-03
Help!

The computer is ALSO not recognising a digital camera as a device when connected to a usb port.  It was happy with it just a few weeks ago.

Can anyone help?

If I refreshed /dev from a copy of a few weeks ago, would this cure it? Or is there something else as well or instead?

---

### Post by col48 on 2010-04-09
bump.

I can't find anything I can make use of to get a handle on this issue.

---

### Post by slooow on 2010-04-09
For the scanner investigate the driver. Which driver did it use, is it loaded with `sudo lsmod`.
For the camera I usually just load it as usb-storage. Once plugged in, you find it in dmesg. Then as root you can mount it: sudo mount -t vfat /dev/sdX1 /mnt/pen, make sure that /mnt/pen exists otherwise create it sudo mkdir /mnt/pen.

---

### Post by col48 on 2010-04-10
Thanks slooow for your reply.

The MFP uses hplip (version 3.9.4b).  The printing side is fine, it's just the scanning which has gone awol.  When I run lsmod I can see no mention of hplip.

With the camera, the output of dmesg is prolific and I am not entirely sure what I am looking for but when I plug in the camera, switch it on and then run dmesg I don't see anything like 'usb-storage' or 'camera'.  But there are quite a few lines like

[   63.252011] usb 2-7: device not accepting address 13, error -71

where the address (13) runs through about 20 values.  Is this relevant?

---

### Post by col48 on 2010-05-03
bump

No progress made on these.

I have old copies of system folders (/etc /dev, /lib and so on). Which of these should I use to replace current versions to restore the old status quo when these peripherals were working fine?

If that is too dangerous to contemplate, how do I roll back the last two sets of Synaptic updates?

---

### Post by col48 on 2010-05-11
Well, it is solved, but not totally diagnosed.

Hardy Synaptic (at least, the copy of its database I have) knows 2.8.2 as the one to install.  In the last couple of weeks, version 3.9.x had got overwritten by 2.8.2 courtesy of Synaptic as I tried to solve the problem.

Reading the hplip website, I read that the F2280 needs (minimum) version 2.8.6 to work.  So I download 3.10.2 (the latest) and install it and Bingo! the scanning function works again.

It does not explain why it went awol in the first place, but never mind!

By the way, the camera problem turns out to be a USB port which has developed a fault.

---

