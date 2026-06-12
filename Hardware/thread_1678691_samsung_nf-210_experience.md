---
title: "samsung nf-210 experience"
date: 2011-01-30
forum: Hardware
---

### Post by s0ullight on 2011-01-30
Hello, I recently bought a samsung nf-210. One of the first things I did was to run ubuntu on it. Most hardware worked out of box. To get the bcm4313 to work, I had to enable its restricted driver. (too bad b43 doesn't cover this device)

What I got stuck with was the trackpad this device has (Elan tech smartpad). It is wrongly seen as a "logitech ps/2 wheel". A little bit of searching showed that this bug was indeed discovered before and reported [_here_]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/681904"). Since I didn't install ubuntu yet on this device, I haven't messed with anything (like the samsung tools to get fn keys to work+backlight). (But I did prepare a partition)

A youtube movie showed it has an unused mini pci-e port inside, unfortunately the n550 atom processor doesn't support intel turbo memory (one I have). so i'm considering to put in an intel 4965 wireless card (will it work?).

I started this thread so others can share their experiences with this device.

Thanks in advance ;)

**Update** The initial setup (unboxing) asked me to use 2 partitions or 1, I chose 2 back then. Appearantly D:\ is in an extended partition. I used windows own built in tools to shrink the partition to half of it's size (100gb initially) and used a live usb to create an ext4 partition using the free space (/dev/sda6). During the install proces I chose /dev/sda6 as root, no swap and installing the bootloader to /dev/sda6. This way I preserved the windows bootloader (as I'm not sure if the mbr part is involved in recovery setup). Next was to install easybcd under windows and add a linux entry. Now I have windows 7/ubuntu 10.10 existing next to each other with windows bootloader on mbr (preserving recovery etc.) As a backup plan I extracted the first 512 bytes (mbr) of /dev/sda and saved it elsewhere.

**Update2** I added the voria ppa as a source, updated my system with packages from there, installed samsung-backlight samsung-tools and easy-slow-down-manager. Now the fn keys work excellent (grabs are released). Dimming backlight isn't working, while the system does think i'm dimming it. Got a workaround for it: "sudo setpci -s 00:02.0 f4.b=<value between 0 and ff>". Now the biggest concern remains the trackpad.
I also tried out brcm80211 for the bcm4313, a driver still in development. Using compat-wireless (bleeding edge) it built fine, loaded fine, but upon connecting caused a freeze of my system. Guess it's not stable enough yet.

** Update3** I have found a working solution for the backlight, add "acpi_backlight=vendor" as a kernel parameter. After a reboot, it will work as desired.

---

### Post by seraphina46 on 2011-04-28
Hey there,

I found your information really helpful - I've just installed 11.04 on my Samsung NF210, keeping the WIndows partition. I found it a bit awkward in that I manually set up all my partitions using gparted and the live USB distro, and then when I went to install, Ubuntu tried to make another partition. Ho hum, no big deal to manually select the install point.

All of my hardware so far has worked fine - wifi sorted itself out straight away, and I installed samsung-tools and samsung-backlight with no problems.

---

### Post by s0ullight on 2011-04-28
Good to hear it was helpful :)
Indeed, 11.04 includes brcm80211, which is very stable.
For the Elantech touchpad, there is a working patch to enable multitouch. I got mine working working under 10.10. I hope the patch goes upstream soon and will be available as an update :)

---

### Post by seraphina46 on 2011-04-29
A multitouch upgrade would be great!

I do however get weird behaviour when I pull my power cable out. I would expect the system to recognise that I'm now running on battery, and adjust the screen brightness etc accordingly, but whenever I pull the power cable out, it goes straight to sleep:/ If I hit the power button, it comes right back up again to an unlock screen, and at that point it figures out that it's running on battery and dims the screen. Do you have the same issue?

---

### Post by s0ullight on 2011-05-06
So, for multitouch there are currently 2 patches: one for 10.10 and one for 11.04. Consider these as experimental and use them at your own risk.

For 10.10: [https://bugzilla.kernel.org/attachment.cgi?id=55292]("https://bugzilla.kernel.org/attachment.cgi?id=55292")
For 11.04: [https://bugzilla.kernel.org/attachment.cgi?id=56242]("https://bugzilla.kernel.org/attachment.cgi?id=56242")

For a reference about how to apply one of them, look at this forum thread:
[http://ubuntuforums.org/showthread.php?p=9175201#post9175201]("http://ubuntuforums.org/showthread.php?p=9175201#post9175201")

Note1: You only have to apply one of the patches mentioned here.
Note2:  To get 2-finger-scrolling to work, you have to enable it from the mouse preferences.

---

### Post by jediayaddle on 2011-06-30
UPDATE: It decided to finally connect to a random internet connection, so I quickly enabled the driver.

> **s0ullight said:**
> To get the bcm4313 to work, I had to enable its restricted driver. (too bad b43 doesn't cover this device)

May I ask how you accomplished this? I can't get at the hardware drivers page w/o an internet connection. I've been having troubles with both my wired and wireless cards on my NF210. Without any internet, so I can't really install/update anything! Have to use my windows partition to get stuff from the internet onto my computer.

 What's funny is that my wireless can pick up networks, it just doesn't want to connect (the wireless arcs cycle through as they would normally, except the icon also flickers).

---

### Post by s0ullight on 2011-07-03
brcm80211 is included in 11.04 and works out of box, I'm having no problems with it. However, if you want to install the restricted driver there is a deb file on the install disc: pool/restricted/b/bcmwl that one should get you going :)

---

### Post by LifeBringer on 2011-08-20
Thanks for the links, found the right bug and patch.

---

