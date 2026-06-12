---
title: "Ubuntu Network Remix doesn't seem to boot from USB"
date: 2009-05-06
forum: Installation &amp; Upgrades
---

### Post by Ampi on 2009-05-06
I wrote the UNR image to a flashdrive using the dd-command. It seems to finish just fine. 
When I plug the flasdrive into my already booted laptop, it is perfectly well recognized. 
My BIOS says: FDD -> CDROM -> "don't remember"-> HDD. So the HD being the last option should make the laptop want to boot from the flashdrive. 

But when I boot the computer with the flashdrive it just boots from the HD. 

Did I do something wrong with the flashdrive or is it the laptop that is unable to boot from a flashdrive?

---

### Post by Brandon Williams on 2009-05-06
What kind of laptop do you have? Someone with the same model or brand might be able to tell you whether there's something special about getting it to boot from a USB stick. I've got a Dell mini 9, and interfacing with the bios to select alternate boot media is a bit different. 

As far as creating writing the image to the USB stick, it _should_ be the case that all you need to do is
```
$ dd if=ubuntu-9.04-netbook-remix-i386.img of=/dev/sd*X*
```
where *X* is the actual drive letter of your USB stick. I assume that's what you did.

It has been noted by Dell mini 9 users (at least) that some specific USB sticks will not work for booting the mini-9. This could be true of your laptop model, too. Have you booted your laptop off this particular USB stick before?

---

### Post by dandnsmith on 2009-05-06
On a positive note, I created the UNR 9.04 installation on a USB stick, and it worked first time off.

As to the ability of the laptop to boot from a flash drive
1. FDD is floppy disk, not Flash Drive
2. pendrivelinux.com can guide you to a test setup which will enable you to set up  a drive for simple test to see whether it works - confirmed that an older laptop couldn't boot from USB.

---

### Post by Ampi on 2009-05-06
thanks for the help. 
I did indeed do the dd-command as posted.
I have a tashoba satellite which I think is 6 years old, so not a real netbook..
I'll try to see if something is wrong with the posted link.
Let you know!

P.S. The "unknown" option is LAN. So I guess that's not the one either...

---

### Post by dandnsmith on 2009-05-07
At 6 years old, I wouldn't be at all surprised to find the facility is lacking, so you may need an alternative strategy (like having a boot CD)

---

### Post by Ampi on 2009-05-07
Yes, that is what I am thinking. The problem is that the OS I want to boot is the Ubuntu Netbook Remix that as far as I can see is only downloadable as an .img. 
I did burn this on a CD but it doesn't burn as an image because it is only an image for USB-sticks. 
I would love to be able to boot from CD, but for that I need the CD...
I've heard .img is not convertable to .iso. 
Any other options??

---

### Post by Brandon Williams on 2009-05-07
There's really nothing in the netbook remix install that you can't get from a standard install. I suggest that you download the i386 desktop iso and install from that. Then you can 'aptitude install ubuntu-netbook-remix' and 'aptitude remove ubuntu-desktop'. This will leave you with a UNR install.

There is a problem with the desktop-switcher application currently in Jaunty. After using it to switch to the UNR interface, you should run this command:
```
$ gconftool-2 --set /desktop/gnome/session/required_components_list --list-type=string ["windowmananger","panel"]
```

---

### Post by Ampi on 2009-05-07
Okay that was the best help ever! :)

Just simple and easy solution, got myself a working netbook remix :) yay!

---

### Post by patricearnal on 2009-05-18
> **Brandon Williams said:**
> There's really nothing in the netbook remix install that you can't get from a standard install. I suggest that you download the i386 desktop iso and install from that. Then you can 'aptitude install ubuntu-netbook-remix' and 'aptitude remove ubuntu-desktop'. This will leave you with a UNR install.

There is a problem with the desktop-switcher application currently in Jaunty. After using it to switch to the UNR interface, you should run this command:
```
$ gconftool-2 --set /desktop/gnome/session/required_components_list --list-type=string ["windowmananger","panel"]
```

I followed previous instructions, but the last command ends with "specify a type when setting a value".
I have now the Remix desktop embedded in a classical desktop (with the 2 tool bars at the top and bottom....)

---

### Post by Ampi on 2009-05-18
I got the exact same output, ignored it completely and I haven't found any problems yet...

---

