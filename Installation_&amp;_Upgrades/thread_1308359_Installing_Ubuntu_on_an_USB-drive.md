---
title: "Installing Ubuntu on an USB-drive"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by Gwynplaine on 2009-10-31
I'm sure this topic has been up before, but I tried the search and didn't find anyone who have experienced the same problem as I have... anyway:

I'm building a HTPC, and in order to get it as silent as possible I'm planning to install the OS on a USB-drive instead of a regular HDD. I began by trying to install XBMC live, but it didn't boot – it just stopped with a black screen. Thereafter I tried geexbox and it booted smootly, but the digital audio didn't work.

As a last attempt, I tried to install ubuntu 9.04 instead, by using an liveCD. I started the installer, choosed to install on my USB-disk and waited until everything was finished. But when I'm booting from the USB-disk the same thing happens as it did with XBMC live: I see the bootscreen (the ubuntu tex, and the square which travels horizontally back and forth), but then the screen turns black and nothing happens!

I've worked with this for over a month now, and starting to get really frustrated. Has anyone here installed ubuntu to an usb-drive and know what have turned wrong?

Setup:
Motherboard: Asus M4A785D-M
Graphic card: the internal one on the motherboard; ATI Radeon HD4200
USB-drive: SanDisk Extreme Cruzer Contour 4 GB
Monitor: A NEC-projector, connected with the VGA-cable.

Thanks in regard!

---

### Post by phillw on 2009-10-31
> **Gwynplaine said:**
> I'm sure this topic has been up before, but I tried the search and didn't find anyone who have experienced the same problem as I have... anyway:

I'm building a HTPC, and in order to get it as silent as possible I'm planning to install the OS on a USB-drive instead of a regular HDD. I began by trying to install XBMC live, but it didn't boot – it just stopped with a black screen. Thereafter I tried geexbox and it booted smootly, but the digital audio didn't work.

As a last attempt, I tried to install ubuntu 9.04 instead, by using an liveCD. I started the installer, choosed to install on my USB-disk and waited until everything was finished. But when I'm booting from the USB-disk the same thing happens as it did with XBMC live: I see the bootscreen (the ubuntu tex, and the square which travels horizontally back and forth), but then the screen turns black and nothing happens!

I've worked with this for over a month now, and starting to get really frustrated. Has anyone here installed ubuntu to an usb-drive and know what have turned wrong?

Setup:
Motherboard: Asus M4A785D-M
Graphic card: the internal one on the motherboard; ATI Radeon HD4200
USB-drive: SanDisk Extreme Cruzer Contour 4 GB
Monitor: A NEC-projector, connected with the VGA-cable.

Thanks in regard!


Hi, have u tried this set of instructions ?

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

Phill.

---

### Post by Gwynplaine on 2009-10-31
> **phillw said:**
> Hi, have u tried this set of instructions ?

[http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

Phill.

No, Ubuntu 9.10 wasn't released when I began, so I guess these instructions weren't available then. I've followed this guide: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

I'm gonna try the guide you linked to right now, thanks!

---

### Post by phillw on 2009-10-31
> **Gwynplaine said:**
> No, Ubuntu 9.10 wasn't released when I began, so I guess these instructions weren't available then. I've followed this guide: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

I'm gonna try the guide you linked to right now, thanks!


It's worth a try.. I've never done a boot usb, guess i should, just to get some practice :p

I have a spare 'fast' 2GB usb stick twiddling it's thumbs, it was the 'speed-boost' one for my Vista installation.

What the heck, I'll give it go - we can compare notes :D

I'll be using  [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

as I don't want to boot back into Vista ... other than that, we should be following the same instructions. - If I find yours doesn't work, then I'll try the windows method, however - that site is pretty darn good for instructions.

Phill.

---

### Post by Gwynplaine on 2009-10-31
> **phillw said:**
> It's worth a try.. I've never done a boot usb, guess i should, just to get some practice :p

I have a spare 'fast' 2GB usb stick twiddling it's thumbs, it was the 'speed-boost' one for my Vista installation.

What the heck, I'll give it go - we can compare notes :D

I'll be using  [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-from-cd/)

as I don't want to boot back into Vista ... other than that, we should be following the same instructions. - If I find yours doesn't work, then I'll try the windows method, however - that site is pretty darn good for instructions.

Phill.

Thanks, that worked like a charm! I didn't get the audio working though, but I'll start a new thread about that.

---

### Post by Gwynplaine on 2009-11-02
This is probably not ubuntu related, but each time I reboot the computer (or start it after turning it off) I have to remove the USB-stick and insert it again. If I don't do that it says that it isn't a proper boot disk.

---

### Post by phillw on 2009-11-02
> **Gwynplaine said:**
> This is probably not ubuntu related, but each time I reboot the computer (or start it after turning it off) I have to remove the USB-stick and insert it again. If I don't do that it says that it isn't a proper boot disk.

It possibly could be, my usb internet device has been having problems if it is plugged in on boot ... I'm going to do a bit of hunting.

Phill

Added, I've had a look round and the launchpad issues seem to have been sorted - I can't issue a new launchpad report, as none of the various options for reporting one see to apply.

Hopefully a mod will pop by and let us know how to report our, quite probably, seperate issues. It's pretty hard to track down the process ID of a misbehaving device when Ubuntu just fails to see it - You may have more suceess, as you get an error message - mine is just plain ignored as a device :-\

Do, please, get a launchpad account & follow the instructions as to what information the tech people need.

Phill

---

### Post by PRC09 on 2009-11-02
Dont know if this helps but in the bios when boot from usb is enabled it may be looking at your usb internet device for a boot sector.Had this happen today,my daughter had plugged in her ipod in the rear usb port and the machine would not boot up until it was unplugged.Took awhile to find that as I didnt know it was there........

---

### Post by phillw on 2009-11-02
> **PRC09 said:**
> Dont know if this helps but in the bios when boot from usb is enabled it may be looking at your usb internet device for a boot sector.Had this happen today,my daughter had plugged in her ipod in the rear usb port and the machine would not boot up until it was unplugged.Took awhile to find that as I didnt know it was there........

thanks, there's also this thread ... but that seems to have been a 'red-herring'

[http://ubuntuforums.org/showthread.php?t=1301350](http://ubuntuforums.org/showthread.php?t=1301350)


In my case, it just ignores the device, the OP does, at least get an error message. I haven't seen postings of 3G usb network devices mis-behaving and, as I have a pretty weird set-up, I'm not going to cal "BUG" untill I can find out something to report, other than 'it doesn't work'.

---

