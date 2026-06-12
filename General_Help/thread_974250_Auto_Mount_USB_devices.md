---
title: "Auto Mount USB devices"
date: 2008-11-07
forum: General Help
---

### Post by Ellaine on 2008-11-07
I'm running 7.10 because it auto mounts all usb devices each time i put one in my system. This feature was stopped in the 8.04 & up kernel per this forum. How can I add this feature to the later kernels or a work around? I swap usb devices about 12 times a day; and am tired of putting "lsusb" in terminal every time I want to change devices. There must be a simple way to put this feature back in the kernel?

---

### Post by Therion on 2008-11-07
I have an external USB hard drive, a USB printer and a USB thumb-drive that all auto-mount at startup (assuming of course they're plugged in).  Auto-mounting of these devices has worked for me in both versions 8.04 and 8.10 so I'm not sure why you're being told auto-mounting USB devices is/was disabled in the kernel.

---

### Post by petermck on 2008-11-07
Same here. I have two machines one with 8.04 and the other with 8.10. No problems with my USB printer with multi card reader or 3 different USB memory sticks.

---

### Post by Ellaine on 2008-11-07
I will remove my 7.10 HD, install my 8.04 drive and be back in ten minutes.

---

### Post by ronz0o on 2008-11-07
The same happened to me on my laptop. On my desktop computer, it works fine though. For my laptop, if you plug a device in, it shows up in places. Just go to Places and click the drive once its plugged in. I personally like this better, because if I'm working on something, I can tell it to mount. =)

---

### Post by Ellaine on 2008-11-07
OK. I booted 8.04 with a thumbdrive installed at boot. It finds the usb drive. I then plugged another usb device and it finds it and auto mounts it. This is very different from 7.10; which doesn't require a usb device to be in at boot. I guess the way for me is to put a small thumbdrive in the back of the tower and leave it there forever so that I can install/remove usb devices and they will auto mount? I just removed both usb devices, reinstalled a thumbdrive and it is NOT found in "places" or mounted to the desktop. Not shown in My Computer either. Oh well!

Any other ideas????

---

### Post by timcredible on 2008-11-07
i've run 7.04, 7.10, 8.04, and now 8.10 on 4 different computers, and every time i've ever plugged anything in via usb, the system recognizes it and mounts it if it's a hard drive, opens a photo program if it's a camera, opens rhythmbox if it's an mp3 player, etc.  and i plug in the following routinely, and i do not have to have anything connected at boot for it to work:

many, many different flash drives
sansa mp3 player
3 different ipods
5 different cameras
xm radio pcr
wireless broadband
3 different external hard drives
many different sd and xd cards
2 different phones
psp

so, i have to say that it's probably your computer's usb ports rather than the ubuntu software.

---

### Post by Therion on 2008-11-07
I didn't mean to imply that I had to leave a USB device connected at all times for me to be able to hot-swap things like my thumb drive.  

Now, my external hard drive IS connected at all times, but I don't think it's a requirement that a USB device be connected during boot in order to hot swap USB devices (like your thumb-drive) generally speaking.  If that IS required... It's news to me!

What happens if you simply boot your PC into 8.10 with no USB devices connected and then hot-swap your thumb drive a few times?  
You're saying the drive DOESN'T auto-mount for you when you do this?  I'll bet you dollars to donuts it will.

---

### Post by Ellaine on 2008-11-07
timcredible. Auto mount usb for me has always worked in 6.10 7.04 7.10 without a usb device in at boot. It just won't mount in 8.04 or 8.10 in this system. This is using mobo usb inputs or a PCI usb card. I just rebooted to my 7.10 hd and it works perfectly. I can't see how it's my system usb ports. But I will upgrade my 7.10 (80GB HD) to 8.04 and leave a thumbdrive in at boot until I find a better solution.

---

### Post by Ellaine on 2008-11-07
Therion: I just put a thumbdrive in 8.04 10 times and it never finds it or auto mounts. I then plugged in a usb hard drive in three different usb ports & nothing found.

---

### Post by AudioPhlake on 2008-11-07
I have had no auto-mount issues with 8.04 on any of my computers, but on my laptop, I cannot mount a USB hard-drive in 8.10 that works perfectly on the same laptop with 8.04.  I have tested this by running 8.04 and 8.10 from live cd, just to make sure it wasn't an installation error.  At least one of my USB thumb drives auto-mount just fine.

---

### Post by philinux on 2008-11-07
The only regression I had was that 8.04 would not mount my camera. Had to buy a £4 card reader but 8.10 mounts it and even has a nice little camera icon.

---

### Post by Ellaine on 2008-11-07
Thanks to everyone for the help. I am going to boot 7.10, leave a small thumbdrive in the tower and upgrade to 8.04. I don't use 8.10 yet because I can't get a DVD movie to play using any player. When Stchman includes codec for VLC using in 8.10, then I may upgrade.


Thanks again!

---

### Post by AudioPhlake on 2008-11-07
I did a quick check- if I boot into kernel 8.10 2.6.27.7 generic with the USB drive attached it doesn't mount, but if I boot into 8.10 2.6.24.21 it does.  Hmmm.

---

### Post by kugel. on 2008-11-07
> **AudioPhlake said:**
> I have had no auto-mount issues with 8.04 on any of my computers, but on my laptop, I cannot mount a USB hard-drive in 8.10 that works perfectly on the same laptop with 8.04.  I have tested this by running 8.04 and 8.10 from live cd, just to make sure it wasn't an installation error.  At least one of my USB thumb drives auto-mount just fine.

I have this very problem too! Non of my mp3 players or USB sticks auto mount anymore in 8.10 on my laptop.

---

### Post by Ellaine on 2008-11-07
Some success. Third try upgrading from 7.10>8.04. My tower rear USB ports auto mount and display devices on the desktop. No such luck on the front 4 port hub. It's a powered hub connected to the mobo usb internally. Must have a usb device in the hub during boot for it to auto mount. I give up fighting; I can live with this just fine. I think this is a hardware driver problem for the hub in 8.04.

The driver listed for the 4 port front hub just says:
info.linux.driver    type: string  value:  usb
Vendor: Genesys Logic. inc

---

### Post by DLF44 on 2008-12-06
i have similar problems with my sony walkman NWZ-B105F
and a 512MB sony memory stick duo


the mp3 player shows up in places, but i can not mount it in anyway, when i click mount. nothing happens.

and my memory card reader doesnt recognize anything (its a laptop)

i do have an external hard drive and a USB stick that work though.
not sure why they do and not these.

---

### Post by Kanga on 2009-01-12
Hi,
Having just installed 8.04, I'm very suprised to find that my usb stick is not recognised.
I've put it in the front 4 port hub, and re-booted and its recognised staight away, and I can access my files. Its going to be a pain having to do it like this.
Is there a fix ?:(

---

### Post by petermck on 2009-01-12
Kanga,
Was it a clean install of 8.04 or an upgrade?

---

### Post by dionp2 on 2009-01-17
I have similar problems... See thread

USB ports not working with flash drives and external drives

---

### Post by Kanga on 2009-01-18
to Petermck:
It started off as an upgrade from Dapper, then the kids restarted the computer to XP whilst the upgrade was taking place.
I ended up with a blank screen when booting to Dapper from GRUB.
I then reinstalled Dapper from my cd, then upgraded to Heron.

---

