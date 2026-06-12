---
title: "New Convert - Minor (hopefully) hardware issues"
date: 2007-11-20
forum: Hardware &amp; Laptops
---

### Post by gnelson on 2007-11-20
Long time lurker, first time poster.

After using k/ubuntu in lesser roles, I am trying to make the full move from Windows to Ubuntu Gutsy.  For those that are interested, - my dislike of Vista on my new notebook PC is what really prompted it.

Getting to the point ...  I have 2 hardware issues with my notebook that I can't seem to find self-help for.

My set up is a HP DV6324US notebook PC, AMD Turion 64 x2, 2 GB RAM, Broadcom wireless, nvidia graphics.  OS is Ubuntu Gutsy AMD64.

1)  Occasionally (usually after a long period of use) the wireless network connection fails and the only way that I know how to restore it is through a reboot.  When this happens, the applet in the system tray still shows a connection.  Clicking on "Connect to other wireless network" seems to crash the applet (icon disappears).

2) I bought a 2.5" USB external hard drive to back up my data.  I was once able to get it recognized in Ubuntu and formatted it as FAT32.  It was /dev/sdb1.  However, that was one time of 10 attempts before and about 10 after.  fdisk -l gives an empty response. It is plugged in, power light is on, I can hear the drive spinning.

I have used the "noapic" and "noapic nolapic" boot options because my notebook won't boot without them.  If there's a better solution, I'd love to know.  The one time the external HD worked was when I used "noapic nolapic".  I mention this because these can supposedly affect USB.  This whole area is dark and mysterious to me.  I'm only relying on what I've read.

I hope I've provided enough information and I appreciate any help that anyone can offer.


Greg

---

### Post by dabl on 2007-11-20
Can't offer you anything on the wireless card, but this may help if you're willing to format the USB drive as NTFS:

[http://kubuntuforums.net/forums/index.php?topic=3084679.0](http://kubuntuforums.net/forums/index.php?topic=3084679.0)

:)

---

### Post by gnelson on 2007-11-20
Thanks for the reply, but I was able to format the disk as FAT32 the one time I could access it.

Also, I just tried the disk on my Kubuntu Gutsy server and it works fine there, so I'm leaning  toward a laptop/USB issue.

---

### Post by gnelson on 2007-11-21
As Murphy would have it, not long after I posted this I think I have found at least a partial fix.

phssthpok in [this thread]("http://ubuntuforums.org/showthread.php?t=478050&page=4") recently posted the following workaround:

(1) Make a backup of /etc/network/interfaces. This might come in handy later.
(2) Edit /etc/init.d/udev and change instances of

/sbin/udevtrigger

to

/sbin/udevtrigger --subsystem-nomatch="*misc*"

(3) Disable hwclock scripts in /etc/init.d/ (there are 2) (look around the forums for how to remove startup scripts using update-rc.d

(4) Reboot. If you are running Gnome you may have a problem with gnome-settings-daemon not loading. I fixed this by commenting out all the IPv6 lines in /etc/hosts. I have also heard of people finding that references to the loopback device have disappeared from /etc/network/interfaces (thus the backup; if anything has changed, restore it to how it was).

(5) Un-blacklist ehci_hcd if you have added it to /etc/modprobe.d/blacklist.
(6) Reboot. At this point, everything started working for me.

Doing this has allowed my laptop to boot without noapic and my USB drive was instantly recognized when I plugged it in.  We'll see about the wireless issue.

---

### Post by Trevorius on 2007-11-21
I've been having the exact same problem with my wireless as described in problem #1. I normally have to reboot 2-3 time a day because of it, even tho I'd prefer to reboot only once every week or two lol.

---

### Post by gnelson on 2007-11-21
It's too early to tell for sure, but so far (fingers crossed) I have not had the wireless problem after doing that fix yesterday.

---

### Post by gnelson on 2007-11-25
OP here.  The mentioned workaround had no effect on the wireless.  It still drops out after what seems to be a random period of time.  It did fix the problem with by USB external hard drive, but I started having problems with the system clock.  I'm now trying to undo this workaround, and still in need of a better one.

---

